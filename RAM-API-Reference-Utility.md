# Utility

### Summary

This page shows some useful class e.g. pick node by clicking, save/load motion data programatically, and store camera settings.

### table of content
- [ramNodeFinder](#wiki-ramNodeFinder)
- [ramNodeIdentifer](#wiki-ramNodeIdentifer)
- [ramCameraSettings](#wiki-ramCameraSettings)
- [ramTSVCoder](#wiki-ramTSVCoder)



<h1 id="wiki-ramNodeFinder">ramNodeFinder</h1>

ramNodeFinder searches node(s) from nodearrays managed by ramActorManager.  
If you want to manipulate not ramNodeArray but specific nodes, it is more easier than using for-loop. Proberbly ramNodeFinder is used not in drawActor(), drawRigid() but in draw().

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

Returns true if ramActorManager has ramNodeArray whose name is same to ramNodeFinder::name, and the ramNodeArray has node which has id same to ramNodeFinder::index. 
If it's true, search result node is set to `ramNode &node`.

---

##### vector<ramNode> findAll()

Returns all nodes which matches to target name and target joint id.

---

##### vector<ramNode> findByID()

Returns all nodes which matches to target joint id.

---

<br>



<h1 id="wiki-ramNodeIdentifer">ramNodeIdentifer</h1>

A tiny class to identify node.  
Generally it's used for ramNodeFinder.

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

Checks target name and target id are set.

---

##### friend ostream& operator<<(ostream &os, const ramNodeIdentifer& o)

Puts name and id to stream.

---


<br>


<h1 id="wiki-ramCameraSettings">ramCameraSettings</h1>

ramCameraSettings stores some settings used for control ofCamera.  

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

Sample XML format is in _RAMDanceToolkit/resources/Settings/cam.moving.xml_


---


##### ramCameraSettings(ofxXmlSettings& setting)

Loads one setting from XML

---

##### static vector<ramCameraSettings> loadSettings(ofxXmlSettings& setting)

Loads settings from XML.

---


<br>


<h1 id="wiki-ramTSVCoder">ramTSVCoder</h1>

##### bool load(const string filePath)

Returns true if load `const string filePath` succeeded.

---

##### bool save(const ramSession &src)

Returns true if save `const ramSession &src` as tsv file.

