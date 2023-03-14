## Hi all! On this page, you will find a guide for 4 different command-line options for the `find` command in _bash_, each with 2 detailed examples for clarity.

---
## What is "find"?

Linux has been a popular choice of operating system due to its inherent stability. When operating in a linux shell, users must manipulate files through a terminal using a variety of commands. 

One of those commands is `find`, which is used for "finding" files. It will return the path of the file that we are finding.

> This guide is very similar to _lab-report-3_ in format and will focus on **4** of the command line options for the command `find`. 
> The reason why I chose find is because I felt a bit illiterate in using `find`, and learning it will help me in the final performance task.

To use it, we use the following syntax format:

```
find [OPTION] [PATH...] [EXPRESSION]
```

> It should be noted that some parts of the syntax format ([-Olevel], [-D debugopts]) have been left out as they are irrelevant to our discussion on **"options"**.

* **`[OPTION]`** are modifiers to limit or specify conditions for the operation (which we'll look at today)
* **`[PATH]`** is the directory that you want `find` to search in, recursively. 
* **[EXPRESSION]** must be the name(s) of the file(s) in which you want to search for the pattern 

> General tip for _bash_:
> When using a command you are not familiar with, you can use
> `[whatever-command-you-use] --help`
> to ask _bash_ to print a guide for the command, as seen below.

![image](https://user-images.githubusercontent.com/117701031/224870689-b1766aa0-227f-42cb-bba2-423e8a25a3e4.png)

## Setting it up

Let's first set up the environment. For this demonstration, I will be using the data set from the **CSE15L Skill Demo 1** that I cloned and stored on my local machine, and I will be operating using _Bash_ terminal, as seen below. 

![image](https://user-images.githubusercontent.com/117701031/220243639-21a262e5-d2b9-48b9-8dfb-5d97602e16c6.png)

Our operations will mainly be done on this `written_2/` directory.

# Option 1: find -type

An option we will look at is '-type'. This is selected through the github repo [https://math2001.github.io/article/bashs-find-command/](https://math2001.github.io/article/bashs-find-command/)

















