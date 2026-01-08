---
layout: book
title: "Unix Command Line Basics"
nav_order: 100
has_children: false
parent: "Learning Your Environment"
---

# Unix Command Line Basics

In this course we'll be using Unix-style commands to work with our code. Linux and Mac use unix-style commands on their command line by default, and on Windows we can emulate unix-style commands using Git Bash or by developing inside Linux containers / VMs. In this section we'll learn a few of the fundamental commands and concepts.

## Opening Your Command Line

We'll start by opening your command line. On Windows, open Git Bash (press the Windows key and search for "Git Bash"). On Mac, open your search bar with `cmd-space` (hold the command key and press the space bar), then type terminal and hit enter.

You should be greeted by a simple text based prompt.

## Your Home Directory

We'll now open your **Home Directory**. This is a folder where all of the files owned by your specific user account are located.

> ### Directory vs. folder
> When we're on the command line we often use the word *directory*. This means the exact same thing as *folder*. It's just a more command-liney way to say it.
{: .note}

What does it mean to open a directory on the command line? It means that we change our **working directory**. A working directory is the directory that we are currently in where all of our command will be executed in. You can think of it as similar to the Windows Explorer / Mac Finder, where we always have a specific folder that's open and we're able to see its contents. It's the same idea on the command line! We always have a working directory where all of our commands will be executed from. It's very important to know what directory we're in - many commands will not work if we're in the wrong directory.

To change to your home directory, type the below command and hit enter:

```
cd ~
```

On Windows you CANNOT use ctrl-C / ctrl-V to copy/paste to Git Bash. ctrl-C has a special different meaning on the command line that we'll learn later. Instead, if you want to copy a command you can use the right mouse button.
{: .error}

What did `cd ~` do? It **changed** our working **directory** to our home directory. That's what the `cd` stands for: **c**hange **d**irectory. The `~` (pronounced "tilde") is a nickname for our home directory. But where is that?

## Print Working Directory

At any point we can always check what our working directory is with the below command. Run it now:

```
pwd
```

`pwd` stands for **p**rint **w**orking **d**irectory. It will show you the full path of your working directory. Make a note of where your working directory is, it's different on Windows vs. Mac.

## Listing Files in a Directory

So now we know where we are, but what's in your home directory? We can list the the files/folders in it to find out. Use the `ls` command:

```
ls
```

`ls` stands for **l**i**s**t. It shows us what's inside our working directory. There may be a LOT of stuff in there. Take a quick peruse! Explore your curiosity.

> ### What about hidden files?
> Want to see hidden files? Use `ls -a` to show **a**ll the files. The `-a` is a command line flag. It modifies how the command operates. We'll learn more about flags later.
{: .question}

## Making a New Directory

Next, let's make a new directory (a new folder). Run the following command:

```
mkdir gba-scenic
```

You won't see any feedback. That's OK and expected! Often our commands on the command line don't show any output when they're successful.

`mkdir` stands for **m**a**k**e **dir**ectory. It creates a new folder named `gba-scenic` *in your current working directory*. That's important! Commands do different things depending on what your working directory is!

So how do we check that it worked? Simple! We can use `ls`.

```
ls
```

Scroll through the output and verify that there's a new `gba-scenic` directory.

## Changing to Your New Directory

Let's now change our working directory to `gba-scenic`. You can use `cd` again, this time specifying the `gba-scenic` directory.

```
cd gba-scenic
```

Note that your command line prompt will change - the end of it should now say `gba-scenic`. This is a nice little hint as to what our current directory is.

What's in this new directory? Run `ls` to find out:

```
ls
```

There's nothing there! We haven't made anything yet. Let's go ahead and change that. In the next section we'll populate this directory with some Game Boy Advance code we'll get from a GitHub repository. 