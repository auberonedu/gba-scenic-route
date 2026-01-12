---
layout: book
title: "Docker / VS Code Setup"
nav_order: 200
has_children: false
parent: "Environment Setup"
---

# Docker / VS Code Setup

We will be using Docker Desktop, VS Code, and Devcontainers for our development environment. This page will lead you through setting them up.

## Install Docker Desktop

Install [Docker Desktop](https://www.docker.com/products/docker-desktop/). Once it is installed, open it. Note that this may require a restart and admin privileges.

On Windows, you may get a message stating that WSL needs to be installed or updated. If you get this message, follow the instructions it gives to either run `wsl --install` or `wsl --update` in Git Bash.

We will always need Docker Desktop running in the background when we're doing our development! If later you're ever trying to open a devcontainer and it's not working, double-check that Docker Desktop is running.

## VS Code

Next, install [VS Code](https://code.visualstudio.com/download). This will be the editor we'll use for our code.

Mac Only - Follow these instructions to [add VS Code to your PATH](https://code.visualstudio.com/docs/setup/mac#_configure-the-path-with-vs-code).

## Dev Containers Extension

Install the [Dev Containers Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) for VS Code. This will allow VS Code, Docker Desktop, and special development environments I've configured specifically for this scenic route to work together. Note that when you click the install button, it will ask for permission to open VS Code. Give it permission to do so.