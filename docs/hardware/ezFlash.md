---
layout: book
title: "EZ Flash Air Setup"
nav_order: 200
has_children: false
parent: "Hardware"
---

# EZ Flash Air Setup

This page leads you through setting up the EZ Flash Air. If you are planning to work only in an emulator or own a different type of flash cart you can skip this section.

## Prerequisites

This page assumes you have:

- A development computer
- A Gameboy Advance / GBA SP / GBA Micro / DS with a GBA slot
- A microSD card (EZ Flash says it needs to be from 4GB to 128GB, but I've used 1GB cards without problem)
- An EZ Flash Air flash cart

## Reference
This guide expands on parts of the official [EZ-Flash Air FAQ](https://www.ezflash.cn/air.pdf). Consider looking there for more authoritative information if something isn't working here.

## Formatting your microSD card

You will first need to **format** the microSD card - to delete all the data on it and put it in a certain filesystem format that the EZ Flash Air can read.

### Formatting on Mac

If you are on Mac, follow these steps:
1. Insert the MicroSD card. You may need to use an adapter (as of early 2026 the EZ Flash Air comes with microSD to USB-A adapter)
1. Open the **Disk Utility**. Press `cmd-space` type "Disk Utility" and hit enter.
1. Choose the MicroSD card on the left. BE VERY CAREFUL THAT YOU CHOOSE THE SD CARD! If you accidentally format another drive/device you risk permanently losing all your data!
1. Click "Erase" at the top.
1. Choose a name for your card. Perhaps `ezflash`?
1. Choose a format
    - If your card has a capacity below 32GB, choose `MS-DOS(FAT)`
    - If your card has a capacity of 32GB or bigger, choose `exFAT`
1. Click "Erase"

Your MicroSD Card should now be formatted!

### Formatting on Windows

If you are on Windows, follow these steps:

# TODO

## Copying Games

After the MicroSD card has been formatted, you can simply copy over your GBA ROMs onto the card just like a normal drive on your computer. Make sure to copy over the `.gba` files, NOT the `.elf` files.

To start, try copying over the ROM you made for the "Learning Your Environment" section! I'd also recommend copying over something more substantial. Perhaps the excellent [GBA Microjam 23 ROM](https://gbadev.itch.io/gba-microjam-23)? Make sure to copy at least two ROMs over, they'll help us see something important.

Once the files have been copied, eject the MicroSD card and remove it from your computer.

## Using the EZ Flash Air

First, insert the MicoSD card into the side of the EZ Flash Air cart. Be gentle and don't force it! The tolerances aren't perfect, and I've accidentally jammed the card in before in a way it wasn't supposed to fit.

Next, insert the cartidge and start up the GBA! The EZ Flash logo will show, and you will be plopped into the bootloader. Use the L/R shoulder buttons to navigate the tabs of the bootloader. Select the SD Card tab, which should show the ROMs you copied to the card.

### NOR Flash

Unlike more premium carts like the EverDrive Mini, the EZ Flash Air cannot directly play from the SD Card. Games must first be copied to the cart's NOR flash memory before they can be played.

Select the game you want to start copy to NOR using the D-pad and A button. Choose `WRITE TO NOR CLEAN` to copy. Depending on how large the ROM is, it might take a little bit!

> ## What's NOR Flash?
> NOR flash memory is a type of phycial computer data storage that operates using NOR gates. It's fast and good for random access reads, and keeps storage even when powered off (it's non-volatile). If you're interested, follow your curiosity with [this Wikipedia article](https://en.wikipedia.org/wiki/Flash_memory) to learn more about NOR flash memory and its sister, NAND flash memory.
{: .question}


> If you're keeping a close eye on the progress indicator, the ROM might look like it's 8 times bigger than you might expect! That's because the progress shows kilo**bits** or mega**bits** instead of the more typical kilo**bytes** or mega**bytes**. A byte is 8 bits, hence the 8x difference in number displayed.
{: .note}




