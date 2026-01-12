---
layout: book
title: "Buttons"
parent: "Tutorial: Bubble Wrap"
nav_order: 200
---

# Buttons

On this page we'll be exploring how to get user input from the GBA's buttons.

## Small verifiable goal

As always we want to make a small goal that we can verify is working. Our goal in this section is going to be making it so that the backdrop color changes when the user presses A or B. It'll look something like the below:

![A gif of a GBA backdrop shifting between blue, pink, and white](./backdropColors.gif)

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

```cpp
#include <bn_keypad.h>
```

You can learn about what's in this namespace using the [Butano keypad documentation](https://gvaliente.github.io/butano/namespacebn_1_1keypad.html). But there's another way we can see it too!

Somewhere inside your `main` function, begin typing a line:

```cpp
bn::keypad::
```

You should see a lot of suggestions come up! These are all functions/types/etc that are avaialble to use from `bn::keypad`. Take a quick scroll through them and see what's there. There's a lot, but they're nicely named, so a lot should be self-explanatory.

## Making a plan

Before writing the actual C++, it's often helpful to plan what we want to do first. In our case, here's what we want:

```
if A button is pressed, change backdrop color to pastel pink
```

For more complex ideas it can be useful to write out our plan in English (or any other natural language), make psuedocode, draw pictures, talk about it with a friend, &c. Taking just a bit longer to plan can often save you a lot of pain in the long run.

## Button presses

To see whether the A button is pressed, we'll use the `a_pressed` function:

```cpp
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

## if this, then that

Next, we're going to use that press to control the behavior of our code. Remember, this is what we want:

```
if A button is pressed, change backdrop color to pastel pink
```

Make a prediction of how we can do that! Try it out first before seeing the answer. You can choose your own color instead of pink.

<details>
    <summary>
        Expand to see answer
    </summary>
<div markdown="1">
Combine an `if` statement with our `a_pressed()` and `set_color`.
```cpp
if (bn::keypad::a_pressed()) {
    bn::backdrop::set_color(bn::color(31, 21, 22));
}
```

The `if` statement checks whether the expression between the parentheses evaluates to `true` or `false` (more generally truthy or falsy). If it's `true`, then the code between the curly braces gets executed. If the expression is `false`, the code get skipped. `a_pressed()` returns `true` or `false` depending on whether A has been pressed, so it works perfect here.

> You may be used to expressions like `if (x == 5)` or `if (word == "hello")`. So why not `if (bn::keypad::a_pressed() == true)`?
>
>It's because the result of `a_pressed()` is already a boolean - it's already `true` or `false`. So we don't need a comparison to check, we can just use the boolean directly. You should almost never need to use `== true` or `== false`. Just use the boolean directly.
{: .question}
</div>
</details>

## Logic placement

So where does does that if-block go? Let's try a few places and see what works and what doesn't.

### Outside the while loop

To start, let's try putting it **outside** the while loop. Our code up to this point should look something like the below (it's OK if your code has some other stuff going on based on what you added to experiment or if you've chose different colors)


<details>
    <summary>
        Expand to see code
    </summary>
<div markdown="1">
```cpp
#include <bn_color.h>
#include <bn_backdrop.h>
#include <bn_core.h>
#include <bn_keypad.h>

int main() {
    bn::core::init();
    bn::backdrop::set_color(bn::color(20, 20, 31));

    if (bn::keypad::a_pressed()) {
        bn::backdrop::set_color(bn::color(31, 21, 22));
    }

    while(true) {
        bn::core::update();
    }
}
```
</div>
</details>

Now, compile your code again with make, and try running it in mGBA. By default, the `X` key is used for the A button in mGBA.

Give it a try and you'll see... pressing the key does nothing.

So why didn't that work? Take a guess and see if you're right.

<details>
    <summary>
        Expand to see answer
    </summary>
Because the if-block is outside of the while loop, we only ever check whether the A button is pressed at the very beginning when the game starts up. Later presses of the A button get completely ignored. 
</details>

### Inside the while loop
What we really want to do is check it **each frame** if the A button has been pressed. That way it gets updated whenever the user presses the button. So our new plan should be:

```
EACH FRAME if A button is pressed, change backdrop color to pastel pink
```

To do so, we're going to put our logic inside the `while` loop. Move the if-block inside the while loop so it looks like this:

```cpp
while(true) {
    if (bn::keypad::a_pressed()) {
        bn::backdrop::set_color(bn::color(31, 21, 22));
    }

    bn::core::update();
}
```

Now, the loop will alternate between checking for A presses and updating Butano. The Butano `update` method automatically locks to frame refreshes (approximately 60 frames per second), so our key press properly gets called once per frame!

Trying using `make` to compile again, and run your code in mGBA. This time, pressing the Z key (to simulate the A button) should change the color. It will only change once - you'll need to restart the game to get back to the original color. But we're making progress!

You've accomplished some new functionality here! Make sure to save your progress: add, commit and push your code. You might also consider testing this on real hardware if you have access to it.
{: .note}

## A third color and beyond

Let's make it so we can go to a third color when we press the B button (z by default on mGBA). We'll want to keep all our old code, but add something new. Think of what you need and give it a try before looking at the answer.

<details>
    <summary>
        Expand to see answer
    </summary>
You need to add another if-block inside your while loop, this one checking `b_pressed()` and setting to another color. Go ahead and do so now if you haven't already.
</details>

`make` your code, and verify that you can toggle between colors. Got it working? Add, commit, push! Then go ahead and add more colors for more buttons if you like!

> Ideas on more challenging things you optionally can do here:
>
> Some of these get quite tricky! You may need to do some extra research to learn new techniques to solve these.
> - Can you make it so that there's a default color when no buttons are pressed, and that each button's color is only displayed for as long as that button is held down?
> - Alternatively an you make it the color only stays for 1 second (60 frames) after pressing a button before returning to the default color?
> - Can you make it so that when you hold down two buttons their colors get blended together?
> - Can you come up with something more creative to do here?
>
> You definitely don't *need* to do any of these, but they can be fun to try or at least think about how you would approach.
{: .challenge}

## What's Next?

That's enough of just solid backdrops - let's start putting some real graphics on our screen! Make sure you've added, committed and pushed your changes and then head on to the next page.