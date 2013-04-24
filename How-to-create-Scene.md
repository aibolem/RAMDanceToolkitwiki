## How to create own Scene

As noted at the end of [Structure of RAMDanceToolkit](Structure-of-RAMDanceToolkit), you can create your own scene using this sample code of empty scene. 

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
		    // To be called as many as number of recieving OSC data of ramActor.  
		    // Each of the actor is passed as the argument `const ramActor &actor`.
		}

		void drawRigid(const ramRigidBody &rigid)
		{
		    // To be called as many as number of recieving OSC data of ramRigidBody.  
		    // Each of the actor is passed as the argument `const ramRigidBody &rigid`.
		}
	
		void onActorSetup(const ramActor &actor)
		{
		    // To be called when ramActorManager start to recieve OSC data of new ramActor.  
		    // The new actor is passed as the argument `const ramActor &actor`.
		}

		void onActorExit(const ramActor &actor)
		{
		    // To be called when `const ramActor &actor` is outdated.  
		    // 1.0 sec is set to RAM_OUTDATED_DURATION in ramConstants.h as default.
		}

		void onRigidSetup(const ramRigidBody &rigid)
		{
		    // To be called when ramActorManager start to recieve OSC data of new ramRigidBody.  
		    // The new rigidbody is passed as the argument `const ramRigidBody &rigid`.
		}

		void onRigidExit(const ramRigidBody &rigid)
		{
		    // To be called when `const ramRigidBody &rigid` is outdated.  
		    // 1.0 sec is set to RAM_OUTDATED_DURATION in ramConstants.h as default.
		}
	};


`{RAM_ROOT}/examples/example-emptyScene` is a simple example to understand how to create own scene.

[[Images/Introduction/fig-scene-1.png]]


### Defining your scene name

getName() is used as display text and key for managing scenes.
Make sure that the scene key is not overlapped among the other scenes in your project.

	string getName() const { return "My new scene"; }


### Initializing GUI

You can add GUI parts to the panel writing some code in setupControlPanel().
ofxUICanvas is used as scene panel.

		void setupControlPanel()
		{
			// getting scene panel 
			ofxUICanvas* panel = ramGetGUI().getCurrentUIContext();
			
			// do something with panel...
		}


### Writing your scene code

Here is a sample code of displaying simple text on stage.

	void draw()
	{
		ofSetColor(255);
		
		ramBeginCamera();
		ofDrawBitmapString("Hello, "+getName()+ "!", ofVec3f(0,200,0) );
		ramEndCamera();
	}

You can write your OF code in setup(), update(), draw(), and other methods which works same to ramBaseApp which is explained on [RAM API Reference Core](RAM-API-Reference-Core)!


