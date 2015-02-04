As noted at the end of [Structure of RAMDanceToolkit](Structure-of-RAMDanceToolkit), you can create your own scene. The following EmptyScene sample code shows you how:

	class EmptyScene : public ramBaseScene
	{

	public:
		
		// The name of your scene. It will be displayed on the GUI.
		string getName() const { return "My scene"; }
		
		void setupControlPanel()
		{
			// GUI Initializer
			// to be called after setup()
		}
		
		void setup()
		{

		}

		void update()
		{

		}

		void draw()
		{
			
		}

		void drawActor(const ramActor& actor)
		{
		    // To be called for as many number of recieving OSC data of ramActor objects.
		    // Each of the actor is passed as the argument `const ramActor &actor`.
		}

		void drawRigid(const ramRigidBody &rigid)
		{
		    // To be called for as many number of recieving OSC data of ramRigidBod objects.  
		    // Each of the actor is passed as the argument `const ramRigidBody &rigid`.
		}
	
		void onActorSetup(const ramActor &actor)
		{
		    // To be called when ramActorManager starts to recieve the OSC data of a new ramActor.  
		    // The new actor is passed as the argument `const ramActor &actor`.
		}

		void onActorExit(const ramActor &actor)
		{
		    // To be called when `const ramActor &actor` is outdated.  
		    // 1.0 sec is set to RAM_OUTDATED_DURATION in ramConstants.h as default.
		}

		void onRigidSetup(const ramRigidBody &rigid)
		{
		    // To be called when ramActorManager starts to recieve OSC data of a new ramRigidBody.  
		    // The new rigidbody is passed as the argument `const ramRigidBody &rigid`.
		}

		void onRigidExit(const ramRigidBody &rigid)
		{
		    // To be called when `const ramRigidBody &rigid` is outdated.  
		    // 1.0 sec is set to RAM_OUTDATED_DURATION in ramConstants.h as default.
		}
	};


`{RAM_ROOT}/examples/example-emptyScene` provides a simple example of how to create own scene.

[[Images/Introduction/fig-scene-1.png]]


### Defining your scene name

getName() is used to display text and key for managing scenes.
Make sure that the scene key is not duplicated among the other scenes in your project.

	string getName() const { return "My new scene"; }


### Initializing GUI

You can add GUI parts to the panel by writing some code in setupControlPanel().
ofxUICanvas is used as scene panel.

		void setupControlPanel()
		{
			// getting scene panel 
			ofxUICanvas* panel = ramGetGUI().getCurrentUIContext();
			
			// do something with the panel...
		}


### Writing your scene code

Here is a sample code for displaying simple text on stage.

	void draw()
	{
		ofSetColor(255);
		
		ramBeginCamera();
		ofDrawBitmapString("Hello, "+getName()+ "!", ofVec3f(0,200,0) );
		ramEndCamera();
	}

You can write your openFrameworks code in setup(), update(), draw(), as well as other methods which work with ramBaseApp. These methods are explained in [RAM API Reference Core](RAM-API-Reference-Core)!


<hr>
<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="http://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">This Document</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://interlab.ycam.jp/projects/ram" property="cc:attributionName" rel="cc:attributionURL">YCAM InterLab, Yoshito Onishi, Satoru Higa, Motoi Shimizu, and Kyle McDonald</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
