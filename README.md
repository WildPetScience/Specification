# Wild Pet Science - Specification
## Overview and Use Cases
## System Components

### Client
The client software will run on a small, network-connected computer with a
camera attached that is capable of processing the live video into data to be
uploaded to the server.

#### Image Capture
Images should be captured as frequently as possible on the client device and
processed locally on the client device. This processing should consist of motion
detection capable of calculating the current position of an animal.

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

#### Server Communication
#### Raspberry Pi "Plug & Play"
### Server
#### Upload Processing
#### Data Visualisation
#### Web Serving
## Documentation
### End User Guide
### Technical Documentation
## Project Management
### Technical
#### Source Control
#### IDE / Environment
### Non-Technical
#### Group Organisation
#### Meetings
