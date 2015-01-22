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
#### Image Capture
#### Movement Tracking
#### Data Analysis
#### Server Communication
#### Raspberry Pi "Plug & Play"
### Server
#### Upload Processing
#### Data Visualisation
#### Web Serving

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
