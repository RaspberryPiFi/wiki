name:Modules

Other than HTML and Javascript this project is written entirely in Python. This page will provide details of the basic overall structure and how it is split into modules. 

Cloud Web Interface
-------------------

The cloud-based web interface is split into the following modules:

### Custom Framework

Custom Framework contains some additions to the webapp2 framework that provides:
* More user-friendly error messages. By Default webapp2 will simply present a user with black text on a white screen, this provides styled error pages with the ability to show custom error messages.
* Automatic generation of menu content using names specified on creation of a RequestHandler
* Template render function to remove complexity from each Request Handler (this also adds the site name stored in the appsettings datastore entity

### Models

The models module contains all of the datastore models that will be used. These models include:
* Page
* Group
* Device
* Song
* Album
* Artist
* AudioData (Made up of repeated Songs, Albums and Artists)

### API Handlers

This module provides handlers for each of the API functions. The API will only be used for communication between the Raspberry Pi and the Cloud Service initially but may be developed further in the future. Examples of functions provided by the API include:
* Group and device enroll functions
* Update request function (for polling)
* Library update function

### Frontend Handlers

This module will handle any requests made on the front-end by a user. As an addition to this, the module will also handle requests from the JavaScript that will be used on the front-end for updating the current status and sending commands to devices.

### Settings Handlers

The settings handlers module provides functions for dealing with requests to settings related pages. This includes:
* The primary setting page where users can test and re-name their devices
* The group enroll page. This will be the first page a user sees and is used for setting up a new set of devices.





