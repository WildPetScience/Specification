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

## Antoanela

## Bruce

## Nick

## Stuart

## Vlad

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
