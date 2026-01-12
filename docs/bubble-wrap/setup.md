---
layout: book
title: "Bubble Wrap Setup"
parent: "Tutorial: Bubble Wrap"
nav_order: 100
---

# Bubble Wrap Setup

Let's get set up! I'll be writing these instructions assuming that you've followed the instructions in the [Environment Setup]({% link env-setup/index.md %}). It will be possible to follow along using only the online Codespace environment, but it might be a bit painful at points. You've been warned!

## GitHub Configuration

This will look very similar at the start of each project. We'll be starting from a repository already provided for you, and editing from there. Below are abbreviated steps, if you want more detail feel free to look back at the [Forking and Cloning instructions]({% link env-practice/forkClone.md %}). Just make sure to do it with the new <a href="https://github.com/auberonedu/bubble-wrap" target="_blank" rel="noopener">Bubble Wrap Repo</a>.

1. Open the <a href="https://github.com/auberonedu/bubble-wrap" target="_blank" rel="noopener">Bubble Wrap Repo</a> in a new tab.
1. FORK THE REPO by cliicking the fork button. This is important! If you forget to fork you won't be able to push any changes.
1. Enable workflows under the Actions tab
1. Under Settings > Code and automation > Pages > Build and deployment > Source choose **GitHub Actions**

## Cloning and opening in VS Code
1. Open a new terminal / git bash.
1. Navigate to the gba-scenic directory `cd ~/gba-scenic`
1. Go back to GitHub and get copy the clone link (Code tab > Green Code Button > HTTPS tab)
1. Go back to your terminal and run `git clone CLONE_URL`
1. Switch into the `bubble-wrap` directory: `cd bubble-wrap` (DO NOT FORGET THIS! THE DEV CONTAINER WILL NOT WORK PROPERLY IF YOU SKIP THIS)
1. Open VS Code: `code .`
1. Reopen in Dev Container. Click the button to reopen in container if prompted, otherwise click the arrows at the VERY bottom left of the window, and choose to reopen in container (DO NOT FORGET THIS!)

If you did everything properly, your code should be open in VS Code, the bottom left hand corner will note that you're in a Dev Container, and the open workspace will be for `bubble-wrap`. If that's all good, we can finally get to coding!
