---
layout: book
title: "Adding, Committing, Pushing"
nav_order: 500
has_children: false
parent: "Learning Your Environment"
---

# Adding, Committing, Pushing

In this section we'll learn about how to use git to version our code and back it up on GitHub.

## Making a change

1. Go back to VS Code and open `README.md`. This is what first shows up when the repo is viewed on GitHub.
1. Make some small change to the README. It can be as simple as adding the word "hello".
    > Note that the change you make will be public for anyone on the internet to see.
1. Save the changes.

## Add and commit changes
1. Return to the terminal. It should still be in the `env-learning` directory.
1. Run the below command to check the status of your changes.
    ```
    git status
    ````
    You should expect to see `README.md` in red text.
1. Run the below command to stage your change for a commit:
    ```
    git add README.md
    ```
    > This tells git that you want your changes to the `README.md` file to be included in your next commit.
1. Check the status again:
    ```
    git status
    ```
    `README.md` should now be in green text.
1. Commit the change with some meaningful description:
    ```
    git commit -m "SOME MEANINGFUL DESCRIPTION"
    ```
    > Make sure your description is in quotation marks. It should be a short phrase like "Added haiku to README." For now, do not use special characters like an exclamation mark. This can confuse your terminal.

    > Making a commit is like making a checkpoint. You'll always be able to come back to the way your code is now. However, your commit is only on your computer right now. It is not yet backed up to GitHub.

## Push changes
1. Check the status:
    ```
    git status
    ```
    You should see a message that includes the line `Your branch is ahead of 'origin/main' by 1 commit`.
    > This is telling us that we have one commit that isn't yet backed up to GitHub
1. Push the change to GitHub
    ```
    git push
    ```
1. You should get a pop-up asking you to authenticate using GitHub. Follow the steps to do so on the web in your browser.
1. If it completes without errors, return to your browser page with YOUR fork (your username should be at the top of the screen and in the URL) of the repo open. Refresh the page and you should see your new change to the README!
   > Note that the changes you have made so far apply ONLY to your fork, not to the original repoitory that I created. Your version is changed, but GitHub won't let you change mine without my permission.

## Your turn
1. Great! Now it'll be your turn to make a more meaningful change.
1. First, go to `main.cpp`.
1. Make a change to the game (consider first doing something like just changing a color).
1. Run `make` to compile the game again. Fix any errors if they come up.
    ```
    make
    ```
1. Open your ROM in mGBA to see your new changes.
1. Once you're satisfied with your changes, follow the above steps to add, commit, and push your modifications to `src/main.cpp`

Next, we'll explore how your game gets published to the web for anyone to play!