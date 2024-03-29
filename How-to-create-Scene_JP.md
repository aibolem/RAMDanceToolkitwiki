[Structure of RAMDanceToolkit](Structure-of-RAMDanceToolkit_JP)にも書かれていますが、自分でシーンを作成する事が出来ます。下記のEmptySceneのコードに書かれているものが基本的なシーンの骨組みになります。

.hファイル

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
	    
		float mySlider;

	};

.cppファイル

	#include "EmptyScene.h"

	void EmptyScene::setupControlPanel()
	{
		// GUIの設定をここで行います。
		// setup()の後で実行されます。

		// このシーン用のGUIにスライダーを登録しています。
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
		//スライダーの値はsetupControlPanel()で指定した変数で取得できます。
	    ofDrawBitmapString("Slider value: " + ofToString(mySlider), ofVec3f(0,200,0));
	    ramEndCamera();
	}
	
	void EmptyScene::drawActor(const ramActor& actor)
	{
		// OSCで受信しているramActorの人数の分だけ呼ばれます。
		// それぞれのアクターが、`const ramActor &actor`の形で
		// 引数として渡されます。
	}
	
	void EmptyScene::drawRigid(const ramRigidBody &rigid)
	{
		// OSCで受信しているramRigidBodyの個数の分だけ呼ばれます。
		// それぞれのアクターが、`const ramRigidBody &rigid`の形で
		// 引数として渡されます。
	}
	
	void EmptyScene::onActorSetup(const ramActor &actor)
	{
		// 新しいramActorが入ってきた時に呼ばれます。  
		// 新しく入ってきたアクターは`const ramActor &actor`の形で
		// 引数として渡されます。
	}
	
	void EmptyScene::onActorExit(const ramActor &actor)
	{
		// `const ramActor &actor`のデータが更新されなくなった時に呼ばれます。
		// ramConstants.hのRAM_OUTDATED_DURATION定数に、
		// デフォルトのデータ更新のタイムリミットとして1.0秒が設定されています。
	}
	
	void EmptyScene::onRigidSetup(const ramRigidBody &rigid)
	{
		// 新しいramRigidBodyが入ってきた時に呼ばれます。  
		// 新しく入ってきたリジッドボディは、
		// `const ramRigidBody &rigid`の形で引数として渡されます。
	}
	
	void EmptyScene::onRigidExit(const ramRigidBody &rigid)
	{
		// `const ramRigidBody &rigid`のデータが更新されなくなった時に呼ばれます。
		// ramConstants.hのRAM_OUTDATED_DURATION定数に、
		// デフォルトのデータ更新のタイムリミットとして1.0秒が設定されています。
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
			// パネルの設定をします...

			// このシーン用のGUIにスライダーを登録しています。
		    ramGetGUI().addSlider("Slider", 0.0, 10.0, &mySlider);
			
		}

上のsetupControlPanel()のように登録したスライダーの情報は

		//スライダーの値はsetupControlPanel()で指定した変数で取得できます。
	    ofDrawBitmapString("Slider value: " + ofToString(mySlider), ofVec3f(0,200,0));

のように登録した変数を使う事で取得する事が出来ます。また下記のようなメンバー関数を用意し、

.hファイル

	    void onPanelChanged(ofxUIEventArgs &e);

.cppファイル

	void EmptyScene::onPanelChanged(ofxUIEventArgs &e)
	{
	    const string name = e.widget->getName();
	    if (name == "slider") {

	    }
	    
	    // do something...
	}

さらにsetupControlPanel()の中で

	    ofAddListener(ramGetGUI().getCurrentUIContext()->newGUIEvent, this, &EmptyScene::onPanelChanged);

などとすることで、GUIが変更された時にのみ実行されるイベントリスナーを登録することも可能です。


### シーンの登録
シーンをramSceneManagerに登録する事で、GUIへの登録とGUI上でのシーンの操作が出来るようになります。
ここで実装方法を説明します。

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

`{RAM_ROOT}/examples/example-emptyScene`のプロジェクトで実際に実装されているのでチェックしてみてください。


シーンを書くコードには、ramBaseAppでサポートされているRAMDanceToolkitの機能のほかに、openFrameworksの機能もすべて使用する事が出来ます。RAMDanceToolkitでサポートされている機能に関しては[RAM API Reference Core](RAM-API-Reference-Core)を参照してください。またopenFrameworksに関しては[openFrameworks.cc](http://www.openframeworks.cc/)を参照してください。

<hr>
<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="http://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">This Document</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://interlab.ycam.jp/projects/ram" property="cc:attributionName" rel="cc:attributionURL">YCAM InterLab, Yoshito Onishi, Satoru Higa, Motoi Shimizu, and Kyle McDonald</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
