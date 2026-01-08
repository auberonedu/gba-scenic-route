---
layout: book
title: "Running a game in mGBA"
nav_order: 400
has_children: false
parent: "Learning Your Environment"
---

# Running a game on mGBA

In this section we will use the mGBA emulator to run a Game Boy Advance game.

## Determine the ROM location
1. Go back to the terminal you already had open OUTSIDE of VS Code (Git Bash or Mac terminal). We will use this to determine where our ROM is on your computer. We are **not** interested in where it is in the Dev Container.
1. Make sure you're in the right directory by running `pwd`
    ```
    pwd
    ```
1. This should end with `env-learning`. Everything before it is the folders of where `env-learning` is on your computer. Make a note of where it is. This is how we'll find the ROM. 

## Open the ROM

1. Open mGBA on your computer. Depending on how you installed it, you will either be able to search for it using the windows key or cmd-space, and then typing `mgba` or by going to your downloads and running it from there.
1. Click File > Load ROM
1. Find your ROM based off of where `pwd` said it was. Open the `env-learning.gba` ROM.
1. Run the game! The arrow keys correspond the to the d-pad and `z` and `x` are the **A** and **B** buttons.

Now that the game is running, let's try making a change!

