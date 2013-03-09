
# classes
- Core
	- ramBaseApp
	- ramActor, ramRigidBody, ramNodeArray
	- ramNode
	- ramActorManager

- Global shortcut
- Events
	- ramBaseEvent
- Filter
	- ramBaseFilter
- Graphics
- Recognizer
	- ramBaseRecognizer
- Scenes
	- ramSceneManager
- UI
	- ramControlPanel
- Utility
	- ramNodeSelector








# Core

## ramBaseApp

ramBaseApp pass recieved OSC message (generally listening on port 10000) to ramActorManager automatically for managing data from MOTIONER or other sensors as ramActor and ramRigidBody.

testApp is inherited several functions and events from ramBaseApp to manipulate actors and rigidbodies.  

	//--------------------------------------------------------------
	void testApp::setup()
	{
	
	}
	
	//--------------------------------------------------------------
	void testApp::update()
	{
	
	}
	
	//--------------------------------------------------------------
	void testApp::draw()
	{
		
	}
	
	
	
	#pragma mark - ram methods
	//--------------------------------------------------------------
	void testApp::drawActor(const ramActor &actor)
	{
		// To be called as many as number of recieving OSC data of ramActor.  
		// Each of the actor is passed as the argument `const ramActor &actor`.
	}
	
	//--------------------------------------------------------------
	void testApp::drawRigid(const ramRigidBody &rigid)
	{
		// To be called as many as number of recieving OSC data of ramRigidBody.  
		// Each of the actor is passed as the argument `const ramRigidBody &rigid`.
	}
	
	
	#pragma mark - ram Events
	
	//--------------------------------------------------------------
	void testApp::onActorSetup(const ramActor &actor)
	{
		// To be called when ramActorManager start to recieve OSC data of new ramActor.  
		// The new actor is passed as the argument `const ramActor &actor`.
	}
	
	//--------------------------------------------------------------
	void testApp::onActorExit(const ramActor &actor)
	{
		// To be called when `const ramActor &actor` is outdated.  
		// 1.0 sec is set to RAM_OUTDATED_DURATION in ramConstants.h as default.
	}
	
	//--------------------------------------------------------------
	void testApp::onRigidSetup(const ramRigidBody &rigid)
	{
		// To be called when ramActorManager start to recieve OSC data of new ramRigidBody.  
		// The new rigidbody is passed as the argument `const ramRigidBody &rigid`.
	}
	
	//--------------------------------------------------------------
	void testApp::onRigidExit(const ramRigidBody &rigid)
	{
		// To be called when `const ramRigidBody &rigid` is outdated.  
		// 1.0 sec is set to RAM_OUTDATED_DURATION in ramConstants.h as default.
	}
<!--
---

#### void ramBaseApp::drawActor(const ramActor &actor)

To be called as many as number of recieving OSC data of ramActor.  
Each of the actor is passed as the argument `const ramActor &actor`.

---

#### void ramBaseApp::drawRigid(const ramRigidBody &rigid)

To be called as many as number of recieving OSC data of ramRigidBody.  
Each of the actor is passed as the argument `const ramRigidBody &rigid`.

---

#### void ramBaseApp::onActorSetup(const ramActor &actor)

To be called when ramActorManager start to recieve OSC data of new ramActor.  
The new actor is passed as the argument `const ramActor &actor`.

---

#### void ramBaseApp::onActorExit(const ramActor &actor)

To be called when `const ramActor &actor` is outdated.  
1.0 sec is set to RAM_OUTDATED_DURATION in ramConstants.h as default.

---

#### void ramBaseApp::onRigidSetup(const ramRigidBody &rigid)

To be called when ramActorManager start to recieve OSC data of new ramRigidBody.  
The new rigidbody is passed as the argument `const ramRigidBody &rigid`.

---

#### void ramBaseApp::onRigidExit(const ramRigidBody &rigid)

To be called when `const ramRigidBody &rigid` is outdated.  
1.0 sec is set to RAM_OUTDATED_DURATION in ramConstants.h as default.

---

#### void ramBaseApp::collision(const ramNode& jointA, const ramNode& jointB)

text here

---
-->


And ramBaseApp provides some more functions.


#### void ramBaseApp::setDrawFloorAuto(bool v = true)

Floor is not drawn if `bool v` is false.









## ramActor, ramRigidBody, ramNodeArray

RAMDanceToolkit manages OSC data sent from MOTIONER or other sensor as ramActor or ramRigidBody.   
ramActor always has 23 nodes these has a parent‐child relationship. 
ramRigidBody is a simple nodes cluster which doesn't have a parent‐child relationship and fixed number of nodes.

### Joints of ramActor

[[/Images/JointNames_osc.png]]

Both of these classes are inherited from ramNodeArray which provides some calculation methods to control positions. See also [ofxNodeArary](https://github.com/YCAMInterlab/ofxNodeArray) inherited by ramNodeArray.


---

#### int ramNodeArray::getNumNode()

Returns size of the nodes in ramNodeArray.

---

#### ramNode& ramNodeArray::getNode(int node_id)

Returns reference to ramNode which corresponds to `node_id`.
In case of ramActor, using enum Joint defined in _ramActor.h_ is useful to find ramNode what you want to access.

	enum Joint
	{
		JOINT_HIPS              = 0,
		JOINT_ABDOMEN           = 1,
		JOINT_CHEST             = 2,
		JOINT_NECK              = 3,
		JOINT_HEAD              = 4,

		JOINT_LEFT_HIP          = 5,
		JOINT_LEFT_KNEE         = 6,
		JOINT_LEFT_ANKLE        = 7,
		JOINT_LEFT_TOE          = 8,

		JOINT_RIGHT_HIP         = 9,
		JOINT_RIGHT_KNEE        = 10,
		JOINT_RIGHT_ANKLE       = 11,
		JOINT_RIGHT_TOE         = 12,

		JOINT_LEFT_COLLAR       = 13,
		JOINT_LEFT_SHOULDER     = 14,
		JOINT_LEFT_ELBOW        = 15,
		JOINT_LEFT_WRIST        = 16,
		JOINT_LEFT_HAND         = 17,

		JOINT_RIGHT_COLLAR      = 18,
		JOINT_RIGHT_SHOULDER    = 19,
		JOINT_RIGHT_ELBOW       = 20,
		JOINT_RIGHT_WRIST       = 21,
		JOINT_RIGHT_HAND        = 22,

		NUM_JOINTS              = 23,
	};


Therefore the code to access nodes in your testApp.cpp will be like this:
	
	void testApp::drawActor(const ramActor &actor)
	{
		// access to right hand
		ramNode& rightHand = actor.getNode(ramActor::JOINT_RIGHT_HAND);
		
		// do something with rightHand...
	}
	
	void testApp::drawRigid(const ramRigidBody &rigid)
	{
		// access to all nodes
		for(int i=0; i<rigid.getNumNode(); i++)
		{
			ramNode& node = rigid.getNode(i);
			
			// do something with node...
		}
	}


---

#### bool ramNodeArray::isActor()

Returns true if the ramNodeArray is ramActor.

---

#### bool ramNodeArray::isRigid()

Returns true if the ramNodeArray is ramRigidBody.

---

#### bool ramNodeArray::isTypeOf(ramNodeArrayType t)

Returns true if the ramNodeArray is same type to `ramNodeArrayType t` which is defined in _ramActor.h_.

	enum ramNodeArrayType
	{
		RAM_NODEARRAY_TYPE_ACTOR     = 0,
		RAM_NODEARRAY_TYPE_RIGIDBODY = 1
	};

---

#### string& ramNodeArray::getName()

Return the name of node array e.g. _Yoko_, _Cyril_, _Yasu_ …

---

#### bool ramNodeArray::operator==(const ramNodeArray &arr)

Return true if the right hand side ramNodeArray is same to left hand side.

---

#### bool ramNodeArray::operator!=(const ramNodeArray &arr)

Return true if the right hand side ramNodeArray is not same to left hand side.

---

#### ramNodeArray& ramNodeArray::operator+(const ramNodeArray &arr)

Returns ramNodeArray which has synthesized global position.

---

#### ramNodeArray& ramNodeArray::operator+=(const ramNodeArray &arr)

Returns ramNodeArray which has synthesized global position.

---

#### ramNodeArray& ramNodeArray::operator-(const ramNodeArray &arr)

Returns ramNodeArray which has synthesized global position.

---

#### ramNodeArray& ramNodeArray::operator-=(const ramNodeArray &arr)

Returns ramNodeArray which has synthesized global position.

---

#### bool ramNodeArray::xxxxxxxxxxxxxxxxx



---

#### bool ramNodeArray::xxxxxxxxxxxxxxxxx



---

#### bool ramNodeArray::xxxxxxxxxxxxxxxxx



---

#### bool ramNodeArray::xxxxxxxxxxxxxxxxx


---

#### float ramNodeArray::getTimestamp()

Returns the last update client time of the ramNodeArray.
The last update client time is updated when RAMDanceToolkit recieved new OSC data of the node array.

---



## ramActorManager
