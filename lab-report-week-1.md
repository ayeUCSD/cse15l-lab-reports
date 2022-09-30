
# Week 1 Lab Report



Dear diary,
This lab, I had an absolutely frustrating time logging in to the SSH. In fact, as of writing now, I STILL cannot log in.  
Luckilly, one of the tutors let me use their login so I could at least try some of the lab.


What we went over:
- our cse15l Account!
- vs code
- connecting to an ssh 
- some command line... commands
- moving files with command scp
- ssh keys
------


## CSE15L Account
To log into our ssh, we needed our CSE15L course specific account.
We found this by going to the [account look up tool](https://sdacs.ucsd.edu/~icc/index.php) and logging in.

>The website
>>![image](./w1images/accountLookup.png)

The process should be pretty simple, but I encountered a big problem. We had to reset our passwords in order to initialize our accounts. For some reason, however, my passwords does not work still.


-----

## VS Code

Next we downloaded VS code. I already had it installed and running, so other than reading over the step, I did nothing. 
> Me typing in VScode right now
>> ![image](./w1images/vscode.png)

---
## Connecting to the ssh

We then went to connect to the SSH via the command line.  
Boiled down, you essentially had to type this command:

    ssh cse15lfa22zz@ieng6.ucsd.edu

There are three parts to this line. 
1. ssh 
    - This is the ssh command. Put the place you want to connect after it
2. cse15lfa22zz
    - This is your username for the ssh. Replace zz with your account letters. eg: If your last two letters are ej, then cse15lfa22ej
3. @ieng6.ucsd.edu
    - Where you are connecting to. In this case, it would be ieng6 servers.
> This is me logging into the TA6 account because my password was not being accepted.
![image](./w1images/sshLogged.png)


---
## Running Commands on ssh
Here, we started to run some command line... commands.  
Here are a few that we used
|Command|Function|
|-------|--------|
|cd     |change directory|
|ls     |lists files in current directory|
|cp     |copy; can be used on files and directories (?)
|cat    |prints contents of a file|
|mkdir  |makes a new directory

I image of me accessing my partners directory via TA account (probably cannot do this on a regular student account)
 ![image](./w1images/sshcommands.png)


-----
## Moving files via scp
