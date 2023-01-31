## Hi all! On this page, you will see 3 parts of my lab report for week 2 and 3.

---


# 1. StringServer in action
The structure of my answer for part 1 will be first an explanation of my code, and then answers to the questions below. That way, I can answer the questions more easily without worrying about whether the reader knows what I'm saying. If you would like to jump to the answer, feel free to skip to the section titled "**Screenshots of using StringServer's add-message query:**"

__Questions to be answered__:
> Which methods in your code are called?


> What are the relevant arguments to those methods, and the values of any relevant fields of the class?


> How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.

As you will see, we have 3 imports in both of these files. Since we are dealing with commandline arguments, we imported `java.io.IOException`. We also imported `java.net.URI` for self-explanatory reasons. These will not be further explained in the following texts.

## StringServer.java

![image](https://user-images.githubusercontent.com/117701031/215586644-0e0ed492-743e-449b-ab31-2dc93d8e3e18.png)

StringServer.java file is really quite simple. 
```
if(args.length == 0){
    System.out.println("Missing port number! Try any number between 1024 to 49151");
    return;
}
```
If the port number isn't provided, it tells the human to provide one. 
```
int port = Integer.parseInt(args[0]);
```
It parse and store the integer from the commandline argument as the port number, and it then uses that port number to host a local server (i.e. webpage). 
```
Server.start(port, new Handler());
```
It uses the Server object provided by the starter code in week 2 lab (which will not be shown because it is too complicated for me to understand at this moment) and starts a server with a new Handler object, (which will be explained below).


## Handler.java
![image](https://user-images.githubusercontent.com/117701031/215586532-76adcf46-521a-4ff7-9455-5a183435d15e.png)

`Handler.java` file is a little more complicated. 


It has a field called **str** that stores the single string to keep track of.
```
    String str = new String("");
```
 The page shows the string in its current state if the root path is accessed.

```
if (url.getPath().equals("/")) {
    System.out.println("Path: " + url.getPath());
    return str;
}
```
The server responds to the `add-message?s=<string>` request by splitting the request argument with the "__=__" and concatenating the string (that is behind the "__=__") after the current String `str` as well as a new line. It also tells the page the then show the new String `str` in its current state.

Of course, if the String/Character before the "**=**" isn't "**s**", it will return an unknown query error. 

Technically, I don't know if this "split path with =" method is required since `add-message` is the only request the server needs to respond to. ~~Tell me in the comments below what you think~~ 
```
else if (url.getPath().contains("/add-message")) {
    System.out.println("Path: " + url.getPath());
    String[] parameters = url.getQuery().split("=");
        if (parameters[0].equals("s")) {
            str+=(String)(parameters[1])+"\n";
            return str;
        }
        return "Error: Unknown Query";
}
```
That is it. The `system.out.println` is there simply for me to know that the server started running.

Now that we understand what the code does, let's answer the questions for the following 2 screenshots.

## Screenshots of using StringServer's add-message query:

![image](https://user-images.githubusercontent.com/117701031/215585986-8100a48a-2966-44c3-91fe-c31eb864ccd1.png)

In this screenshot, I first tested the query with the word "**nice**". 
> Which methods in your code are called?

The `handleRequest()` in Handler.java is called.

> What are the relevant arguments to those methods, and the values of any relevant fields of the class?

The url path is the relevant argument; specifically, the `/add-message` part tells the handler to add a message, and the `?s=<string>` part tells the handler what the message is. The value for the relevant field `str` before this method was called was "" (i.e. empty string), and it changed to "nice\n" after the method is executed. The URI is essentially what we put into the browser, requests from which the handler handles.

> How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.

The value for the relevant field `str` before this method was called was "" (i.e. empty string), and it changed to "nice\n" after the method is executed. The URI is essentially what we put into the browser, requests from which the handler handles.


![image](https://user-images.githubusercontent.com/117701031/215586255-0084af3b-111e-499d-8926-37bfdbb63b97.png)
In this screenshot, I used the query with the phrase "**holy jesus its working**", because it finally worked after about 30 minutes of me trying to understand why it had a bug. Notably, I typed the `space` character directly in the query.
> Which methods in your code are called?

The `handleRequest()` in Handler.java is called.

> What are the relevant arguments to those methods, and the values of any relevant fields of the class?

The url path is the relevant argument; specifically, the `/add-message` part tells the handler to add a message, and the `?s=<string>` part tells the handler what the message is. The value for the relevant field `str` before this method was called was "nice\n" (i.e. empty string), and it changed to "nice\nholy jesus its working\n" after the method is executed. The URI is essentially what we put into the browser, requests from which the handler handles. 

> How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.

The value for the relevant field `str` before this method was called was "nice\n" (i.e. empty string), and it changed to "nice\nholy jesus its working\n" after the method is executed. The URI is essentially what we put into the browser, requests from which the handler handles.

# 2. Debugging a bug from buggy lab 3 files










What did I learn today?

I also learned two trivial things:
1. In markdown, we can put emojis like :joy: using `colon "joy" colon`
2. In query, space is `%20` in query language
