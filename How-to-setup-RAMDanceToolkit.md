## Downloads

You can download the RAMDanceToolkit in three different ways:

1) [Compiled application](Overview#downloads)

2) Source code via zip file

3) [Cloned Github repository](https://github.com/YCAMInterlab/RAMDanceToolkit)

The following sections will walk you through how to setup installing the RAMDanceToolkit depending on which method you choose.

At the end, we will describe how to get MotionData into the app for testing

## Compiled Application

Unzip the downloaded file and launch your RAMDanceToolkit app.  

[[/Images/Introduction/fig-setup-1.png]]

## Source code zip

Download the source code via zip file and put the downloaded files into your openFrameworks (version 0.7.4+) directory.

[[/Images/Introduction/fig-setup-of.png]]

If you are a developer, you can modify the RAMDanceTookit source code found in `RAMDanceToolkit/apps/RAMDanceToolkit`. Please reference the RAM API Reference found on this wiki as well.

The follow is a description of the directories found in the source code:

### Addons 

These are ofxAddons which are loaded from core libs. If you want to add other addons, we recommend adding it to `{OF_ROOT}/addons`.

### Apps

This directory includes RAMDanceToolkit and OpenNIOSC. You can use OpenNIOSC instead of MOTIONER or other sensors for a simple mocap test if you have a Microsoft Kinect. Open the .sln file for Windows VisualC++ or the .xcodeproj file for OS X XCode to edit and use. If you are using a newly downloaded version of openFrameworks, you need to open<br />
`openFrameworks Folder/libs/openFrameworksCompiled/project/vs2010/openframeworksLib.sln`<br />
and build it using debug and release build settings before compiling RAM Dance Toolkit projects.

### Examples

Sample projects for understing the RAMDanceToolkit API. To check which files you need to usefor each project, please read the "[[apps|https://github.com/YCAMInterlab/RAMDanceToolkit/wiki/How-to-setup-RAMDanceToolkit#apps]]" above.

### Libs

This is the RAMDanceToolkit core library.

### Resources

These are shared resources which are loaded for each application. You can use `ramToRecourcePath(...)` in your code to get the path to this directory.

This directory also contains recorded motion data, which is described in more detail below.

## Cloneing the RAMDanceTookit repository

Clone the RAM repository into your top-level openFrameworks (version 0.7.4+) directory.

[[/Images/Introduction/fig-setup-of.png]]

After you clonse the RAMDanceToolkit, you need to do the following to steps:

### 1. Run the submodules script to download additional addons and patch ofxUI

This repo doesn't include any addons in `RAMDanceToolkit/addons`. They are instead managed as submodules.

Run this shell script after cloning the repo.
  
**[git](http://git-scm.com/downloads) has to be installed beforehand.**


	$ cd {RAM_ROOT}
	$ ./submodules.sh


#### tasks of submodules.sh

This script simply checks out the submodules, and applies the ofxUI.patch on the ofxUI directory. ofxUI requires the `GUI/NewMedia Fett.ttf` font file which is located at `bin/data`, so we  duplicate the font to every project. After applying this patch, the path to font file will be changed to `{RAM_ROOT}/resources/Fonts/FreeUniversal-Regular.ttf`.

### 2. Download resources

This repo doesn't include some big size files e.g. Sounds, MotionData so you have to download them manually.

- [RAM-Sound_MotionData_v1_0_0.zip](https://raw.github.com/wiki/YCAMInterlab/RAMDanceToolkit/releases/resources/RAM-Sound_MotionData_v1_0_0.zip) (29.5MB)

After downloading this zip file, add `Sounds` and `MotionData` directories into your `{RAM_ROOT}/resources` directory.

[[/Images/Introduction/fig-setup-4.png]]

## MotionData playback

You can test the RAMDanceToolkit without MOTIONER or other sensors by playing back recorded motion data.

**note: In RAMDanceToolkit version 1.0.0, motion data playback is available only for Mac OS.**

The recorded motion data `Ando_1` appears only at the first time of launching the RAMDanceToolkit. The other motion datas, named `Ando`, `Cyril`, `Richi`, are available in `RAMDanceTookit/resources/MotionData`.  To start playback, click "Load file" button on Actors panel or drag and drop the motion data file into the application.

[[/Images/Introduction/fig-setup-3.png]]

Note that you can playback only four motion data at the same time. If you are sending one ramActor OSC message from MOTIONER or other motion capture system to the RAMDanceToolkit, you can playback up to three motion data recordings.

[[/Images/Introduction/fig-setup-2.png]]

## Motion data OSC Server

[[/Images/Introduction/fig-setup-osc1.png]]

This application allows you to send OSC messages without using MOTIONER or other sensors.

The Resources zip file found above contain XML files for recorded motion data. This application will start sending OSC message when you drag and drop XML files into the app screen. Hopefully it will be helpful in testing RAMDanceToolkit :)


<hr>
<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="http://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">This Document</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://interlab.ycam.jp/projects/ram" property="cc:attributionName" rel="cc:attributionURL">YCAM InterLab, Yoshito Onishi, Satoru Higa, Motoi Shimizu, and Kyle McDonald</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
