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


