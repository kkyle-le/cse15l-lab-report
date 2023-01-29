# StringServer.java Code | Part 1 #
``` java
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler {
    ArrayList<String> library = new ArrayList<String>();

    public String handleRequest(URI url) {

        if (url.getPath().equals("/")) {
            return toString(library);

        } else if (url.getPath().contains("/add-message")) {

            String[] parameters = url.getQuery().split("=");

            if (parameters[0].equals("s")) {
                library.add(parameters[1]);

                return toString(library);
            }

        }

        return "404 Not Found!";
            
    }

    public static String toString(ArrayList<String> library) {
        String listStrings = "";

        for(int i = 0; i < library.size(); i++) {
            listStrings += library.get(i) + "\n";
        }
        return listStrings;
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```

# Screenshots and Responses #

After creating a new server and visiting the fresh link, there should be nothing displayed as expected since no methods have been called.

![image](https://user-images.githubusercontent.com/122570961/215349061-ea25266c-9c97-490b-adc6-ae154fad8c62.png)

## /add-message

These two screenshots demonstrates the usage of the /add-message feature.

(**1**)
![image](https://user-images.githubusercontent.com/122570961/215349084-fd294cff-caf6-454f-808a-fcb070bfdde5.png)

(**2**)
![image](https://user-images.githubusercontent.com/122570961/215349115-8e8c6590-1259-4523-9e66-0047738ddb4d.png)

From surface level analysis, it appears that the written code is functioning correctly and returning the expected output. Further testing of different URL paths is needed to ensure that the code is functional for all conceivable inputs.

In screenshot (1), the arrayList *library* is initially empty, but with the entered path "/add-message?s=Hello!" it invokes the two methods; handleRequest and toString. This results in the webpage reloading and displaying the input "Hello!".

Scrrenshot (2) also invokes the same two methods but this time, *library* now contains the element "Hello!" from the prvious entry. This results in toString printing out "Hello!" and "Goodbye!" both on new lines using "\n".



Deeper look into the two called methods.
### method handlerRequest(URI url) ###
This method has one specific argument which is url. This is the url passed by the user in the search bar associated with the webserver that runs other methods. The method splits the url into specific part, the path (`url.getPath()`) and the query (`url.getQuery()`).

The path portion of the URL determines the functionality of the entered URL, either to display the *library* (path --> / or empty), or to add an entry into *librry* and display its contents (path --> /add-message).

The query is comes into play if the latter is the path in the URL, which determines what is added into *library* (i.e /add-message?s=NO! --> "NO!" is added)

The method as a whole breaks and throws an exception when anything other than a URL/URI is passed through as the method relies on a set standard on how URLs are formatted and is unable to pass through any random number or strings. Methods such as `getPath` and `getQuery` are also bounded to the URI class therefore if any classes are not of that class or are not a subclass of it, the inputs will not have access to its implementation.

### method toString(String[] library) ###

This method is a helper method as it allows for the code to me condensed down and assists with the main functionality of `handlerRequest`. It takes in a String array and outputs it in the correct format to be displayed on the webserver. 

---

It is expected that all inputs after the ?s= should be able to be displayed on the page, as they are all typecasted into a String object as seen in the code line below. 

` String[] parameters = url.getQuery().split("="); `

This expectation is foritfied when 123 is passed through. Even though it is an int, it is typecasted into a string and therefore is printed correctly after the two previous entries.

![image](https://user-images.githubusercontent.com/122570961/215349824-77e070a7-a64f-4903-93a3-683e6b6bced3.png)

# Testing and Debugging | Part 2 #

In Lab 3, I focused on the array method: `averageWithoutLowest(double[] arr)`

### A failure inducing bug input that was found was ###
```java
@Test
  public void testAverageWithoutLowest() {
    double[] doubleRepeating = {2.0, 2.0, 2.0, 2.0, 3.0};
    assertEquals(3.0, ArrayExamples.testAverageWithoutLowest(doubleRepeating), 0);
  } 
```

### An input that did not demonstrate the bug was ###
```java
@Test
  public void testAverageWithoutLowest() {
    double[] doubleList = {1.0, 2.0, 3.0, 5.0};
    assertEquals(10.0/3.0, ArrayExamples.testAverageWithoutLowest(doubleList), 0);
  } 
```

### Symptom | The test running (combined the two tests) ###
![image](https://user-images.githubusercontent.com/122570961/215352375-a7f4d3e2-3567-442a-ac36-854cc2a980da.png)

### Bug | Fixing the Code ###

*Please note that the expected implementation of this method was not clear nor was it explained in lab when personally questioned. I took the route with the assumption that the implementation of this method removes ALL occurences of the lowest value. If the method was to only remove the first occurence of the lowest value, the implementation will be different.*

### Original Code ###
``` java
  static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - 1);
  }
  ```
  
### Debugged Code ###
  
I added a number counter `numOcc` for the number of times the lowest vaue occures within a given array. This is then subtracted from the total length of the array. The original code had it where the code assumed that the lowest value will only appear once in the array, and therefore only subtracted 1 from the array length. This resulted in the mean calculation being incorrect as the denominator did not reflect how many values were being summed in the mean.
  ```java
    static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    int numOcc = 0;
    for(double num: arr) {
      if(num <= lowest) { 
        lowest = num; 
        numOcc++;

      }
    }

    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - numOcc);
  }
  ```
  
# Reflection Part 3 #
  
Coming out of both Lab 2 and 3, I learned the importance of testing ones code to full correctness. Lab 3 was the main focuse of this lesson as it made me create thorough testers to check for any and all possible inputs that might return something that was not expected. While Lab 2 did not have testign as its primary task, it allowed me to apply the skills learned in Lab 3 into actual use as I had to think of unusual inputs to ensure my code works as expected. It is important that the code is fully correct up to my limited knowledge as these two labs helped enforce this habit of code testing.
