# Core

### Summary

This page shows the basic structure of RAMDanceToolkit. After reading this page, you will have a firm understanding of how RAMDanceToolkit works, including how to use the data sent from external sensors to create, use, and visualize ramActor, ramRigidBody and ramNode objects.

### Table of Contents

- [ramBaseApp](#wiki-ramBaseApp)
- [ramActor, ramRigidBody, ramNodeArray](#wiki-ramNodeArray)
- [ramNode](#wiki-ramNode)
- [ramActorManager](#wiki-ramActorManager)


<h1 id="wiki-ramBaseApp">ramBaseApp</h1>

The ramBaseApp passes OSC messages (received on port 10000 by default) to the ramActorManager. The ramActorManager, described in more detail below, manages data from MOTIONER or another motion sensor, and uses it for ramActor and/or ramRigidBody objects.

Our normal testApp inherits several functions and events from ramBaseApp for manipulating ramActor and ramRigidBody objects.

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
		// To be called for as many number of ramActor objects received as OSC data.  
		// Each ramActor is passed as the argument `const ramActor &actor`.
	}
	
	//--------------------------------------------------------------
	void testApp::drawRigid(const ramRigidBody &rigid)
	{
		// To be called for as many number of ramRigidBody objects received as OSC data..  
		// Each ramRigidBody is passed as the argument `const ramRigidBody &rigid`.
	}
	
	
	#pragma mark - ram Events
	
	//--------------------------------------------------------------
	void testApp::onActorSetup(const ramActor &actor)
	{
		// To be called when a ramActorManager starts to recieve OSC data from a new ramActor.  
		// The new ramActor is passed as the argument `const ramActor &actor`.
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
		// To be called when a ramActorManager starts to recieve OSC data of a new ramRigidBody.  
		// The new ramRigidBody is passed as the argument `const ramRigidBody &rigid`.
	}
	
	//--------------------------------------------------------------
	void testApp::onRigidExit(const ramRigidBody &rigid)
	{
		// To be called when `const ramRigidBody &rigid` is outdated.  
		// 1.0 sec is set to RAM_OUTDATED_DURATION in ramConstants.h as default.
	}
<!--
---

##### void ramBaseApp::drawActor(const ramActor &actor)

To be called as many as number of recieving OSC data of ramActor.  
Each of the actor is passed as the argument `const ramActor &actor`.

---

##### void ramBaseApp::drawRigid(const ramRigidBody &rigid)

To be called as many as number of recieving OSC data of ramRigidBody.  
Each of the actor is passed as the argument `const ramRigidBody &rigid`.

---

##### void ramBaseApp::onActorSetup(const ramActor &actor)

To be called when ramActorManager start to recieve OSC data of new ramActor.  
The new actor is passed as the argument `const ramActor &actor`.

---

##### void ramBaseApp::onActorExit(const ramActor &actor)

To be called when `const ramActor &actor` is outdated.  
1.0 sec is set to RAM_OUTDATED_DURATION in ramConstants.h as default.

---

##### void ramBaseApp::onRigidSetup(const ramRigidBody &rigid)

To be called when ramActorManager start to recieve OSC data of new ramRigidBody.  
The new rigidbody is passed as the argument `const ramRigidBody &rigid`.

---

##### void ramBaseApp::onRigidExit(const ramRigidBody &rigid)

To be called when `const ramRigidBody &rigid` is outdated.  
1.0 sec is set to RAM_OUTDATED_DURATION in ramConstants.h as default.

---

##### void ramBaseApp::collision(const ramNode& jointA, const ramNode& jointB)

text here

---
-->


ramBaseApp provides another function for drawing a base floor for the actors to "dance" on.

---

##### void ramBaseApp::setDrawFloorAuto(bool v = true)

Floor is not drawn if `bool v` is false.


---

<br>

<h1 id="wiki-ramNodeArray">ramActor, ramRigidBody, ramNodeArray</h1>

A ramActor object always has 23 nodes. These nodes have a parent‐child relationship, as described in the image below. For example, the hand is a child of the wrist, and the wrist is a child of the elbow. Conversely, the knee is the parent of the ankle, and the ankle is parent of the toe.
 
A ramRigidBody object is a simple node cluster which doesn't have a parent‐child relationship or a fixed number of nodes.

### Joints of ramActor

[[/Images/API-Structure/fig-Joint_names_osc.png]]

Both of these classes inherit from ramNodeArray, which provides some methods for calculating control positions. Please refer to [ofxNodeArray](https://github.com/YCAMInterlab/ofxNodeArray), which ramNodeArray inherits from.

---

##### int ramNodeArray::getNumNode()

Returns number of the nodes in ramNodeArray.

---

##### ramNode& ramNodeArray::getNode(int node_id)

Returns reference to ramNode which corresponds to `node_id`.
In the case of ramActor, using enum Joint defined in _ramActor.h_ is useful for finding the ramNode what you want to access.

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


Therefore the code for accessing nodes in your testApp.cpp might look like this:
	
	void testApp::drawActor(const ramActor &actor)
	{
		// accessing the right hand
		ramNode rightHand = actor.getNode(ramActor::JOINT_RIGHT_HAND);
		
		// do something with rightHand...
	}
	
	void testApp::drawRigid(const ramRigidBody &rigid)
	{
		// accessing all nodes
		for(int i=0; i<rigid.getNumNode(); i++)
		{
			ramNode node = rigid.getNode(i);
			
			// do something with node...
		}
	}


---

##### bool ramNodeArray::isActor()

Returns true if the ramNodeArray is a ramActor.

---

##### bool ramNodeArray::isRigid()

Returns true if the ramNodeArray is a ramRigidBody.

---

##### bool ramNodeArray::isTypeOf(ramNodeArrayType t)

Returns true if the ramNodeArray is the same type as `ramNodeArrayType t` which is defined in _ramActor.h_.

	enum ramNodeArrayType
	{
		RAM_NODEARRAY_TYPE_ACTOR     = 0,
		RAM_NODEARRAY_TYPE_RIGIDBODY = 1
	};

---

##### string& ramNodeArray::getName()

Return the name of the ramNodeArray e.g. _Yoko_, _Cyril_, _Yasu_ …

---

##### bool ramNodeArray::operator==(const ramNodeArray &arr)

Return true if the right-hand side ramNodeArray is same as the left-hand side ramNodeArray.

---

##### bool ramNodeArray::operator!=(const ramNodeArray &arr)

Return true if the right-hand side ramNodeArray is not the same as left-hand side ramNodeArray.

---

##### ramNodeArray ramNodeArray::operator+(const ramNodeArray &arr)

Returns a ramNodeArray which has a synthesized global position.

---

##### ramNodeArray& ramNodeArray::operator+=(const ramNodeArray &arr)

Returns self which has a synthesized global position.

---

##### ramNodeArray ramNodeArray::operator-(const ramNodeArray &arr)

Returns ramNodeArray which has a synthesized global position.

---

##### ramNodeArray& ramNodeArray::operator-=(const ramNodeArray &arr)

Returns self which has a synthesized global position.

---

##### ramNodeArray& ramNodeArray::lerp(const ramNodeArray &base, float t)

Returns the reference to self which is lerped using `float t`.

---

##### ramNodeArray ramNodeArray::getLerpd(const SuperClass &base, float t)

Returns the copy of self which is lerped using `float t`.

---

##### ramNodeArray& ramNodeArray::normalize(const ramNodeArray &base, float length)

Returns the reference to self which is normalized using `float length`.

---

##### ramNodeArray ramNodeArray::getNormalized(const SuperClass &base, float length)

Returns the copy of self which is normalized using `float length`.

---

##### ramNodeArray& ramNodeArray::limited(const ramNodeArray &base, float length)

Returns the reference to self which is limited using `float length`.

---

##### ramNodeArray ramNodeArray::getLimited(const SuperClass &base, float length)

Returns the copy of self which is limited using `float length`.

---

##### float ramNodeArray::getTimestamp()

Returns the last updated client time of the ramNodeArray.
The last updated client time is updated when RAMDanceToolkit received new OSC data for the node array.

---


<br>


<h1 id="wiki-ramNode">ramNode</h1>

A ramNode is used as a joint for a ramActor and ramRigidBody object. A ramNode inherits from [ofNode](http://www.openframeworks.cc/documentation/3d/ofNode.html). See also [ofxNodeArray::Node](https://github.com/YCAMInterlab/ofxNodeArray) .

---

##### ramNode* ramNode::getParent()

Returns its parent node.

---

##### bool ramNode::hasParent()

Returns true if ramNode has a parent node.

---

##### ofVec3 ramNode::operator ofVec3f()

Returns its global position. This can be used as a shortcut for ofNode::getGlobalPosition(). The following sample code shows how to draw shapes using oF methods.

	void testApp::drawActor(const ramActor &actor)
	{
		ramNode rightHand = actor.getNode(ramActor::JOINT_RIGHT_HAND);
		ramNode leftHand = actor.getNode(ramActor::JOINT_LEFT_HAND);
		
		// line between two node
		ofLine(rightHand, leftHand);
		
		// a box on right hand
		ofBox(rightHand, 100);
		
		// a sphere on left hand
		ofSphere(leftHand, 100);
	}

In the following example, we can draw a ramActor by using ofBox and ofLine:

	void testApp::drawActor(const ramActor &actor)
	{
		for(int i=0; i<actor.getNumNode(); i++)
		{
			ramNode node = actor.getNode(i);
			
			// draw box as joint
			ofBox(node, 10);
			
			
			// draw line if it has parent node
			if(node.hasParent())
			{
				ofLine(node, *node.getParent());
			}
		}
	}

---

##### ofVec3f ramNode::getVelocity()

Returns the velocity between the previous frame and the current frame.

---

##### ofVec3f ramNode::getAcceleration()

Returns the acceleration calculated from the previous frame and the current frame.

---

##### ofQuaternion ramNode::getAngularVelocity()

Returns the angular velocity calculated from the previous frame and the current frame.

---

##### ofQuaternion ramNode::getAngularVelocity()

Returns the anguler velocity calculated from the previous frame and the current frame.

---

##### ofQuaternion ramNode::getAngularAcceleration()

Returns the anguler acceleration calculated from the previous frame and the current frame.

---

##### string& ramNode::getName()

Returns the node name e.g. _JOINT_HEAD_, _JOIND_RIGHT_TOE_ ...

---

##### void ramNode::drawNodeName(int floatPos = 20);

Draws the node name `int floatPos = 20` cm above the node. 

---

##### void ramNode::beginTransform()

Alias to _transformGL()_ .

---

##### void ramNode::endTransform()

Alias to _restoreTransformGL()_ .  

The following sample code works like the previous sample, but now it uses the orientation of the ramNode via beginTransform() and endTransform().

	void testApp::drawActor(const ramActor &actor)
	{
	    for(int i=0; i<actor.getNumNode(); i++)
	    {
	        ramNode node = actor.getNode(i);
	
	        // draw box as joint
	        node.beginTransform();
	        ofBox(10);
	        node.endTransform();
	    }
	}

---

##### bool ramNode::operator==(const ramNode &arr)

Return true if the right-hand side ramNode is the same as the left-hand side ramNode.

---
	
##### bool ramNode::operator!=(const ramNode &arr)

Return true if the right-hand side ramNode is not the same as the left-hand side ramNode.

---

##### ramNode ramNode::operator+(const ramNode &arr)

Returns a ramNode with synthesized global position.

---

##### ramNode& ramNode::operator+=(const ramNode &arr)

Returns self with synthesized global position.

---

##### ramNode ramNode::operator-(const ramNode &arr)

Returns a ramNode with synthesized global position.

---

##### ramNode& ramNode::operator-=(const ramNode &arr)

Returns self with synthesized global position.

---

##### ramNode& ramNode::lerp(const ramNode &base, float t)

Returns the reference to self which is lerped using `float t`.

---

##### ramNode ramNode::getLerpd(const SuperClass &base, float t)

Returns the copy of self which is lerped using `float t`.

---

##### ramNode& ramNode::normalize(const ramNode &base, float length)

Returns the reference to self which is normalized using `float length`.

---

##### ramNode ramNode::getNormalized(const SuperClass &base, float length)

Returns the copy of self which is normalized using `float length`.

---

##### ramNode& ramNode::limited(const ramNode &base, float length)

Returns the reference to self which is limited using `float length`.

---

##### ramNode ramNode::getLimited(const SuperClass &base, float length)

Returns the copy of self which is limited using `float length`.



<br>


<h1 id="wiki-ramActorManager">ramActorManager</h1>

As noted in the introduction, the RAMDanceToolkit manages OSC data sent from MOTIONER or other sensor as ramActor or ramRigidBody objects. The ramActorManager stores these objects and updates their states.

The following functions can be used in your testApp, as well as scenes that inherit from ramBaseScene, to access these actors.


---

##### ramActorManager& getActorManager()

Returns a reference to ramActorManager.

---

##### ramNodeArray& getNodeArray(string name)

Returns a reference to ramNodeArray whose name is the same as `string name`.

---

##### ramNodeArray& getNodeArray(int index)

Returns reference to ramNodeArray whose index is the same as `int index`.  
For example, the index of first actor RAMDanceToolkit recieves is `0`.

---

##### ramNodeArray& hasNodeArray(string name)

Returns true if ramActorManager has a ramNodeArray whose name is the same as `string name`.

---

##### size_t getNumNodeArray()

Returns the number of ramNodeArray objects that the RAMDanceToolkit is recieving at the time.

---

##### vector<string>& getNodeArrayNames()

Returns the names of all the ramNodeArray objects that the RAMDanceToolkit is receving at this time.

---

##### vector<ramNodeArray> getAllNodeArrays()

Returns all ramNodeArray objects that the RAMDanceToolkit is recieving at the time.


---

##### ramNodeIdentifer& ramActorManager::getLastSelectedNodeIdentifer()


---

##### ramNode* ramActorManager::getLastSelectedNode();


---

##### ramActorManager::getLastSelectedNodeArray();


---

##### ramActorManager::clearSelected();


---

##### ramActorManager::bool hasBus(const string& bus_name)


---

##### void ramActorManager::setBus(const string& bus_name, const ramNodeArray &arr) 


---

##### const ramNodeArray& ramActorManager::getBus(const string& bus_name)


---

##### map<string, ramNodeArray>& ramActorManager::getAllBus()


---

##### inline size_t ramActorManager::getNumBus()


---

##### inline size_t ramActorManager::eraseFromBus(const string& bus_name)





<hr>
<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="http://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">This Document</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://interlab.ycam.jp/projects/ram" property="cc:attributionName" rel="cc:attributionURL">YCAM InterLab, Yoshito Onishi, Satoru Higa, Motoi Shimizu, and Kyle McDonald</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.


