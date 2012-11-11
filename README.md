#Kane QuNeo Mixxx Preset
Version 0.9.0

------------------------
###[Introductory Video](http://google.com)
------------------------
+ This repository contains all the components necessary to link a QuNeo to Mixxx with
my customized set of controls and LEDs.

+ Here are several quick-reference guides for the [The Controls](#i-controls-list).

+ Feel free to [Contact Me](#iii-contact-me) with any questions, suggestions, or bug reports!

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

### II) Potentially Important files/folders
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

###I) Modes
![QuNeo Diagram](https://raw.github.com/wolfbiter/quneo-mixxx/master/quneo-mixxx-controls.png)
+ To switch modes, first press the mode button, then the pad of the mode you want to select (see above),
and finally the assertLEDs button to tell the the KANE_QuNeo script that you've changed modes. It's important to do
this last step: otherwise, behaviour is undefined.
+ If the LEDs are messed up, you can simply change into the mode you're already in and reassert LEDs to clear garbage
values.
+ The mode you're currently in is usually clear from the LEDs that are present, but if you are unsure, you can always
press the mode button and the pad of the mode you're in will highlight. Pressing either the mode button again or the pad
will return you to your original mode.

### <a id="controls"></a>II) Controls List
Many of the controls map directly to Mixxx - further details of them can be found 
[here](http://www.mixxx.org/wiki/doku.php/mixxxcontrols) - and are marked with (M)
#### DJ Mode (13)
![QuNeo Diagram](https://raw.github.com/wolfbiter/quneo-mixxx/master/quneo-mixxx-controls.png)

#####1) Horizontal Sliders
The horizontal sliders each manipulate one control in Mixxx.
+ Slider 1: Master Volume (M), but the LEDs correspond to the Master VuMeter (M)
+ Slider 2: Headphone Volume (M)
+ Slider 3: Flanger LFO (M)
+ Slider 4: Flanger Depth (M)

#####2) Horizontal Arrows
The horizontal arrows correspond to on/off toggles for controls for each deck. When the left arrow is on, the control
is enabled for the left deck. Symmetrically, hen the right arrow is on, the control is enabled for the right deck.
The controls are as follows:
+ Topmost: Keylock (M)
+ Middle Top: pfl (sends selected decks to headphones) (M)
+ Middle Bottom: Slip Enabled (M)
+ Bottom: Flanger (M)

#####3) Rotaries / Playscratch
The rotaries, in dj mode, serve one of two functions:
+ If playscratch is enabled (the play transport button is green), then the left and right rotaries are play buttons on
touch for the left and right decks respectively.
+ Pressing the playscratch button toggles playscratch off (the play transport button is dark), which turns the rotaries
into turntables for scratching.
+ The sensitivity of the scratches can be modified by tweaking the KANE_QuNeo.scratchSpeed variable in
kane-quneo-mixxx/mixxx-controls/KANE_QuNeo_scripts.js (make sure to reinstall after modifying!).

#####4) Vertical Sliders / Rhombus
The rhombus serves as a bank to the vertical sliders. This means that pressing the rhombus will cycle through different
vertical slider modes, with unique functionality offered by each mode. The modes are denoted by rhombus color:
+ Off == 1, Green == 2, Red == 3, and Orange == 4. 
+ Refer to the diagram to see which modes correspond with which functionality.
+ Zoom: zooms the waveform in and out with 6 discrete steps.
+ Cursor: transforms the slider into a 1 - 0 position indicator for the deck. For example, if deck 1 is at the start of
the loaded song, then the slider will be full. As deck 1 progresses through the song, the slider LED value will decrease
linearly until it reaches empty when the song is at the end. Touching the slider will jump the song to the place you
press; however, be forewarned that the limited range of slider values (0 - 127) lends the cursor to imprecision.
+ Gain:                                                                          


#####5) 


### III) Troubles
#####1. LED's out of whack
You can simply reselect whatever mode you happen to be in, and reassert the LEDs.
Doing this should simultaneously clear any garbage LED values and assert the proper values.

#####2. [Contact Me!](#iii-contact-me)

### IV) TODO:
+ allow for 4 decks
+ 1 shot samples via sampler decks
+ allow for cue place/delete undos
+ shift button to allow for up to 32 (64?) cues
+ revamp jumploop system
+ VuMeters to reflect volume when track stopped
+ more sliders to pulse to kicks, hitting true value? (maybe too noisy for practical use)

### <a id="contact"></a>V) Contact Me
#####One of four ways:
+ post to this preset's [Mixxx Forum Thread](http://mixxx.org/forums/viewtopic.php?f=7&t=4130&sid=d276c35cf0670fa571eb4e8519a6ffa8)
+ post to this preset's [KMI Forums Thread](http://forum.keithmcmillen.com/viewtopic.php?f=52&t=677)
+ check out our music group [beatfn](http://beatfn.com)
+ email me: wolfbiter--at--gmail.com