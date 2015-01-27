# Wild Pet Science - Specification

## Background & Motivation
Children often have a small pet - for example, a hamster or a gerbil. This
project aims to use the sense of ownership children often feel about their pets
to drive an interest in science by allowing children to gather interesting
statistics about their pet. Professional ecological studies use sophisticated
techniques such as sonar and GPS to track animals, but this project aims to take
a low cost and user-friendly approach using widely available computing hardware
together with custom software.

## Overview and Use Cases
The Wild Pet Science project allows users to compare their pets' behaviour to
other pets and animals in the wild. Our main metric for comparison will be the
movement of the animal, using a computer and small digital camera that tracks 
the position of a pet in its cage. Image processing techniques will be applied 
to prepare the data, along with statistical analysis to infer information about 
routine and habits. The collected data can then be compared to the pets of other
users of the software and some wild animals (using publicly available data
from [Movebank](http://movebank.org)).

### Project Success Criteria
The project will be judged as having been successful if the following system
functionality exists in a correct, well tested and well-documented state:

* Users should be able to plug a Raspberry Pi device into a power source,
  connect it to a camera and to a network, then be able to configure the device
  appropriately to take pictures of a small animal in a cage.

* Once configured, the system should take periodic pictures of the animal in its
  cage by using the attached Raspberry Pi camera.

* These pictures should then be used to track the movement of the animal over
  time.

* Analysis should be performed on the collected image data to reconstruct
  movement paths around the environment, and to make inferences about the
  activities being performed by the animal.

* This data should be uploaded to a server, where users should be able to log in
  with a Google account to view their animal's data and compare it to data
  obtained from open data sets on animal movement.

Additionally, there are some important criteria relating to how the project is
managed and administered that will factor into our evaluation of success:

* All members of the team should have a significant and equal contributing role
  to the project.

* Time should be managed effectively, so that the overall time taken for the
  project is close to that recommended in the briefing book.

If the above criteria are met then the project will be judged a success.

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

##### Image normalisation
As it is impossible for the user to keep the camera from moving, images will be
normalised so that they provide a constant viewpoint over the cage. This will be
accoplished by the use of special visual markers the user would have to apply on
the corners of the animal's cage.

#### Movement Tracking
The stream of images provided through the capture interface will be analysed by
a motion tracker in order to detect the position (XY coordinates) of the animal
in each image. These coordinates will be compared to a set of user defined
zones (such as water, food, bed etc) to determine what the animal is currently
doing.

##### Performance
Small animals tend to either move quickly or stay still. This implies that the
motion tracker algorithm should be able to operate at frame rates of at least 10-15 FPS
in order to achieve reasonable accuracy in determining the location of the animal.

#### Data Analysis
The movement tracking software will output a stream of data containing the
location of the animal at a given time. These data must then be analysed to provide 
different kinds of information to the user about the animal.

##### Behavior Identification
It should be possible for the user to manually specify areas of interest specific
to their pet (for example, picking out the sleeping area and water bottle). The behavior
of the animal will be determined based on its proximity to such areas of interest.
Also, the software should be able to identify the times during which each behavior is most
frequent (for example, determine that the animal sleeps mostly during the day, and
forages during evenings and mornings).

##### Migration Patterns
The data should also be used to determine the movement of the animal during some 
timeframe (for example: last hour, last 24 hours, etc.). As the visualisation of this data
is would be done by superimposing the migration pattern on a still image of the cage,
this feature would only be available on the client software.

#### Server Communication
The client software will periodically upload analysed data to the server for 
processing, visualisation and public/remote access. These data will represent 
the positions of the pet in the cage since the last upload. All information 
will be stored in the server's database and users will be able to access it 
by logging in with their Google account.

#### Raspberry Pi "Plug & Play"
The Raspberry Pi client should be easy to set up for non-technical users (ideally plug and play).

### Server
In this specification, the server runs a web application to receive and visualise 
data from all clients.

#### Upload Processing
The server should be able to receive and process uploaded data from individual clients.

#### Front End
The front end will allow the user to select multiple data sets in order to view
and compare the movement of animals.

##### Data Visualisation
The server should have some functionality to visualise the received data in an
intuitive and useful way. Data shown for each animal should include a breakdown
of time spent in user-defined zones/activities. A graphical display of the
movement of the animal should also be included, for example a heatmap, or a
step-through display of the animal's path over time.

##### Web Serving
The server should serve a website with information about the project, and
providing a menu of available animals and access to their visualised data. The
website should have an intuitive layout that is accessible and appealing to
children.

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
camera attached. This camera will point at the cage and detect the location of
the animal under study. The Pi Noir camera is capable of low-light and
infra-red vision meaning that we will be able to track the animal during the
night.

The Pi will also be connected to the internet; for a reliable connection we
recommend that an Ethernet connection is used, however the application will
work with any kind of reliable internet connection.

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
The guide for end users needs to be accessible to people without a technical
background (i.e. no jargon, little assumed knowledge etc). The documentation
should include information on setting up the system from scratch, using it
once it has been configured, and common troubleshooting solutions. The
documentation will be available as a README in the git repository, as well as by
means of a standalone PDF download from the project web page.

Users should be walked through the process of setting up the system in a way
that is accessible without being patronising. Solutions to common issues will be
included at each stage of the process.

### Technical Documentation
As there are multiple people working together on this project, clear and
effective technical documentation will be important to its success. The source
code of the project will have JavaDoc comments used throughout development in
order to facilitate automatic documentation generation. Additionally, external
APIs should have clear documentation written in order that modules can be reused
easily.

All members of the team will be responsible for documenting code that they
write, in a way that is consistent with the project's style. Our policy of code
review will help to ensure that code committed is documented appropriately.
