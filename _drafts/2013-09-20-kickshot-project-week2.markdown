---
layout: post
title:  "KickShot / Week 2 - Unit Testing"
date:   2013-09-20 15:20:00

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

In my last post I talked about never having written a custom view, and with the Board view taking shape, I now get to learn how to perform unit testing on that view. My previous projects have used a combination of the following tools:

- [Android JUnit](http://developer.android.com/tools/testing/testing_android.html)
- [Robotium](https://code.google.com/p/robotium/) | Unit testing for Android functionality, allowing the tests of clicks
- [Spoon](http://square.github.io/spoon/) | Multi-device test runner

I figure that Robotium is a good place to start for testing click events on the Custom View because it can trigger events such as OnClick based on its resource id.

`solo.clickOnView(solo.getView(android.R.id.home));`

With a quick change the the Board view I should be able to return which line the ball is currently on and pass that value onto Android JUnit.

`board.ballGetCurrentLine()`

Something that I wanted to try this time around is to have the testing code and the source code in the same project/repository. For previous projects the testing code ended up in its own Eclipse project and as a result in its own git repo. This lead to having to check multiple issue lists and confusion about where bugs should be logged. Android documentation, and the use of Eclipse make using separate Eclipse projects for the Application and the Application's tests, so I created a _tests_ folder in the Application's Eclipse project and then created an Android Testing Project and set its path to _/workspace/KickShot/tests_ so now I have the best of Eclipse's multiple projects and a single git repository.

