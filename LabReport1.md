# Lab Report 1
# Installing Visual Studio Code (VSC)
Go to <https://code.visualstudio.com/> and follow the instructions for installing Visual Studio Code onto your specific device. Open it once done, it should look something like the image below. **Note: I have previously used VSC before, therefore there are already items loaded, but the basic window layout should look similar**
![image](https://user-images.githubusercontent.com/122570961/212625408-ffe656cb-527e-474d-b2c7-98d7e7ad7e2d.png)



# Github Installation and the Git Bash Terminal
Then go to <https://www.github.com> and follow the instructions for installing Github. This will be used to transfer code and files onto the remote computer. Once completed, go back to the VSC window and in the top left click Terminal > New Terminal.
![image](https://user-images.githubusercontent.com/122570961/212626230-ec721f39-71e3-4c89-9e67-1eee8d6856fc.png)

This should now appear at the bottom of the window.
![image](https://user-images.githubusercontent.com/122570961/212626592-33672aae-96b0-4f48-aed6-63a440973ec2.png)



Within this section next to "powershell" on the right, click the bottom arrow which will bring up a list, then click "Git bash". This will open up a terminal to run specific commands to connect to the remote computer.

![image](https://user-images.githubusercontent.com/122570961/212626830-c32aeb08-50af-41fe-937b-fa5cc24c55ef.png)

# Accessing the Remote Computer

Within this new Git bash terminal, you will need to paste the following line of code:
`$ ssh cs15lwi23zz@ieng6.ucsd.edu`

**important notes**
- The $ is to be omitted, this is the first default character added in by the terminal itself, start at ssh
- Replace "zz" with your CSE15L specific letters connected to your account. To know what these letters are, go to https://sdacs.ucsd.edu/cgi-bin/alloc-query and follow the steps to retreving your account username. The letters succeed cs15lwi23 and preceed @ieng6.ucsd.

Once pasted in, press enter. A yes/no question should prompt up in the terminal, type in "yes" and press enter once more. You will then recieve the password prompt. It should look like this:
![image](https://user-images.githubusercontent.com/122570961/212628803-41ee2273-e0cd-4917-84e6-f37142ff80b7.png)

*The yes/no question from the previous step has been omitted, it usually only pops up for users first accessing their account*

Now, type in the password associated wth your cs15lwi23 account and press enter. If you do not know the password, you can reset it at <https://sdacs.ucsd.edu/cgi-bin/alloc-query> but please allow 15 minutes to pass before attempting to acces the remote computer after resetting.

**IMPORTANT: YOU WILL NOT SEE WHAT YOU ARE TYPING WHEN ENTERING YOUR PASSWORD IN THE TERMINAL. THIS IS A SAFETY FEATURE.**

If entered successfully, the terminal should now show this. You have now accessed the remote computer!
![image](https://user-images.githubusercontent.com/122570961/212629998-50a4e210-207c-4c5b-90ec-631178efb122.png)

# Running Commands

It's time to test out the remote computer! Since this remote computer is not housed on the device you are using, the files it contains (and potentially the OS itself as it is running Linux) will be different. So it's best to run commands handing files to visually see differnces in your current device and the remote computer.

## Commands
- `pwd`
- `cp`
- `ls`
- `cd`
- `ls -lat`
- `ls -a`
- `ls /home/linux/ieng6/cs15lwi23/cs15lwi23abc` (replace "abc" with your account letters)
- `cat /home/linux/ieng6/cs15lwi23/public/hello.txt`


Here are what some commands ran through the terminal could output (slightly different for each account)
![image](https://user-images.githubusercontent.com/122570961/212632165-7de891b6-0431-41b9-88cf-afacf2b8047b.png)

The commands I used in the particular screen shot above were `ls -a` and `ls -lat`. They are extremely useful as they are the like the file explorer on the local computer (for a windows OS). I usually gravitate towards using `ls -lat` over the other as it shows files in a vertical view from newest to oldest which makes it easier to find files recently copied from the local computer to the remote computer. 

# Exiting the Remote Terminal

To exit, you can either Ctrl-D or run the command `exit`.

The following lines will appear and you will now be back in a terminal connected to your current computer. You can also now try the same commands above and see the differences.

```
logout
Connection to ieng6.ucsd.edu closed.
```



