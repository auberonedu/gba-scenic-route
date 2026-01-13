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
1. Choose the MicroSD card on the left. If you are using the USB adapter, it may show up as a USB device. BE VERY CAREFUL THAT YOU CHOOSE THE SD CARD! If you accidentally format another drive/device you risk permanently losing all your data!
1. Click "Erase" at the top.
1. Choose a name for your card. Perhaps `ezflash`?
1. Choose a format
    - If your card has a capacity below 32GB, choose `MS-DOS(FAT)`
    - If your card has a capacity of 32GB or bigger, choose `exFAT`
1. Click "Erase"

Your MicroSD Card should now be formatted!

### Formatting on Windows

If you are on Windows, follow these steps:

1. Insert the MicroSD card. You may need to use an adapter (as of early 2026 the EZ Flash Air comes with microSD to USB-A adapter)
1. Open a Windows explorer window.
1. On the left side find the MicroSD card under This PC. If you are using the USB adapter, it may show up as a USB device. BE VERY CAREFUL THAT YOU CHOOSE THE SD CARD! If you accidentally format another drive/device you risk permanently losing all your data!
1. Right click the drive for the MicroSD card.
1. Choose a volume label for your card. Perhaps `ezflash`?
1. Choose a file system
    - If your card has a capacity below 32GB, choose `FAT (Default)`
    - If your card has a capacity of 32GB or bigger, choose `exFAT`
1. Click Start, then OK.

Your MicroSD card should now be formatted!

## Copying Games

After the MicroSD card has been formatted, you can simply copy over your GBA ROMs onto the card just like a normal drive on your computer. Make sure to copy over the `.gba` files, NOT the `.elf` files.

To start, try copying over the ROM you made for the "Learning Your Environment" section! I'd also recommend copying over something more substantial. Perhaps the excellent [GBA Microjam 23 ROM](https://gbadev.itch.io/gba-microjam-23)? Or anything from the [Homebrew Hub](https://hh.gbdev.io/search?platform=GBA&typetag=game)? Double-check that the ROMs you download are Game Boy Advance Games, not Game Boy (Color) or NES. Make sure to copy a few ROMs over, they'll help us see something important.

Once the files have been copied, eject the MicroSD card and remove it from your computer.

## Using the EZ Flash Air

First, insert the MicoSD card into the side of the EZ Flash Air cart. Be gentle and don't force it! The tolerances aren't perfect, and I've accidentally jammed the card in before in a way it wasn't supposed to fit.

Next, insert the cartidge and start up the GBA! The EZ Flash logo will show, and you will be plopped into the bootloader. Use the L/R shoulder buttons to navigate the tabs of the bootloader. Select the SD Card tab, which should show the ROMs you copied to the card.

### Writing to NOR Flash

Unlike more premium carts like the EverDrive Mini, the EZ Flash Air cannot directly play from the SD Card. Games must first be copied to the cart's NOR flash memory before they can be played.

Select the game you want to start copy to NOR using the D-pad and A button. Choose `WRITE TO NOR CLEAN` to copy. Depending on how large the ROM is, it might take a little bit!

> #### What's NOR Flash?
> NOR flash memory is a type of phycial computer data storage that operates using NOR gates. It's fast and good for random access reads, and keeps storage even when powered off (it's non-volatile). If you're interested, follow your curiosity with [this Wikipedia article](https://en.wikipedia.org/wiki/Flash_memory) to learn more about NOR flash memory and its sister, NAND flash memory.
{: .question}


> If you're keeping a close eye on the progress indicator, the ROM might look like it's 8 times bigger than you might expect! That's because the progress shows kilo**bits** or mega**bits** instead of the more typical kilo**bytes** or mega**bytes**. A byte is 8 bits, hence the 8x difference in number displayed.
{: .note}

### Playing from NOR Flash

Once the game has been copied, navigate to the NOR flash tab. Select the ROM and choose `DIRECT BOOT`. Your game will start playing! Have fun, go wild, be a kid again.

### Managing Games

Once you're done with one game and want to play the other, turn off the GBA and turn it back on. This is the only way to get back to the bootloader. Go back to the SD card menu and copy the other game to NOR Flash. When you go back to the NOR Flash you'll see that there both are now written to NOR.

The EZ Flash Air has 120MB of NOR flash memory, and most GBA games end up being smaller than 8MB. This means you can store a fair number of games, but at some point you may need to delete some to make room for others. There unfortunately is a bit of an annoyance when deleting games. You can only delete the game that was most recently added. If you want to delete the very first game you added, you have to delete all the other games too. You can of course always re-write them from the SD card, but it's a pain!

To see this, go to the NOR Flash tab on the EZ Flash Air and select the first game you added. Choose `DELETE` and you will be met with the unfortunate message `SELECT THE LASTEST`. If you cancel and then do select the last game you added, you will be able to delete it.



<details markdown="1" class="question">
<summary>If you've learned about data structures before, does this "only being able to add or remove to the end of a list" sound like a classic data structure you know?</summary>
It's a [stack](https://www.w3schools.com/dsa/dsa_data_stacks.php)!
</details>



