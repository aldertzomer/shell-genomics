---
title: "Introducing the Shell"
teaching: 20
exercises: 10
questions:
- "What is a command shell and why would I use one?"
- "How can I move around on my computer?"
- "How can I see what files and directories I have?"
- "How can I specify the location of a file or directory on my computer?"
objectives:
- "Describe key reasons for learning shell."
- "Navigate your file system using the command line."
- "Access and read help files for `bash` programs and use help files to identify useful command options."
- "Demonstrate the use of tab completion, and explain its advantages."
keypoints:
- "The shell gives you the ability to work more efficiently by using keyboard commands rather than a GUI."
- "Useful commands for navigating your file system include: `ls`, `pwd`, and `cd`."
- "Most commands take options (flags) which begin with a `-`."
- "Tab completion can reduce errors from mistyping and make work more efficient in the shell."
---

## What is a shell and why should I care?

A *shell* is a computer program that presents a command line interface
which allows you to control your computer using commands entered
with a keyboard instead of controlling graphical user interfaces
(GUIs) with a mouse/keyboard/touchscreen combination.

There are many reasons to learn about the shell:

* Many bioinformatics tools can only be used through a command line interface. Many more 
have features and parameter options which are not available in the GUI.
BLAST is an example. Many of the advanced functions are only accessible
to users who know how to use a shell.  
* The shell makes your work less boring. In bioinformatics you often need to repeat tasks with a large number of files. With the shell, you can automate those repetitive tasks and leave you free to do more exciting things.  
* The shell makes your work less error-prone. When humans do the same thing a hundred different times
(or even ten times), they're likely to make a mistake. Your computer can do the same thing a thousand times
with no mistakes.  
* The shell makes your work more reproducible. When you carry out your work in the command-line 
(rather than a GUI), your computer keeps a record of every step that you've carried out, which you can use 
to re-do your work when you need to. It also gives you a way to communicate unambiguously what you've done, 
so that others can inspect or apply your process to new data.  
* Many bioinformatic tasks require large amounts of computing power and can't realistically be run on your
own machine. These tasks are best performed using remote computers or cloud computing, which can only be accessed
through a shell.

In this lesson you will learn how to use the command line interface to move around in your file system. 

## How to access the shell

On a Mac or Linux machine, you can access a shell through a program called "Terminal", which is already available
on your computer. The Terminal is a window into which we will type commands. If you're using Windows, you'll need to download a separate program to access the shell.

To save time, we are going to be working on a remote server where all the necessary data and software is already available. When we say a 'remote sever', we are talking about a computer that is not the one you are working on right now. You will access the Carpentries remote server where everything is prepared for the lesson.
We will learn the basics of the shell by manipulating some data files. Some of these files are very large, and would take a long time to download to your computer.
We will also be using several bioinformatic packages in later lessons and installing all of the software would take up even more time. A 'ready-to-go' sever let's us focus on learning how to use it. 

## How to access the remote server

From edition 2024 forward at Utrecht University we will use the gemini server for all our remote work. To access this server we need some software like a terminal and a file browser/commander. You can find a detailed guide at this [setup section](https://aldertzomer.github.io/shell-genomics/setup.html) After you installed the required software and connect we end-up in a black box with text where you can issue commands that will run on the server. It will look similar to the example below:

&nbsp;&nbsp;&nbsp; ![image](https://github.com/user-attachments/assets/998ac1d4-2b7a-4fa1-92fe-d17ca938437b)

The welcome text already provides us some server related information. It is important that we activate our (conda) course working environment using the `course B-MBIMIGE` command. The prompt should change (arrow) indicating that the environment is ready!  

At any time the terminal gets too cluttered, type the word `clear` into the terminal and press the `Enter` key.

~~~
$ clear
~~~
{: .bash}

This will scroll your screen down to give you a fresh screen and will make it easier to read. 
You haven't lost any of the information on your screen. If you scroll up, you can see everything that has been output to your screen
up until this point.

> ## Tip
> Hot-key combinations are shortcuts for performing common commands.
> The hot-key combination for clearing the console is `Ctrl+L`. Feel free to try it and see for yourself.
{: .callout}

## Navigating your file system

The part of the operating system that manages files and directories
is called the **file system**.
It organizes our data into files,
which hold information,
and directories (also called "folders"),
which hold files or other directories.

Several commands are frequently used to create, inspect, rename, and delete files and directories.

> ## Preparation Magic
> You may have a prompt (the characters to the left of the cursor) that looks different from the `$` sign character used here. Usually depending on the linux system it also shows you the PATH (folder) your are currently in compared to your HOME (~/) folder.
{: .callout}

~~~
$
~~~
{: .bash}

The dollar sign is a **prompt**, which shows us that the shell is waiting for input;
your shell may use a different character as a prompt and may add information before
the prompt. When typing commands, either from these lessons or from other sources,
do not type the prompt, only the commands that follow it.

Let's find out where we are by running a command called `pwd`
(which stands for "print working directory").
At any moment, our **current working directory**
is our current default directory,
i.e.,
the directory that the computer assumes we want to run commands in,
unless we explicitly specify something else.
Here,
the computer's response is similar to `/nethome/solisid`,
which is the top level directory within our cloud system:

~~~
$ pwd
~~~
{: .bash}

~~~
/nethome/solisid
~~~
{: .output}

Let's look at how our file system is organized. We can see what files and subdirectories are in this directory by running `ls`,
which stands for "listing":

~~~
$ ls
~~~
{: .bash}

~~~
data
~~~
{: .output}

`ls` prints the names of the files and directories in the current directory in
alphabetical order,
arranged neatly into columns. 
We'll be working within the `shell_data` subdirectory, and creating new subdirectories, throughout this workshop.  

The command to change locations in our file system is `cd`, followed by a
directory name to change our working directory.
`cd` stands for "change directory".

Let's say we want to navigate to the `data` directory we saw above.  We can
use the following command to get there:

~~~
$ cd data
~~~
{: .bash}

We will now move a few directories deeper (since we are in a linux environment all files and folders needed are available from the `~/data/DataCarpentry` directory. Let us mover there first and then look at what it contains. This directory is READ ONLY so you cannot damage anyones files.  
  
Let's move and look at what is in this directory:

~~~
$ cd ~/data/DataCarpentry/shell_data
$ ls
~~~
{: .bash}

~~~
sra_metadata  untrimmed_fastq
~~~
{: .output}

We can make the `ls` output more comprehensible by using the **flag** `-F`,
which tells `ls` to add a trailing `/` to the names of directories:

~~~
$ ls -F
~~~
{: .bash}

~~~
sra_metadata/  untrimmed_fastq/
~~~
{: .output}

Anything with a "/" after it is a directory. Things with a "*" after them are programs. If
there are no decorations, it's a file.

Another useful option is --color. The command `ls --color` will show the same but now using colors to discriminate between folders, executable files/programs or regular files. In many linux environments (for instance those based on debian/Ubuntu) the coloring is the default (also for our server we currently work on it might be that we already enabled this by default).

`ls` has lots of other options. To find out what they are, we can type:

~~~
$ man ls
~~~
{: .bash}

`man` (short for manual) displays detailed documentation (also referred as man page or man file)
for `bash` commands. It is a powerful resource to explore `bash` commands, understand
their usage and flags. Some manual files are very long. You can scroll through the
file using your keyboard's down arrow or use the <kbd>Space</kbd> key to go forward one page
and the <kbd>b</kbd> key to go backwards one page. When you are done reading, hit <kbd>q</kbd>
to quit.  
  
Alternative many commands give you a shorter explanation by appending &minus;&minus;help after the command or if that doesn't work try &minus;h instead. Try it yourself for the `ls` command: `ls --help`.  


> ## Challenge
> Use the `-l` option for the `ls` command to display more information for each item 
> in the directory. Since it is used very often most shell environments provide the alias `ll` which stands for `ls -l` which is laborious to type every time.  
> What is one piece of additional information this long format gives you that you don't see with the bare `ls` command?
>
> > ## Solution
> > ~~~
> > $ ls -l
> > ~~~
> > {: .bash}
> > 
> > ~~~
> > total 8
> > drwxr-x--- 2 dcuser dcuser 4096 Jul 30  2015 sra_metadata
> > drwxr-xr-x 2 dcuser dcuser 4096 Nov 15  2017 untrimmed_fastq
> > ~~~
> > {: .output}
> > 
> > The additional information given includes the name of the owner of the file,
> > when the file was last modified, and whether the current user has permission
> > to read and write to the file. In section [Section 3 - working with files and directories](https://aldertzomer.github.io/shell-genomics/03-working-with-files/) we'll explain more what the actual letters in which position actually mean.
> > 
> {: .solution}
{: .challenge}

No one can possibly learn all of these arguments, that's what the manual page and --help option 
is for. You can (and should) refer to the manual page or other help files as needed. They can be viewed in the shell but most of the manpages are also available online!

Let's go into the `untrimmed_fastq` directory and see what is in there.

~~~
$ cd untrimmed_fastq
$ ls -F
~~~
{: .bash}

~~~
SRR097977.fastq  SRR098026.fastq
~~~
{: .output}

This directory contains two files with `.fastq` extensions. FASTQ is a format
for storing information about sequencing reads and their quality.
We will be learning more about FASTQ files in a later lesson.

### Shortcut: Tab Completion

Typing out file or directory names can waste a
lot of time and it's easy to make typing mistakes. Instead we can use tab complete 
as a shortcut. 

Return to your home directory:

~~~
$ cd
~~~
{: .bash}

then enter:

~~~
$ cd da<tab>
~~~
{: .bash}

Here `<tab>` means the actual TAB key (<kbd>Tab</kbd>) on your keyboard. The shell will fill in the rest of the directory name for
`shell_data`. If there are more directories or files matching the entered text hit <kbd>Tab</kbd><kbd>Tab</kbd> and a list of matches will be shown allowing you to further specify which directory you actually mean y adding additional characers and hit <kbd>Tab</kbd> again.

Now change directories to `untrimmed_fastq` in `data` using tab-completion, we'll have to navigate through 2 additional directories

~~~
$ cd ~/data/DataCarpentry/shell_data/untrimmed_fastq
~~~
{: .bash}

Using tab complete can be very helpful. However, it will only autocomplete
a file or directory name if you've typed enough characters to provide
a unique identifier for the file or directory you are trying to access.

For example, if we now try to list the files which names start with `SR`
by using tab complete:  

~~~
$ ls SR<tab>
~~~
{: .bash}

The shell auto-completes your command to `SRR09`, because all file names in 
the directory begin with this prefix. When you hit
<kbd>Tab</kbd> again, the shell will list the possible choices.

~~~
$ ls SRR09<tab><tab>
~~~
{: .bash}

~~~
SRR097977.fastq  SRR098026.fastq
~~~
{: .output}

Tab completion can also fill in the names of programs, which can be useful if you
remember the beginning of a program name.

~~~
$ pw<tab><tab>
~~~
{: .bash}

~~~
pwck      pwconv    pwd       pwdx      pwunconv
~~~
{: .output}

Displays the name of every program that starts with `pw`. 

## Summary

We now know how to move around our file system using the command line.
This gives us an advantage over interacting with the file system through
a GUI as it allows us to work on a remote server, carry out the same set of operations 
on a large number of files quickly, and opens up many opportunities for using 
bioinformatic software that is only available in command line versions. 

In the next few episodes, we'll be expanding on these skills and seeing how 
using the command line shell enables us to make our workflow more efficient and reproducible.
