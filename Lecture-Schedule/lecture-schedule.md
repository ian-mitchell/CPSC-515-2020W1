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

* 2020-09-30: Motion / sensing models and extensions of particle filters.
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
  * We did not manage to get to path planning during the lecture. There was some discussion of the [course project](https://sites.google.com/view/ubccpsc515winter2020/projects).
  * [Slides](https://www.cs.ubc.ca/~mitchell/Class/CPSC515-2020W1/2020-10-05-system-models.pdf) about system models and the meaning of optimal control (including objective and value functions).  Slides include notations added during and after class.
  * [Recorded lecture](https://ubc.zoom.us/rec/share/E7iPB6Vor0kKUw-8BVHMWOT0fz5G6kplk5z4_ZnF94lVyklY4CWf_NKj74Jo_dv1.aJRxi4kVVLB6dhvD) with passcode `fv*p%.C2`.


* 2020-10-07: Dynamic Programming and Path Planning.
  * Preparation: AIfR Lesson 12 (if you did not already finish it) and 13-14 (the main problem in Lesson 13 is easier than the final example in Lesson 12).
  * [Slides](https://www.cs.ubc.ca/~mitchell/Class/CPSC515-2020W1/2020-10-07-dynamic-programming.pdf) on path planning as a dynamic programming problem, equations and algorithms for value functions, and policy extraction.  We covered slides 1-5 today.  Slides include notations added during and after class.  
  * [Notes](https://www.cs.ubc.ca/~mitchell/Class/CPSC515-2020W1/2020-10-07-notes.pdf) created during lecture examining how problems from Lesson 12 videos 17 and 19 are encoded as objective functions.
  * [Recorded lecture](https://ubc.zoom.us/rec/share/3F3dD0ElpaNSmroaa7jofv_prV0dnPYHw4S01NSgx2eXkcFASn4KiC72NH1DfOHq.-l_j5aFmkJqvAHKP) with passcode `fmJE*tw6`.
  * Optional reading: PR chapter 14 discusses value iteration in the context of Markov Decision Processes (MDPs), which are a discrete state, discrete time, stochastic model of system evolution.  "System evolution" is a more general name for what we have been calling a "motion model".

* 2020-10-12: **No lecture** (Thanksgiving holiday).
  * No preparation or readings.

* 2020-10-14: Dynamic programming / value functions and other planning algorithms for robotics.
  * Preparation:
    * [SHR chapter *Motion Planning*](https://link.springer.com/chapter/10.1007/978-3-319-32552-1_7) sections 7.1-7.3 presents a more traditionally computer science perspective on the motion planning problem and an overview of methods to solve it without value function approximation.
    * "[The Open Motion Planning Library](https://dx.doi.org/10.1109/MRA.2012.2205651)" by Sucan, Moll & Kavraki, *IEEE Robotics & Automation Magazine*, 19(4):72-82 (December 2012) presents a popular library of planners.
  * The [OMPL](https://ompl.kavrakilab.org/) is interfaced to ROS through [MoveIt](https://moveit.ros.org/).
  * [Slides](https://www.cs.ubc.ca/~mitchell/Class/CPSC515-2020W1/2020-10-07-dynamic-programming.pdf) on path planning as a dynamic programming problem, equations and algorithms for value functions, and policy extraction.  Same slide deck as 2020-10-07, but we covered slides 6-9.
  * [Notes](https://www.cs.ubc.ca/~mitchell/Class/CPSC515-2020W1/2020-10-14-notes.pdf) created during lecture recalling the value iteration equations for the deterministic case (Lesson 12 videos 17 & 19), extending the equations to the stochastic case (Lesson 13, video 5), and sketching out the complexity of value iteration.
  * [Recorded lecture](https://ubc.zoom.us/rec/share/LaS8PhDoKeiNTJn92te4c53eqO16FVK6MI050HtJ9pYln_TsQDo9-lOllYCRYvZ5.j7vq7I4PlQE33YC4) with passcode `QMMOV^2a`.

* 2020-10-19: Path smoothing and planning / control through optimization.
  * Preparation: AIfR Lesson 15.
  * [Notes](https://www.cs.ubc.ca/~mitchell/Class/CPSC515-2020W1/2020-10-19-notes.pdf) created during lecture deriving (in a far from rigourous fashion) the update equations used in Lesson 19 video 6, and then considering what other aspects of our robot model / goals we might add into the resulting optimization problem.
  * [Recorded lecture](https://ubc.zoom.us/rec/share/8pnl0tEVF8bt8kfxf-quwzwN3VgPNq9uT1H66sBbH7j-N7LqE0ocuK24UuQvBxw1.qRCyaPKpx4F-XLPd) with passcode `%ZU!N1Nd`.

* 2020-10-21: MPC and stability.
  * Preparation: AIfR Lessons 16-18.  Lecture covers generalizations of smoothing and PID.
  * MPC:
    * [Matlab videos](https://www.youtube.com/c/matlab/) giving a brief primer on MPC: *Understanding Model Predictive Control* [part 1](https://youtu.be/8U0xiOkDcmw) and [part 2](https://youtu.be/cEWnixjNdzs).  There are many subsequent parts explaining various aspects of MPC in more detail, but these two provide the key concepts.
    * The [diagram of MPC operation](https://en.wikipedia.org/wiki/Model_predictive_control#/media/File:MPC_scheme_basic.svg) that I showed comes from the [MPC entry](https://en.wikipedia.org/wiki/Model_predictive_control) at Wikipedia (which I find rather simplistic).
    * The [block diagram of an MPC system](https://www.ist.uni-stuttgart.de/bilder/forschung/MPC_general.png) comes from the University of Stuttgart's Institute for Systems Theory and Automatic Control [Model Predictive Control page](https://www.ist.uni-stuttgart.de/research/topics/mpc/), which also gives a brief overview of several different branches of MPC research.
  * Stability and mass-spring-damper system:
    * I showed you a brief bit of the [How Centrifugal Governors Work](https://youtu.be/ASIl3HWTT4U) animation, and you can get pictures and diagrams at the [Govenor](https://en.wikipedia.org/wiki/Governor_(device)) Wikipedia page.
    * The [mass-spring system diagram](https://s3-us-west-2.amazonaws.com/courses-images/wp-content/uploads/sites/2952/2018/01/31200835/CNX_UPhysics_15_01_MassSpring.jpg) that I showed in class is lacking a damper / friction.  You can see a full diagram and corresponding equation at the [mass-spring-damper model](https://en.wikipedia.org/wiki/Mass-spring-damper_model) Wikipedia page.
    * You can find more than enough information about the [eigendecomposition of a matrix](https://en.wikipedia.org/wiki/Eigendecomposition_of_a_matrix) on Wikipedia.
    * The [stability theory](https://en.wikipedia.org/wiki/Stability_theory) Wikipedia entry has the diagram of how systems might behave near an equilibrium, although the axes are related to the trace and determinant of the matrix rather than its eigenvalues.  There are many tables showing the connection between eigenvalues and the stability and/or oscillation of the resulting trajectories, such as [here](http://cozybeehive.blogspot.com/2009/09/dynamic-stability-of-bicycle-design_18.html) or [here](https://www.researchgate.net/figure/This-table-presents-the-classification-and-connection-between-eigenvalues-stability-and_tbl1_334125895).  If you have taken an intro course on differential equations, there is probably a similar table / diagram in your textbook.
  * [Notes](https://www.cs.ubc.ca/~mitchell/Class/CPSC515-2020W1/2020-10-21-notes.pdf) created during lecture covering various definitions of stability and deriving the solution of the linear mass-spring-damper system in the input-free case.
  * [Recorded lecture](https://ubc.zoom.us/rec/share/cQ9tbBtSmV4mezYLGryIH1c08gvsso8l3OmsiFI4WLqHqtjPjqpFNs2Axghiqb37.eu30a1O7Uzop9v3b) with passcode `k7=wJy%W`.

* 2020-10-26: PID for control
  * Recommended: Get started on AIfR Lesson 19.

## Simultaneous Localization and Mapping (SLAM)

### General Notes

### Lectures

* 2020-10-28: FastSLAM
  * Preparation: AIfR Lesson 19.

* 2020-11-02: Implementing SLAM.
  * Preparation: AIfR Lessons 20-21.


## Advanced Topics

### Lectures

* Other dates

* 2020-11-18: Potentially [DFP@UBC](https://dfp.ubc.ca/) [Seminar](https://dfp.ubc.ca/taxonomy/term/64)
  * "[Emotional robots and magical objects: What part of our internal experience is readable by a touch-sensitive machine?](https://dfp.ubc.ca/news-and-events/events/emotional-robots-and-magical-objects-what-part-our-internal-experience-0)" by [Karon MacLean](https://www.cs.ubc.ca/labs/spin/) (UBC Computer Science)

