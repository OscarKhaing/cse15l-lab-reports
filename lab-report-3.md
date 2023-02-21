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

* **`[OPTION]`** are modifiers to limit or specify conditions for the operation (which we'll look at today)
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

## Option: `grep -r`
An option we will look into is `-r`, `--recursive`. 

As you can tell, the syntax of grep actually takes in individual files as the targets to search. If one uses a directory in place of a file name, the following error is returned:

![image](https://user-images.githubusercontent.com/117701031/220246264-86b3f27c-a9df-4840-8db4-5714b586fbc1.png)

However, there are definitely times when you wish to search for a pattern in all the files in a directory and all its subdirectories, and it would be a nightmare to input the file names one by one.

To make this happen more easily, one can use the `-r` option

```
grep -r 'pattern' directory/
```

For the first example, I searched for the word **"Dizengoff Street"** in all the files in `written_2/` recursively, and it successfully returns **all** the lines from **all** the files in `written_2/` that contain that word. The first part of each line indicates the absolute paths of the files that the phrase **"Dizengoff Street"** is found in, and the second part prints out the individual lines in each file that contains the phrase.
```
$ grep -r 'Dizengoff Street' ./
./travel_guides/berlitz1/HandRIsrael.txt:        Kassit ❁❁ 117 Dizengoff Street, Tel Aviv; Tel. (03) 522
./travel_guides/berlitz1/HandRIsrael.txt:        Dizengoff Street. Friendly staff. Hearty Sabbath meals.
./travel_guides/berlitz1/WhatToIsrael.txt:        Crowds congregate along the promenade and along Dizengoff Street, but
./travel_guides/berlitz1/WhatToIsrael.txt:        here or at the Cameri Theatre, Dizengoff Street (tel. 03-523 3335/527
./travel_guides/berlitz1/WhereToIsrael.txt:        busiest thoroughfare, Dizengoff Street. A good place to stroll and
```
As we can see, there are 3 different files that contain that word:
1. HandRIsrael.txt
2. WhatToIsrael.txt
3. WhereToIsrael.txt

And we easily found all of the files and the surrounding lines in one line of command.

For the second example, I searched for the word **"Sabbath"** instead. 

```
$ grep -r 'Sabbath' ./
./non-fiction/OUP/Abernathy/ch2.txt:The Slater mill not only copied British technology but recreated that country’s arrangement of family labor, which included young children, six-day weeks, the minimum twelve-hour day, Sabbath schools, and payment of wages partly in goods and partly in cash. The form of ownership and management also followed British lines—one partner financed the venture, while the other furnished the technical know-how. For these accomplishments, Samuel 
Slater has been called “the father of American manufactures.” His story underscores the international role of textiles and apparel, their impetus in national economic development, and their place in conflicts over domestic production and imports—a theme that recurs throughout U.S. history. For example, from the outset of the new nation, President George Washington and his Secretary of the Treasury Alexander Hamilton wanted to encourage U.S.-based industry. Indeed, Washington wore a dark brown suit, entirely made in America, for his first inaugural on April 30, 1789.3
./non-fiction/OUP/Berk/CH4.txt:On Friday nights, they marked the Sabbath in a special way, by imagining that they were at home. They talked about the evening’s events in minute detail to make the image of family life ﬁrm and real. Alice had always had the responsibility of setting the table, and her mother would correct her if she left out even small, nonessential items. In play, Edith would murmur, “Alice, it’s time to set the table. Find the nicest tablecloths, and don’t forget the ﬂowers. Where are the napkins for the guests? You forgot the fork for Father. You really shined the candelabra beautifully this week, better than before.” 16 After their pretend meal, the two sisters would whisper songs.
./non-fiction/OUP/Fletcher/ch9.txt:The values of the second constitution continue to collide with those of the first. The egalitarian approach toward freedom of religion dictates a leveling of two conflicting clauses in the First Amendment on freedom of religion. One clause prescribes “establishment of religion”; the other mandates “the free exercise of religion.” For the past thirty years or so, the tendency has been to read these two clauses together to prohibit both the state financing of religious activities and the state’s favoring one religion by granting to believers special exemptions from the laws applicable to everyone.31 The opposition claims that religious reasons warrant exceptional treatment, say, for refusing to work on one’s personal Sabbath,32 for using hallucinatory 
drugs,33 or for keeping one’s children out of school in violation of truancy laws.34 Again the conflict is between equality and freedom. Equality requires that all be treated alike—no exceptions for those motivated by fear of God. The faithful object and insist on the teaching found in Matthew 22:21: “Render therefore, unto Caesar the things which are Caesar’s; and unto God, the things that are God’s.”35 The constitutional right to “freedom of religion,” they argue, requires special exemptions for those who dissent, as a matter of conscience, from the laws applicable to others.
./travel_guides/berlitz1/HandRIsrael.txt:        Closed Sabbath and Saturday evening.
./travel_guides/berlitz1/HandRIsrael.txt:        lovely large summer patio. Kosher. Closed Sabbath.
./travel_guides/berlitz1/HandRIsrael.txt:        terrace in summer. Kosher. Closed Sabbath.
./travel_guides/berlitz1/HandRIsrael.txt:        upstairs. Kosher. Closed Sabbath.
./travel_guides/berlitz1/HandRIsrael.txt:        Sabbath.
./travel_guides/berlitz1/HandRIsrael.txt:        Dizengoff Street. Friendly staff. Hearty Sabbath meals.
./travel_guides/berlitz1/HandRIsrael.txt:        Not for the squeamish. Kosher. Closed on the Sabbath.
./travel_guides/berlitz1/HandRIsrael.txt:        atmosphere. Kosher. Closed on the Sabbath.
./travel_guides/berlitz1/IntroJerusalem.txt:        planning your day is not easy. Each religion has a different Sabbath
./travel_guides/berlitz1/WhatToIsrael.txt:        a.m. to 2:00 or 3:00 p.m. Shops close for the Sabbath (Saturday) and
./travel_guides/berlitz1/WhereToJerusalem.txt:        Fridays (the Muslim Sabbath) and on major Islamic holidays, including
./travel_guides/berlitz1/WhereToJerusalem.txt:        entertainments. Remember the Sabbath difference: Muslims have Friday as
./travel_guides/berlitz1/WhereToJerusalem.txt:        on Friday). Many shops and offices are closed for the Sabbath, but
./travel_guides/berlitz1/WhereToJerusalem.txt:        Yehuda, which is especially crowded before the Sabbath and holidays.
```

This time, even though it does indeed find the files for us, the texts it prints are not so user-friendly, because there're simply too much. So, this is the perfect time segue into our next **option** and introduce:

## Option: `grep -l`
`-l`, '--files-with-matches' essentially prints out only the name of the files, and omit the surrounding texts that grep normally prints. For a side by side comparison, let's try to find the phrase **"Sabbath"** again, this time with both the **recursive** search option and the **list** option.

```
$ grep -lr 'Sabbath' ./
./non-fiction/OUP/Abernathy/ch2.txt
./non-fiction/OUP/Berk/CH4.txt
./non-fiction/OUP/Fletcher/ch9.txt
./travel_guides/berlitz1/HandRIsrael.txt
./travel_guides/berlitz1/IntroJerusalem.txt
./travel_guides/berlitz1/WhatToIsrael.txt
./travel_guides/berlitz1/WhereToJerusalem.txt
```

There we go! So much cleaner and calming to look at. 

> To use more than one command-line options, put the letters that indicate each option in succession as the `-rl` shown above. The order does not matter, `-rl` and `-lr` prints the same results. 

For the second example, let's try to find the string **"Stupid"** amongst the files:

```
$ grep -rl 'Stupid' ./
./non-fiction/OUP/Kauffman/ch9.txt
```

The results tell us that there is only 1 file containing the string **"Stupid"**. Notice that I am specific with the fact that it's a string, and this is because `grep` is case-sensitive by default. If we searched for **"stupid"** instead, we would get a different output 

```
$ grep -rl 'stupid' ./
./non-fiction/OUP/Castro/chC.txt
./non-fiction/OUP/Kauffman/ch9.txt
./travel_guides/berlitz1/WhereToMalaysia.txt
```
which shows us 3 files instead of 1 that contains the word **"stupid"**.

In some real scenarios, we care more about the content of the word that we're searching for instead of the format and specificities. In that case, we can use: 

## Option: `grep -i`


