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
In this screenshot, I used the query with the phrase "**holy jesus its working**", because it finally worked after about 30 minutes of me trying to understand why it had a bug. Notably, I typed the `space` character directly in the query instead of the `%20` it shows here.
> Which methods in your code are called?

The `handleRequest()` in Handler.java is called.

> What are the relevant arguments to those methods, and the values of any relevant fields of the class?

The url path is the relevant argument; specifically, the `/add-message` part tells the handler to add a message, and the `?s=<string>` part tells the handler what the message is. The value for the relevant field `str` before this method was called was "nice\n" (i.e. empty string), and it changed to "nice\nholy jesus its working\n" after the method is executed. The URI is essentially what we put into the browser, requests from which the handler handles. 

> How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.

The value for the relevant field `str` before this method was called was "nice\n" (i.e. empty string), and it changed to "nice\nholy jesus its working\n" after the method is executed. The URI is essentially what we put into the browser, requests from which the handler handles.

# 2. Debugging a bug from buggy lab 3 files
The bug I've chosen for this exercise was in the `ArrayExamples.java` file, under the `reversed` method, shown below:

```
  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```
First, by looking at the code, it seems that the function of the method was commented out, and the method is supposed to return the array in reverse order.


To start debugging, we must find the symptoms of the bug. In the given `ArrayTests.java` file, I have written new tests in addition to the given one. 
```
  @Test
  public void testReversed() {
    //Empty array
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
    //Positive integers array
    int[] input2 = {1,2,3,4 };
    assertArrayEquals(new int[]{4,3,2,1 }, ArrayExamples.reversed(input2));
    //Single element array
    int[] input3 = {1};
    assertArrayEquals(new int[]{1 }, ArrayExamples.reversed(input3));
    //Negative integers array
    int[] input4 = {-1,-3,-4,-5 };
    assertArrayEquals(new int[]{-5,-4,-3,-1 }, ArrayExamples.reversed(input4));
  }
```

These tests include inputs of:
1. An empty array,
2. An positive integers array,
3. A single element array, and
4. A negative integers array,
respectively.

And the output was:
![image](https://user-images.githubusercontent.com/117701031/215651561-614d59c8-c7e8-44c8-8a9a-64766549008f.png)

```
$ java -cp ".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore ArrayTests
JUnit version 4.13.2
..E
Time: 0.008
There was 1 failure:
1) testReversed(ArrayTests)
arrays first differed at element [0]; expected:<4> but was:<0>
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:78)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:28)
        at org.junit.Assert.internalArrayEquals(Assert.java:534)
        at org.junit.Assert.assertArrayEquals(Assert.java:418)
        at org.junit.Assert.assertArrayEquals(Assert.java:429)
        at ArrayTests.testReversed(ArrayTests.java:18)
        ... 32 trimmed
Caused by: java.lang.AssertionError: expected:<4> but was:<0>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at org.junit.internal.ExactComparisonCriteria.assertElementsEqual(ExactComparisonCriteria.java:8)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:76)
        ... 38 more

FAILURES!!!
Tests run: 2,  Failures: 1
```
_Note: it says 2 tests because there are other tester methods in the file._


It seems that `input 2` did not work. But I don't know the case for other ones, so I put the 4 tests into the tester method individually to see each case. In all of the cases except the empty string input, it seemed that the first element of the returned array was always `0` no matter the expected. This is the symptom of the bug.


Now, would an array that contains all `0`s and one that contains some `0` be not symptom-inducing inputs? I tried it out and added the following in the tester:
```
int[] input5 = {0,0,0,0,0};
assertArrayEquals(new int[]{0,0,0,0,0 }, ArrayExamples.reversed(input5));
int[] input6 = {-1,0,1,2,3};
assertArrayEquals(new int[]{3,2,1,0,-1}, ArrayExamples.reversed(input6));
```
The output was:
![image](https://user-images.githubusercontent.com/117701031/215651476-904c674f-daa2-44ed-adc1-f841e06fc416.png)

```
$ java -cp ".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore ArrayTests
JUnit version 4.13.2
..E
Time: 0.008
There was 1 failure:
1) testReversed(ArrayTests)
arrays first differed at element [0]; expected:<3> but was:<0>
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:78)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:28)
        at org.junit.Assert.internalArrayEquals(Assert.java:534)
        at org.junit.Assert.assertArrayEquals(Assert.java:418)
        at org.junit.Assert.assertArrayEquals(Assert.java:429)
        at ArrayTests.testReversed(ArrayTests.java:18)
        ... 32 trimmed
Caused by: java.lang.AssertionError: expected:<3> but was:<0>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at org.junit.internal.ExactComparisonCriteria.assertElementsEqual(ExactComparisonCriteria.java:8)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:76)
        ... 38 more

FAILURES!!!
Tests run: 2,  Failures: 1
```

It seems that even an array with some `0`s won't work, and only an array with all `0`s and empty arrays can pass the test. In these cases, the array returned is congruent to the original array. 
![image](https://user-images.githubusercontent.com/117701031/215653456-0ac14cff-b751-4de5-8827-4b1db7665f54.png)
![image](https://user-images.githubusercontent.com/117701031/215653496-713a17dc-256c-4580-8d64-f0d08040a3fe.png)


Now, going back to the original code,
```
// Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```
we can see that the for loop attempts to copy the last `newArray` element onto the first `arr` element, the second last `newArray` element onto the second `arr` element, and so on. 


We can tell immediately that the problem is that the array `arr` is copying `newArray` elements right after `newArray` was initialized. 


As we know, a newly initialized int array will have its values set to 0 as default. This means that the method is returning an all 0 array with the length of the original array no matter what, which made correspondence to the test results.


To fix this, I had to copy over the elements from the original array `arr` to `newArray` before the for-loop, so that the code is assigning the correct integers instead of just `0`s. I tried to use a for each loop so that I don't have to type out `i=0;i<arr.length;i++` in the code, but I realized that I need the index for assigning to `newArray`, so not only did I type an extra for each loop, I typed out `i=0;i<arr.length;i++` 3 (now 4) times plus this explanation. It was not a smart investment of time. Do not be like me.


```
// Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i=0;i<arr.length;i++){
      newArray[i]=arr[i];
    }
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```

Cool. After I ran the tests again, they all passed. Instead of just copying a full-zeros `newArray` into `arr`, it is now copying the correct elements. The bug has been obliterated. HOORAY!


# 3. What did I learn from these labs?
First and foremost, I learned the basics of how to host a web server in Java, which opens up a lot of doors for what I can do with Java. At the same time, I also had some hands-on experience in using the JUnit testing kit and scrutinized a program to debug it.

Other than that, I also learned two trivial things:
1. In markdown, we can put emojis like :joy: using `colon "joy" colon`
2. In query, space is `%20` in query language


That will be all, thank you for reading. 

Ctrl C
