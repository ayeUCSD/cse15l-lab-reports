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
|-o[file_name]|takes [file_name] as an input if it came from a pipe|



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



- press the single quote," ' ", and then the letter to return to the marked text! (behavior: it saves the screen scroll too. If the text highlighted is the same but the screen scroll is different, going to the two letters will look different)


----------


## **The -o Option**

This option is a way to open a path given to the `less` command via a pipe.   



---------
-x ?????

**-i**
- ignores cases sensitivity for searches

**-o[file_name]**
- takes [file_name] as an input if it came from a pipe

**-s**
- merges consecutive whitespace lines


**-N**
- shows lines





_____

