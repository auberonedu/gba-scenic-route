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

We'll begin opening up `main.cpp` which you can find in the `src` directory. It's totally empty to start!

### `int main()` function

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
be accessing something from the `backdrop` namespace within the `bn` namespace. Namespaces are ways of organizing and packaging together different pieces of code. We'll learn more about them on a later exploration. *TODO: link to later exploration*

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

Now that we've got the correct imports, let's try compiling again:

```
make
```

This one might take a little bit. You'll see that it lists off a lot of files from Butano. Just setting the backdrop colors causes a ton of dependencies to get pulled in! Don't worry though, it won't take this long every time. `make` is smart enough to only recompile files that have changed or that have had their dependencies changed since you last ran `make`.

But once it's finally done running, the last line should say `ROM fixed!`. If you look at the files, you'll see that a `bubble-wrap.gba` file has been created!

There's a lot of other files and folders that get created too. If you're curious, take a look in the `build` folder. There's dozens of files in there that get created when you run make! There's also a `bubble-wrap.elf`. Feel free to explore on your own for now, we'll talk more about what these files are later
{: .note }

## Running the ROM

We'll use our emulator mGBA to run the ROM you just created. 

# TODO: mGBA instructions

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

