## Hi all! On this page, you will find a guide for 4 different command-line options for the `grep` command in _bash_, each with 2 detailed examples for clarity.
---
## First, what is `grep`?
Linux has been a popular choice of operating system due to its inherent stability. When operating in a linux shell, users must manipulate files through a terminal using a variety of commands. 

One of those commands is `grep`, which is used for finding patterns within files. It will return the line in the file that contains the specified pattern.
> `grep` stands for "Global regular expression print"

To use it, we use the following syntax format:

```
grep [OPTION]... PATTERN [FILE]...
```

* **`[OPTION]`** will be one of the things we look at today.
* **`PATTERN`** is the pattern you are looking for, which must be in single quotation marks
* **[FILE]** must be the name(s) of the file(s) in which you want to search for the pattern 

There can be multiple command-line arguments for **`option`** and **`file`**, as indicated by the ellipsis "..." 

> General tip for _bash_:
> When using a command you are not familiar with, you can use
> `[whatever-command-you-use] --help`
> to ask _bash_ to print a guide for the command, as seen below.


![image](https://user-images.githubusercontent.com/117701031/220244234-157e1ad9-7e0d-42b0-b8fe-6147db0a9bb5.png)




## Setting it up
Let's first set up the environment. For this demonstration, I will be using the data set from the **CSE15L Skill Demo 1** that I cloned and stored on my local machine, and I will be operating using _Bash_ terminal, as seen below. 

![image](https://user-images.githubusercontent.com/117701031/220243639-21a262e5-d2b9-48b9-8dfb-5d97602e16c6.png)

Our operations will mainly be done on this `written_2/` directory.

## Option: grep -r
An option we will look into is `-r`, `--recursive`. 

As you can tell, the syntax of grep actually takes in individual files as the targets to search. If one uses a directory in place of a file name, the following error is returned:

![image](https://user-images.githubusercontent.com/117701031/220246264-86b3f27c-a9df-4840-8db4-5714b586fbc1.png)

However, there are definitely times when you wish to search for a pattern in all the files in a directory and all its subdirectories. To make this happen, one can use the `-r` option

```
grep -r 'pattern' directory/
```

For example, here I searched for the word **"Dizengoff Street."** in all the files in `written_2/` recursively, and it successfully returns **all** the lines from **all** the files in `written_2/` that contain that word.
```
$ grep -r 'Dizengoff Street.' ./
./travel_guides/berlitz1/HandRIsrael.txt:        Kassit ❁❁ 117 Dizengoff Street, Tel Aviv; Tel. (03) 522
./travel_guides/berlitz1/HandRIsrael.txt:        Dizengoff Street. Friendly staff. Hearty Sabbath meals.
./travel_guides/berlitz1/WhatToIsrael.txt:        Crowds congregate along the promenade and along Dizengoff Street, but
./travel_guides/berlitz1/WhatToIsrael.txt:        here or at the Cameri Theatre, Dizengoff Street (tel. 03-523 3335/527
./travel_guides/berlitz1/WhereToIsrael.txt:        busiest thoroughfare, Dizengoff Street. A good place to stroll and
```


## Option: grep -l

## Option: grep -i
