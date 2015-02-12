---
layout: post
title: "A Simple Billiard Ball Game"
description: ""
category: "programming"
tags: [python, pygame, animation, python game, code]
---
{% include JB/setup %}

Upon familiarity with the pygame framework, the next step is to add some animation. [Chapter 2] (http://inventwithpython.com/pygame/chapter2.html) introduces a cat animation program in which a cat moves in rectangle path, turning its way when about to hit the wall, forever and ever.

I decided to try something fun, something physics. An object moving on canvas is confined by the boundaries. How about some elastic collision? Back in high school, I did so many physics problems on collision that I can call this equation right off the top of my head:

![](http://upload.wikimedia.org/math/a/b/6/ab6645eaf09c6da1ba47b0f662615140.png)
![](http://upload.wikimedia.org/math/e/0/f/e0fa187fc3065bad45710620be5f7687.png)

In a simplified case, when a perfectly elastic ball hits a rigid surface, it retains its kinetic energy and reflects away from the surface. Like reflection of light, the velocity component parallel to the surface stays unchanged, and the velocity component perpendicular to the surface turns back. 

Conservation of energy sounds more interesting than a cat lost in a rectangle. First I draw a 500 X 300 pixel pool table as canvas. 

![](https://raw.github.com/fengs/Python-Game/master/Fig/PoolTable.png)

↑ It is drawn in Adobe Illustrator. Next is a 26 X 26 pixel billiard ball

![](https://github.com/fengs/Python-Game/raw/master/Fig/BilliardBall.png)

The ball might be invisible on a white background:( but it is there :)

I use tuple to store (x,y) coordinates. Initially the ball was set at (250,100) . Initial velocity is (1.5, 2). The main game loop does several things:

Draw the pool table

    SURF.blit(table,(0,0))

If the ball has not fallen into any holes, draw the ball

    SURF.blit(ball,(x-13,y-13)) # radius of the ball is 13

If the ball is striking a boundary, update the velocity. Update the ball location

    if x + v[0] >= 466 or x + v[0] <= 34:
        v = (-v[0],v[1])
    elif y + v[1] <= 34 or y + v[1] >= 266:
        v = (v[0],-v[1])
    b = (x + v[0], y + v[1])

Otherwise if ball has fallen, draw the text.

    SURF.blit(textSurfObj,textRectObj)

Check if a QUIT event occurs. If so quit the program.

Tick the clock.

    fpsClock.tick(FPS)

The recorded animation is here:

![](https://github.com/fengs/Python-Game/raw/master/BilliardBall/BilliardBall.gif)

Full code is available on [Github] (https://github.com/fengs/Python-Game/blob/master/BilliardBall/BilliardBall.py).
I'll try adding sound effects and music to the games when I find suitable audio files :) Cannot wait for the next project.
 
