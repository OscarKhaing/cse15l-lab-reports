## Hi all! On this page, you will find a guide for 4 different command-line options for the `find` command in _bash_, each with 2 detailed examples for clarity.

---
## What is "find"?

Linux has been a popular choice of operating system due to its inherent stability. When operating in a linux shell, users must manipulate files through a terminal using a variety of commands. 

One of those commands is `find`, which is used for "finding" files. It will return the relative path of the file that we are finding.

> This guide is very similar to _lab-report-3_ in format and will focus on **4** of the command line options for the command `find`. 
> The reason why I chose find is because I felt a bit illiterate in using `find`, and learning it will help me in the final performance task.

To use it, we use the following syntax format:

```
find [PATH...] [EXPRESSION]
```

> It should be noted that some parts of the syntax format ([-Olevel], [-D debugopts]) have been left out as they are irrelevant to our discussion on **"options"**, or in the case of `find`, **"expressions"**.

* **`[PATH]`** is the directory that you want `find` to search in, recursively. 
* **[EXPRESSION]** is the "option" modifier that we are going to look at today. 

**_Note:_** _"option" and "expression" will be used interchangeably hereinafter._

> General tip for _bash_:
> When using a command you are not familiar with, you can use
> `[whatever-command-you-use] --help`
> to ask _bash_ to print a guide for the command, as seen below.

![image](https://user-images.githubusercontent.com/117701031/224870689-b1766aa0-227f-42cb-bba2-423e8a25a3e4.png)

## Setting it up

Let's first set up the environment. For this demonstration, I will be using the data set from the **CSE15L Skill Demo 1** that I cloned and stored on my local machine, and I will be operating using _Bash_ terminal, as seen below. 

![image](https://user-images.githubusercontent.com/117701031/220243639-21a262e5-d2b9-48b9-8dfb-5d97602e16c6.png)

Our operations will mainly be done on this `written_2/` directory.

# Option 1: -type 

An option we will look at is '-type'. This is selected through the github repo [https://math2001.github.io/article/bashs-find-command/](https://math2001.github.io/article/bashs-find-command/).

By default, `find`, without any options or other arguments, returns both files and directories recursively in the current working directory.

```
$ find
.
./non-fiction
./non-fiction/OUP
./non-fiction/OUP/Abernathy
./non-fiction/OUP/Abernathy/ch1.txt
./non-fiction/OUP/Abernathy/ch14.txt
./non-fiction/OUP/Abernathy/ch15.txt
./non-fiction/OUP/Abernathy/ch2.txt
./non-fiction/OUP/Abernathy/ch3.txt
./non-fiction/OUP/Abernathy/ch6.txt
./non-fiction/OUP/Abernathy/ch7.txt
./non-fiction/OUP/Abernathy/ch8.txt
./non-fiction/OUP/Abernathy/ch9.txt
./non-fiction/OUP/Berk
./non-fiction/OUP/Berk/ch1.txt
./non-fiction/OUP/Berk/ch2.txt
./non-fiction/OUP/Berk/CH4.txt
./non-fiction/OUP/Berk/ch7.txt
```
_(long list, omitted)_

As you can see, it returns all of _non-fiction_, _OUP_, and _Abernathy_, which are directories, and assorted `.txt` files, which are files.

But as you know, _bash_ differentiates very distinctly between files and directories, and especially with other commands like 'grep' that we talked about in lab report 3. So we do actually have the `-type` option to conveniently single out either files or directories using the following code:

```
find -type [type input]
```

## Example 1: 

Let's first look at an example for `-type f`. It tells the `find` command that we only want to output found "things" if they are of type `f`, which stands for files, so it returns only files.

```
$ find -type f
./non-fiction/OUP/Abernathy/ch1.txt
./non-fiction/OUP/Abernathy/ch14.txt
./non-fiction/OUP/Abernathy/ch15.txt
./non-fiction/OUP/Abernathy/ch2.txt
./non-fiction/OUP/Abernathy/ch3.txt
./non-fiction/OUP/Abernathy/ch6.txt
./non-fiction/OUP/Abernathy/ch7.txt
./non-fiction/OUP/Abernathy/ch8.txt
./non-fiction/OUP/Abernathy/ch9.txt
./non-fiction/OUP/Berk/ch1.txt
./non-fiction/OUP/Berk/ch2.txt
./non-fiction/OUP/Berk/CH4.txt
./non-fiction/OUP/Berk/ch7.txt
```
_(long list, omitted)_


As you can see, the directories are no longer in the output of the list of found "things". 

In contrast with the previous call, this time, directories like _non-fiction_ are not there.

## Example 2:

For the second example, we will see output for `-type d`. It tells the `find` command that we only want to ouput found "things" if they are of type `d`, which stands for directories, so it returns only directories.

```
$ find -type d
.
./non-fiction
./non-fiction/OUP
./non-fiction/OUP/Abernathy
./non-fiction/OUP/Berk
./non-fiction/OUP/Castro
./non-fiction/OUP/Fletcher
./non-fiction/OUP/Kauffman
./non-fiction/OUP/Rybczynski
./travel_guides
./travel_guides/berlitz1
./travel_guides/berlitz2
```

As you can see, the long list of files are not included; there are only directories in the output. 

This is extremely helpful to have, since we can redirect the output all the file names/paths and use it as a list to bulk modify the files for some other purposes. 



# Option 2: -name 

Another option we will look at today is `-name`. This is selected through the github repo [https://math2001.github.io/article/bashs-find-command/](https://math2001.github.io/article/bashs-find-command/).

This will help us differentiate between different files with their names and further specify the file we want. The syntax is as follows:

```
find -name [name input]
```

## Example 1:

For the first example, we will see the output for `find -name "berlitz2"`, which specifies the name of folder **"berlitz2"**.

> The name input following "`-name`" must be enclosed in quotation marks `" "`. 

```
$ find -name "berlitz2"
./travel_guides/berlitz2
```

`find` thus returns the relative path of the directory called **"berlitz2"**, which is exactly what we wanted.

## Example 2:

For the second example, let's take a look at the output of `find -name "*.txt"`; this tells find to return all files with **".txt"** in their name, which is specified through the character **"*"**.

```
$ find -name "*.txt"
./non-fiction/OUP/Abernathy/ch1.txt
./non-fiction/OUP/Abernathy/ch14.txt
./non-fiction/OUP/Abernathy/ch15.txt
./non-fiction/OUP/Abernathy/ch2.txt
./non-fiction/OUP/Abernathy/ch3.txt
./non-fiction/OUP/Abernathy/ch6.txt
./non-fiction/OUP/Abernathy/ch7.txt
./non-fiction/OUP/Abernathy/ch8.txt
./non-fiction/OUP/Abernathy/ch9.txt
./non-fiction/OUP/Berk/ch1.txt
./non-fiction/OUP/Berk/ch2.txt
./non-fiction/OUP/Berk/CH4.txt
./non-fiction/OUP/Berk/ch7.txt
```
_(long list, omitted)_

It evidently worked. Only relative paths of `.txt` files are returned

> Note that this is the same output as `find -type f` because only .txt files exist in this data bank; if there were files with other extensions like `.jpg`, it would not be included with the output.

This can be used to further filter the files you want to single out; for example, if you are organizing a folder containing videos and photos, you can single out file paths of `.jpg` and `.mp4` files separately.


# Option 3: -maxdepth

The third option we will look at is `-maxdepth`. This is selected through the github repo [https://math2001.github.io/article/bashs-find-command/](https://math2001.github.io/article/bashs-find-command/).

As its name suggests, `-maxdepth` basically tells the find the only recursively find "things" in subdirectories that are in only specified levels under the current working directory.


For your reference, below is the directory structure of the current working directory `written_2/`:

```
.
├── non-fiction
│   └── OUP
│      ├── Abernathy
│      ├── Berk
│      ├── Castro
│      ├── Fletcher
│      ├── Kauffman
│      └── Rybczynski
└── travel_guides
    ├── berlitz1
    └── berlitz2
```
![image](https://user-images.githubusercontent.com/117701031/224883307-a0b581ec-1730-4344-aae2-ad78094501e0.png)


The syntax for this command looks like this:

```
find -maxdepth [depth input]
```


