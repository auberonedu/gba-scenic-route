---
layout: book
title: "Butano Boilerplate"
parent: "Tutorial: Bubble Wrap"
nav_order: 200
---

# Butano Boilerplate

To start off, we'll be learning the required **boilerplate** for Butano. Boilerplate is rote code that needs to be repeated almost verbatim for every project. In Butano, we'll almost always need to:

- Import Butano libraries
- Make a main function
- Initialize Butano
- Set up an event loop

## Small Verifiable Goals

When we're programming it's best to set small incremental goals. It's OK (and good!) to dream big, but once we get down to the actual work of it, we want to to go bit by bit. What's the smallest useful thing I can do **THAT I CAN VERIFY IS WORKING**? That's what we're going to ask ourself over and over! We'll make a small goal, attempt to solve it, verify what works, fix what doesn't, and then come up with our next small goal. Often we'll need to loop back and forth between fixing and verifying many times before we can move on.

If we take hours and try to do everything at once and then it doesn't work, it'll be a nightmare trying to figure out what went wrong. But if we work incrementally, we have a lot smaller space of possibilities to search when something goes wrong.

Our goal for this first part of Bubble Wrap is going to be simply setting the backdrop color. We just want to have SOME visual confirmation that what we're doing is working. Setting the backdrop of the screen to show all blue will let us know we've done that. So let's get to work!

## `int main()` function

We'll begin opening up `main.cpp` which you can find in the `src` directory. It's totally empty to start!

The first thing we'll want to add is a `main` function. We'll need this in every game we make. It's where the Game Boy will look to begin executing our code.

```cpp
int main() {
    
}
```

Every game needs an `int main()`
{: .note}

## Setting the backdrop color

Now let's make the main do something! We'll put a line of code in it that sets the backdrop to a nice pastel blue:

```cpp
int main() {
    bn::backdrop::set_color(bn::color(20, 20, 31));
}
```

Hmmm... when we put that in you'll probably get some red squiggles underneath parts of it. Our IDE isn't happy with us. Oh well! Let's worry about that in a moment. First let's talk about what we're trying to do, and then we'll see what's going wrong

The `bn` stands for Butano. It lets the compiler know we're using a function from the Butano library. `bn::backdrop` means that we're going to 
be accessing something from the `backdrop` namespace within the `bn` namespace. Namespaces are ways of organizing and packaging together different pieces of code. We'll learn more about them later.

`set_color` is a function within the `bn::backdrop` namespace. You can learn about it in the [Butano Docs](https://gvaliente.github.io/butano/namespacebn_1_1backdrop.html). `set_color` expects a color to be passed in, so we need to create one. We do so using the `bn::color` function.

`bn::color` takes 3 arguments: a red, green, and blue value. These are combined to describe the color. Lower values correspond to less of that color component. So our values of `20, 20, 31` means that there's a moderate amount of red, a moderate amount of green, and a lot of blue. This comes together to make a nice pastel blue. For each color component the values can go from 0 to 31.

Why 0 to 31? We'll answer this in more detail later when we discuss binary and hexadecimal, but the short answer is that the Game Boy Advance supports 15-bit colors - 5 bits for each color channel.
{: .question}

## Compiling

Let's try to compile this and see what happens! If it's not already there, pull up your termainl in VS Code (Terminal > New Terminal). If you're on Windows, make sure it's using Git Bash. If you're on Mac, make sure it's zsh.

Make sure you're in the `bubble-wrap` directory on your terminal. This won't do what it needs to if you're in the wrong directory! Then, type `make` and hit enter.

```
make
```

There will be a lot of output, but we should expect to get an error that looks something like this somewhere near the bottom. This is actually expected! I've given you some broken code so we can figure out what's wrong. To be fair, I warned you at the beginning this would be a scenic route.

```
/Users/auberon/programming/bubble-wrap/src/main.cpp: In function 'int main()':
/Users/auberon/programming/bubble-wrap/src/main.cpp:5:5: error: 'bn' has not been declared
    5 |     bn::backdrop::set_color(bn::color(20, 20, 31));
```

> ### I got a different error!
> The above error is expected and good at this point! But if you got a different error, there's something wrong with your setup. If you got an error that said that make is not installed or it doesn't know the command make, your overall setup was incorrect. Take another look at the [Environment Setup](../env-setup/index.md) and see if you can figure out what's going wrong.
> 
> If you got an error saying no makefile found, you're in the wrong directory. Use `cd` to find your way to the `bubble-wrap` directory and try again. Consider closing and re-opening your VS Code so it's exactly in the `bubble-wrap` directory, not above or below it.
{: .error}

## #include

What's going on? Well, we told the compiler that we want to use the `bn::backdrop` namespace, but then never included that in our code. Right now, all our `main.cpp` knows about is what we've written directly there. We need a way for `main.cpp` to see code that [GValiente](https://github.com/GValiente) wrote when he created Butano.

We do that using the `#include` preprocessor directive.

> ### Preprocessor directives and #include
> A **preprocessor directive** describes something that should happen in our build system even before the compiler sees the code. We'll recognize preprocessor directives because they start with a `#` (typically called a "pound", not a "hashtag").
>
> `#include` says to take something from another file, and essentially copy-paste it to the top of our file. So if I had `#include <cool_file.h>` in my `main.cpp` it would be as if I had copy-pasted all of `cool_file.h` at the top of `main.cpp` before sending it to the compiler.
> We'll meet a lot of other preprocessor directives later, like `#define`, `#ifndef` and so on.
{: .note}

For our file we'll need two includes: one for `bn::backdrop` and one for `bn::color`. Add these to the top of your `main.cpp`

```cpp
#include <bn_backdrop.h>
#include <bn_color.h>
```

How did I know which files to include? I looked at the docs! For example, on the [bn::backdrop page](https://gvaliente.github.io/butano/namespacebn_1_1backdrop.html) the needed include statement is on the top right corner. Nifty!


The Butano docs are a FANTASTIC source of information. It's **the** authoritative source of how to use Butano. As of early 2026, AI chatbots frequently get things wrong with Butano (a lot more so than for other more common libraries), hallucinating Butano functions or using them incorrectly. Prefer looking at the real documentation. Consider even just browsing through it, even when you don't have a speicifc problem to solve. It's cool just to see everything Butano can do!
{: .note}

Now that we've got the correct imports, let's try compiling again:

```
make
```

This one might take a little bit. You'll see that it lists off a lot of files from Butano. Just setting the backdrop colors causes a ton of dependencies to get pulled in! Don't worry though, it won't take this long every time. `make` is smart enough to only recompile files that have changed or that have had their dependencies changed since you last ran `make`.

But once it's finally done running, the last line should say `ROM fixed!`. If you look at the files, you'll see that a `bubble-wrap.gba` file has been created!

There's a lot of other files and folders that get created too. If you're curious, take a look in the `build` folder. There's dozens of files in there that get created when you run make! There's also a `bubble-wrap.elf`. Feel free to explore on your own for now, we'll talk more about what these files are later
{: .note }

## Running the ROM

We'll use our emulator mGBA to run the ROM you just created. Open up your ROM (the `.gba` file) in mGBA.

...but there's a problem. We wanted a blue screen, and when we actually got was all white! It turns out there's a few more things we need to add to set Butano up properly.

## Butano init

Before we call any functions for Butano, we need to *initialize* the Butano system. Do this by adding the following line to the beiginning of your `main` function (just before the `set_color`).

```cpp
bn::core::init();
```

We're also going to need to add something else to the top of our file. Can you think of what?

<details>
    <summary>
        Expand to see answer
    </summary>
<div markdown="1">
We need an include for `bn::core`
```cpp
#include <bn_core.h>
```
</div>
</details>

We can try it again! We'll `make` and run it in mGBA again. Fair warning though: it's not going to quite work and it's going to cause an annoying sound.

```
make
```

The good news is that compiling is much faster! You'll see it only needs to recompile `main.cpp` and not all of the Butano dependencies from before. The bad news is that we're only seeing a black screen and hearing an awful ticking sound.

## The update loop

Our issue is that we initialized Butano, set the backdrop, and †hen... nothing. We reached the end of our main method. Running on a normal computer this is where our program would end and control would return to the operating system. But the Game Boy Advance doesn't have an operating system! There's no good place to return to. If we try, bad garbage like our mysterious ticking sound can occur. We need to make sure our `main` never ends.

> ### Is it because we didn't `return 0;`?
> You may have noticed that `main` is an `int` function, and there's nowhere that we return an `int`. This is a problem for most C/C++ functions - it normally can cause all sorts of unsavory undefined behavior if we don't have a return statement for a non-void function. But there's actually an exception for `main` only. In `main`, if we don't have a return statement hit by the end of the function, it is implictly threated as a `return 0;`. Programming for a normal computer this is fine, but as explained above, `main` ending in ANY way is bad news on the GBA!
{: .question}

So what's a good way to make sure `main` never ends? How can we make sure a function keeps on executing forever? Take a guess as to how you think we'll do it!

<details>
    <summary>
        Expand to see answer
    </summary>
<div markdown="1">
We'll use an infinite loop.
</div>
</details>

This approach is going to be important beyond just making our ticking problem go away. In a real game we want to be continually doing stuff! Characters should be moving, music playing, AI plotting. We don't want to just run a piece of code and be done. It needs to keep going as the player interacts with the game.

By having an infinite loop, we can repeatedly do things like checking what buttons the player is pressing, moving characters around, and updating the positions of sprites on the screen. Butano will be a big help here. Once per screen refresh, we'll call `bn::core::update()`. Everything else that we do in Butano will get relfected with that update call. This update also automatically synchronizes with the screen refresh, so it should get called at 60fps so long as we keep calling it in a loop.

We'll definitely be expanding our loop later, but for now we'll start simple. Place this at the end of your `main` function (but still inside it, before that last curly brace!)

```cpp
while(true) {
    bn::core::update();
}
```

`while(true)` just means, "loop forever". A while statement stops looping when its condition is `false`, so if we say it's always `true`, it never stops! `bn::core::update();` handles the updating and will get called over and over again (synchronized to 60fps) until you turn off your GBA or the battery dies.

Make your code and run it one more time. I've got a good feeling about this one.

```
make
```

When running it in mGBA you should finally see a blue screen. Hallelujah! 

![A screenshot of a GBA running a ROM that displays a baby blue background](./blue_rect.png)

## Victory Lap

Phew! That was a lot just to get a blue background. We did take the scenic route to get there though, when you start a new project you can pretty much just copy-paste this boilerplate (standard piece of code) to get started.

We've got a lot more to do, but let's pause for a moment. The first thing you should be do is make sure your changes are saved and backed up. Do that using `git`

You should very frequently be adding, committing, and pushing in `git`! Every time you've got a new useful set of changes, make sure to make a commit!
{: .note}

### Git refresher
1. Make sure you're in the correct repository directory by running `pwd` (the path should end with `bubbleWrap`). If you're not, `cd` to the correct directory.
1. Run `git status` to check that the file(s) you edited show up in red.
1. Use `git add FILENAME` for each file you want to stage for a commit. Replace `FILENAME` with the name of the file.
    If you have multiple files to add, you can run `git add FILENAME FILENAME2 FILENAME3` and so on to add them all at once
    {: .note}
1. Use `git status` again to check that all the files you want to add are in green. Double check that you've got everything you want, and nothing you don't want.
    #### I made a mistake and added a wrong file!
    If you made a mistake and need to unstage a change, take a look at the output from `git status`. It'll tell you the correct command to unstage a file. Unstaging makes it so the file doesn't get added to the commit, but it doesn't delete the changes locally. `git` is very descriptive in its error messages and `git status` output. If you're ever unsure how to proceed with git, start by just reading what these messages say! It'll often directly tell you what to do.
    {: .error}
1. Use `git commit -m "YOUR COMMIT MESSAGE"` to make a commit.
    I recommend not using special characters like `!` for now, as your shell may interpret them as special commands. It is possible to include this punctuation, but it can be a bit of a pain using `-m`. If you're interested, search online for "escaping special characters in bash" or search for how to write commit messages using vim.
    {: .note}
1. Use `git push` to push your changes to GitHub.

### Experimenting and Verifying

Now is a great time to experiment. Trying changing the color around! Experiment with different numbers 0-31 in the red, green, and blue locations. Find a color you like! Or be mischevous: what happens if you try to put in a number that's outside of that 0 to 31 range? Only one way to find out!

If you've got a physical Game Boy Advance, now's a great time to experiment on there too. Copy over the ROM you created, and see what the color looks like on the Game Boy's screen. You'll notice that it looks a lot different than on your computer monitor! It's extremely useful to test on physical hardware frequently if you can.

Check that it works online too so you can easily share your game. On the right side of your repo, look for **Deployments** and choose **GitHub Pages**. Then click on the link to see the live "game" online.

> #### Not seeing the Deployments?
> If you don't see the deployments, there's likely one or more of a few issues:
> - It's your first time pushing and it's just not done deploying yet. Give it a minute or two.
> - You forgot to configure your repository properly
{: .error}

If you're going through this tutorial as part of a class I'm teaching, you are REQUIRED to choose a new color at this point. Fun and creativity is MANDATORY. I never want to see an assignment that you turn in that's just exactly what the tutorial told you to do. Always put at least a little spin on it. You'll have more and more opportunity to do this as your knowledge grows.

> #### Oh no, I broke it!
> As you're experimenting, things might stop working, and you may forget how to get them working again. This is OK, expected, and even GOOD! If you never break anything you're not experimenting enough!
>
> Git gives us a safety net so we can go back. A few simple ways to go back.
> - You can discard changes to a file since your last commit by using `git restore FILENAME`. DO be careful though! All those uncommitted changes are gone forever if you do this!
> - You can look at the state of your code from an earlier commit. The easiest way is to go to GitHub for your repository and click on the commit history button. It's just under the green code button, and says `N Commits`, where `N` is the number of commits in the repo.You'll then see the whole commit history (even commits I made before you forked the repo). Click on the the brackets `<>` next to a commit to see what the repo looked like at a previous point. You can copy some or all of the needed code.
>
> There are much more sophisticated ways to handle your git history (reverting/resetting commits etc.) but we'll explore those later.
{: .error}

Once you're done experimenting, add, commit, and push your changes again! Make sure your fun experiment gets saved!

## Next Steps

We've finally got SOMETHING working, but it's not really a game yet. Let's add some interactivity!