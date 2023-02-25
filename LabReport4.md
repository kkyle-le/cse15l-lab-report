(Steps 1-3 completed off screen. Keys in quotes are simple typing)
# 4. Logging into ieng6
## Keys: `<up><enter>`
![image](https://user-images.githubusercontent.com/122570961/221375774-f06f7710-db74-416a-b45f-0dd2dd0317fc.png)
  
  I was able to skip manually typing in the ssh [username] command since the typed command (which was the most recent command on the local computer's scope) was already in my command history, so pressing the up key retrieved that command and I was able to enter immediately. To log in usually required a password but this computer that the lab is being tested on already has a ssh_key attached to the ieng6 account therefore it recognizes that this is an authorized computer and does not require a password to log in, saving me from manually typing in the password.
 
 # 5. Cloning repository
 ## Keys: `"git clone "<left click><enter>"cd l"<tab><enter>`
![image](https://user-images.githubusercontent.com/122570961/221376209-1f02fcc3-c9de-4e70-95d9-a7a9ceda811b.png)
![image](https://user-images.githubusercontent.com/122570961/221376509-28833b9a-9d2a-4c05-83e0-d71c07c71c04.png)
  
  There is no other *reasonable* shortcut to type "git clone" that would save time beyond just typing "git clone ". I already had the ssh url (`git@github.com:kkyle-le/lab7.git`) for the forked repository to clone, therefore a simple left-click will paste what has been copied to my clipboard. Pressing enter will run the command. I quickly changed diretory to lab7/ through typing it out. I did not need to type the whole directory name out as since it is the only directory starting with the character "l", I could press the tab key and it will autofill in the rest of the `lab7/` directory.
  
 # 6. Run the tests, demonstrating that they fail
 ## Keys: `<Ctrl-R> "javac" <enter><Ctrl-R> "java " <enter>`
![image](https://user-images.githubusercontent.com/122570961/221376554-c9a8f3ca-1f84-4a81-8f48-232904eccd22.png)
![image](https://user-images.githubusercontent.com/122570961/221376626-9fe2be07-8c5a-47a5-bcfd-64ee8a6c5a31.png)
![image](https://user-images.githubusercontent.com/122570961/221376638-d7bf180e-9caf-4f0e-86bc-4b7ea1c7abcb.png)
 
 The first approach when it came to mind was using the up keys to find the respective `javac` and `java` commands but that would have resulted in me pressing the key more than 15+ times. Therefore a more efficient approach would be to use the `Ctrl-r` keybind to search through my cmd history using a keyword. Using the keyword "javac " gave me the whole javac command for JUnit while doing "java " gave me the java run command. It is important to include the space in the "java" keyword as it will only give you the run commands rather than the compile commands. Hitting enter after finding the command will run the command.
 
 # 7. Edit the code file to fix the failing test
 ## Keys (Open in terminal editor): `"nano " "L" <tab> "." "j" <tab><enter>`
![image](https://user-images.githubusercontent.com/122570961/221376921-7c8eb79f-23a2-43df-a124-16b69acd623b.png)
![image](https://user-images.githubusercontent.com/122570961/221376935-e1b4c1b7-836d-43f8-8bf2-e46a6606e56c.png)

 To open the in-terminal file editor, typing in "nano" then the file name you want to edit will do the job. Using tab auto complete can make it faster to open up nano as you don't have to type the whole filename out.
 
 ## Keys (Editing): `<Ctrl-W> "return" <enter><up><up><right><right><right><right><right><right><right> "2" <backspace>`
![image](https://user-images.githubusercontent.com/122570961/221377119-3168ee36-017b-444e-8b49-2873d0744073.png)

![image](https://user-images.githubusercontent.com/122570961/221377124-9dda8472-95a8-4c17-a9fa-9f305e7599a0.png)

It is possibe to brute force and move the cursor down all the way to the position where you want but that will be too inefficient. Since I see where the error in the code is, I can use the `Ctrl-W` function to find a unique keyword to get there as quick as possible. Since the line of error is near the return statement, I used the keyword "return" to get there as soon as possible. Not using unique keywords may result in your cursor being moved to the first occurance rather than the position you want to be at. Now that the cursor is near the place I want to be, I will manually go to the position I want (using less keys) and edit the code to fix the program (fixing the infinite loop).

## Keys (Saving): `<Ctrl-O><enter><Ctrl-X>`
![image](https://user-images.githubusercontent.com/122570961/221377147-99fddd16-a2eb-4a13-9334-1b6a46941433.png)

The bottom section is a legend of commands, pretty straight forward using the saving and exiting commnads. After doing the `Ctrl-O` command, it will confirm that the file has been saved.

# 8. Re-Running tests, successful now
## Keys: `<up><up><enter><up><up><up><enter>`
![image](https://user-images.githubusercontent.com/122570961/221377349-449c239d-1526-4de7-afcb-a7ed7c1cacfb.png)
  
 The same procedure for the compile and run commands as step 6. However since I recently ran those commands, I can use just the up keys to scroll through my history to get these respective commands as they only need 2-4 key pressess to access them compared to the original 15+ key presses.

# 9. Committing and Pushing
## Keys (Add): `"git add " <tab> "." "j" <tab><enter>`
![image](https://user-images.githubusercontent.com/122570961/221377485-3473a512-67a4-4312-b8b3-1d6edbcc0290.png)

To add the changes in the updated file to the committed files to be pushed, running the "git add" command followed by the filename will do. Again, using the tab autocomplete will speed the process up faster as you do not need to input the entire filename (ListExamples.java)

## Keys (Commit): `"git commit -m "yay done w lab!"<enter>`
![image](https://user-images.githubusercontent.com/122570961/221377496-40f52952-55d2-40a1-be9e-4c601f611385.png)

Command to commit, important to include a message! It will not allow you to go through with committing without a commit message.

## Keys (Push): `"git push"<enter>`
![image](https://user-images.githubusercontent.com/122570961/221379900-8029b1ca-05ad-4a0b-9611-d23c0c4e6009.png)
![image](https://user-images.githubusercontent.com/122570961/221377468-0601cfb1-264d-46c8-87a0-137fa0b04ef8.png)

Last simple command, `git push` will push all files to the repository, as seen in the screenshot it was sucessful since we can see the message inputted in the commit command.
