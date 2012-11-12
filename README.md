#Kane QuNeo Mixxx Preset
Version 0.9.0

------------------------
###[Introductory Video](http://google.com)
------------------------
+ This repository contains all the components necessary to link a QuNeo to Mixxx with
my customized set of controls and LEDs. Virtually every LED pulses to the beat!

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

###I) Information on Modes
![QuNeo Diagram](https://raw.github.com/wolfbiter/quneo-mixxx/master/quneo-mixxx-controls.png)
+ The KANE_QuNeo preset utilizes many of the QuNeo's modes to allow more complete control over Mixxx.
+ To switch modes, first press the mode button, then the pad of the mode you want to select (see above),
and finally the assertLEDs button to tell the the KANE_QuNeo script that you've changed modes. It's important to do
this last step: otherwise, behaviour is undefined.
+ If the LEDs are messed up, you can simply change into the mode you're already in and reassert LEDs to clear garbage
values.
+ The mode you're currently in is usually clear from the LEDs that are present, but if you are unsure, you can always
press the mode button and the pad of the mode you're in will highlight. Pressing either the mode button again or the pad
will return you to your original mode.

### <a id="controls"></a>II) Controls List
+ Many of the controls map directly to Mixxx.
+ These are indicated by (Group, Control), and further details of them can be found
[here](http://www.mixxx.org/wiki/doku.php/mixxxcontrols).

#### DJ Mode (13)
+ The core functionality mode, it is assumed that the QuNeo is in this mode when turning on Mixxx.
![QuNeo Diagram](https://raw.github.com/wolfbiter/quneo-mixxx/master/quneo-mixxx-controls.png)

#####1) Horizontal Sliders
The horizontal sliders each manipulate one control in Mixxx.
+ Slider 1: Master Volume (Master, volume), but the LEDs correspond to the Master VuMeter (Master, VuMeter)
+ Slider 2: Headphone Volume (Master, headVolume)
+ Slider 3: Flanger Period (Flanger, lfoPeriod)
+ Slider 4: Flanger Depth (Flanger, lfoDepth)

#####2) Horizontal Arrows
The horizontal arrows correspond to on/off toggles for controls for each deck. When the left arrow is on, the control
is enabled for the left deck. Symmetrically, hen the right arrow is on, the control is enabled for the right deck.
The controls are as follows:
+ Topmost: Keylock (ChannelN, keylock)
+ Middle Top: Send deck to headphones (ChannelN, pfl)
+ Middle Bottom: Slip Enabled (ChannelN, slip_enabled)
+ Bottom: Flanger (ChannelN, flanger)

#####3) Rotaries / Playscratch
The rotaries, in dj mode, serve one of two functions:
+ If playscratch is enabled (the play transport button is green), then the left and right rotaries are play buttons on
touch for the left and right decks respectively.
+ Pressing the playscratch button toggles playscratch off (the play transport button is dark), which turns the rotaries
into turntables for scratching.
+ Playscratch defaults to on unless otherwise specified.

#####4) Vertical Sliders / Rhombus
The rhombus serves as a bank to the vertical sliders. This means that pressing the rhombus will cycle through different
vertical slider modes, with unique functionality offered by each mode. The modes are denoted by rhombus color:
+ Off == 1, Green == 2, Red == 3, and Orange == 4. 
+ Refer to the diagram to see which modes correspond with which functionality.

**Vertical Slider Mode 1 (Rhombus Off)**
+ *Zoom*: zooms the waveform in and out with 6 discrete steps.
+ *Cursor*: transforms the slider into a 1 - 0 position indicator for the deck. For example, if deck 1 is at the start of
the loaded song, then the slider will be full. As deck 1 progresses through the song, the slider LED value will decrease
linearly until it reaches empty when the song is at the end. Touching the slider will jump the song to the place you
press; however, be forewarned that the limited range of slider values (0 - 127) lends the cursor to imprecision.

**Vertical Slider Mode 2 (Rhombus Green)**
+ *Gain* (ChannelN, gain)
+ *Rate* (ChannelN, rate)

**Vertical Slider Mode 3 (Rhombus Red)**
+ *Deck Volume* (ChannelN, volume), but the LEDs correspond to the *Deck VuMeter* (ChannelN, VuMeter)
+ *Highs* (ChannelN, filterHigh)

**Vertical Slider Mode 4 (Rhombus Orange)**
+ *FilterMids* (ChannelN, filterMid)
+ *FilterLows* (ChannelN, filterLow)

#####5) Rate Nudging / Crossfader
+ The *Crossfader* (Master, crossfader) works however your Mixxx settings dictate (default: left for left deck
full volume, middle for both decks full volume, right for right deck full volume).
+ A single press given to the vertical arrows will *Rate Nudge* (ChannelN, rate_perm_X_small) the appropriate deck in
the pressed direction.
+ *Auto Rate Nudge*: pressing and holding any of the vertical arrows for more than the prescribed time (default: 500ms)
will activate auto nudge in the direction of the pressed arrow. Auto nudge, indicated by the vertical arrow LEDs in
the direction chosen, will proceed to nudge all decks and samplers at the prescribed rate (default: 800ms between
nudges) until one of two things happen: 1) pressing any vertical arrow will stop auto nudge, or 2) the deck corresponding
to the vertical arrow press nears its natural (file) bpm (0% rate adjustment). The 2nd option is sugar to allow the DJ
to, for example, unnoticably nudge down during the outtro of a 132 BPM song to reach 125 BPM for the next song with
a single button press (thereby freeing the DJ to perform more complex transitions).

#####6) Hotcues
+ *Hotcues* (ChannelN, hotcue_X_activate) jump to the location of the hotcue in the corresponding deck, and if held
while track is not playing, will temporarily play until release (after release, the track jumps back to the
pressed hotcue).
+ Hotcue LEDs convey information about the track:
+ A **Set** hotcues is **Red** if the track has *passed*,
+ **Orange** if it's the *next* hotcue vis-a-vis track position,
+ and **Green** if it's *yet to be passed*.
+ **Unset** hotcues are **off**.

#####7) Kills
These buttons toggle bands from the deck's frequency spectrum on/off. The size of the bands is determined by
preferences in Mixxx.
+ *Kill Highs* (ChannelN, filterHighKill).
+ *Kill Mids* (ChannelN, filterMidKill).
+ *Kill Lows* (ChannelN, filterLowKill).

#####8) Sync / Cue / Jumpsync / Beat Counters
+ *Sync* syncs the deck's phase and tempo (ChannelN, beatsync).
+ *Cue* defaults to CDJ behaviour (ChannelN, cue_default).
+ *Jumpsync* toggles jumpsync on/off. If the deck position changes in any way other than moving forward by playing
(ie the deck jumps to a pressed hotcue), and jumpsync is active for that deck, the jumpsync button will flash red
and the jumping deck will be synced to the other deck. Note, this sync is in terms of **phase** and **not tempo**.
+ *Beat Counters*: these are effectively hexidecimal counters which keep track of which beat (1 through 16) each deck is
on. For a given deck, the LED on the cue button corresponds to X*4^0, whereas the LED on the sync button corresponds
to X*4^1. X is 1 when the LED is off, 2 when the LED is green, 3 when the LED is red, and 4 when the LED is orange.
NOTE: The beat counters aren't always correct, due to the wide variety of music and the difficulty associated with
reading waveforms. The counter can be manually reset to 1 using the reset beat button in visualizer mode.
NOTE: Jumpsync will not sync unless the other deck is playing. This is to prevent glitchy jumpsync loops.

#####9) Jumping / Looping / Scheduling Loops
+ When in *Looping* mode (looping button LED orange), you can set a loop by selecting the desired length from {1,2,4,8}.
The LED corresponding to the length of a present, activate loop lights up orange.
+ When a loop is present, it can be doubled or halved by pressing *Double Loop* (ChannelN loop_double) or *Halve Loop*
(ChannelN, loop_halve)
+ *Reloop* (ChannelN, reloop_exit) will toggle a set loop on or off.
+ When *Jumping Mode* is on (either forward or backward LED red), you can jump a number of beats by pressing the
desired distance {1,2,4,8}. The track will jump either forwards or backwards appropriately. If the track's metadata
contains the correct BPM information, jump will jump exactly on the beatgrid.
NOTE: Activating jumping mode will automatically toggle off looping mode, whereas deactivating jumping mode will
automatically toggle on looping mode. These behaviours are for ease of use while DJing.
+ *JumpLoop Mode* (looping LED orange and either forward or backward LED red) can be achieved by toggling looping mode
while already in jumping mode. While in jumploop mode, pressing {1,2,4,8} will jump the deck that number of beats
forward or backward depending upon which jump is on, and then loop over that many beats. This is incredibly useful if,
while mixing two songs, you miss a looping point and need to smoothly recover.
+ *Loop Scheduling Mode* (looping LED green and both jump LEDs off) is achieved by toggling off looping mode while in
looping mode. Pressing {1,2,4,8} in this mode will light the LED corresponding to that number red, indicating that a
loop of that length is scheduled for that deck's next jump. A jump is defined as the deck position changing in any way
other than moving forward by playing or jumping forward one beat. A loop may be unscheduled if it is reselected while
in loop scheduling mode.

####Cueleft Mode (14) / Cueright Mode (15)
+ These modes are used for cuing, as they provide cue deletes for the left and right decks respectively.
+ Unless otherwise specified, all controls default to the functionality specified in DJ Mode (13)
![QuNeo Diagram](https://raw.github.com/wolfbiter/quneo-mixxx/master/quneo-mixxx-controls.png)
![QuNeo Diagram](https://raw.github.com/wolfbiter/quneo-mixxx/master/quneo-mixxx-controls.png)

#####1) Hotcue Deletes
+ Deletes the hotcue (ChannelN, hotcue_X_delete)

#####2) Beatgrid
+ Sets the beatgrid of the corresponding deck to its current visual playposition (ChannelN, beats_translate_curpos)

#####3) Visual Nudge / Visual Scroll
+ *Visual Nudge*: each vertical arrow press nudges the corresponding deck's visual play position in the direction of
the press (up => forward, down => backward). This is incredibly useful for setting precise beatgrids; the distance
nudged can be customized.
+ *Visual Scroll*: when a visual nudge arrow is held for greater than a customizable amount of time (default: 500ms),
the corresponding deck will continuously nudge (at a customizable speed) in the pressed direction until button release.

####Library Mode (16)
+ This mode is for selecting and loading songs from your playlists into your decks and samplers.
+ Includes pleasant LED visualizers where cues would normally go in DJ Mode (13)!
+ Unless otherwise specified, all controls default to the functionality specified in DJ Mode (13)
![QuNeo Diagram](https://raw.github.com/wolfbiter/quneo-mixxx/master/quneo-mixxx-controls.png)

#####1) Load Buttons
+ Loads the highlighted track into the selected deck or sampler iff the selected deck or sampler is not playing.
(ChannelN, LoadSelectedTrack) or (SamplerN, LoadSelectedTrack).
+ The color of the load LED corresponds to the play status of the deck or sampler. Red means the deck or sampler is
playing and therefore will not accept a load command; vice versa for green.

#####2) Playlist Scroll / Tracklist Scroll / Playscratch
+ *Playscratch* retains similar functionality, except that now it toggles the rotaries between play and scroll.
NOTE: Activating library mode defaults playscratch to off.
+ *Playlist Scroll* allows for quick, coarse scrolling through playlists.
+ *Tracklist Scroll* allows for quick, coarse scrolling through tracks.

#####3) Playlist Step / Tracklist Step
+ *Playlist Step* scrolls up/down through playlists, one at a time (Playlist, Select****Playlist)
+ *Tracklist Step* scrolls up/down through tracks, one at a time (Playlist, Select****Track)

####Visualizer Mode (16)
+ This mode basically unbinds most functionality and replaces it with LED visualizations.
![QuNeo Diagram](https://raw.github.com/wolfbiter/quneo-mixxx/master/quneo-mixxx-controls.png)

#####1) Reset Beat
+ *Reset Beat* sets the beat count (internal to the KANE_QuNeo script) of the corresponding deck to 1.
+ Useful for lining up the LEDs while enjoying visualizer mode.

#####2) Sync
+ The sync button (described in DJ Mode (13)) is still active so that visualizers between decks may be synced.

### III) Customizing This Preset
+ documentation TODO
+ EXAMPLE: The sensitivity of the scratches can be modified by tweaking the KANE_QuNeo.scratchSpeed variable in
kane-quneo-mixxx/mixxx-controls/KANE_QuNeo_scripts.js (make sure to reinstall after modifying!).

### IV) Troubles
#####1. LED's out of whack
You can simply reselect whatever mode you happen to be in, and reassert the LEDs.
Doing this should simultaneously clear any garbage LED values and assert the proper values.

#####2. [Contact Me](#iii-contact-me) with any other troubles or bugs!

### V) Todo:
+ allow for 4 decks
+ 1 shot samples via sampler decks
+ allow for cue place/delete undos
+ shift button to allow for up to 32 (64?) cues
+ revamp jumploop system
+ VuMeters to reflect volume when track stopped
+ more sliders to pulse to kicks, hitting true value? (maybe too noisy for practical use)
+ add functionality to discretely change the key of a given deck up/down one half-step at a time
+ fix auto nudge so that the nudge rates are consistent between decks (it's messed up because nudge operates on % of
natural BPM, which is off course different for different natural BPMs). 
+ fix cue/sync/beatcounter LED interplay
+ documentation on customizing the preset
+ documentation for when beat counters are/aren't correct
+ make it clear that others can switch which modes my presets are mapped to, in case they need the modes for other things
+ clarify when reset beat does/does not work

## <a id="contact"></a>Contact Me
#####One of four ways:
+ post to this preset's [Mixxx Forum Thread](http://mixxx.org/forums/viewtopic.php?f=7&t=4130&sid=d276c35cf0670fa571eb4e8519a6ffa8)
+ post to this preset's [KMI Forums Thread](http://forum.keithmcmillen.com/viewtopic.php?f=52&t=677)
+ check out our music group [beatfn](http://beatfn.com)
+ email me: wolfbiter--at--gmail.com