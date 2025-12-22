---
layout: book
title: "A Lonesome Dot"
parent: "Exploration: Bubble Wrap"
nav_order: 200
---

# A Lonesome Dot

## Small Verifiable Goals

When we're programming it's best to set small incremental goals. It's OK (and good!) to dream big, but once we get down to the actual work of it, we want to to go bit by bit. What's the smallest useful thing I can do **THAT I CAN VERIFY IS WORKING**? That's what we're going to ask ourself over and over! We'll make a small goal, attempt to solve it, verify what works, fix what doesn't, and then come up with our next small goal. Often we'll need to loop back and forth between fixing and verifying many times before we can move on.

If we take hours and try to do everything at once and then it doesn't work, it'll be a nightmare trying to figure out what went wrong. But if we work incrementally, we have a lot smaller space of possibilities to search when something goes wrong.

Our goal for this first part of Bubble Wrap is going to be showing just a single circle on our GBA screen.

# TODO: Screenshot of a dot

We can go deeper though - having even smaller subgoals for each goal. Let's start with about as barebones as we can get...

## Microgoal #1: Getting the screen to show a blue background

We just want to have SOME visual confirmation that what we're doing is working. Setting the backdrop of the screen to show all blue will let us know we've done that. So let's get to work!

We'll begin opening up `main.cpp` which you can find in the `src` directory. It's totally empty to start! The first thing we'll want to add is a `main` method. We'll need this in every game we make. It's where the Game Boy will look to begin executing our code


