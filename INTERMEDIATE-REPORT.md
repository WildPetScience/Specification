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

Since the last meeting, Stuart has implemented an initial version of the
analysis stage of the pipeline. This accepts (x,y,time,probability) points from
the image processing stage and zone definition data from the config stage.

The analysis performed so far includes:

* Classifying the points into zones.
* Tracking the number of visits for each zone.
* Replacing unlikely points using simple linear interpolation between the
  current location of the animal and the last known likely location.
* Computing the speed of the animal as an activity metric.
* Packaging the data into a class for sending.

Stuart has also worked with Will on creating a demo for the analysis stage of
the pipeline to show the data analysis in action.

## Vlad

Vlad has implemented an initial version of the motion tracker based on the 
differentiation of images in a three-frame sliding window. The tracker 
removes some of the noise in the images using a median filter, then detects
the individual pixels where motion has occurred. It then determines the position
of the animal by averaging those values. This approach could be further refined
by running a clustering algorithm to determine the largest area of motion.
(if the performance of the Raspberry Pi permits it).

Vlad has also worked on a class that permits the transform of plane coordinates
from camera perspective to normalised perspective and vice-versa. This is used
in determining the final position of the animal in the normalised view of the
cage.

## Will
Will has completed the project structure setup mentioned at the previous client
meeting and has finished the cross-platform component of the project; both
codebases can now be developed on multiple platforms, and the client can be
deployed to the raspberry pi as a runnable JAR file that can utilise the
Raspberry Pi's camera as a webcam.

Since the last meeting, Will has also worked on creating the pipeline that
handles data input, processing and output. This pipeline is now functional and
is deployed in the entrypoint of the application.

Will has created a set of demonstrations that allow other team members to
easily see the output of their part of the code; these demos show the output
from varying stages of the pipeline to a user. These demos will be useful
during the end-of-project presentations since we can use them to demonstrate
how our application works.
