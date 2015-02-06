[Structure of RAMDanceToolkit](Structure-of-RAMDanceToolkit_JP)にも書かれていますが、自分でシーンを作成する事が出来ます。下記のEmptySceneのコードに書かれているものが基本的なシーンの骨組みになります。

ヘッダファイル

	#pragma once

	#include "ramMain.h"
	
	class EmptyScene : public ramBaseScene
	{
	
	public:
		// GUIに表示されるシーン名をここで指定します。
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
		
	    void onPanelChanged(ofxUIEventArgs &e);
	    
		float mySlider;
		bool myToggle;
	};

cppファイル

	void EmptyScene::setupControlPanel()
	{
		// GUIの設定をここで行います。
		// setup()の後で実行されます。
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
	    
	    //RAMDanceToolkitの座標にあわせるにはramBeginCamera()と
	    //ramEndCamera()の間で描画をする必要があります。

	    ramBeginCamera();
	    ofDrawBitmapString("Slider value: " + ofToString(mySlider), ofVec3f(0,200,0));
	    ramEndCamera();
	}
	
	void EmptyScene::drawActor(const ramActor& actor)
	{
	    
	}
	
	void EmptyScene::drawRigid(const ramRigidBody &rigid)
	{
	    
	}
	
	void EmptyScene::onActorSetup(const ramActor &actor)
	{
	    
	}
	
	void EmptyScene::onActorExit(const ramActor &actor)
	{
	    
	}
	
	void EmptyScene::onRigidSetup(const ramRigidBody &rigid)
	{
	    
	}
	
	void EmptyScene::onRigidExit(const ramRigidBody &rigid)
	{
	    
	}
	

`{RAM_ROOT}/examples/example-emptyScene`がシンプルなシーン実装のサンプルプロジェクトになっているので、参考にしてみてください。

[[Images/Introduction/fig-scene-1.png]]


### シーンの名前を決める

getName()はシーン管理用に、シーン名を登録するためのメソッドです。
シーン名は同じプロジェクト内の他のシーンと重複しないようにしてください。

	string getName() const { return "My new scene"; }


### GUIの初期化

setupControlPanel()でGUIのパーツを加える事ができます。
シーンごとのGUIパネルとしてofxUICanvasを使う事が出来ます。詳細は[ofxUIのサイト](https://github.com/rezaali/ofxUI)か、RAMDanceToolkit内の`{RAM_ROOT}/apps/RAMDanceToolkit`プロジェクト等を参照してください。

		void setupControlPanel()
		{
			// シーンごとのパネルを取得します。 
			ofxUICanvas* panel = ramGetGUI().getCurrentUIContext();
			
			// パネルの設定をします...
		}


### シーンの登録
シーンをramSceneManagerに登録する事で、GUIへの登録とGUI上でのシーンの操作が出来るようになります。
`{RAM_ROOT}/examples/example-emptyScene`に具体的な方法が実装されています。ここでの実装方法を説明します。
まずtestApp.hファイルで作成したシーンのヘッダファイルをincludeします。

		#include "EmptyScene.h"

またtestAppのメンバオブジェクトとしてシーンを宣言します。

		class testApp : public ramBaseApp
		{
		    public:
		      //省略
		    EmptyScene myScene;
		}

testApp.cppでramInitialize(int port)のあとにramSceneManagerへのシーンの登録を行います。これで、GUIへの登録が完了します。

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




シーンを書くコードには、ramBaseAppでサポートされているRAMDanceToolkitの機能のほかに、openFrameworksの機能もすべて使用する事が出来ます。RAMDanceToolkitでサポートされている機能に関しては[RAM API Reference Core](RAM-API-Reference-Core)を参照してください。

<hr>
<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="http://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">This Document</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://interlab.ycam.jp/projects/ram" property="cc:attributionName" rel="cc:attributionURL">YCAM InterLab, Yoshito Onishi, Satoru Higa, Motoi Shimizu, and Kyle McDonald</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
