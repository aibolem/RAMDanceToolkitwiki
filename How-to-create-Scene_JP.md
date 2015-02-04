[Structure of RAMDanceToolkit](Structure-of-RAMDanceToolkit_JP)にも書かれていますが、自分でシーンを作成する事が出来ます。下記のEmptySceneのコードに書かれているものが基本的なシーンの骨組みになります。

	class EmptyScene : public ramBaseScene
	{

	public:
		
		// GUIに表示されるシーン名をここで指定します。
		string getName() const { return "My scene"; }
		
		void setupControlPanel()
		{
			// GUIの設定をここで行います。
			// setup()の後で実行されます。
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
		    // OSCで受信しているramActorの人数の分だけ呼ばれます。
		    // それぞれのアクターが、`const ramActor &actor`の形で引数として渡されます。
		}

		void drawRigid(const ramRigidBody &rigid)
		{
		    // OSCで受信しているramRigidBodyの個数の分だけ呼ばれます。
		    // それぞれのアクターが、`const ramRigidBody &rigid`の形で引数として渡されます。
		}
	
		void onActorSetup(const ramActor &actor)
		{
		    // 新しいramActorが入ってきた時に呼ばれます。  
		    // 新しく入ってきたアクターは、`const ramActor &actor`の形で引数として渡されます。
		}

		void onActorExit(const ramActor &actor)
		{
		    // `const ramActor &actor`のデータが更新されなくなった時に呼ばれます。
		    // ramConstants.hのRAM_OUTDATED_DURATION定数に、デフォルトで1秒が設定されています。
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


また、`{RAM_ROOT}/examples/example-emptyScene`がシンプルなシーン実装のサンプルプロジェクトになっています。

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
