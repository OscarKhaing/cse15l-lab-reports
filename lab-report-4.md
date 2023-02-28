## Hi all! On this page, you will find a detailed step-by-step walk-through of the keys I pressed to complete the competition task from Week 7 Lab. 

---

For this guide, I will separate the 6 steps into different sections of this page as they are numbered (steps 4 to 9). Here is the original list for your reference:

1. **Setup Delete any existing forks of the repository you have on your account**
2. **Setup Fork the repository**
3. **The real deal Start the timer!**
4. Log into ieng6
5. Clone your fork of the repository from your Github account
6. Run the tests, demonstrating that they fail
7. Edit the code file to fix the failing test
8. Run the tests, demonstrating that they now succeed
9. Commit and push the resulting change to your Github account

The first 3 highlighted steps are skipped, so we actually start from step 4. Just to avoid confusion, **I will keep the original step number**, so the title of the sections will start from step 4. 

Meanwhile, we will start with the terminal already open and ready to receive input. At the beginning, I will be using the _bash_ terminal, though it doesn't really matter once we log into the **ieng6** secure-shell.

> The keys pressed will be listed as they are pressed exactly, and special characters like `<shift>` will be highlighted using the code format and angle brackets, as shown. Commands that are done on different lines will be separated by commas. 

# Step 4: Log into ieng6

_Keys pressed:_ 
ssh `<space>` cs15lwi23aki `<shift-2>` ieng6.ucsd.edu `<enter>`

[Here, I typed my password] `<enter>`

![image](https://user-images.githubusercontent.com/117701031/221756185-4fdfcfab-1d8b-4ec6-b575-891c4beb9230.png)
![image](https://user-images.githubusercontent.com/117701031/221756670-8e0ede99-2a23-4ebb-a1fb-4e19517e84d2.png)

In this sequence, I logged into my **ieng6** secure-shell. 

The only notable special-character I pressed was `<shift>`, which was to type the `@` symbol. It should be noted that I held the `<shift>` key while I pressed `2`, then released it afterwards.

# Step 5: Clone your fork of the repository from your Github account

_Keys pressed:_
git `<space>` clone `<space> <alt-tab> <ctrl-L> <ctrl-c> <alt-tab> <ctrl-v> <enter>`, ls `<enter>`

Note: "L" is capital to avoid confusion because its lower-case looks like "I" 

![image](https://user-images.githubusercontent.com/117701031/221757395-9b582b10-53dc-46f0-b11b-2c04ec7ebe80.png)

In this sequence, I cloned my forked repository from Github using the link URL of my forked repository, and I have my forked repository opened in Chrome on my local machine. 

After the word "clone ", I `<alt-tab>` to switch to my browser, `<ctrl-L>` to select the URL, `<ctrl-c>` to copy, `<alt-tab>` to switch back into VS Code, and `<ctrl-v>` to paste the URL. Then, I clicked `<enter>` to start the cloning. Then, I listed the contents of the current working directory using `ls` to see confirm that the cloned repository is there.






# Step 6: Run the tests, demonstrating that they fail
_Keys pressed:_
cd `<space>` lab7 `<enter>`, ls `<enter>`, `<alt-tab> <mouse-button-1-click> <ctrl-c> <alt-tab> <ctrl-v> <enter>`, `<alt-tab> <mouse-button-1-click> <ctrl-c> <alt-tab> <ctrl-v> <ctrl-backspace>` ListExamplesTests.java <enter>`

![image](https://user-images.githubusercontent.com/117701031/221759781-c1d7ac85-3940-4040-bc3b-1736aa7ccdaa.png)

![image](https://user-images.githubusercontent.com/117701031/221759612-301a7056-7ffe-4432-b62b-c1db7078715c.png)

In this sequence, I first changed directory into the **`lab7`** diretory to access the cloned files, listed the contents of **`lab7`** to look at the name of the files, then switched to the browser that has the **week 3** lab page open so that I can copy the `compile` command. The `<mouse-button-1-click>` was to select the command I wanted to copy.

```
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ArrayTests
```

After copying and pasting the second line, I used `<ctrl-backspace>` to delete the file name from week 3 and replace it with the name of the file we are running.
  
> You may wonder why the code line number went from 166 to 168. The reason for this anomaly is that I copied over the wrong compile command (for windows) on Line 167, which didn't work because we are in a linux shell.


# Step 7: Edit the code file to fix the failing test
_Keys pressed:_




