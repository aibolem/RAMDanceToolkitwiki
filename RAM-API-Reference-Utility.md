# Utility

### Summary

This page shows some useful classes, including selecting a node, programatically saving/loading motion data, as well as storing camera settings.

### Table of Contents
- [ramNodeFinder](#wiki-ramNodeFinder)
- [ramNodeIdentifer](#wiki-ramNodeIdentifer)
- [ramCameraSettings](#wiki-ramCameraSettings)
- [ramTSVCoder](#wiki-ramTSVCoder)



<h1 id="wiki-ramNodeFinder">ramNodeFinder</h1>

ramNodeFinder searches for a node or multiple notes from an array of nodes managed by ramActorManager.
If you want to manupulate specific nodes, this is much easier than a for-loop. 
ramNodeFinder should be used in your draw() loop, and not in drawActor() or drawRigid()

---

##### ramNodeFinder()

Constructor.

	ramNodeFinder nf;
	nf1.setTargetName("Yoko");
	nf1.setJointID(ramActor::JOINT_HEAD);

---

##### ramNodeFinder(const ramNodeIdentifer& copy)

Constructor.
	
	ramNodeIdentifer cyril_head("Cyril", ramActor::JOINT_HEAD);
	ramNodeFinder nf(cyril_head);

---

##### void setTargetName(string name_)

Sets target name.

---

##### void setJointID(int index_)

Sets target joint id.

---

##### bool ramNodeFinder::findOne(ramNode &node)

Returns true if ramActorManager has ramNodeArray whose name is the same as ramNodeFinder::name, and the ramNodeArray has a node which has the same id as ramNodeFinder::index. 
If this is true, the search result node is set to `ramNode &node`.

---

##### vector<ramNode> findAll()

Return all nodes which matches the target name and target joint id.

---

##### vector<ramNode> findByID()

Return all nodes which matches the target joint id.

---

<br>



<h1 id="wiki-ramNodeIdentifer">ramNodeIdentifer</h1>

A tiny class for identifying a node.  
Generally it is used with ramNodeFinder.

---

##### ramNodeIdentifer()

Constructor.

---

##### ramNodeIdentifer(int index)

Constructor.

---

##### ramNodeIdentifer(const string &name)

Constructor.

---

##### ramNodeIdentifer(const string &name, int index)

Constructor.

---

##### ramNodeIdentifer(const ramNodeIdentifer& copy)

Constructor.

---

##### ramNodeIdentifer& operator=(const ramNodeIdentifer& copy)

Name and id are copied from right hand side.

---

##### void set(const string &name, int index)

Sets target name and target id.

---

##### void set(const string &name)

Sets target name.

---

##### void set(int index)

Sets target id.

---

##### void clear()

Clears target name and target id.

---

##### bool isValid() const

Checks to see if target name and target id are set.

---

##### friend ostream& operator<<(ostream &os, const ramNodeIdentifer& o)

Puts name and id into stream.

---


<br>


<h1 id="wiki-ramCameraSettings">ramCameraSettings</h1>

ramCameraSettings stores some settings used for controlling ofCamera.  

`string name`,
`ofVec3f pos`,
`ofVec3f look_at`,
`float fov`,
`unsigned int moving_type`,
`bool bMoving`,
`ofVec3f moving_from`,
`ofVec3f moving_to`,
`float moving_duration`,
`float moving_start_time`,
`float moving_end_time`,
`ofVec3f moving_axis_pos`,
`ofVec3f moving_axis_up_vector`,
`float moving_radius`,
`float moving_speed`,
`float moving_deg`,

A sample XML format is available here: _RAMDanceToolkit/resources/Settings/cam.moving.xml_


---


##### ramCameraSettings(ofxXmlSettings& setting)

Loads one setting from XML

---

##### static vector<ramCameraSettings> loadSettings(ofxXmlSettings& setting)

Loads all settings from XML.

---


<br>


<h1 id="wiki-ramTSVCoder">ramTSVCoder</h1>

##### bool load(const string filePath)

Returns true if loading `const string filePath` is successful.

#ramCommunicationManager
ramCommunicationManager is communication tools with other applications via OSC.

An example is available at examples/example-communicationManager

###Setup
	//communicationManager setup
	ramCommunicationManager::instance().addSender("localhost", 8000);

###Send OSC to another app
	//Send from communicationManager
	ramCommunicationManager::instance().sendCC("rightHand", handPos, 3);
	
###Receive OSC from another app and use it
	//Receive from communicationManager

	//[Send format]
	//Port    : same as the port passed to ramInitialize( ... )
	//Address : /ram/communicate/cc
	//Args    : string(Instrument name), float(cc value), float(cc value), ...

	float scale = 10 + ramCommunicationManager::instance().getCC("someInst", 0) * 50.0;

	ofEnableDepthTest();
	ramEnableShadow();
	ramBeginCamera();

	ofDrawBox(0, 100, 0, scale);

	ramEndCamera();

#ramOscReceiveTag
ramOscReceiveTag is OSC receiver class for each scenes.
###Setup
	ofxOscReceiveTag receiver;
	
	receiver.addAddress("/Signals");
	ramOscManager::instance().addReceiverTag(&receiver);
###Receive
	while (receiver.hasWaitingMessages()){
		
		ofxOscMessage m;
		receiver.getNextMessage(&m);

		if (m.getAddress() == "/Signals/bang"){
			cout << "Receive bang" << endl;
		}
		if (m.getAddress() == "/Signals/control"){
			cout << "Control :" << m.getArgAsInt32(0) << endl;
		}
		
	}
	
<hr>
<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="http://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">This Document</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://interlab.ycam.jp/projects/ram" property="cc:attributionName" rel="cc:attributionURL">YCAM InterLab, Yoshito Onishi, Satoru Higa, Motoi Shimizu, and Kyle McDonald</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
