## Hi all! On this page, you will find a step-by-step guide on how to log into a course-specific account on the **ieng6** domain.

---


# 1. Installing VScode
Firstly, we need a terminal to work with. For this, I like to use VS Code because it has a very friendly interface. The computer I worked with on the lab day already had it installed. After having it on your computer, launch it; it should look something like this when it opens:


![Image](https://github.com/OscarKhaing/cse15l-lab-reports/blob/main/vscode.JPG?raw=true)


Go to the top left corner menu, click on *Terminal*, and click on *New Terminal*. It would open a terminal window for you. By default, it will be on Windows Powershell, but you want to work with Bash instead. To switch, click on the arrow beside the *+* sign at bottom right, and click on Bash. It should look something like a dollar sign, $

And there you have your functional command line for the Linux operations we will do.




# 2. Remotely Connecting
## 1. Find your account on the following webpage
[https://sdacs.ucsd.edu/~icc/index.php](https://sdacs.ucsd.edu/~icc/index.php)
![Image](https://github.com/OscarKhaing/cse15l-lab-reports/blob/main/1-account-search.JPG)


Under “Username,” input your Active Directory account (i.e. your UC San Diego email address without the domain name, i.e. all the characters before ‘@’ in your email). 

```
For example, if your email is:
[*famousperson*@ucsd.edu]
You would put “*famousperson*” into Username box
```
Under “Student ID,” simply enter the 9 digit UCSD PID (including the ‘A’ at the beginning) you were assigned.

Click “Submit” to search query.

## 2. Initialize password

If you’re logging in for the first time, click “change your password” to initialize a passphrase that you will use to log into your account on command line later. A thing to note is that after you finish typing in your new password a second time, click *Enter* on your keyboard directly. Clicking on *Check Password* will only erase what you typed.
![Image](https://github.com/OscarKhaing/cse15l-lab-reports/blob/main/2-account-search.JPG)


After setting your password, it takes about 15 minutes or longer for the server to update. Then, you can begin logging into the Linux shell via the command line.

## 3. Logging in
Open a new Bash terminal in VS Code, and type in the following line, but replace [youraccount] with your account.
```
$ ssh [youraccount]@ieng6.ucsd.edu
```
Then, enter the password you set in step 2. It is intentional that the password you are typing in does not show up on the screen; this way, no one else can see it.


Wait for it to connect. It might take anywhere between 5 seconds to 5 minutes. It should look something like below after it finishes connecting.

![image](https://user-images.githubusercontent.com/117701031/212815644-65b276b8-9747-4a28-904e-1078b533b425.png)


# 3. Trying some commands
You are free to try out some commands as you'd like! Play around with creating and deleting files, editing them, and more!
Some common commands you can try are:
* cd ~
* cd
* ls 
* ls <directory> 
* echo
* rm
  
You can see my attempt at playing around with the shell below (I did not know what I was doing):
  
![image](https://user-images.githubusercontent.com/117701031/212816385-485910ff-c5c0-4020-82f3-b2d9bf390bdb.png)

# Logging out
To log out, you can use ```Ctrl+D``` or ```exit```

Hope you had fun in this tutorial!
