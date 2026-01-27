---
layout: book
title: "Sprite Transformations"
parent: "Tutorial: Bubble Wrap"
nav_order: 600
---

# Sprite Transformations

In this section we will explore how to access items within a vector and introduce some transformations we can perform on sprites. You may have experimented a lot in the previous section. That's OK! Just make sure you've got a vector with at least 5 dots showing on the screen.

## Enlarging a Specific Sprite

Let's select one of our sprites and make it bigger. We can choose a specific element in a vector by **indexing**. After the vector has been created but before the `while` loop, choose the first element of your sprite vector and set the scale of that sprite:

```
circles[0].set_scale(1.8);
```

We use square brackets `[]` to choose a single element in a vector (indexing). Inside the square brackets we put the **index**, the position of the element in the vector. Vecotrs in C++ are **zero-indexed** meaning that the first element is at index 0. So `circles[0]` will choose the first element of the vector, `circles[1]`, will choose the second, and so on. 
{: .note}

Compile your code and run your game and see the result. You should see that the first sprite is now bigger than all the others.

## Scale

When we scale, you can think of it roughly as percent.
- A scale of 1.0 is 100% size - the same size of the sprite unchanged.
- 2.0 is 200% size - double the size of the sprite.
- 0.5 is 50% size - half the size of the sprite.
- Values in between are corresponding, e.g. 0.7 is 70%

Give this a try with a few elements! Set the sprite at index 1 to a 0.5 scale, the sprite at index 2 to 2.0, the sprite and index 3 to something else etc. Make and run your game and see the various sizes all next to each other.

What is the maximum scale supported? See if you can experiment and find out. What happens when you go over this scale? What's the minimum? What happens when you go under the minimum? There are real hardware limits on the Game Boy Advance to how far a sprite can scale, it's not an arbitrary restriction of Butano. Explore here and see what you find.
{: .question}

## More transformations

Experiment with a few more methods as well:
- `set_horizontal_scale`
- `set_vertical_scale`
- `set_shear`
- `set_rotation_angle` (might be hard to see the effect of if your sprite is a circle)
- See if you can figure out what some other `set` methods on the [`sprite_ptr` class](https://gvaliente.github.io/butano/classbn_1_1sprite__ptr.html) do. Some of them are a bit tricky to figure out.

Set a couple of different items in your vector and see what they do. See what happens when you apply multiple transformations to a single sprite.

![Sprites transformed in various ways](./transforms.png)

## Affine Sprite Limit

We call these types of transformations "affine transformations" and a sprite that is currently being transformed is an "affine sprite". There are circuits hardwired in the Game Boy Advance for the specific purpose of drawing affine sprites quickly and efficiently. However, this does mean that there are real limits on what we can do. In particular, there are a maximum of 32 affine transformation matrices available at a time. Try making a vector with more than 32 sprites and set the scale of each of them (this is easiest to do with a loop). You'll see that Butano asserts an error once you reach the 33rd sprite.


