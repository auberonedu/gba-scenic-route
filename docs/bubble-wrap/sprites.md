---
layout: book
title: "Intro to Sprites"
parent: "Tutorial: Bubble Wrap"
nav_order: 400
---

# Intro to Sprites

In this section we'll start to explore **sprites** one of the core graphical concepts of the Game Boy Advance. You can think of a sprite as a small that the Game Boy is able to render to the screen. The Game Boy advance hardware has support for quickly rendering and moving many sprites, as well as rotating, scaling, and otherwise transforming some sprites. When we work with the Game Boy Advance graphics, we'll mostly be working with **sprites** and **backgrounds** because of the hardware-accelerated support for these types of graphics.

It's not just at the software level! There is actual hardware-level support hard-wired into the Game Boy Advance for dealing with sprites and backgrounds. 
{: .note}

> Are there non-sprite ways to make graphics using the Game Boy Advance?
>
> Yes, there are other modes that the GBA supports for making graphics that aren't sprite based, namely bitmap modes. These however are much less commonly used because the rendering needs to happen on the software side. The vast majority of Game Boy Advance games make heavy use of sprites.
{: .question}

## Files needed for a sprite

To make a sprite in Butano, we use two files: a BMP and a JSON file. In the bubble-wrap repo you forked there is already a sprite set up. You can see the files under the `graphics` directory. Take a look at `dot.bmp` and `dot.json` now! What do you see?

Any time you want to add a new sprite, you'll need to make a new BMP AND a new JSON file. It won't work without the JSON!


## Image requirements

As of Butano 21.0.0, there are a number of requirements for images to be imported as sprites. For authoritative details on what's required, see Butano's [Importing Assets page](https://gvaliente.github.io/butano/import.html). There's A LOT in there though, so I'll summarize the most important parts for our purposes below.

### Images must be plain bmps

Butano requires a very specific format: BMPs that
- are uncompressed
- have no color space information
- have 16 or 256 colors in the palette

Most image editors or BMPs you find on the internet will not work due to these constraints. That's part of why we're using LibreSprite (particularly in indexed mode): because it handles all the formatting we need and makes editing palettes easy.

> What about Usenti?
>
> The Butano docs recommend using [Usenti](https://github.com/gb-archive/usenti) to edit sprites. This is a great option, but it unfortunately is Windows-only. To make this tutorial cross-platform we'll be using LibreSprite, but feel free to use Usenti instead if you prefer it.
{: .question}

> OK, what about Aseprite then?
>
> LibreSprite is actually a fork of another sprite editor called [Aseprite](https://www.aseprite.org/). Aseprite used to be fully free open-source software, but it is no longer. You can buy it, or use it for free if you choose to compile from source. It is more-fully featured that LibreSprite, and might be a bit nicer to work with. But to keep things FOSS for this guide and to avoid needing to do a full buoild of a sprite editor, the instructions here will be for LibreSprite. That being said, feel free to use Aseprite if you are willing to pay for it or compile.
{: .question}

## Image JSON files
Each image needs an accompanying JSON file to tell Butano how to use the image. There are A LOT of different attributes you can put here (again look at Butano's [Importing Assets page](https://gvaliente.github.io/butano/import.html) if you want full details), but we'll just focus on a few for now.

- **type** specifies how Butano should use this image. Is it a sprite? A background? Just a palette?
- **height** specifies how tall a sprite is

> Why do we need to specify the height? Can't Butano tell from the image itself?
>
> The reason we need to specify the height is because we we will end up including multiple sprite images in a single bmp. This will be valuable for showing different versions of a sprite, like a selected/unselected button or multiple frames of a walking animation. The height will tell Butano how tall each individual sub-image is so that Butano can cleanly separate them. LibreSprite will help us with making spritesheets that hold multiple sub-images.
{: .question}

## Compiling the images

You may not have noticed, but we've actually already compiled the `dot.bmp` image into your game when we ran `make`. Let's take a look!

### The build directory

To see that, look into the `build` directory. There's A LOT there, but don't be concerned, you don't need to understand all of this and most of the time you never need to look here! In fact, we should NEVER need to edit any of the files in the `build` directory directly; they're all machine generated. Take a moment to explore, but know that VS Code won't render `.o` or `.bin` files because they're not text files.

> I don't see a `build` directory!
>
> The build directory only gets created when you compile your game using `make`. If you're just browsing the files on GitHub or you haven't compiled your game yet you won't see any build directory. 
{: .error}

The build directory is where all our intermediate files go as the compilation occurs. It's not just a quick one step from code to a finished `.gba` file, there's a LOT that happens behind the scenes when you run make!

One of the benefits of having these intermediate files is that it makes recompiling after incremental changes much faster. Our build process is able to re-use work that it's already done, and only recompile the things that have changed.
{: .note}

There are a few main types of files you'll see in your build directory:

- `.o` **Object files**: These are compiled C/C++ code files
- `.d` **Make Dependency files**: These files tell `make` what files depend on others. This is how `make` knows what needs to be recompiled and what doesn't when you make a change.
- `.h` **Header files**: These C/C++ files are often used for declaring functions/classes/etc. are defined in the `.o ` files. They form an interface so different pieces of code know how to call one another. We'll be making our own header files later!
- `.bin` **Binary files**: These files hold raw data. This is mostly used by Butano for storing sounds.
- `.s` **Assembly Source files**: These files hold assembly code - direct descriptions of CPU instructions and data that can be converted into machine code.
- `.txt` **Plain text files**: These files hold extra metadata in plain text
