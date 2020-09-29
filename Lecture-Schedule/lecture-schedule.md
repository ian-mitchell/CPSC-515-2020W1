# CPSC 515 2020W1 Lecture Schedule

* Future lectures are subject to change.
* Some readings and/or links may not work on computers outside of UBC.  If you are working from home, use UBC's [myVPN service](https://it.ubc.ca/services/email-voice-internet/myvpn).  If you still have problems with a link, contact the instructor.
* Material from [Artificial Intelligence for Robotics](https://classroom.udacity.com/courses/cs373) is denoted "AIfR".

## Introduction

* 2020-09-08: Course Introduction.
  * Preparation: None.
  * Lecture recording did not work.

## Localization

* 2020-09-14: Bayes filter and histogram localization.
  * Preparation: AIfR Lesson 1.
  * [Recorded lecture](https://ubc.zoom.us/rec/share/h3zWbbupK8L18Rjps8L3_3tZCqeAH2ALLXC5R_kx9QYug9wGa8y13KfumXHr0ny0.UZJpl8KBeMRzaCDN) and access passcode: 3Dhx+2bp

* 2020-09-16: Generic Bayes filter and cost of histogram filter implementation.
  * Preparation: AIfR Lessons 2 & 3.
  * [Bayes filter equations and cost analysis](Lecture-Files/lecture-03.md) from class.
  * [Recorded lecture](https://ubc.zoom.us/rec/share/iLDjdivwGYXQToyT6pxNpL_YfhFAYH4xYgKM1dluCx4S07sGQ_apD_OQDdRTaQs.Ju0BSL8H7hGdtgfM) and access passcode: S@H0&j&2.  The first 37 minutes of lecture are missing because I forgot to turn on the recording.  My apologies.

* 2020-09-21: Kalman filter.
  * Preparation: AIfR Lesson 4.
  * [Kalman Filter slides](https://stanford.edu/class/ee363/lectures/kf.pdf) from Stephen Boyd's [EE363 Linear Dynamical Systems](https://stanford.edu/class/ee363/index.html) course at Stanford.
  * Implementing KF with Python's NumPy library: Colaboratory notebooks with [problem definition and starter code](https://colab.research.google.com/drive/10y7ObCYRR3KuCSSNAUR2ycP6d4iSEWN6?usp=sharing) and [solution](https://colab.research.google.com/drive/1shrBktsbRDqPmt4TI5JkOLyE2hNRsjsm?usp=sharing).  *Do not look at the solution until you have attempted to solve the problem from the starter.* 
  * [Recorded lecture](https://ubc.zoom.us/rec/share/0a6W2JNRYWenrC1BIj8Lv-o9IKW633gYo5L6ZxKSqt-KT9Ain7PA4ytobw1Uf5gY.0RTEfiF5FcjBJtbh) and access passcode: iWr2G%*g.  (I forgot to turn off the recording during the ~20 minute breakout near the end.)

* 2020-09-23: Kalman filter complexity, limitations, and extensions.
  * Preparation: AIfR Lessons 5-7.
  * [Kalman filter slides](http://probabilistic-robotics.informatik.uni-freiburg.de/ppt/kalman.ppt) from the PR textbook.  We looked at slides 6, 7, 17, 21-27, 29, 40-43, 55, 57.
  * [Recorded lecture](https://ubc.zoom.us/rec/share/9yt7DwWHgM-TrTf6fVPk8eXFG12LdfdZT1ZfhDfmWlB2xwENekonhSs82SASVR6a.zOhzHschal4cifGY) with passcode ?4hyVl!&.
  * KF Homework: [Jupyter notebook](Lecture-Files/lecture-05-homework.ipynb) or [on Colaboratory](https://drive.google.com/file/d/1H4Kf8roRwBdJQ0tybEBDWfwx9Qy3OoAO/view?usp=sharing).
    * Homework is due Friday October 2.
    * Submission instructions will be posted soon.

* 2020-09-28: Particle filter.
  * Preparation: AIfR Lesson 8.
  * [Recorded lecture](https://ubc.zoom.us/rec/share/pdZ_qf-4_EoXgzZ_eMOjhvH-JVZcl-OLG-8P3o3SHYgTprsJ_C1NBqYnZrrAIvYV.x6nyllYMJ3jVLkzf) with passcode Wb=S^2LR.

* 2020-09-30: More particle filter.
  * Preparation: AIfR Lessons 9-11.

## Search / Planning

* 2020-10-05: