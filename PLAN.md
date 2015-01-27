# Wild Pet Science - Project Plan

This document lays out the tasks to be primarily undertaken by each member of
the team, as well as the estimated time for these tasks to be completed. A
section of the implementation of the project has been allocated to each team
member such that all members will have the opportunity to demonstrate practical
programming skills, and that the overall division of work remains close to
equal.

## Overview
The specification document for the project includes a detailed breakdown of what
the requirements and functionality of the system should be when implemented
fully, as well as providing an overview of project management policy.

In contrast, here the project is broken down into implementation modules,
separated by the team member primarily responsible.

All estimated times given here include the writing of tests to be run by our
Travis CI continuous integration system, as well as carrying out suitability and
integration testing.

## Antoanela

## Bruce
**Config Interface and System Image Creation**

This part of the project has been estimated to take between 20 and 25 hours.

### Web Serving
As detailed in the specification, users need to be able to perform some basic
setup tasks when the system is first used, as well as potentially reconfiguring
the system. The primary goal of Bruce's work on the project is to implement a
web application written using the SparkJava framework to serve a site
on the user's local network. This site will be a single page with a small number
of controls on it. On the configuration site, AJAX requests will provide a
convenient way of relaying configuration information back to the Java
application.

### Zone Marking
The most technically challenging aspect of the configuration interface will be
the creation of a facility for marking zones on an image of the cage. To do
this, an HTML canvas element will be used, and a custom module developed in
Javascript to allow drawing of zones.

### Other Configuration
The other elements of configuration (start / stop and code generation) can be
implemented relatively easily by AJAX calls to web framework endpoints.

### System Image Creation
Towards the end of the project, Bruce's work will involve investigating
techniques for creating a burnable Raspberry Pi SD card image. This will involve
creating a method of including the app in a minimal Linux image, then writing
build scripts to automate the process.

A potentially promising approach to this task that has been investigated briefly
is using a base Arch Linux system together with Docker to run the application in
a more platform-independent way. However, depending on how the development of
the project progresses, certain approaches may become more or less viable.

## Nick

## Stuart
**Analysis of movement data**

This part of the project has been estimated to take between 15 and 20 hours.

### Data Input
After an image of the monitored habitat has been captured and processed, some data for that frame will be produced, including:


* The position of the animal within the habitat in (x,y) coordinates.

* Various metadata produced by the processing stage, e.g. the likelihood of the
  animal being in that position.

The following data will also be used for analysis:

* The time at which the frame is produced.

* The positions of zones that are marked in the config stage, along with their
  descriptions or associated activities (sleeping, feeding etc.).

### Analysis
The relevant data will be produced/updated and sent to the server
periodically. The analysis includes:

* The position of the animal and the zones will be used to produce a set of
  (x,y,t,zone) values for use by the front end libraries that will produce
  heatmaps.

* The time spent in each zone, along with existing data about the zone (size,
  location, description).

* The speed of the animal will be computed using differences in displacement to
  produce (v,t) values, graphed as a measure of activity.

More sophisticated analysis may further be produced such as the most common
transition chains of the animal moving from zone to zone.

## Vlad
**Motion tracking**

We expect this part of the project to take between 15-20 hours.

### Input / output
The module Vlad is assigned to work on will receive a stream of images as input
from the image normalisation module and output a stream of data containing:

* The coordinates of the center of motion (x,y)

* Time the position was recorded (t)

* Other metadata relevant to the analysis stage, such as the probability of the
animal being located at those coordinates (m)

### Motion tracking algorithm
For the purpose of implementing thie motion tracker algorithm, the open source
computer vision and graphics library OpenCV will be used find differences between
consecutive images in the input stream. Then clustering algorithms will be used to
determine areas of motion within the cage, the center of the largest area being
the most likely place where the animal is located.

The algorithm will also be able to identify which motions aren't caused by the
animal (either small changes in the habitat, or motions caused by people checking
the cage).

The main challenge this module presents is to implement an efficient motion tracker
algorithm capable of processing at least 10 frames per second.


## Will
**Build system, image capture and testing**

We expect this part of the project to take approximately 20-30 hours.

### Build system
This project will need to run on a wide range of platforms - development will
happen on Windows, Mac OS X and Linux, and deployment on a Raspberry Pi. Hence
it is important to ensure that our project will work reliably in a wide range
of software and hardware environments. The first part of Will's work is to set
this up to allow the other team members to develop and deploy in a platform
independent maner.

### Image capture
When running on a Raspberry Pi we need to be able to capture images from the
Pi's camera - since this uses a different interface to standard webcams, Will
will create a common interface for this camera and other data sources.

When running on a computer we will need capture images from a local webcam -
Will can also investigate how we can do this from within Java on different
platforms.

During regular development it makes sense to use test footage rather than a
live webcam feed, and so Will will also work on inputting this data in the same
format as the live data from webcams.

### Testing
Code should be unit-tested where relevant. Will will also set up a testing
platform for verifying that, firstly our code, and secondly our image
processing algorithms are behaving in a correct fashion. This can be checked by
comparing their output to that from existing motion detection software.
