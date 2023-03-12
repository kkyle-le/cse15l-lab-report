# `-curl` | Lab Report 5

## `curl -o` Copy Into File w/ Custom Name

Using `curl` with the `-o` will allow you to redirect the output into a file with your choice of name without initially making the file to be imported to, similar to using `>>`. This is useful when original filenames do not have names that can be easily organize (random letters and numbers) or for making your own personal file system that is different from what the creator of the URL had in place.

URL used: [<https://ftp.nhc.noaa.gov/atcf/pub/al092022.public.023>](https://ftp.nhc.noaa.gov/atcf/pub/al092022.public.023)

### Example 1 (Meaningful Name)
The original name of this file was "al092022.public.023" however to the public eye, it might not make sense, using the `-o` command to copy its content into a file with a recognizable name can be useful for organization.

```ssh
[cs15lwi23agv@ieng6-201]:~:526$ curl -o HurricaneIanAdvisory.txt https://ftp.nhc.noaa.gov/atcf/pub/al092022.public.023
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  8006  100  8006    0     0   2688      0  0:00:02  0:00:02 --:--:--  2688
[cs15lwi23agv@ieng6-201]:~:527$ ls
HurricaneIanAdvisory.txt  lab7  list-examples-grader  perl5
```
```
[cs15lwi23agv@ieng6-201]:~:528$ cat HurricaneIanAdvisory.txt 
ZCZC MIATCPAT4 ALL
TTAA00 KNHC DDHHMM

BULLETIN
Hurricane Ian Special Advisory Number  23
NWS National Hurricane Center Miami FL       AL092022
700 AM EDT Wed Sep 28 2022

...RAPIDLY INTENSIFYING IAN FORECAST TO CAUSE CATASTROPHIC
STORM SURGE, WINDS, AND FLOODING IN THE FLORIDA PENINSULA...
[ . . . ]
```
(Output has been chopped at `[ . . . ]` to reduce length of this blog post, full advisory from link above was printed when `cat` command was called)

### Example 2 (Own File System)
The name original file name, "al092022.public.023", can be broken down to:

`al = Atlantic Basin, 09 = 9th Hurricane (Ian), 2022 = Current Year, public.023 = Public Advisory #23 for This Storm System`

However to another person, they may want to use a different filing system, so using `-o` to rename a file to abide by their filing rules can come in handy such that, instead of being organized by basin first (Atlantic, Eastern Pacific, Western Pacific), it is organized by year first. (2022_ATL-Ian)

```
[cs15lwi23agv@ieng6-201]:~:529$ curl -o 2022_ATL-Ian.txt https://ftp.nhc.noaa.gov/atcf/pub/al092022.public.023
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  8006  100  8006    0     0  13512      0 --:--:-- --:--:-- --:--:-- 13523
[cs15lwi23agv@ieng6-201]:~:530$ ls
2022_ATL-Ian.txt  HurricaneIanAdvisory.txt  lab7  list-examples-grader  perl5
[cs15lwi23agv@ieng6-201]:~:531$ cat 2022_ATL-Ian.txt 
ZCZC MIATCPAT4 ALL
TTAA00 KNHC DDHHMM

BULLETIN
Hurricane Ian Special Advisory Number  23
NWS National Hurricane Center Miami FL       AL092022
700 AM EDT Wed Sep 28 2022

...RAPIDLY INTENSIFYING IAN FORECAST TO CAUSE CATASTROPHIC
STORM SURGE, WINDS, AND FLOODING IN THE FLORIDA PENINSULA...
```
(Output has been chopped at `[ . . . ]` to reduce length of this blog post, full advisory from link above was printed when `cat` command was called)


## `curl -O` Copy Into File Using Existing Name

### Example 1 (Fast Search w/ Known Directory)
### Example 2 (Fast Search w/o Known Directory)


## `curl -r` Copy Specific Range

### Example 1 (No exact match)
### Example 2 (Exact match found)


## `curl -`

### Example 1 (Flexibility)
### Example 2 (Scope Compared to `-i`)


# Source Used:
## [<https://curl.se/docs/manpage.html>](https://curl.se/docs/manpage.html)
## [<https://www.geeksforgeeks.org/curl-command-in-linux-with-examples/>](https://www.geeksforgeeks.org/curl-command-in-linux-with-examples/)
