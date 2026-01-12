---
layout: book
title: "Buttons"
parent: "Exploration: Bubble Wrap"
nav_order: 200
---

# Buttons

On this page we'll be exploring how to get user input from the GBA's buttons.

## Small verifiable goal

As always we want to make a small goal that we can verify is working. Our goal in this section is going to be making it so that the backdrop color changes when the user presses A or B.

# TODO: gif of screen color changing

## GBA Buttons

There are 10 buttons on the Game Boy Advance.

- A
- B
- L
- R
- Start
- Select
- D-pad up
- D-pad right
- D-pad down
- D-pad left

For our user to interact, we want to know what buttons are held down on what frames. Butano gives us some great tools to do this!

## Exploring bn::keypad

Butano calls buttons the "keypad." Let's start off by importing the keypad functionality. Place this with your other includes at the top:

```
#include <bn_keypad.h>
```

You can learn about what's in this namespace using the [Butano keypad documentation](https://gvaliente.github.io/butano/namespacebn_1_1keypad.html). But there's another way we can see it too!

Somewhere inside your `main` function, begin typing a line:

```
bn::keypad::
```

You should see a lot of suggestions come up! These are all functions/types/etc that are avaialble to use from `bn::keypad`. Take a quick scroll through them and see what's there. There's a lot, but they're nicely named, so a lot should be self-explanatory.

## Making a plan

Before writing the actual C++, it's often helpful to plan what we want to do first. In our case, here's what we want:

```
if A button is pressed, change backdrop color to red
```

For more complex ideas it can be useful to write out our plan in English (or any other natural language), make psuedocode, draw pictures, talk about it with a friend, &c. Taking just a bit longer to plan can often save you a lot of pain in the long run.

## Button presses

To see whether the A button is pressed, we'll use the `a_pressed` function:

```
bn::keypad::a_pressed()
```

We need the open and close parentheses because `a_pressed()` is a function call - we want to execute the function and get a value back. If the a button has just been pressed, `a_pressed()` will return `true`, otherwise it will return `false`.

> ### What's the difference between held, pressed, and released?
> You may have noticed that `bn::keypad` has 3 functions for each button. For the A button it has `a_held()`, `a_pressed()`, and `a_released()`. What's each do?
>
> `a_held()`: returns true if the A button is held down on the current frame. This returns true for as long as the button is held, and false if the button is not held.
>
> `a_pressed()`: returns true if the A button was JUST pressed on the current frame. It WAS NOT held down in the previous frame, but it IS held down now. It only returns true on the first frame of the press.
>
> `a_released()`: returns true if the A button was JUST released on the current frame. It WAS held down in the previous frame, but it IS NOT held down now.
>
> You need to choose which is appropriate depending on what you want to have happen in your game. For example, do you want your spaceship to constantly shoot a stream of bullets as A is held down? Or does the player need to repeatedly press A to shoot more bullets. It's up to you as a game designer to decide what's appropriate for each situation!
>
> In our case, we need to backdrop to change when the button is pressed, but it doesn't need to continually keep on changing as it's held. That's why we chose to used `a_pressed()`
{: .question}

### if this, then that

Next, we're going to use that press