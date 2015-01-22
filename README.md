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
#### Upload Processing
#### Data Visualisation
#### Web Serving
## Documentation
### End User Guide
### Technical Documentation
