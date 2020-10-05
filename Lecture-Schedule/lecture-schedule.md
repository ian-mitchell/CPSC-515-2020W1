# CPSC 515 2020W1 Lecture Schedule

* This page lists just topics, expected preparation, lecture recordings and lecture associated links.  Detailed agenda for each lecture are stored in [this Google Drive folder](https://drive.google.com/drive/folders/1Exau_rTwjTxsIDH9iFSPuaIjj7NLzqhw?usp=sharing).
* Future lectures are subject to change.
* Some readings and/or links may not work on computers outside of UBC.  If you are working from home, use UBC's [myVPN service](https://it.ubc.ca/services/email-voice-internet/myvpn).  If you still have problems with a link, contact the instructor.
* Material from [Artificial Intelligence for Robotics](https://classroom.udacity.com/courses/cs373) is denoted "AIfR".
* Although not required for the course, two text sources are recommended for students seeking additional reading material:
  * "PR": [*Probabilistic Robotics*](http://www.probabilistic-robotics.org/) by Thrun, Burgard & Fox, MIT Press.  Does not appear to be available in electronic form through the UBC library.  I will provide chapter numbers from my first edition copy (2005), but I definitely recommend a later edition if you buy one since the first edition had some non-trivial errors (which can be found in the errata at the web page above).
  * "SHR": [*Springer Handbook of Robotics*](https://link.springer.com/book/10.1007%2F978-3-319-32552-1) edited by Siciliano & Khatib ($2^{nd}$ edition from 2016).  The entire book or individual chapters can be downloaded in electronic form from the UBC library.

## Introduction

* 2020-09-08: Course Introduction.
  * Preparation: None.
  * Lecture recording did not work.

## Localization

### General Notes

Localization is a subset of the broader problem of sensing and estimation.  
  * These sections of AIfR focus on three different representations and hence implementations of Bayes filters for localization, and the presentation is focused on simplified versions of the algorithms.
  * For a broader view of sensing and estimation, a decent general overview is [SHR chapter *Sensing and Estimation*](https://link.springer.com/chapter/10.1007/978-3-319-32552-1_5).

Although we did not discuss it explicitly in class, a key requirement of localization (in fact, all aspects of robotics discussed during AIfR) is creating models of motion and sensing.
  * PR chapters 5 & 6 discuss some basic models of motion and sensing respectively that work well with the filters discussed in AIfR and PR.
  * [SHR section C: *Sensing and Perception*](https://link.springer.com/book/10.1007%2F978-3-319-32552-1) provides chapters on specific sensing technologies.
  * [SHR section E: *Moving in the Environment*](https://link.springer.com/book/10.1007%2F978-3-319-32552-1) provides chapters on the modeling and control of specific classes of robots.

Some lectures also include pointers to readings on their specific topics.

### Lectures

* 2020-09-14: Bayes filter and histogram localization.
  * Preparation: AIfR Lesson 1.
  * [Recorded lecture](https://ubc.zoom.us/rec/share/h3zWbbupK8L18Rjps8L3_3tZCqeAH2ALLXC5R_kx9QYug9wGa8y13KfumXHr0ny0.UZJpl8KBeMRzaCDN) and access passcode `3Dhx+2bp`.
  * Optional reading: PR chapters 2, 4.1 and 8.2

* 2020-09-16: Generic Bayes filter and cost of histogram filter implementation.
  * Preparation: AIfR Lessons 2 & 3.
  * [Bayes filter equations and cost analysis](Lecture-Files/lecture-03.md) from class.
  * [Recorded lecture](https://ubc.zoom.us/rec/share/iLDjdivwGYXQToyT6pxNpL_YfhFAYH4xYgKM1dluCx4S07sGQ_apD_OQDdRTaQs.Ju0BSL8H7hGdtgfM) and access passcode: `S@H0&j&2`.  The first 37 minutes of lecture are missing because I forgot to turn on the recording.  My apologies.

* 2020-09-21: Kalman filter.
  * Preparation: AIfR Lesson 4.
  * [Kalman Filter slides](https://stanford.edu/class/ee363/lectures/kf.pdf) from Stephen Boyd's [EE363 Linear Dynamical Systems](https://stanford.edu/class/ee363/index.html) course at Stanford.
  * Implementing KF with Python's NumPy library: Colaboratory notebooks with [problem definition and starter code](https://colab.research.google.com/drive/10y7ObCYRR3KuCSSNAUR2ycP6d4iSEWN6?usp=sharing) and [solution](https://colab.research.google.com/drive/1shrBktsbRDqPmt4TI5JkOLyE2hNRsjsm?usp=sharing).  *Do not look at the solution until you have attempted to solve the problem from the starter.* 
  * [Recorded lecture](https://ubc.zoom.us/rec/share/0a6W2JNRYWenrC1BIj8Lv-o9IKW633gYo5L6ZxKSqt-KT9Ain7PA4ytobw1Uf5gY.0RTEfiF5FcjBJtbh) and access passcode: `iWr2G%*g`.  (I forgot to turn off the recording during the ~20 minute breakout near the end.)
  * Optional reading: PR chapter 3.2.  Note that the basic KF does not work for typical ground robot models because those models are nonlinear.

* 2020-09-23: Kalman filter complexity, limitations, and extensions.
  * Preparation: AIfR Lessons 5-7.
  * [Kalman filter slides](http://probabilistic-robotics.informatik.uni-freiburg.de/ppt/kalman.ppt) from the PR textbook.  We looked at slides 6, 7, 17, 21-27, 29, 40-43, 55, 57.
  * [Recorded lecture](https://ubc.zoom.us/rec/share/9yt7DwWHgM-TrTf6fVPk8eXFG12LdfdZT1ZfhDfmWlB2xwENekonhSs82SASVR6a.zOhzHschal4cifGY) with passcode `?4hyVl!&`.
  * KF Homework: [Jupyter notebook](Lecture-Files/lecture-05-homework.ipynb) or [on Colaboratory](https://drive.google.com/file/d/1H4Kf8roRwBdJQ0tybEBDWfwx9Qy3OoAO/view?usp=sharing).
    * Homework is due Monday October 5 by 11:45 am (*before class*).
    * Submit `.ipynb` Jupyter notebook file through Canvas.  Look for "KF Homework (submit here)" under the "Assignments" tab.
  * Optional reading: Extensions of KF in PR chapters 3.3, 3.4 & 7.

* 2020-09-28: Particle filter.
  * Preparation: AIfR Lesson 8.
  * [Recorded lecture](https://ubc.zoom.us/rec/share/pdZ_qf-4_EoXgzZ_eMOjhvH-JVZcl-OLG-8P3o3SHYgTprsJ_C1NBqYnZrrAIvYV.x6nyllYMJ3jVLkzf) with passcode `Wb=S^2LR`.
  * Optional reading: PR chapter 4.3

* 2020-09-30: More particle filter.
  * Preparation: AIfR Lessons 9-11.
  * [Recorded lecture](https://ubc.zoom.us/rec/share/yLNmFOr_8yjFIo36GvuCjgNpTkGXtkwvY-aVvAH857eA_uRCBGc6M21IR-hGS9-e.jpFy9861fSYe9M_Z) with passcode `.C9Tjj7@`.
  * Optional reading:
    * "[Adapting the Sample Size in Particle Filters through KLD-Sampling](https://doi.org/10.1177%2F0278364903022012001)" by Fox, *Int. J. Robotics Research* 22(12): 985-1003 (Dec 2003).
    * "[Improved Techniques for Grid Mapping with Rao-Blackwellized Particle Filters](https://doi.org/10.1109/TRO.2006.889486)" by Grisetti, Stachniss & Burgard, *IEEE Trans. Robotics* 23(1):34-46 (Feb 2007).
    * [UBC Wiki Page about RBPF](https://wiki.ubc.ca/Course:CPSC522/Rao_Blackwellized_Particle_Filtering) by Jocelyn Minns from an old offering of CPSC 522.

## Planning and Control

### General Notes

These two terms can be confusing because they are used interchangeably by some and distinctly by others.  Here are some common reasons / ways to distinguish between the two:
* Planning is high level and control is low level.
* Planning works with discrete elements (time, state, goals) and control with continuous.
* Planning uses techniques from computer science and control techniques from traditional engineering.

Of course, getting a robot to accomplish a job often requires more than just two levels of planning / control, and robotics is a field where computer science, engineering and many other fields overlap, so although many practioners personally draw a distinct line between the two that line may fall in a very different place depending on who you ask.

As with Localization above, AIfR considers a very narrow subset of a much broader field.  Other reading on the topics:
* PR section IV *Planning and Control* gives a fairly disinct and more general overview of planning based on Markov Decision Processes.  It does not discuss what I would call control.
* [SHR chapter *Motion Planning*](https://link.springer.com/chapter/10.1007/978-3-319-32552-1_7) gives a broader if somewhat dated view of planning from a CS perspective.
* [SHR chapter *Motion Planning and Obstacle Avoidance*](https://link.springer.com/chapter/10.1007/978-3-319-32552-1_47) gives an even better overview of where planning and control meet.
* Other chapters of [SHR section E: *Moving in the Environment*](https://link.springer.com/book/10.1007%2F978-3-319-32552-1) provide details on the control of specific classes of robots.
* [*Planning Algorithms*](http://lavalle.pl/planning/) by LaValle is the definitive text on classical CS planning algorithms.
* [*Dynamic Programming and Optimal Control*](http://athenasc.com/dpbook.html) by Bertsekas provides a readable but still rigorous introduction to DP and its connections to control.

Of course, the rise of machine learning over the past 5-10 years has lead many to declare the death of traditional planning and control techniques.  I hope to explore the impact of ML more during the second half of the class.

### Lectures

* 2020-10-05: Discrete Path Planning.
  * Preparation: AIfR Lesson 12.  The final problem is quite challenging -- try it and come to class with questions.
  * Optional reading: PR chapter 14 discusses value iteration in the context of Markov Decision Processes (MDPs).

* 2020-10-07: Dynamic Programming.
  * Preparation: AIfR Lesson 12 (if you did not already finish it) and 13-14 (the main problem in Lesson 13 is easier than the final example in Lesson 12).
