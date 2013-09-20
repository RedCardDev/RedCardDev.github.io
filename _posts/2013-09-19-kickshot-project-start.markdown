---
layout: post
title:  "Starting KickShot for Android Development!"
date:   2013-09-19 16:13:07
categories: jekyll update

post_author: Nicholas Otter
post_gravatar: e893c15695d7d0e39e09d1462129edb6
---

A little introduction
------

We (Nick and Jordan) are two University of Idaho, Computer Science Seniors who are working on a Senior Capstone Project. This project is for a local (Moscow, ID) board game call KickShot (created by Aziz Makhani) whos goal is to educate its players on the rules and procedures of soccar while still being engadging and entertaining. Our goal for the semester is to publish the Junior version of KickShot to the Google Play Store.

Nick's First Week of Development
------
After meeting with Aziz for our first customer meeting, I was rather excited about working on an Android Game. This is not my first Android application but it is my first Android Game and as such there are a number of problems/tasks that I had not looked into before. 

The first of these was how to display and move objects on the screen based on user intraction. My previous applications have all leaned towards data entry and management and didn't require any custom views (the basic views provided by Android had always worked fine for my projects), so I went home and started trying different solutions to manipulate a ball on a soccar board. What I ended up with was a prototype game board constructed as a custom Android view that rendered the position ball chip as a Bitmap within the view.

Working off that prototype I began to add other game board requirements such as a dice and the ability for the ball chip to change which image is loaded based on which playe has possesion of the ball.

My board class ended up looking like (sudo code):

```
class Board extends Android.View:
    - moveBallChipTowardsHome(int steps)
    - moveBallChipTowardsAway(int steps)
    - positionDiceHome()
    - positionDiceHome()
    - changeDiceFace(int numberToShow)

```

There was very little condition checking, if someone roled a 4 and there were only 2 spaces left on the board then the ball chip moved off screen and the chip wasn't moving on the soccar field lines, but it was a start.

Jordan's First Week of Development
-----

Building on Nick's API and functions that were set in place on Saturday, I went through to make the game look a little more like the kickshot that we want to make. The first task that I completed was to make sure that there were multiple dice showing up on the board and when we called the RollDice function there would be multiple instances.

Since KickShot Junior relies on a series of dice rolls to advance, I made sure that the higher of the two values was the value that the ball advanced with. If doubles was rolled, the amount advanced was the face of one of the dice incremented by one. E.g. for a 3x3 roll, the player would advance four spaces.

Once I had the proper advancement set up, I made sure that there were boundaries on the board. When the board was initially set up, the ball would continue advancing to the edge of the screen and beyond. By placing both upper and lower boundaries on how far the ball could run, I could set up for when the shot function was implemented.

I, also, attempted to create a very rudimentary animation algorithm that would animate the dice while they were rolling. The code was similar to this:

```
numloops = 0;
while numloops < 8{
    seconds = 250 ms;
    changeDiceFace(rand() % 6 + 1);
    numloops++;
}
```

Unfortunately, this didn't work the way I intended and the application would hang until the loop was finished, then send a message telling me that 600+ frames had been skipped. Back to the drawing board for that one.

Moving Forward
------

Our next step is to start unit testing our Board view (trying to start testing early) and to start on our documentation.

