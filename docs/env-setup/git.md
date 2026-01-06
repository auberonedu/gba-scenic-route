---
layout: book
title: "Git / GitHub Setup"
nav_order: 100
has_children: false
parent: "Environment Setup"
---

# Git / GitHub Setup

## Creating a GitHub Account
We will be making use of GitHub to download code, back up our changes, and host our games online for anyone to play. If you already have a GitHub account, sign into it now. If you do not, create one on [GitHub](https://github.com/).

## Installing Git
Git is Version Control Software. It will allow us to keep track of our changes, collaborate with others, and handle pushing/pulling to/from GitHub.


### Installing Git on Windows
For Windows - install [Git For Windows](https://gitforwindows.org/)


### Installing Git on Mac
1. Press `cmd-space` (hold down the command key and press space) and then type `terminal` and hit enter. This will open open a terminal where you can write commands. We will use commands to install Homebrew, XCode Command Line Tools, Git, and the Git Credential Manager.
1. Follow these instructions on [How to Use Homebrew to Install Xcode Command Line Tools](https://www.freecodecamp.org/news/install-xcode-command-line-tools#heading-how-to-use-homebrew-to-install-xcode-command-line-tools). Make sure you're following the part of the page that walks you through using Homebrew for the installation!
1. Close all open terminals, then open a new one again. Run the below command to install the git credential manager:
    ```
    brew install --cask git-credential-manager
    ```


## Configuring Git

We will now configure your git installation from the command line. Note that on Windows you CANNOT copy-paste using ctrl-c/ctrl-v. Instead, use the right mouse to paste to your command line.

On Windows, open Git Bash (press the windows key and type `Git Bash`).
On Mac, open a terminal (`cmd-space` then type `terminal`).

1. First, verify that git is installed correctly. Run the below command by copying it and hitting enter:
    ```
    git --version
    ```
    You should see the version number of your git. If you get an error message instead, please close all your open terminals, reopen and try again. If you're still getting an error message there is an issue with your git installation.
1. Set your username. This name will be publicly posted to GitHub. If you do not want your real name to be posted it is OK to use a pseudonym. Set your name by typing the following command and hitting enter:
    ```
    git config --global user.name "YOUR_NAME"
    ```
    (Replace YOUR_NAME with the name you want to use, but make sure to keep the quotation marks.)
1. Set your email to private. Keep your terminal open, but also open a browser window. Make sure you're logged into GitHub. The go to [the GitHub email settings page](https://github.com/settings/emails). 

    Scroll down and find a checkbox for "Keep my email addresses private". Make sure it is checked. Next to the checkbox will be a long description that will include a no-reply email that will look something similar to 12345678+fakeuser@users.noreply.github.com. Copy that address from GitHub. Switch back to the terminal window.
1. Set your email. In your terminal, type the below and then hit enter:
    ```
    git config --global user.email "YOUR_NOREPLY_EMAIL"
    ```
    (replace YOUR_NOREPLY_EMAIL with the no-repy email you copied from GitHub, but keep the quotation marks)
1.  Set your merging strategy. In your terminal, type the below and hit enter. This will configure the way that git acts when collaborating with others.
    ```
    git config --global pull.rebase false
    ```
1. Set default push behavior. In your terminal, type the below and hit enter. This allows for easy creation of branches.
    ```
    git config --global push.default current
    ```
1. Set line ending behavior. This helps to avoid problems between Mac/Linux/Windows handling of files:
    ```
    git config --global core.autocrlf false
    git config --global core.eol lf
    ```
