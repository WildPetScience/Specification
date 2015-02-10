# Wild Pet Science - Intermediate Report

The majority of the discrete code modules have now been completed and have been
tested in isolation. This document details the implemented components and 
describes the testing procedures and results. 

## Overview


## Antoanela


## Bruce
Since the previous client meeting, Bruce has been working on implementing the
configuration interface for the application. The progress so far of the
implementation is as follows:

* The application's main entry point serves a local web page to allow
  configuration. The Bootstrap CSS library has been used to provide an
  attractive user interface while minimising development effort.

* The configuration interface allows for start / stop requests to be made to the
  running application. Currently the actual starting and stopping of the system
  has not been implemented, but will be easy to connect to the config page when
  they are.

* A framework for storing persistent application data as JSON has been
  developed, allowing the application's state and generated data (e.g. system
  logs) to be stored and retrieved from disk. Care has been taken with regard to
  writing to disk in this section, as performance on the Raspberry Pi SD card
  can be slow.

* Using the image pipeline developed by the other members of the team, a webcam
  feed was added to the configuration page. This streams images from an input
  source and displays them in an HTML canvas element. Currently, this feature
  allows users to make sure that their camera is aligned correctly. In the next
  stage of the implementation, this feature will allow the user to mark areas of
  interest on the images of their animal's cage they are shown.

## Nick


## Stuart


## Vlad


## Will
