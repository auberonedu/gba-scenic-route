---
layout: book
title: "Flash Carts"
nav_order: 100
has_children: false
parent: "Hardware"
---

# Flash Carts

The tool we'll be using to play our games on the GBA is a **flash cart**. There are other ways to do it, but this is by far the most flexible and straightforward. The flash carts we'll discuss are specialized GBA game cartidges made specifically for homebrew development. They can read GBA ROMs stored on MicroSD cards and provide an interface for the Game Boy to play them just as if it were a native cartidge, no emulation required!

> ## What other ways could we play our games other than a flash cart?
> The main other method to play our games would be using the GBA **multiboot** capability. This functionality was originally designed so that multiplayer games could be played on multiple Game Boys even if only one of the players owned a cartridge. The Game Boys would be linked via a Link Cable, and the Game Boy with the cartridge would send game data over the cable to the other handheld. The handheld without the cartidge would store the game data in RAM, and then both could play together.
>
> We can exploit this to play our own games if we physically modify a link cable so that one side connects to a GBA and the other connects to our computer. We then have our computer send over the game data for our homebrew game, and the GBA can play it!
>
> A modified link cable is cheaper than a flash cart, so why are we choosing to use flash carts instead of multiboot in this guide? It's because there's one very big drawback to multiboot games. The game can only be stored in a 256kB section of RAM known as **EWRAM** (we will learn about the various types of RAM and storage later in this guide). 256 kilobytes is small, even by the Game Boy Advance's standards. For reference, Pokémon Emerald is about 6 **mega**bytes, more than 20x what could fit in EWRAM!
>
> Using multiboot, we would only be able to make teeny tiny games; using a flash cart we will be able to make games that are the same size as commercial GBA games. That's why this guide will focus on flash carts.
{: .question}

## Flash Cart Recommendations

I have personally used 2 flash carts, the [EZ Flash Air](https://www.ezflash.cn/product/ez-flash-air/) and the [Everdrive GBA Mini](https://krikzz.com/our-products/cartridges/everdrive-gba-mini.html). I would be happy to recommend either, depending on the price point you are looking for.

**Budget Pick**: EZ Flash Air

**Premium Pick**: Everdrive GBA Mini

There are many other options out there, but I simply can't speak to them because I haven't used them myself. For now, this guide will focus on the **EZ Flash Air** because I bought a set of them for my students, and they are the first consumers of this guide. I may return and add sections on the Everdrive later if I find the time.

This guide is being written in early 2026, and the opinions here are solely my own. I have not received any compensation from any flash cart manufacturer to recommend their products.
{: .note}



