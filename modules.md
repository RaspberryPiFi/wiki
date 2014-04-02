name:Modules

Other than HTML and Javascript this project is written entirely in Python. This page will provide details of the basic overall structure and how it is split into modules. 

Cloud Web Interface
-------------------

The cloud-based web interface is split into the following modules:

### Custom Framework

Custom Framework contains some additions to the webapp2 framework that provides:

* More user-friendly error messages. By Default webapp2 will simply present a user with black text on a white screen, this provides styled error pages with the ability to show custom error messages
* Automatic generation of menu content using names specified on creation of a RequestHandler
* Template render function to remove complexity from each Request Handler. This also adds the site name (stored in the appsettings datastore entity) to each page

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
* The group setup page. This will be the first page a user sees when first installing their device.

Raspberry Pi Code
-----------------

Although there are modules that are only executed on either a slave or master device, other modules are shared and used by both. Therefore all of the Raspberry Pi modules will be listed together.

### PiSync Launcher

The PiSync Launcher is executed on both the master and slave devices and is used to start the application. It provides the following functionality:

* Ability to launch from command-line with arguments such as what mode the device should start in
* Auto-detection of whether the device should start as a master or slave (by passing the 'auto' argument)
* Retrieval and loading of saved configuration
* Enrolling facilities called if no configuration was found (for both master and slave devices)
* Demonising tool that runs the application in the background

### Master & Slave modules

Either the master or slave module is called by the launcher depending on the configuration loaded, the automatically detected device type, or the argument given by the user. These modules provide the following functionality:

* Setup of each device's player
* Setup of remote objects using [Pyro4](http://pythonhosted.org/Pyro4/)
* Event listener and polling setups
* Execution of Gobject mainloop

### Group & Device Enroll modules

These modules handle the enrollment of new devices with the cloud server. They are called by the Launcher if no appropriate configuration is found. The group enroll module is called when a new master device is being set-up and provides the following functionality:

* Generation of unique setup code that is agreed with the cloud server
* Enrollment with the cloud server using the unique setup code generated
* Communication of the setup code and instructions provided to the user in audio form (meaning that these devices do not need a screen attached to them)

The device enroll module is a remote object hosted on the master device and is called when a new device enters the network. It provides the following:

* Automatic discovery of the master upon entering the network
* Enrollment with the cloud server via the master device resulting in the device being setup with no user interaction required

### Player Module

This module consists of three classes for playing audio files (MP3s) on each device. The three classes are the base player, and a master and slave player. The master and slave player are both children on player class, all shared functionality is within the player class while the master and slave player classes add the synchronisation capabilities.

The players are capable of playing lists of audio files provided by the cloud interface and can play these either by themselves or synchronised to the master player resulting (party mode). Standard controls such as play, pause, stop, skip and volume are also provided by these players and can be controlled via the cloud interface

### Auto-Mount module

The auto-mount module listens for new storage devices (such as a USB flash drive) being added to the device and will attempt to mount any that are added, making them available to use. This module uses udev to listen to and mount the devices and does not require Superuser rights to do so. The devices mounted by Automount have an ID generated using the serial number of the drive and each partition number. The module then calls a 'callback function', provided during setup, with the ID number.

### Music Scan Module

The music scan module is used to recursively scan a directory (usually a storage device) for music. It provides the following functionality:

* Recursive scan of a directory provided
* Metadata retrieval from any music discovered
* Metadata lookup using the Music Database MusicBrainz to ensure data is correct and remove any duplicate artists or albums
* Communication of the metadata retrived to the cloud server for storage and presentation to the user
