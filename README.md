#Kane QuNeo Mixxx Preset
------------------------
###[Introductory Video](http://google.com)
------------------------
+ This repository contains all the components necessary to link a QuNeo to Mixxx with
my customized set of controls and LEDs.

+ Here are several quick-reference guides for the [Controls](#controls).

+ Feel free to [Contact Me](#contact) with any questions, suggestions, or bug reports!

####NOTE: The guide assumes the user already has Mixxx installed.
[Link-to-Mixxx's-Website](http://www.mixxx.org/).
## Install:
### I) How to apply this preset
####1. Copy presets to mixxx preset folder
######These two files need to be copied straight into the preset folder:
mixxx-controls/KANE_QuNeo.xml.midi   
mixxx-controls/KANE_QuNeo_scripts.js   
######The location of the preset folder depends upon your OS:
Windows: C:\Program Files\Mixxx\midi    
Linux: /usr/share/mixxx/midi (or /usr/local/share/mixxx/midi)    
OS X: /Applications/Mixxx.app/Contents/Resources/midi    
####2. Update your QuNeo's midi output preset
######Plug in your QuNeo
Via usb, this should be trivial. The QuNeo's LED's will go from left to right
when it is successfully connected.
######Run QuNeo Editor/QuNeo Editor.exe
It is important that you run the editor in the above folder so that the correct presets are loaded.
File > Import Preset, select

######Click "Update All Presets

There might be a QuNeo flash to this; I'm not certain.

######Switch QuNeo's mode to DJ Mode
+ Press the mode button,
+ Then select the upper left pad.

####3. Start Mixxx, select the preset

While running Mixxx, do the following:
######Options > Preferences > MIDI Controllers > QUNEO MIDI 1 > Load Preset

(If the QuNeo is not listed, refer to Mixxx's Midi Controller documentation)
######Select, from the drop down menu, the preset KANE_QuNeo

Click ok for success!

### II) Important files/folders
#####1. QuNeo Editor
This folder has the factory presets for the QuNeo mappings, where I have modified
several presets to output midi notes consistent with my settings for Mixxx controls.
This folder also contains the windows executable "QuNeo Editor.exe", which is necessary for
updating a given QuNeo's presets.
#####2. mixxx-controls
This folder contains the two files (xml and js) necessary for mapping midi notes into
Mixxx's controls.
#####3. dj
This is a home-brewed script which places the relevant files from Mixxx Controls into
the appropriate folder for Mixxx presets (according to my machine), then runs Mixxx.
#####4. install-tools
Custom scripts to export all the files necessary to install mixxx with my presets on a
linux debian machine.

## Usage:

### <a id="controls"></a>I) Controls List
Features List to come
![QuNeo Diagram](https://raw.github.com/wolfbiter/quneo-mixxx/master/quneo-mixxx-controls.png)

### II) Troubles
#####1. LED's out of whack
You can simply reselect whatever mode you happen to be in, and reassert the LEDs.
That should clear any garbage LED values.

### <a id="contact"></a>III) Contact Me
#####One of four ways:
+ post to this preset's [Mixxx Forum Thread](http://mixxx.org/forums/viewtopic.php?f=7&t=4130&sid=d276c35cf0670fa571eb4e8519a6ffa8), or
+ post to this preset's [KMI Forums Thread](http://forum.keithmcmillen.com/viewtopic.php?f=52&t=677)
+ check out our music group [beatfn](http://beatfn.com)
+ email me: wolfbiter--at--gmail.com
