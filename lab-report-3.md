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

**Note:**
The requirements for this lab report requires that **"along with each option/mode [I] show, cite [my] source for how [I] found out about it as a URL or a description of where [I] found it."** Thus, even though I found all of these options and their functions using the `grep --help` command, I will repeat this information for each of the examples.


## Setting it up

Let's first set up the environment. For this demonstration, I will be using the data set from the **CSE15L Skill Demo 1** that I cloned and stored on my local machine, and I will be operating using _Bash_ terminal, as seen below. 

![image](https://user-images.githubusercontent.com/117701031/220243639-21a262e5-d2b9-48b9-8dfb-5d97602e16c6.png)

Our operations will mainly be done on this `written_2/` directory.

# Option 1: `grep -r`

An option we will look into is `-r`, `--recursive`. This option was chosen from the guide returned by the aforementioned `grep --help` command, under the **"Output control"** section.

As you can tell, the syntax of grep actually takes in individual files as the targets to search. If one uses a directory in place of a file name, the following error is returned:

![image](https://user-images.githubusercontent.com/117701031/220246264-86b3f27c-a9df-4840-8db4-5714b586fbc1.png)

However, there are definitely times when you wish to search for a pattern in all the files in a directory and all its subdirectories, and it would be a nightmare to input the file names one by one.

To make this happen more easily, one can use the `-r` option

```
grep -r 'pattern' directory/
```

## Example 1
For the first example, I searched for the word **"Dizengoff Street"** in all the files in `written_2/` recursively, and it successfully returns **all** the lines from **all** the files in `written_2/` that contain that word. 

```
$ grep -r 'Dizengoff Street' ./
./travel_guides/berlitz1/HandRIsrael.txt:        Kassit ❁❁ 117 Dizengoff Street, Tel Aviv; Tel. (03) 522
./travel_guides/berlitz1/HandRIsrael.txt:        Dizengoff Street. Friendly staff. Hearty Sabbath meals.
./travel_guides/berlitz1/WhatToIsrael.txt:        Crowds congregate along the promenade and along Dizengoff Street, but
./travel_guides/berlitz1/WhatToIsrael.txt:        here or at the Cameri Theatre, Dizengoff Street (tel. 03-523 3335/527
./travel_guides/berlitz1/WhereToIsrael.txt:        busiest thoroughfare, Dizengoff Street. A good place to stroll and
```

The first part of each line indicates the absolute paths of the files that the phrase **"Dizengoff Street"** is found in, and the second part prints out the individual lines in each file that contains the phrase.

As we can see, there are 3 different files that contain that word:
1. HandRIsrael.txt
2. WhatToIsrael.txt
3. WhereToIsrael.txt

And we easily found all of the files and the surrounding lines in one line of command.

## Example 2
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

This time, even though it does indeed find the files for us, the texts it prints are not so user-friendly, because there're simply too much. At the same time, you will also notice that multiple lines from the same document are printed an abundant number of times. So, this is the perfect time segue into our next **option** and introduce:

# Option 2: `grep -l`

`-l`, '--files-with-matches' essentially prints out only the name of the files, and omit the surrounding texts that grep normally prints. This option was chosen from the guide returned by the aforementioned `grep --help` command, under the **"Output control"** section.

## Example 1

For a side by side comparison, let's try to find the files containing the phrase **"Sabbath"** again, this time with both the **recursive** search option and the **list** option.

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

There we go! So much cleaner and calming to look at. Here, grep essentially ditches the surrounding texts and only output the absolute paths of the files where the pattern was found, as well as printing each file path only **once**, which makes it more aethetic and clear.

> To use more than one command-line options, put the letters that indicate each option in succession as the `-rl` shown above, or separately `-r -l`. The order does not matter, `-rl`,`-r -l`, `-l -r`, and `-lr` prints the same results. 


## Example 2

For the second example, let's try to find the string **"Stupid"** amongst the files:

```
$ grep -rl 'Stupid' ./
./non-fiction/OUP/Kauffman/ch9.txt
```

The results tell us that there is only 1 file containing the string **"Stupid"**. 

Notice that I am specific with the fact that it's a string, and this is because `grep` is case-sensitive by default. If we searched for **"stupid"** instead, we would get a different output 

```
$ grep -rl 'stupid' ./
./non-fiction/OUP/Castro/chC.txt
./non-fiction/OUP/Kauffman/ch9.txt
./travel_guides/berlitz1/WhereToMalaysia.txt
```

which shows us 3 files instead of 1 that contains the word **"stupid"**. This is very useful if you remembered a phrase but can't remember the source of your memory, or you simply lose where you put your files.

In some real scenarios, we care more about the content of the word that we're searching for instead of the format and specificities. In that case, we can use the following option: 

# Option 3: `grep -i`

The option `-i`, `--ignore-case` tells `grep` to ignore the uppercase and lowercase distinction. This option was chosen from the guide returned by the aforementioned `grep --help` command, under the **"Regexp selection and interpretation"** section.

## Example 1

For our first example, we will look at the search results without option `-i` for the words **"Crazy"** and **"crazy"**, respectively. Then, we will compare those results with the results from searching for **"cRaZy"** using option `-i`.

Search result for **"Crazy"**:

```
$ grep -l -r  'Crazy' ./
./non-fiction/OUP/Castro/chL.txt
./non-fiction/OUP/Castro/chV.txt
./travel_guides/berlitz1/WhatToLasVegas.txt
./travel_guides/berlitz2/Berlin-History.txt
./travel_guides/berlitz2/Canada-WhereToGo.txt
./travel_guides/berlitz2/Paris-WhatToDo.txt
```

Search result for **"crazy"**:

```
$ grep -l -r  'crazy' ./
./non-fiction/OUP/Abernathy/ch1.txt
./non-fiction/OUP/Castro/chB.txt
./non-fiction/OUP/Castro/chP.txt
./non-fiction/OUP/Castro/chV.txt
./non-fiction/OUP/Fletcher/ch9.txt
./travel_guides/berlitz1/WhereToIndia.txt
./travel_guides/berlitz1/WhereToItaly.txt
./travel_guides/berlitz1/WhereToLosAngeles.txt
./travel_guides/berlitz2/Algarve-WhatToDo.txt
./travel_guides/berlitz2/Amsterdam-WhatToDo.txt
./travel_guides/berlitz2/Boston-WhereToGo.txt
./travel_guides/berlitz2/California-WhatToDo.txt
./travel_guides/berlitz2/California-WhereToGo.txt
./travel_guides/berlitz2/Canada-WhereToGo.txt
```

Although some of the files do contain both **"Crazy"** and **"crazy"**, we can clearly see that the returned results from both of those searches all appear in the search using option `-i`. 


Search results for **"cRaZy"**, with option `-i`:

```
$ grep -l -r -i 'cRaZy' ./
./non-fiction/OUP/Abernathy/ch1.txt
./non-fiction/OUP/Castro/chB.txt
./non-fiction/OUP/Castro/chL.txt
./non-fiction/OUP/Castro/chP.txt
./non-fiction/OUP/Castro/chV.txt
./non-fiction/OUP/Fletcher/ch9.txt
./travel_guides/berlitz1/WhatToLasVegas.txt
./travel_guides/berlitz1/WhereToIndia.txt
./travel_guides/berlitz1/WhereToItaly.txt
./travel_guides/berlitz1/WhereToLosAngeles.txt
./travel_guides/berlitz2/Algarve-WhatToDo.txt
./travel_guides/berlitz2/Amsterdam-WhatToDo.txt
./travel_guides/berlitz2/Berlin-History.txt
./travel_guides/berlitz2/Boston-WhereToGo.txt
./travel_guides/berlitz2/California-WhatToDo.txt
./travel_guides/berlitz2/California-WhereToGo.txt
./travel_guides/berlitz2/Canada-WhereToGo.txt
./travel_guides/berlitz2/Paris-WhatToDo.txt
```

This is useful mainly in scenarios where the meaning of the string we search for is more important than its technicalities, like text analysis.

## Example 2
For the second example, we could search for 'Kathmandu' using option `-i`

```
$ grep -r -i -l 'Kathmandu' ./
./travel_guides/berlitz2/Nepal-History.txt
./travel_guides/berlitz2/Nepal-WhatToDo.txt
./travel_guides/berlitz2/Nepal-WhereToGo.txt
```

In this case, unfortunately, the string we are searching for is a proper noun, so searching for it with or without option `-i` does not make a difference at all, since it would not be spelled with a lower-case "k", as seen below.

```
$ grep -r -l 'Kathmandu' ./
./travel_guides/berlitz2/Nepal-History.txt
./travel_guides/berlitz2/Nepal-WhatToDo.txt
./travel_guides/berlitz2/Nepal-WhereToGo.txt
```

This is a prime example of how the programmer is at the heart of these operations, not the computer itself, and everyone should be able to make the distinction about the importance of an option themselves, and whether or not to include it in their commands (for run-time cost purposes).


After seeing so many search results with only the file paths and names, let's see an option that outputs results without them.

# Option 4: `grep -h`
`-h`, `--no-filename` practically erases the file path and leaves only the surrounding texts. It is kind of like the opposite of `-l`. This option was chosen from the guide returned by the aforementioned `grep --help` command, under the **"Output control"** section.

## Example 1

For this first example, let's search for **"Crazy"** using `-h`.

```
$ grep -r -h 'Crazy' ./
Low riders are usually young urban Chicanos, between the ages of eighteen and thirty, and there can be two and three generations of low riders in one family. The cost of fixing and maintaining a low-rider car is fairly high, so the owner typically is a working person. Since finding older cars, say from the 1950s, is 
becoming difficult, some low riders now customize small trucks, motorcycles, and bicycles as well. The movie Mi Vida Loca (My Crazy Life) depicts the work that goes into customizing a pickup truck.
Vato Loco (Crazy Dude)
La Vida Loca (The Crazy Life)
        the “Crazy Girls” — a topless review that gets even more red-light
The Crazy Twenties
Crazy Casa Loma, northwest of Yorkville at 1 Austin Terrace, is Toronto’s answer to California’s Hearst Castle. Its battlements and turrets are all a self-respecting financier like Henry Pellatt could have wished for. After touring the castles of Europe for a few ideas, he built the 98-room mansion in the early 1900s at the then-astronomical cost of $3,500,000. He chose his oak and walnut from North America, teak from Asia, paneling, marble, and glass from Europe. With all its terraces, massive walls, and echoing rooms, it isn’t exactly cozy. That may explain why Pellatt provided himself with a secret escape route through a hidden staircase leading from his study (and now open to the public). Whatever folly of grandeur the financier entertained is best seen in the opulently paneled Oak Room and the stained-glass dome, marble floors, and Italianate bronze doors of the Conservatory. Take the long tunnel from the wine cellar to the stables, where the horses were spoiled silly with a home of Spanish tile and mahogany.
Robson Square also provides a home for Vancouver Art Gallery, in the old courthouse (a proper Neoclassical temple renovated by Erickson). The star feature of this collection of Canadian artists is the outstanding work of Emily Carr (1871–1945). “Crazy Old Millie,” as she was known locally — “Klee Wyck” or the “Laughing One” to her Kwakiutl Indian friends — was a popular eccentric in Victoria, where she kept a boarding house and wheeled a pet monkey around in a baby carriage. Years of painting among the native peoples and studying with French Post-Impressionists produced a unique style of vigorous, expressive landscapes and totemic themes achieved with great sweeps and swirls of bold color. Look for the lush, dramatic Big Raven (1928) and Forest, British Columbia (1932), in which the trees have the sculptural quality of totem poles.
Floor shows keep the “naughty” image of Paris alive. The Folies Bergères (rue Richer), which launched the careers of Josephine Baker, Mistinguett, and Maurice 
Chevalier, and the Lido on the Champs-Elysées are both classic survivors. The most famous modern-day floor show, erotic, brilliantly choreographed, and bordering on chic, is at the Crazy Horse Saloon (avenue George V). Toulouse-Lautrec painted the showgirls of the Moulin Rouge (place Blanche) a century ago, and it still offers tourists a boisterous floor show in the old tradition. The rest of Pigalle plumbs the lower depths with a certain fascinating glee.
```

By eliminating the file paths, we are left with chunks of texts from within the files that contain the specified phrase, separated by lines. 

This is extremely useful in cases where you want to process the output directly using other commands such as output redirection and analyze the text. This could be useful in doing automated research with large amounts of texts or other form of data.

## Example 2

As mentioned before, `-i` is useful for when content and meaning is more important than the phrase's technicalities. In combination with option `-h`, one can find all the relevant texts in a bundle of files and directories using one line of command and redirect the output elsewhere for analysis. 

```
$ grep -r -h -i 'Crazy' ./
The labor intensive [U.S.] apparel market cannot and should not compete with much lower cost labor elsewhere. The stuff depends on somebody sitting at a sewing machine and stitching sleeves on; it is crazy to hurt American consumers by forcing them to buy that at $4 or $5 an hour of labor. We ought to be out of that 
business.26
Bato is a word centuries old that can be translated as “guy” or “dude.” Most recently it has been spelled vato, transposing the v for the b. In Chicano communities, in-group chatter, and published literature one frequently comes across the expression bato loco, meaning a “crazy guy,” a “cool dude,” or a “wise guy.” Bato was a word incorporated into the pachuco jargon of the 1940s, and it is still very much a part of Chicano vocabulary today. The bato loco, or vato loco, is the descendent of the pachuco and a close relation of today’s cholo (urban youth). The bato is often mentioned in connection with his barrio, as in el vato loco del Hoyo Mara.
The bato loco is tantamount to an archetype in Chicano culture; he is that crazy guy who isn’t afraid of life. He may be a gang member, a drug user, or just an entertaining street person. He could also be fully immersed in la vida loca as described by Luis Rodriguez in his book, Always Running, and by Oscar Zeta Acosta in The Autobiography of a Brown Buffalo. In the novel The Road to Tamazunchale, Ron Arias creates a streetwise character, a bato named Mario, who acts as a 
sidekick to the main character, Fausto. The two wander through a mythical Los Angeles in search of “the song of life.” For the contemporary Chicano male, el bato loco is not only a symbol of ethnic identity but also an icon of the urban coming-of-age experience itself.
Low riders are usually young urban Chicanos, between the ages of eighteen and thirty, and there can be two and three generations of low riders in one family. The cost of fixing and maintaining a low-rider car is fairly high, so the owner typically is a working person. Since finding older cars, say from the 1950s, is 
becoming difficult, some low riders now customize small trucks, motorcycles, and bicycles as well. The movie Mi Vida Loca (My Crazy Life) depicts the work that goes into customizing a pickup truck.
Because of its ancient history there are many variants of Los Pastores, and several versions have developed a comic dialogue between Lucifer and Cucharón, Bartolo, and the other characters. One character is named Bato, as in bato loco (crazy guy), a phrase of contemporary usage among Chicanos today. Variants of this 
play have been collected in Texas, New Mexico, and California, and it has been performed in Mexico since the sixteenth century. In San Antonio the performance 
of Los Pastores at Our Lady of Guadalupe Church as been ongoing since 1913. Richard Flores, both as an ethnographer and as a performer, presents a thorough analysis of the historical conditions that continue to provide an environment for the performance of Los Pastores as both ritual and drama. In 1991 El Teatro Campesino produced a video film of their production of Los Pastores titled La Pastorela—The Shepherds’ Tale.
Vato Loco (Crazy Dude)
La Vida Loca (The Crazy Life)
In the novel Maravilla, Laura Del Fuego shows la vida loca of the 1960s in the barrio of Maravilla in Los Angeles. Oscar “Zeta” Acosta, in his Autobiography of a Brown Buffalo, shows the life of batos locos in the barrios of Los Angeles, also during the 1960s and 1970s. Luis Rodriguez has written a wonderful memoir, 
dedicated to his son, that depicts the crazy life he led in Los Angeles in the 1970s. Gus Frias presents a much more somber picture of the violent way of life 
led by those in la vida loca.
But the government’s staying its hand does not mean that hate speech goes unsanctioned. Civil society has it own spontaneous means of chastising those who veer too far from the acceptable range of discourse. The best remedy against the “Auschwitz lie,” as the Germans call it, is to ignore it. Deborah Lipstadt, in her book Denying the Holocaust, wrote that we should not publicly debate unacceptable as well as obviously false claims, and thus she advanced a remedy as powerful as governmental censorship. When civil society turns a deaf ear, crazy ideas lose their edge. The remedy disturbed one historian labeled a “denier” so much that in late 1999 he unsuccessfully sued Lipstadt for libel, primarily to force her to confront his claims.23
        the “Crazy Girls” — a topless review that gets even more red-light
        submerged the newcomer has been replaced by the equally crazy bustle of
        abandoned “to the cats and the crazy. ” And remember, Italians make no
        Not only did his home town not finance his crazy trip to
        Halloween as the lively residents parade around in crazy costumes.
The Netherlands are football (soccer) crazy and Ajax is the Amsterdam team, one of the most successful in Europe over the last 30 years. They play at the Amsterdam Arena, a fine modern stadium, which is also used for other sporting events — but unfortunately it is almost impossible to obtain tickets for matches.     
The Netherlands are football (soccer) crazy and Ajax is the Amsterdam team, one of the most successful in Europe over the last 30 years. They play at the Amsterdam Arena, a fine modern stadium, which is also used for other sporting events — but unfortunately it is almost impossible to obtain tickets for matches.     
The Crazy Twenties
Nearby, on the downtown side of the river, the new temple of this sport- crazy town rises beside North Station. In 1995 FleetCenter replaced the old Boston Garden where fans had cheered on such legends as Bobby Orr of the Boston Bruins and Larry Bird of the Celtics. Tours are given of the new facility.
Running. In this fitness-crazy state you can run just about everywhere, best of all barefoot along the beach. Sports stores will attempt to sell you all manner of “essential” running equipment — haute couture tracksuits and shoes, lap timers, sweatbands, pedometers — but all you really need is a good pair of running 
shoes and a towel.
The roller-coaster dips and crests of the city’s hills, breaking up the monotony of the standard grid system of streets, reach a crazy climax on Lombard Street between Hyde and Leavenworth. After you’ve negotiated all eight hairpin bends lined with gardens of hydrangeas, you’re not going to quibble about the claim that it’s the “crookedest street in the world.” Two blocks south is Filbert Street, boasting the steepest slope — a stomach-churning 31.5 percent gradient, with 
no bends.
Crazy Casa Loma, northwest of Yorkville at 1 Austin Terrace, is Toronto’s answer to California’s Hearst Castle. Its battlements and turrets are all a self-respecting financier like Henry Pellatt could have wished for. After touring the castles of Europe for a few ideas, he built the 98-room mansion in the early 1900s at the then-astronomical cost of $3,500,000. He chose his oak and walnut from North America, teak from Asia, paneling, marble, and glass from Europe. With all its terraces, massive walls, and echoing rooms, it isn’t exactly cozy. That may explain why Pellatt provided himself with a secret escape route through a hidden staircase leading from his study (and now open to the public). Whatever folly of grandeur the financier entertained is best seen in the opulently paneled Oak Room and the stained-glass dome, marble floors, and Italianate bronze doors of the Conservatory. Take the long tunnel from the wine cellar to the stables, where the horses were spoiled silly with a home of Spanish tile and mahogany.
Robson Square also provides a home for Vancouver Art Gallery, in the old courthouse (a proper Neoclassical temple renovated by Erickson). The star feature of this collection of Canadian artists is the outstanding work of Emily Carr (1871–1945). “Crazy Old Millie,” as she was known locally — “Klee Wyck” or the “Laughing One” to her Kwakiutl Indian friends — was a popular eccentric in Victoria, where she kept a boarding house and wheeled a pet monkey around in a baby carriage. Years of painting among the native peoples and studying with French Post-Impressionists produced a unique style of vigorous, expressive landscapes and totemic themes achieved with great sweeps and swirls of bold color. Look for the lush, dramatic Big Raven (1928) and Forest, British Columbia (1932), in which the trees have the sculptural quality of totem poles.
The Maritime Museum in the old courthouse on Bastion Square contains some fine models and navigational paraphernalia of the merchant ships of yore — whalers, steamers, and old Hudson’s Bay paddle-wheelers. The star attraction is the original Tilikum, a 13-m (40-ft) dugout canoe equipped with three sails to take Captain J. C. Voss in 1901 on a crazy three-year voyage round the world. He sailed from Victoria via Australia, New Zealand, Brazil, the Cape of Good Hope, and the 
Azores to land up in the English seaside town of Margate.
Floor shows keep the “naughty” image of Paris alive. The Folies Bergères (rue Richer), which launched the careers of Josephine Baker, Mistinguett, and Maurice 
Chevalier, and the Lido on the Champs-Elysées are both classic survivors. The most famous modern-day floor show, erotic, brilliantly choreographed, and bordering on chic, is at the Crazy Horse Saloon (avenue George V). Toulouse-Lautrec painted the showgirls of the Moulin Rouge (place Blanche) a century ago, and it still offers tourists a boisterous floor show in the old tradition. The rest of Pigalle plumbs the lower depths with a certain fascinating glee.
```

## That concludes my guide to 4 of the useful command-line options for `grep`. Hope you had fun and learned something new on this page!  
