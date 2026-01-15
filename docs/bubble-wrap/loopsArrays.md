---
layout: book
title: "Loops and Arrays"
parent: "Tutorial: Bubble Wrap"
nav_order: 500
---

# Loops and Arrays

In this section we'll be exploring a few different ways to make lines of sprites like in the below image:

![A row of dot sprites](./line.png)

## Making room for new art

In this section we'll be needing a bit of space to draw, and so we'll have to clear out your old art. But let's not forget it!


The actual best way to keep your old art would be to have a separate git branch with your old art and to clear it out of the main branch. We'll talk more about branches later.
{: .note}

## Brute forcing it

One way to achieve this would be to simply make a new named variable for every sprite we want:

```
bn::sprite_ptr myCircle = bn::sprite_items::dot.create_sprite(-40, 40);
    bn::sprite_ptr myCircle2 = bn::sprite_items::dot.create_sprite(-30, 40);
    bn::sprite_ptr myCircle3 = bn::sprite_items::dot.create_sprite(-20, 40);
    bn::sprite_ptr myCircle4 = bn::sprite_items::dot.create_sprite(-10, 40);
    bn::sprite_ptr myCircle5 = bn::sprite_items::dot.create_sprite(0, 40);
    bn::sprite_ptr myCircle6 = bn::sprite_items::dot.create_sprite(10, 40);
    bn::sprite_ptr myCircle7 = bn::sprite_items::dot.create_sprite(20, 40);
    bn::sprite_ptr myCircle8 = bn::sprite_items::dot.create_sprite(30, 40);
    bn::sprite_ptr myCircle9 = bn::sprite_items::dot.create_sprite(40, 40);
```

# TODO: Add picture of line of dots


