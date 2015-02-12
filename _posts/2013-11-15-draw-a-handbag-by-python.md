---
layout: post
title: "Draw A Handbag by Python"
description: ""
category: ""
tags: [python, pygame, drawing]
---
{% include JB/setup %}

I am learning python game buidling from this wonderful [online book](http://inventwithpython.com/pygame/index.html). The very [first lesson] (http://inventwithpython.com/pygame/chapter2.html) is to get familiar with the pygame package by drawing primitives on the canvas (the Surface object).

Instead of randomly drawing lines and strokes here and there, I assemble a simple object, a handbag, by a combination of primitives:
- Polygons
- Lines
- Ellipse
as shown below.

![](https://github.com/fengs/Python-Game/raw/master/Fig/Handbag.jpg)

Notice the partial overlapping of the primitives. Copy a primitive and horizonally translate the copy by several pixels. The uncovered part of the copies mimics the 3D effect and gives the 2D surface some depth. 

Fun, isn't it? The code is here.

<pre><code>
import pygame, sys
from pygame.locals import *

pygame.init()

# window set-up
DISPLAYSURF = pygame.display.set_mode((350, 350), 0, 32)
pygame.display.set_caption('Draw A Handbag from Primitives')

# color set-up
BLACK = (  0,   0,   0)
WHITE = (255, 255, 255)
RED   = (255,   0,   0)
GREEN = (  0, 255,   0)
BLUE  = (30, 144, 255)
PINK  = (255,  20, 147)
AQUAMARINE = (102,205,170)

# draw primitives
DISPLAYSURF.fill(WHITE)
pygame.draw.ellipse(DISPLAYSURF, PINK, (98, 40, 100, 180), 6)
pygame.draw.ellipse(DISPLAYSURF, BLUE, (95, 40, 100, 180), 6)
pygame.draw.polygon(DISPLAYSURF, AQUAMARINE, ((50, 150), (240, 110),(255, 115), (255, 300), (50,300)))
pygame.draw.polygon(DISPLAYSURF, GREEN, ((50, 150), (240, 110), (240, 300), (50,300)))
pygame.draw.line(DISPLAYSURF, BLUE, (145, 130), (145, 300), 6)
pygame.draw.line(DISPLAYSURF,BLUE,(50,225),(240,205),6)

# the game loop
while True:
    for event in pygame.event.get():
        if event.type == QUIT:
            pygame.image.save(DISPLAYSURF,"Handbag.jpg")
            pygame.quit()
            sys.exit()
    pygame.display.update()
</code></pre>

A .jpg image was saved before the program exits.

