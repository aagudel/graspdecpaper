## 1
Controlling a hand prosthesis through a brain interface is an incredibly hard problem.

How do we train a BCI to produce accurate movements such as those required for grasping? 

We propose ProXYZ: a protocol to train accurate BCI hand control.

Let's dive in🧵
!(video2)[video2.mp4]

## 2
It all began with a specific question: can we apply existing, high performance methods to train a BCI for grasping? Two of such methods are ReFIT by @gilja @paul and RNNs by @david. ReFIT, for example, is beautifully simple. It suggest that decoding performance can be improved by rotating the target velocity vectors in a recalibration step
[ReFIT anim]

## 3
The problem? Implementing RNN and ReFIT out of the box in our cased not only failed, it failed bad. Subjects were not able to control joint velocitiy and RNNs worked perfectly offline but misserably online.
[Fail meme or something]

## 4
Although you might guess that hand movements are similar to arm reaches, once you go deep on it, you realize that the problem of grasping is actually different ....
["Similar but different" meme]

## 5
After trial and error, and years of tests, we can say that from our perspective, grasping is particular in 3 aspects:
-Grasping and potentially hand control is a data problem
-Requires developing a latent space
-Different areas might provide different data
[No image needed]

## 6
To address this issues, ProXYZ: consist of 4 compoments:
C1.Building of a kinematic latent space
C2.Training degrees of freedom incrementally
C3.Inspired by ReFIT, retraining the decoder with a fit-to-trajectory strategy
C4.Once developed, improving the latent space mapping with a two layer RNN called NARX
[Figure2]

## 7
Together, these strategies bring some sweet accurate hand prosthesis control our monkeys were quite satisfied with (at least in metrics such as task performance and trejectory accuracy). An example here, in our online MuJoCo physics environment.
[FTvsNARXVideo]

## 8
Why do we believe grasping is a data problem? Given the high number of degrees of freedom involved in hand control only data capture methods can help us describe the kinematic spaces that need to be traversed to achive the multiple configurations of the hand. We used a tracking system to capture real grasps. Doing so made us realize the hand control latent space (e.g. switching from an open hand to a power grip) is a curved trajectory in the latent space.
[Video of real grasps + ApendixFigure1 + anim]

## 9
How to train decoders able to produce trajectories in the latent space? Here is where component 3 plays an important role. Instead of reaching to a specific target, traversal of the trajectories in the latent space is important, we extended ReFIT to consider not only targets but also trajectories.
[Animation of ReMAP]

## 10
Considering trajectories is helpful during hand state transitions as they can prevent collisions (e.g. with own fingers or to quickly prepare the hand for a grasp). Using fit-to-trajectory improves accuracy and helps control in an environment with collisions.
[Collisions task result]

## 11
We only do two grips
(believe us, were a going there next)
[Simulations]

## 12
But wait a minute ... what about component 3?
This is where "Requires developinmg a latent space" comes into place
This has implications for learning
[Expertise plot]

## 13
A big open question for us was, why didn't velocity control baesed methods like ReFIt and @david RNN worked for our case? It turns out area differences might be playing a role. That's where thigs turned wildly 

To create the kinematics latent space, we recorded real grasps 

It is actually closer to a data problem .. similar in a form to the big data problems were are used nowadays

It requires collecting data of grasping, it also implies tranformations bwtween high dimensional spaces and lots of non-linearities everywere

Implementing those methods actually was a big fail

the data doesn't liook quite the same, velocity is not actually the best way to control, you find  that the aeas do not iven represent that signal well ...

After many iterations and training ... and a lot of years of trial an error ... we were able totrain two monkey s to pwerform a grasping task wqith jhgh accuracy

Although they were many little improvements We came to four  aspects that hwere key for the succesful training apprroach those were :

In combinattion the methods lead to accurate hand control able toachive for example precise grasping points

When tested in acollision task ... we were alse able achive higher performance

Although we only tested this with powerfull 

ProTML It might also be a way to study how neural state-spaces evolve.

There are existing approaches ... see for example ... we concentrate on specific aspect 
The 
Our hands are highly dextereus but that is not a skill we get when we are born. This dexterity develops from learning things as grasping whne we are kids, but evolves as we learn motr tricks like writting, typing or playing and instrument.

In the same form ProTML
Just as we learn to use our hands, though different tasks like basic grasping, 
TRaining a full grasping prosthesis 
ProTML 
