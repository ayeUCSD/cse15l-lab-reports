# Weeks 4 & 5 Lab Report

***Contents:***
- Researching Commands

---------------

## Command Research!

This week we are supposed to find 3 command line options or alternate ways to use commands for these commands:
- **less**
- find
- grep


I am exploring the **`less`** command
________
## Fun with `less`
What are 3 interesting functions or commands in less? 



|**Function/Command**| **How does it work?** | 
|:----------:|:---------|
|The Search Feature!|<ul><li>When you are in a file with `less` you can use "/" in order to search for strings!<li>some command-line options allow you to refine your searches as long as they are called when `less` is called!<ul><li>eg: `-i`|
|The Mark Feature! | <ul><li>~~a silly little goblin named mark does your homework!~~<li>highlight text in less and press m to begin marking!<li>press a letter on the keyboard to assign a letter<li>press the single quote," ' ", and then the letter to return to the marked text! |
|Opening multiple Files with Less! | Navigate though multiple files using keyboard commands!|



When you call `less` on a file, it opens the interface in the command line. When it is open you are can type '/' on your keyboard in order to begin searching for a specific string in the file.

Here I call less on `technical/biomed/1468-6708-3-1.txt` using the following command

    less -N technical/biomed/1468-6708-3-1.txt


Note: the -N command simply shows the line count

The ouput / `less` interface can be seen in this following image:

![image](/r3images/lessOpenBiomed.png)

If you take note of the bottom left there is a sort of command line input. This is where you can input '/' to search or 'm' to mark!

**More info below in their own sections**

- ~~that means get scrollin bucko!~~

--------------
## **Search Feature**
The format for searching is as follows

    /[String-To-Find]

Pretty simple right? As long as you put the string you want to find after the '/', `less` will search for it in the opened file!

I will now search for "Older" in the file and we can look at the results of the first page!

    /Older


|Before|After|
|------|-----|
|![image](/r3images/beforeCommand.png)|![image](/r3images/afterCommand.png)|

You can see on the before column, I have the command queued up in the bottom left. On the after column, you can see it highlighted the first "Older" in the text file.

I won't be showing the queued up commands from now on, but I will show the commands I entered.

**How to navigate through entries?**

To navigate to the next or previous string that matches, type 'n' or shift + 'n' (aka 'N') respectively

NOTE: It displays the next line that contains the string at the very top

|`n`|`N`|
|------|-----|
|Before Press: <br>![image](/r3images/searchOlder.png)<br>After Press:<br> ![image](/r3images/searchOlderSmallN.png) | Before Press: <br>![image](/r3images/beforeBigN.png)<br>After Press:<br> ![image](/r3images/AfterBigN.png) |

Handy because this is *THE* way to navigate through searches!

**IMPORTANT NOTE:**
The search feature in less is by default case sensitive. 

You can see that although there is another "older" string at the beginning of the second paragraph (and more sprinkled everywhere between)but when I hit 'n', it states that it tells me `Pattern not found ` and doesnt highlight any other "older" strings.

![image](/r3images/patternNotFound.png)



**`-i` command**

You can ignore case sensitivity with the fancy `-i` command! This command is entered while you are within the `less` command!

    -i

    -I

By typing `-i`, we TURN ON case sensitivity (this is on by default)

By typing `-I`, we TURN OFF case sensitivity.

|`-i`|`-I`|
|------|-----|
|![image](/r3images/smallIgnore.png) You can see that it case sensitivity is significant|![image](/r3images/bigIgnore.png) Here it ignores case sensitivity!|

Now if I type the following command, the other "older" strings in the paragraphs are highlighted!

    /Older

![image](/r3images/findOlderIgnoreCase.png)

This is really nice when you need to manually go through a file and are searching for a specific string!




-------------



## **The Mark Feature**
- you get a goblin named mark! (this is not true)

How to begin?

To start, while in your file you opened with less, highlight your text like so:

![image](/r3images/markLinesG.png)

Now, if you press `m` , you will initiate a mark! (see the bottom left of the next image!)

![image](/r3images/askMark.png)
    

In order to finish marking, you need to press a letter on the keyboard! (a through z)

Here I will assign the highlighted lines the letter 'g'

    g

Now, in order to return to the marked text press the single quote," ' ", and then the letter to return to the marked text!



|EXAMPLE:|
|------|
|I am going to scroll down to the bottom of the file. ![image](/r3images/endOfFile.png)|
|![image](/r3images/goToMark.png) <br>After pressing " ' ", the prompt `goto mark:` shows up, |
|![image](/r3images/wentToMark.png) <br> Then after pressing 'g', it brought me to my marked text!|

INPUTS:

    '
    g

INTERESTING BEHAVIOR: This seems to not actually save the highlighted text. Rather, it saves the screen scroll instead. If the text highlighted is the same but the screen scroll is different, going to the two letters will look different

Example below: Starting from the top of the file, even though mark a and b have the same text highlighted, going to them doesn't yield the same results!

|`mark a`|`mark b`|
|------|-----|
|![image](/r3images/markA.png) |![image](/r3images/markB.png)|



----------


## **Opening Multiple Files!**


A useful feature of `less` is that you are able to open up multiple files, given multiple file paths!

The pattern for this is as follows:

    less path1 path2 path3 ...

You can add as many paths as you want!


***Example:***

Say I want to open the first 4 "rr" files of 9 in the biomed folder shown here:

 ![image](/r3images/rrBiomed.png)

 Using less, I can!

    less rr166.txt rr167.txt rr171.txt rr167.txt rr172.txt

After entering the command above, I see this: 

![image](/r3images/openFourRR.png)


You can see at the bottom that I am looking at rr166.txt and that there are 4 total files open! This is really helpful for opening and looking through multiple files!


**How to navigae through the files:**

In order to navigate, you first must type a colon, " : ".

Then, to go to the next or previous, hit "n" or "p" respectively.

|`n`|`p`|
|------|-----|
|Before Press: <br>![image](/r3images/openFourRR.png)<br>After Press:<br> ![image](/r3images/afterN.png) | Before Press: <br>![image](/r3images/beforeP.png)<br>After Press:<br> ![image](/r3images/afterP.png) |

***Example:***

We can use the star, " * ", in order to "autofill" inputs for less and open up many files. By refining your search with the star, you can cut down on the unnecessary files you open at once.

For this example, I will open every .txt file in /biomed via less!

    less *txt

result:

![image](/r3images/lessAll.png)

>you can see that there are 837 files open!

The star is a super powerful tool to open multiple files to pass into less!


***Example:***

We will now refine our star autofill into less, and open all of the "rr" files in biomed through less using this next command

    less rr*.txt

![image](/r3images/rr9.png)

> after opening and moving through each file, we can confirm that all 9 files open contain "rr" in them!

So in conjunction with the star, less can be used to manually open multiple specific files based off their file names! Very cool!

_____

