---
layout: book
title: "Using VS Code With a Dev Container"
nav_order: 300
has_children: false
parent: "Learning Your Environment"
---

# Using VS Code With a Dev Container

In this section we'll learn how to use VS Code and Dev Containers.

## Opening Docker Desktop
Before running VS Code with a Dev Container, we need to make sure Docker Desktop is running. Please open it now. You can leave it running in the background.

## Opening VS Code
1. Make sure you have your terminal open to the `env-learning` directory.
    ```
    pwd
    ```
    Ensure that the result of `pwd` ends with `env-learning`.
1. Open VS Code in the current directory by running:
    ```
    code .
    ```
    If this does not work, you can instead open VS Code, and click on File > Open Folder. Then find and select the `env-learning` folder. Either way, keep the terminal window open. We will return it it soon.

## Opening in a Dev Container
1. VS Code should automatically detect that there is a Dev Container in this repo. There will likely be a pop-up in the bottom right corner asking if you want to re-open the project in a Dev Container. Click the button to do so.
    > If the pop-up does not appear, you can manually choose to re-open in container by clicking the button with the left and right arrows in the VERY bottom left of the VS Code window. It will pop up a list of options at the top of the window. Choose "Reopen in Container"
    {: .note}
1. This will create a new container (similar to a lightweight virtual machine) that has all the tools we need for Game Boy Advance Development set up in it. It will take a while the first time it sets up, there's a lot it needs to download. It will be faster after the first time.
    > ### How does VS Code Know How to Configure the Environment?
    > The configuration for the Dev Container is in the `.devcontainer` directory. Feel free to take a peek in there to explore your curiosity if you like! You won't need to change anything there, but it might be interesting to see.
    {: .question}

## The Dev Container Terminal
1. Once the repo has been reopened in a container, you will be able to use the environment. Open a new terminal by clicking the "Terminal" button at the top of the screen and choosing "New Terminal". NOTE THAT THIS TERMINAL is running in the *Dev Container* **NOT** on your host computer.
1. Do a quick `ls` in the terminal. You should see roughly the same files/folders as a re shown on the left of `VS Code`.

## Making the Sample Game
1. The code for the game is in `src/main.cpp`. Click on the arrow next to `src` on the left panel to expand the directory, then click on `main.cpp`.
1. Take a quick look through the file. It's OK if you don't fully understand it yet!
1. We will now make a game using `make`. Go to the terminal in VS Code and run:
    ```
    make
    ```
1. This will compile the game. It will take a while the first time, but will be faster on subsequent makes.
    > ### How does `make` know how to make the game?
    > The configuration for `make` is in the `Makefile` file. Feel free to open it up and take a quick look if you're curious. Most of the magic happens in Butano / DevKitArm's Makefiles, but this one shows you how they're configured. Explore your curiosity!
    {: .question}
1. If all goes well, a few files will be created, including `env-learning.gba`. This is your compiled Game Boy Advance ROM!

After the game compiles, we'll try running it in mGBA!
