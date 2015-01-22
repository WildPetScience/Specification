# Wild Pet Science - Specification

## Overview and Use Cases
The Wild Pet Science project allows users to compare their pets' behaviour to
other pets and animals in the wild. This is accomplished using a small computer
that tracks the position of a pet in its cage using a small digital camera and
image processing techniques, then analyses the data for information about 
routine and habits. The collected data can then be compared to the pets of other
users of the software and some wild animals (using publicly available data
from [Movebank](http://movebank.org)).

## System Components
The system will consist of the following components:

* *Server*: The server collects uploaded data about animals and displays results
  to users.

* *Client*: The client runs on a lightweight computer in the user's home and
  captures and analyses images from a live camera and uploads movement 
  data to the server.

These components will be developed independently and concurrently by the team.

### Client
The client software will run on a small, network-connected computer with a
camera attached that is capable of processing the live video into data to be
uploaded to the server. Our solution will be developed and tested on 
Raspberry Pi devices, as they are easily available to all members of the
team, and are a reasonable choice of such a device (for end users) in the 
real world.

#### Image Capture
The client software should provide an interface through which images can be
captured by a digital camera. These images should be captured as frequently 
as possible on the client device and processed locally on the client device. 
This processing should consist of motion detection capable of calculating 
the variation in position of some object (in this case, an animal) over time.

##### Application safety around children
At no point shall the application upload images taken from the camera to the
website; all images are to be processed locally into data that contains no image
data to avoid the risk of remotely storing images that potentially could contain
children. Additionally, no identifying information should be stored as part of the
uploaded data to minimise potential privacy issues.

##### Image Capture in Darkness
It may be necessary to capture movement data in the dark at some stage during
the project (for example, due to a pet being nocturnal). This may entail using
a camera with no infrared filter to capture images. The system's image
processing module should be able to perform its analysis in a way that is
agnostic of the illumination of the scene.

#### Movement Tracking
Small animals tend to either move quickly or stay still. This makes the job of
detecting the location of such animals quite difficult at a low frame rate.
The application should be able to cope in this situation and still work out the
location of the animal.

#### Data Analysis
The movement tracking software will output a stream of data containing the
location of the animal. These data must then be analysed to work out what the
animal is doing. This can either be selected by the user (for example certain
areas representing certain activities), or detected by the program (for example
based on time of day).

##### User Activity Identification
It should be possible for the user to manually specify areas of interest specific
to their pet (for example, picking out the sleeping area and water bottle). This
identification will provide hints to the data analysis module when activities
are being classified.

#### Server Communication
The client should be able to upload analysed data to our server for visualisation and public / remote access.

#### Raspberry Pi "Plug & Play"
The Raspberry Pi client should be easy to set up for non-technical users (ideally plug and play).

### Server
In this specification, the server runs a web application to receive and visualise data from all clients.

#### Upload Processing
The server should be able to receive and process uploaded data from individual clients.

#### Data Visualisation
The server should have some functionality to visualise the received data in an intuitive and useful way.

#### Web Serving
The server should serve a web site with information about the project, and providing access to visualised data.

## Physical environment
There will be lots of physical constraints when setting up this software in a
real environment, such as the type of cage, where the camera is positioned,
lighting and so on. Because each environment will vary so much we hope to design
our software such that it works in as many as possible.

### Camera positioning
The camera may be positioned over the top or at the side of the cage, provided
that the camera has a good view of the animal under inspection. The animal's
environment must be set up such that its activity can be determined from its
location; food, water, wheel, bed and so on should be positioned in different
parts of the cage from the camera's perspective.

### Cage material
The cage should be made from a clear material, or have an open side. This is to
give the camera a clear, unobstructed view of the animal.

#### Corners of cage
The cage should have four markers in the corners visible to the camera; these
will help the camera detect where the cage is when the cage or camera moves.

## Hardware
The device we shall use for demonstration will be a Raspberry Pi, with a Pi Noir
camera attached. It will be connected to the internet via an Ethernet cable,
however as long as the user can set up a suitable connection to the internet,
the specific connection being used won't matter. The Pi will be mounted above
the cage using some sort of mount.

## Software environment
We will distribute a cut-down Linux operating system that contains our software
pre-installed. These distributions will be based on an existing Linux operating
system (such as Raspbian) and will be configured to connect to the internet and
start our software.

## Documentation
This section of the specification deals with how the project will be documented.
There are two important sets of documentation we will produce as part of the
development process:

* *Technical*: The system's code and external APIs should be thoroughly
  documented, with the goal of making the project easily accessible to other
  developers who may wish to use or modify the system for their own needs.

* *End User*: The project involves end users deploying the system themselves
  without direct expert help, and so the documentation should be easy to
  understand and follow without having a technical background. Additionally,
  as the project is targeted at children, another set of documentation
  should be produced for their use.

### End User Guide
### Technical Documentation
