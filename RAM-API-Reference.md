
# classes
- Core
	- ramBaseApp
	- ramActorManager
	- ramActor
	- ramRigidBody
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





## Core


---

### ramBaseApp

ramBaseApp provide several functions that can be used on testApp, and pass recieved OSC message automatically (generally listening on port 10000) to ramActorManager for managing data from MOTIONER or other sensors as ramActor and ramRigidBody.



#### void ramBaseApp::drawActor(const ramActor &actor)

To be called as many as number of recieving OSC data of ramActor.  
Each of the actor is passed as the argument `const ramActor &actor`.



#### void ramBaseApp::drawRigid(const ramRigidBody &rigid)

To be called as many as number of recieving OSC data of ramRigidBody.  
Each of the actor is passed as the argument `const ramRigidBody &rigid`.



#### void ramBaseApp::onActorSetup(const ramActor &actor)

To be called when ramActorManager start to recieve OSC data of new ramActor.  
The new actor is passed as the argument `const ramActor &actor`.



#### void ramBaseApp::onActorExit(const ramActor &actor)

To be called when `const ramActor &actor` is outdated.  
1.0 sec is set to RAM_OUTDATED_DURATION in ramConstants.h as default.



#### void ramBaseApp::onRigidSetup(const ramRigidBody &rigid)

To be called when ramActorManager start to recieve OSC data of new ramRigidBody.  
The new rigidbody is passed as the argument `const ramRigidBody &rigid`.



#### void ramBaseApp::onRigidExit(const ramRigidBody &rigid)

To be called when `const ramRigidBody &rigid` is outdated.  
1.0 sec is set to RAM_OUTDATED_DURATION in ramConstants.h as default.



<!--
#### void ramBaseApp::collision(const ramNode& jointA, const ramNode& jointB)

text here

---
-->

#### void ramBaseApp::setDrawFloorAuto(bool v = true)

Floor is not drawn if `bool v` is false.


---


### global shortcut

ramBaseApp provide several functions that can be used on testApp, and pass recieved OSC message automatically (generally listening on port 10000) to ramActorManager for managing data from MOTIONER or other sensors as ramActor and ramRigidBody.

---

#### void ramBaseApp::drawActor(const ramActor &actor)

text here

---