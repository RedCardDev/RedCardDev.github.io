---
layout: post
title:  "KickShot / Week 3 - Flow Chart Master"
date:   2013-09-30 17:20:00

authors:
    - name: Jordan Leithart
      github: leit7193
---

The Power of Working Together
----------

The benefit of our online blog was made evident when as soon as I posted about our shot function, we got a call from our client. We had unfortunately coded the function incorrectly (and as an aside, made it much more difficult) and our client wanted to make sure that we knew how it worked. This was a huge benefit to us because we were able to meet immediately following that and fix the issue. The meeting to fix the shot function allowed us to sit down and draw up a few flowcharts for the game should work. We realized that if we sat back and simplified the code, we could expand it a later point much more easily.

By pair programming, two programmers working on the same work station, we were able to fix the issues while walking through each state of the game step by step. For example, when the player has possession of the ball, he first rolls the dice. If he doesn't roll doubles, he is allowed to advance the ball. If doubles are rolled, it is a turnover and the computer gets to play offense. If, after advancing, the ball is in shooting position (on the goal line), the player then enters what is called shot mode and calls the player shot function. Here is a picture of our flowchart:

[1]: /images/screenshots/playeroffense.png "Player Offense"

Of course, we also had to make sure that the game knew how the player was supposed to play defense too. In this flowchart, we start with the computer just having rolled to advance the ball (and succeeding). The player then rolls to see if he can intercept the ball by rolling doubles. If he succeeds, ball possession is changed. If not, the computer remains on offense and rolls the dice to see if the ball is advanced. Here's the flowchart that I was describing:

[2]: /images/screenshots/playerdefense.png "Player Defense"

There are two more states that we have to deal with. The first is when the computer finally gets a shot off. The player still has a chance to block that shot, but he must roll doubles in order to succeed. So our flow chart looked more like this:

[3]: /images/screenshots/playerblock.png "Player Block"

I'm sure you all know exactly what state is supposed to come next, but I figured I should say it anyways. What about when the player is supposed to shoot? Well the rules are that if the player advances the ball to the goal line, the defending player (whether computer or human) is allowed one last chance to block. I showed the block state just above, and so for the shot state, the computer takes on the roll of the block chart. If the computer can roll doubles, the shot is blocked, and play continues. Otherwise, it's a goal!!

[4]: /images/screenshots/playershot.png "Player Shot" 

Being able to sit down with Nick and discuss how we were going to do this was a HUGE benefit. One that probably wouldn't have happened if not for Aziz's timely call about the rules. For now? It's further up and further in!
