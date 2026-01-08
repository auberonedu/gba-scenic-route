---
layout: book
title: "Forking and Cloning From GitHub"
nav_order: 200
has_children: false
parent: "Learning Your Environment"
---

# Forking and Cloning From GitHub

In this section we'll learn about how we can make our own copies of code hosted on GitHub. Make sure you've already gone through the previous section on Unix commands and have your command line open to the the `gba-scenic` directory you created.

## Forking

1. Make sure you are logged into your GitHub account.
1. Go to the [env-learning](https://github.com/auberonedu/env-learning) repository.
1. Fork the repository by clicking the **fork** button in the top right hand corner. It may take a moment for the fork to be created.
    > A fork is a *GitHub* concept, not a git concept. It's creating a copy of the repo in your online GitHub account, but it doesn't download the code to your computer.
    {: .note}

## Configuring Permissions
1. Ensure that you are looking at your fork of the repository. You should see `YOUR-USERNAME / env-learning` near the top of the screen, where `YOUR-USERNAME` is your GitHub username.
1. Click on the "Actions" tab at the top-middle of the screen. We will be using GitHub actions to publish your games, so these need to be enabled. Click the green Button to enable workflows.
1. Click on Settings, and then then the "Pages" option from the left bar.
1. Under Builder and deployment > Source, choose "GitHub Actions". This tells GitHub that we want to publish a website with your games, and that we will use GitHub Actions to do so. 


## Cloning
1. Go back to the "Code" tab of your repository.
1. Once again ensure that you are looking at your fork of the repository. You should see `YOUR-USERNAME / env-learning` near the top of the screen, where `YOUR-USERNAME` is your GitHub username. This is really important! We want to make sure we clone **your** version of the code, not the original you forked from.
1. Click on the green **Code** button. A small popup will appear
1. Choose the **Local** and **HTTPS** tabs. These are often selected by default.
1. You should see a URL. Click the overlapping squares next to it to copy the URL to your clipboard.
1. Return to your terminal window. Run the below command, replacing `YOUR-CLONE-URL` with the URL you copied from the green *Code* button on GitHub.
    ```
    git clone YOUR-CLONE-URL
    ```
    > Hint: In Windows Git Bash, paste by right-clicking. In Mac Terminal, paste by pressing cmd-V.
1. Verify that the repository was correctly copied by running `ls`. You should see `env-learning` as a directory. 
    >*Cloning* makes a copy from GitHub onto your computer.
1. Change to the repo directory by running:
    ```
    cd env-learning
    ```
    > Always make sure to `cd` into the repo directory after cloning! We'll be opening up VS Code in the repo directory, and our Dev Container will not work properly if we are a directory above it.
    {: .note}

Next, we'll open up your code in VS Code to start making changes!