## Downloads
`
You can download the RAMDanceToolkit in three different ways:

1) [Compiled application](Overview#downloads)

2) [Source code via zip file](Overview#downloads)

3) [Cloned Github repository](https://github.com/YCAMInterlab/RAMDanceToolkit)

The following sections will walk you through how to setup installing the RAMDanceToolkit depending on which method you choose.

At the end, we will describe how to get MotionData into the app for testing.

## Compiled Application

Unzip the downloaded file and launch your RAMDanceToolkit app.  

[[/Images/Introduction/fig-setup-1.png]]


## Source code zip

Download the source code via zip file and put the downloaded files into your openFrameworks (version 0.8.4) folder.

**RAMDanceToolkit does NOT go into your {OF_ROOT}/app folder**

**It goes into your top-level {OF_ROOT} folder. See image below**

[[/Images/Introduction/fig-setup-of.png]]



## Cloning the RAMDanceTookit repository

**[git](http://git-scm.com/downloads) has to be installed beforehand.**

Clone the RAM repository into your top-level openFrameworks (version 0.8.4) folder.
	
	$ cd {OF_ROOT}
	$ git clone https://github.com/YCAMInterlab/RAMDanceToolkit

**RAMDanceToolkit does NOT go into your {OF_ROOT}/app folder**

**It goes into your top-level {OF_ROOT} folder. See image below**

[[/Images/Introduction/fig-setup-of.png]]

After you clone the RAMDanceToolkit, you need to do the following to steps:

### 1. Run the submodules script to download additional addons and patch ofxUI

This repo doesn't include any addons in `RAMDanceToolkit/addons`. They are instead managed as submodules.

Run this shell script after cloning the repo.
  
	$ cd {RAM_ROOT}
	$ ./submodules.sh


#### What does submodules.sh do?

This script simply checks out the submodules, and applies the ofxUI.patch on the ofxUI folder. ofxUI requires the `GUI/NewMedia Fett.ttf` font file which is located at `bin/data`, so we  duplicate the font to every project. After applying this patch, the path to font file will be changed to `{RAM_ROOT}/resources/Fonts/FreeUniversal-Regular.ttf`.

### 2. Download resources

This repo doesn't include some big size files e.g. Sounds, MotionData so you have to download them manually.

- [RAM-Sound_MotionData_v1_0_0.zip](https://github.com/YCAMInterlab/RAMDanceToolkit/releases/download/v1.0.0/RAM-Sound_MotionData_v1_0_0.zip) (29.5MB)

After downloading this zip file, add `Sounds` and `MotionData` folders into your `{RAM_ROOT}/resources` folder.

[[/Images/Introduction/fig-setup-4.png]]


## Folder structure

If you are a developer, you can modify the RAMDanceTookit source code found in `RAMDanceToolkit/apps/RAMDanceToolkit`. Please reference the RAM API Reference found on this wiki as well.

The follow is a description of the folders found in the source code:

### Addons 

This foler contains ofxAddons which are loaded from core libs. If you want to add other addons, we recommend adding it to `{OF_ROOT}/addons`.

### Apps

This foler contains RAMDanceToolkit and OpenNIOSC. You can use OpenNIOSC instead of MOTIONER or other sensors for a simple mocap test if you have a Microsoft Kinect. Open the .sln file for Windows VisualC++ or the .xcodeproj file for OS X XCode to edit and use. If you are using a newly downloaded version of openFrameworks, you need to open:

`{OF_ROOT}/libs/openFrameworksCompiled/project/vs2010/openframeworksLib.sln`

and build it using debug and release build settings before compiling RAM Dance Toolkit projects.

### Examples

This folder contains sample projects for understing the RAMDanceToolkit API. 

### Libs

This folder contains the RAMDanceToolkit core library.

### Resources

This folder contains resources which are loaded for each application. You can use `ramToRecourcePath(...)` in your code to get the path to this folder. By design, the RAMDanceToolkit searches for a resources folder that is near your application. By default this will be a few directories above your application, in the RAMDanceToolkit parent folder. If you are creating your own release of the RAMDanceToolkit to share with other people, you can place the resources folder wherever you would like and the application will find it easily.

## MotionData playback

You can test the RAMDanceToolkit without MOTIONER or other sensors by playing back recorded motion data.

**Note: Currently, motion data playback is available only for Mac OS. please use Motion data OSC Server if you use Windows.**

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
