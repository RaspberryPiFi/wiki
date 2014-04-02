name: Purpose & Goals

Overview & Background
---------------------

The primary aim of this project is to provide a low cost, multi-room streaming audio solution with an easy to use control system that runs on a low cost hardware platform (e.g. Raspberry Pi). The problem that I aim to solve is that multi-room audio solutions are often expensive, usually involving cable routing and expensive hardware. This solution should be low-cost and simple enough to be installed and used in homes by anyone and configurable enough to be of use to businesses and power users. 

Goals
-----

* Complete initial prototype (with Raspberry Pi image) by the end of March
* Try to gather as much feedback as possible and start to act on the feedback
* Get some more contributors on-board to rip my code to shreds!
* At some point in the future, release a Beta!

Limitations / Issues
--------------------

### Noticeable delay will still be present

Humans are able to detect even short delays between two audio sources and this is one of the major problems that I am attempting to overcome. There are a number of methods that will be investigated in order to keep the audio in sync but there will still be some form of delay. Due to the fact that the devices will most likely be placed in separate rooms, the delay shouldn’t be too noticeable. 

### Delay between actions committed via cloud interface

In the prototype, polling will be used for communication between the master device and the cloud server. In order to prevent the server from being overrun by this polling a delay will be set between each poll. The downside of this is that this will create a delay between actions committed in the cloud and the action executing on the device. Currently the aim is for the delay between polls to be around 2 seconds.
