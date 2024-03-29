The [RAMDanceToolkit](http://ram.ycam.jp/en/) is a C++ creative coding toolkit for creating environments for dancers. This toolkit contains a GUI and helpful functions for accessing, recognizing, and processing motion data, supporting the creation of various environments called “scenes”. By using code in an easy way, the toolkit allows you to provide realtime feedback for dancers. The toolkit uses openFrameworks, a software development toolkit for artists. The structure of the RAMDanceToolkit allows you to use functions from both the RAMDanceToolkit and openFrameworks. The RAMDanceToolkit will also be published as an application for Windows and Mac. As an application, users can choreograph or rehearse with previously programmed scenes.

[[/Images/Home/ram.png]]




## Links

### [Introduction to RAM Dance Toolkit application (Vimeo)](http://vimeo.com/64703174) 
Screencast on how to use the RAMDanceToolkit application by Kyle McDonald

### [Introduction to coding with RAM Dance Toolkit (Vimeo)](http://vimeo.com/64775855)  
Screencast on how to develop with the RAMDanceToolkit API by Kyle McDonald

### [Reactor for Awareness in Motion (RAM) - YCAM InterLab](http://interlab.ycam.jp/en/projects/ram/)   
Full documentation of "Reactor for Awareness in Motion"




## Downloads 

You can download the latest version of RAMDanceToolkit app and source code from the links below.
Afterwards please look at [How to setup RAMDanceToolkit](How-to-setup-RAMDanceToolkit) page for setup instructions. Older releases of RAMDanceToolkit and change log are archived [here](Other_Releases).

### RAMDanceToolkit Application

You can download the compiled application from here. 

- [RAM-app_osx_v1_2_1.zip](http://data.ycam.jp/interlab/ram/other_releases/RAM-app_osx_v1_2_1.zip) (Mac OS 10.7+, 77.0MB, updated on 9 Feb 2015)
- [RAM-app_win_v1_2_1.zip](http://data.ycam.jp/interlab/ram/other_releases/RAM-app_win_v1_2_1.zip) (Windows 7+, 66.3MB, updated on 9 Feb 2015)

Windows needs [Visual C++ Redistributable](https://www.microsoft.com/en-US/download/details.aspx?id=30679). If Visual studio 2012 is not installed your windows, please select your language and download x86 version & install it.

#### Known Issues

  Launching problem precompiled app from `RAM-app_osx_v1_2_1.zip` .
   Since macOS Sierra version, the gatekeeper has become stricter and prevents launching `RAMDanceToolkit.app` . Because some browser adds extended attributes after download it.
   One solution is execute bellow command in the `/Applications/Utilities/Terminal.app`

   `xattr -c {replace_path}/RAM-app_osx_v1_2_1.zip`

### Source code

The following zip files includes the entire source code, as well as motion data that can be used for developing your own projects.

- [RAM_Release_v1_1_0.zip](https://github.com/YCAMInterlab/RAMDanceToolkit/releases/download/v1.1.0/RAM-release-v1_1_0.zip) (Mac OS 10.7+, Windows7+, OF0.7.4+, 107.1MB)

### Motion Data OSC Server

The Motion Data OSC Server sends OSC messages to the RAMDanceToolkit, so you don't have to use MOTIONER or other sensors for testing. The following link includes RAMOSCServer and MotionData XML files. This application will send OSC messages to the RAMDanceToolkit when you drag and drop XML files onto the app screen. This is useful for testing the RAMDanceToolkit.

- [RAM-OSCServer_mac-v1_0_0.zip](https://github.com/YCAMInterlab/RAMDanceToolkit/releases/download/v1.0.0/RAM-OSCServer_mac-v1_0_0.zip) (Mac OS 10.7+, 32.6MB)
- [RAM-OSCServer_win-v1_0_0.zip](https://github.com/YCAMInterlab/RAMDanceToolkit/releases/download/v1.0.0/RAM-OSCServer_win-v1_0_0.zip) (Windows7+, 39.7MB)

#### Known Issues

  Launching problem precompiled app from `RAM-OSCServer_mac-v1_0_0.zip` .
   Since macOS Sierra version, the gatekeeper has become stricter and prevents launching `RAMOSCServer.app` . Because some browser adds extended attributes after download it.
   One solution is execute bellow command in the `/Applications/Utilities/Terminal.app`

   `xattr -c {replace_path}/RAM-OSCServer_mac-v1_0_0.zip`

### External Resourcse (Sound and MotionData)

For users who cloned the RAMDanceToolkit repository, please download the Sounds and MotionData files from the link below (they are not included in the repository).

- [RAM-Sound_MotionData_v1_0_0.zip](https://github.com/YCAMInterlab/RAMDanceToolkit/releases/download/v1.0.0/RAM-Sound_MotionData_v1_0_0.zip) (99.9MB)






## Licenses
RAMDanceToolkit by YCAM InterLab, Yoshito Onishi, Satoru Higa, Motoi Shimizu, and Kyle McDonald is licensed under the [Apache License, Version2.0](http://www.apache.org/licenses/LICENSE-2.0.html)

    Copyright 2012-2013 YCAM InterLab, Yoshito Onishi, Satoru Higa, Motoi Shimizu, and Kyle McDonald

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
    
<hr>
<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="http://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">This Document</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://interlab.ycam.jp/projects/ram" property="cc:attributionName" rel="cc:attributionURL">YCAM InterLab, Yoshito Onishi, Satoru Higa, Motoi Shimizu, and Kyle McDonald</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
