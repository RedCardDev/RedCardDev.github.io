---
layout: post
title:  "KickShot / Week 2 - The Shot"
date:   2013-09-23 22:22:00

authors:
    - name: Jordan Leithart
      github: leit7193
---

To Shoot or Not to Shoot
----------

One of my goals this week was to get the shot function working for KickShot Junior. The rules state that the offense must get the ball to the opponent's goal line before lining up a shot. At that point, the game pauses and both players roll a single die to see who wins the duel. If the shooter gets a higher roll, he scores and the ball is given to the opponent. If the goalie is successful in blocking it (i.e. he rolls equal to or greater than the shooter), the defense receives the ball at the 2 line and is now on offense.

The logic is pretty basic when it comes to algorithms. This doesn't make the game any less fun though. In fact, this elegant design enables a frantic feel to scoring, keeping in line with how the game of soccer can feel to the inexperienced player. The idea that I had was relatively simple. Here's some pseudo-code:
```
function Shoot(){
	//1st player shot
	shot1 = random;
	shot2 = random;

	//implying that player 1 is shooting
	if(shot1 > shot2){
		player1 scores;
	}
	else{
		player2 defends;
	}

	changePossession();
}
```

That's the general idea in my shooting function. Being that this is my first attempt at running any Android code and my first real dabble into Java, I was expecting to have a little more trouble with getting the inheritance and extension of classes. Much to my surprise though, I was able to write the code in a way that is easy to read and understand and hopefully change later when we implement a little more functionality. I was very surprised with how few bugs I wrote in my code, and I think it bodes well for us down the line.

Lastly, this post is mostly about the theoretical function that I wrote today. There is still a lot of tests to do on it using Spoon and JUnit before I feel completely sure of the code that I wrote. The documentation of this project is what I will learn the most from, and I'm excited to see what happens next. I will test it out on my own personal device after I run through the requisite tests.


[1]: /images/screenshots/Screenshot_2013-09-23-prototype1-shotFunction "Shot Example"

