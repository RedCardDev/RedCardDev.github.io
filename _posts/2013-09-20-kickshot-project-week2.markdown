---
layout: post
title:  "KickShot / Week 2 - Unit Testing"
date:   2013-09-22 15:20:00

authors:
    - name: Nicholas Otter
      gravatar: e893c15695d7d0e39e09d1462129edb6
      github: otternq

general:
    - name: Software Test Plan
      link: https://github.com/RedCardDev/KickShotAndroid/wiki/Software-Test-Plan
---

Let the Testing Begin
----------

In last weeks post I discussed the creation of the Board View, which is my first custom view. This week I want to talk about
writing unit/integration tests for that view. I typically use a set of tools to perform unit tests as well as integration
tests, and these tools seem to be a good place to start testing _KickShot for Android_.

- [Android JUnit](http://developer.android.com/tools/testing/testing_android.html)
- [Robotium](https://code.google.com/p/robotium/) | Unit testing for Android functionality, allowing the tests of clicks
- [Spoon](http://square.github.io/spoon/) | Multi-device test runner

Something I wanted to try this time around is have the testing code and the source code in the same repository. 
For previous projects the testing code was stored in it's own Eclipse project and its own separeate directory, resulting
in its own git repo. 
This lead to checking multiple issue lists and confusion about where bugs should be logged. 

Android documentation recommends using separate Eclipse projects for the Application 
and the Application's tests, but also shows how to store the Application Test project within the primary
Applications file structure. Following their instructions, I created a _tests_ folder in the _KickShot_ Eclipse project and 
then created an Android Testing Project and set its path to _/workspace/KickShot/tests_ now I have the 
best of Eclipse's multiple projects and a single git repository.

Now with the _KickShot_ application and test projects created, I started writing tests.
Initially I thought I would be required to test it through an Android activity, but Android 
provides a mock context in their `AndroidTestCase` class so I am able to run tests on the view without 
initializing an activity. I started with tests that would force the changes requested in 
[Issue #7](https://github.com/RedCardDev/KickShotAndroid/issues/7). 
The execution can be seen below. 

![Test Execution][1]

Those tests also make sure that the ball cannot 
be moved past the goal line and that the `ballTowardsX` functions return the current line number; This allows the 
game activity can handle shot logic. The Test Case ended up looking like:

```java

class BoardViewTest extends AndroidTestCase
- private Board board;
- public BoardViewTest
- protected void setUp
- public void testBallTowardsAway
- public void testBallTowardsHome
- public void testBallPosession
- public void testDicePositionAway
- public void testDicePositionHome
- public void testDiceChangeFace


```

with the tests written I changed the Board API to the following:

```java

class Board extends Android.View
- public Board(Context context, AttributeSet attrs)
- public boolean onTouchEvent(MotionEvent event)
- public Boolean ballPosession(int playerTurn)
- public Boolean diceChangeFace(int dice, int diceFace)
- public Boolean dicePositionHome(int dice)
- public Boolean dicePositionAway(int dice)
- public int ballTowardsAway(int steps)
- public int ballTowardsHome(int steps)
- private int ballMove()
- private void init()
- protected void onDraw(Canvas canvas)


```

Then I was able to change the internals of the Board class while not ruining its usage in the LevelOne Activity.


[1]: /images/screenshots/Screenshot_2013-09-20-ball-tests.png "Ball Tests"

