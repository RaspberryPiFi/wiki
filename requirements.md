name:Requirements

Due to the short amount of time that this project is to be completed in, I will be using the MoSCoW technique to categorise the requirements by their importance. I aim to implement the most important requirements first ensuring that they work before proceeding onto those of lower priority. 

<table>
  <tr>
    <th>#</th>
    <th>Summary</th>
    <th>Description</th>
  </tr>
  <tr>
    <th colspan="3">Must have</th>
  </tr>
  <tr>
    <td>1</td>
    <td>Playback on specific device</td>
    <td>It must be possible to select an item of audio to play on a specific decice</td>
  </tr>
  <tr>
    <td>2</td>
    <td>Synchronised audio playback (Party Mode)</td>
    <td>The solution must be capable of synchronised playback of an audio file between 2 or more devices</td>
  </tr>
  <tr>
    <td>3</td>
    <td>Manual Master / Slave ability</td>
    <td>Devices must be able to either be assigned as a Master or Slave device. The master device will provide the clock (for party mode) and playback commands to the slave devices on the network.</td>
  </tr>
  <tr>
    <td>4</td>
    <td>Command line facility</td>
    <td>The software should be capable of being started (with the above functionality in place) via the command line</td>
  </tr>
  <tr>
    <th colspan="3">Should have</th>
  </tr>
  <tr>
    <td>5</td>
    <td>Service Discovery Mechanisms</td>
    <td>The Devices on the network should be capable of discovery and configuration without user interaction. For example, if a master device has been set-up, a new slave entering the network should automatically discover the master and configure itself and be available to use straight away.</td>
  </tr>
  <tr>
    <td>6</td>
    <td>Automatic Master / Slave using service discovery</td>
    <td>As well as specifying whether the device should be a master or slave device via the command line, the software should be capable of ascertaining whether it should configure itself as a master or slave automatically.</td>
  </tr>
  <tr>
    <td>7</td>
    <td>Cloud User Interface</td>
    <td>A web interface should be available to allow a user to control their devices including the setup of device names and the selection of content to be played through each device.</td>
  </tr>
  <tr>
    <td>8</td>
    <td>Purpose built Linux SD card image</td>
    <td>A fully built image that when copied to an SD card and inserted into the Raspberry Pi will be fully functional. The only user interaction will be to copy the image to the SD card and turn the device on.</td>
  </tr>
  <tr>
    <td>9</td>
    <td>Javascript controls on the cloud user interface</td>
    <td>In order to make the user experience richer when controlling a device through the cloud user interface, JavaScript should be used to handle actions committed. This allows for pages to adapt to the user's input quicker and also provides the ability to update the control elements (e.g. volume control) if they change.</td>
  </tr>
  <tr>
    <th colspan="3">Could have</th>
  </tr>
  <tr>
    <td>10</td>
    <td>A Packaged version of the application</td>
    <td>A packaged version of the final solution could be made available that can be installed on practically any Debian system. This could be hosted in a custom repository.</td>
  </tr>
  <tr>
    <td>11</td>
    <td>Allow control of the devices via UPnP and/or AirPlay</td>
    <td>The devices could be configured to render media via UPnP or Airplay allowing them to play audio from external sources such as mobile phone, tablets and other media servers.</td>
  </tr>
  <tr>
    <td>12</td>
    <td>Ability to play music from attached USB device</td>
    <td>A user could store their audio on USB devices (such as flash drives). This music could then be made available for playing when the user plugs the USB device into their master device</td>
  </tr>
  <tr>
    <td>13</td>
    <td>Ability to play music from network storage</td>
    <td>A user could store their audio on a networked storage device. This could be discovered by the master device and the audio made available for playback on all devices.</td>
  </tr>
  <tr>
    <td>14</td>
    <td>Automatic audio metadata discovery</td>
    <td>In order to display a user audio collection is a user friendly way, the audio files could be scanned for their metadata. This metadata could then be used to display the user's collection on the user interface.</td>
  </tr>
  <tr>
    <td>15</td>
    <td>Ability to run as Daemon</td>
    <td>Rather than having the app running interactively, the application could be daemonized allowing it to be run as a service. As the application is controlled entirely through the cloud user interface interactivity is not required. Having the ability to run the application as a service also means that the image can be configured to run at startup using an init script.</td>
  </tr>
  <tr>
    <th colspan="3">Wont have</th>
  </tr>
  <tr>
    <td>16</td>
    <td>Security improvements</td>
    <td>Due to the short amount of time that has been assigned to complete this project in, tight security improvements will not be possible. However with more time the system would use public/private key exchanges in order to provide authentication, confidentiality and integrity as well as web security measures such as XSRF protection.</td>
  </tr>
</table>
