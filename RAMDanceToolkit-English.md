（要伊藤さん、竹下さんからのRAM概要説明と差し替え）  
RAMDanceTooklkit is the primary source/application for the "Reactor for Awareness in Motion" Joint Research Project with Yoko Ando at Yamaguchi Center for Arts and Media. The other source is the Motioner application for accessing data from the custom inertial motion sensor system.

The toolkit itself is built using a project file in libs/. This toolkit is used by applications in apps/ such as RAMDanceToolkit which demonstrates a number of scenes built with the toolkit. addons/ contains submodules that refer to addons which are not shipped with openFrameworks.

[[/Images/Home/ram.png]]







## Links

### [Introduction to RAMDanceToolkit application (vimeo)](#) 
Screencast concerning how to use RAMDanceToolkit application by Kyle McDonald

### [Getting started with RAMDanceToolkit for developer (vimeo)](#)  
Screencast concerning how to develop using RAMDanceToolkit API by Kyle McDonald

### [RAMDanceToolkit - YCAM InterLab](#)   
Whole documentation of "Reactor for Awareness in Motion"




## Downloads 

### Latest version (x.x.x)

- Mac OS X 10.7+ [source code zip](#) (xxxxMB) [compiled application](#) (xxxMB)
- Windows 7 [source code zip](#) (xxxxMB) [compiled application](#) (xxxMB)

### Other versions
Download links are available on [YCAM InterLab server](#).





## Licenses
RAMDanceToolkit by YCAM InterLab, Yoshito Onishi, Satoru Higa, Motoi Shimizu, and Kyle McDonald is licensed under the Apache License, Version2.0

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
    

<!-- 
## [RAM API Reference](RAM API Reference)   
The reference for the RAMDanceToolkit core API
-->







## Structure

### ramBaseApp

[[/Images/Home/inheritence.png]]

Regularly testApp is inherited from ofBaseApp but all of testApp in RAMDanceToolkit projects are inherited from `ramBaseApp` which is inherited from ofBaseApp. The regular methods in testApp can be used as your usual hacking. ramBaseApp provides additional methods and events to testApp to manipulate the data sent from [MOTIONER](https://github.com/YCAMInterlab/Motioner) or other motion capture system. 

RAMDanceToolkit starts running from writing one line code in your testApp::setup() like:

	void testApp::setup()
	{
		// do something…
		
		ramInitialize(10000); // osc port
	}

---


### OSC data format
	
	- インプットのフォーマット : OSCフォーマット(ito3/8)


---

 
### Scene
 
 
[[/Images/Home/structure.png]]

We call the sequence this image shows as `Scene`.  


	- フィルタの概念:
	     - 各フィルタの説明＋スクリーンショット（3/8）
	- レコグナイザの概念: 
	     - 各レコグナイザの説明＋スクリーンショット（3/8）
	- ヴィジュアライザの概念:
	     - 各レコグナイザの説明＋スクリーンショット（3/8）
	- イベントの概念
	    - 各イベントの説明
	- 各シーンごとのスクリーンショット＋パラメータの説明：shmizu







