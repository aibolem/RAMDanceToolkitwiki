As noted at the end of [Structure of RAMDanceToolkit](Structure-of-RAMDanceToolkit), you can create your own scene. The following EmptyScene sample code shows you how:

.h file

	#pragma once

	#include "ramMain.h"
	
	class EmptyScene : public ramBaseScene
	{
	
	public:
		// The name of your scene. It will be displayed on the GUI.
		string getName() const { return "My scene"; }
	
	    void setupControlPanel();
	    void setup();
	    void update();
	    void draw();
	
	    void drawActor(const ramActor& actor);
	    void drawRigid(const ramRigidBody &rigid);
	    void onActorSetup(const ramActor &actor);
	    void onActorExit(const ramActor &actor);
	    void onRigidSetup(const ramRigidBody &rigid);
	    void onRigidExit(const ramRigidBody &rigid);
		
	private:
	    
		// to be registered in GUI 
		float mySlider;

	};

.cpp file

	#include "EmptyScene.h"

	void EmptyScene::setupControlPanel()
	{
			// Setup GUI
			// to be called after setup()

		// register a slider for this scene
	    ramGetGUI().addSlider("Slider", 0.0, 10.0, &mySlider);
	}
	
	void EmptyScene::setup()
	{
	    
	}
	
	void EmptyScene::update()
	{
	    
	}
	
	void EmptyScene::draw()
	{
	    ofSetColor(255,255,255);
	    
	    // to use RAMDanceToolkit coordination system
	    // use ramBeginCamera() & ramEndCamera() and write codes between them

	    ramBeginCamera();
		// you can get slider value using variable 
		// which you registered in setupControlPanel().
	    ofDrawBitmapString("Slider value: " + ofToString(mySlider), ofVec3f(0,200,0));
	    ramEndCamera();
	}
	
	void drawActor(const ramActor& actor)
	{
	    // To be called for as many number of recieving OSC data
	    // of ramActor objects.
	    // Each actor is passed as the argument `const ramActor &actor`.
	}

	void drawRigid(const ramRigidBody &rigid)
	{
	    // To be called for as many number of recieving OSC data  
	    // of ramRigidBod objects.
	    // Each actor is passed as the argument `const ramRigidBody &rigid`.
	}

	void onActorSetup(const ramActor &actor)
	{
	    // To be called when ramActorManager starts to recieve
	    // the OSC data of a new ramActor.  
	    // The new actor is passed as the argument `const ramActor &actor`.
	}

	void onActorExit(const ramActor &actor)
	{
	    // To be called when `const ramActor &actor` is outdated.  
	    // 1.0 sec is set to RAM_OUTDATED_DURATION in ramConstants.h as default.
	}

	void onRigidSetup(const ramRigidBody &rigid)
	{
	    // To be called when ramActorManager starts to recieve  
	    // OSC data of a new ramRigidBody.
	    // The new rigidBody is passed as the argument `const ramRigidBody &rigid`.
	}

	void onRigidExit(const ramRigidBody &rigid)
	{
	    // To be called when `const ramRigidBody &rigid` is outdated.  
	    // 1.0 sec is set to RAM_OUTDATED_DURATION in ramConstants.h as default.
	}
	
`{RAM_ROOT}/examples/example-emptyScene` provides a simple example of how to create own scene.

[[Images/Introduction/fig-scene-1.png]]


### Defining your scene name

getName() is used to display text and be a key for managing scenes.
Make sure that the scene name is not duplicated among the other scenes in your project.
(because it's a key as well)

	string getName() const { return "My new scene"; }


### Initializing GUI

You can add GUI parts to the panel by writing some code in setupControlPanel().
ofxUICanvas is used as scene panel.
Please check [ofxUI website](https://github.com/rezaali/ofxUI) or `{RAM_ROOT}/apps/RAMDanceToolkit` project for details.

		void setupControlPanel()
		{
			// Setup GUI

			// register a slider for this scene
		    ramGetGUI().addSlider("Slider", 0.0, 10.0, &mySlider);
			
		}

a slider value which is set up in setupControlPanel() can be used as following.

		// you can get slider value using variable 
		// which you registered in setupControlPanel().
	    ofDrawBitmapString("Slider value: " + ofToString(mySlider), ofVec3f(0,200,0));

or to use a listener method, you can do like..

in .h file, you should have this line as member method(between {} of class).

	    void onPanelChanged(ofxUIEventArgs &e);

in .cpp file, add this implementation for example.

	void EmptyScene::onPanelChanged(ofxUIEventArgs &e)
	{
	    const string name = e.widget->getName();
	    if (name == "slider") {

	    }
	    
	    // do something...
	}

and register this listener method as following in setupControlPanel(), so you can have a specific method(onPanelChanged(ofxUIEventArgs &e) here) which is called when GUI is changed.

	    ofAddListener(ramGetGUI().getCurrentUIContext()->newGUIEvent, this, &EmptyScene::onPanelChanged);


### Register your scene to SceneManager
You can register your scene to ramSceneManager, then you can operate your scene on the GUI.
Here we'll explain about how you register it.
Please check `{RAM_ROOT}/examples/example-emptyScene` for the details.

at first, include a header file of a scene in testApp.h.

		#include "EmptyScene.h"

create a scene object of your scene class.

		class testApp : public ramBaseApp
		{
		    public:
		      //omitted
		    EmptyScene myScene;
		}

in testApp, register the scene to ramSceneManager after ramInitialize(int port) in setup().

		void testApp::setup()
		{
			ofSetFrameRate(60);
			ofSetVerticalSync(true);
		
			/// ram setup
			// ------------------
			ramInitialize(10000);
		
			ramSceneManager& sceneManager = ramSceneManager::instance();
			sceneManager.addScene(&myScene);
		}

then, you can see and select your scene on the GUI when you run the app.


You can write your openFrameworks code for scenes, as well as other methods which work with ramBaseApp. These methods are explained in [RAM API Reference Core](RAM-API-Reference-Core). and also please check [openFrameworks website](http://www.openframeworks.cc/).


<hr>
<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="http://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">This Document</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://interlab.ycam.jp/projects/ram" property="cc:attributionName" rel="cc:attributionURL">YCAM InterLab, Yoshito Onishi, Satoru Higa, Motoi Shimizu, and Kyle McDonald</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
