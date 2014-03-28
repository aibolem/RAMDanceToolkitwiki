## Downloads

To start using RAMDanceToolkit, you can download [compiled application, whole source code zip](Overview#downloads), or clone [RAMDanceTookit repository](https://github.com/YCAMInterlab/RAMDanceToolkit).

## Compiled Application

Unzip the downloaded file and launch your RAMDanceToolkit app.  

[[/Images/Introduction/fig-setup-1.png]]

### MotionData playback

You can test RAMDanceToolkit without MOTIONER or other sensors using recorded motion data playback.
**note: In RAMDanceToolkit version 1.0.0, motion data playback is available only for Mac OS.**

The recorded motion data `Ando_1` appears only at the first time launching of RAMDanceToolkit. The other motion datas `Ando`, `Cyril`, `Richi` are placed in `RAMDanceTookit/resources/MotionData`.  To start playback, click "Load file" button on Actors panel or drag and drop the motion data file to the application.

[[/Images/Introduction/fig-setup-3.png]]

Note that you can playback four motion data at the same time. If you are sending one ramActor OSC message from MOTIONER or other motion capture system to RAMDanceToolkit, you can playback three motion data.

[[/Images/Introduction/fig-setup-2.png]]


## Motion data OSC Server

[[/Images/Introduction/fig-setup-osc1.png]]

An application which send osc messages instead of MOTIONER or other sensors.
The following link includs MotionData xml files. This application starts sending OSC message when you drag and drop xml files onto app screen.
It will help your testing RAMDanceToolkit.

## Source code zip

Put the downloaded files into your openFrameworks (version 0.7.4+) directory.

[[/Images/Introduction/fig-setup-of.png]]

If you are a developer, you can modify RAMDanceTookit source code which is placed at `RAMDanceToolkit/apps/RAMDanceToolkit`. See also RAM API Reference on this wiki.

### addons 

ofxAddons which are load from core libs.  
If you want to add other addons, we recommend to add it to `{OF_ROOT}/addons`.

### apps

RAMDanceToolkit and OpenNIOSC.
You can use OpenNIOSC instead of MOTIONER or other sensors as simple mocap test if you have Microsoft Kinect. Open .sln file for Windows VisualC++, .xcodeproj file for OSX XCode to edit and use. If you are using newly downloaded openFrameworks, you need to open<br />
`openFrameworks Folder/libs/openFrameworksCompiled/project/vs2010/openframeworksLib.sln`<br />
and build it using debug and release build settings before compiling RAM Dance Toolkit projects.

### examples

Sample codes to understand API. To check which file you need to use projects, please read "[[apps|https://github.com/YCAMInterlab/RAMDanceToolkit/wiki/How-to-setup-RAMDanceToolkit#apps]]" above.


### libs

RAMDanceToolkit core library.

### resources

Shared resources which are load from each application. You can use `ramToRecourcePath(...)` in your code to get the path to directory.

As noted at Compiled Application section, recorded motion data is in the `MotionData`. 


## Clone RAMDanceTookit repository

Clone RAM repository at your openFrameworks (version 0.7.4+) directory.

[[/Images/Introduction/fig-setup-of.png]]

If you clone the RAM repo, you should do two tasks before writing code.

### 1. Submodules checkout and applying patch to modify ofxUI

This repo doesn't include the addons in `RAMDanceToolkit/addons` which are managed as submodules.

Run this shell script after cloning the repo.  
*[git](http://git-scm.com/downloads) has to be installed beforehand.


	$ cd {RAM_ROOT}
	$ ./submodules.sh


#### tasks of submodules.sh

This script simply checkout the submodules, and apply ofxUI.patch at ofxUI directory.  
ofxUI requires `GUI/NewMedia Fett.ttf` font file which is placed at `bin/data` so we have to duplicate the font to every project. After applying this patch, the path to font file will be changed to `{RAM_ROOT}/resources/Fonts/FreeUniversal-Regular.ttf`.


### 2. download resources

This repo doesn't include some big size files e.g. Sounds, MotionData so you have to download it manually.

- [RAM-Sound_MotionData_v1_0_0.zip](https://raw.github.com/wiki/YCAMInterlab/RAMDanceToolkit/releases/resources/RAM-Sound_MotionData_v1_0_0.zip) (29.5MB)

After download, add `Sounds` and `MotionData` directories into `{RAM_ROOT}/resources`.

[[/Images/Introduction/fig-setup-4.png]]

<hr>
<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="http://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">This Document</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://interlab.ycam.jp/projects/ram" property="cc:attributionName" rel="cc:attributionURL">YCAM InterLab, Yoshito Onishi, Satoru Higa, Motoi Shimizu, and Kyle McDonald</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
