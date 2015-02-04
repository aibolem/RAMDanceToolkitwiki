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
		    // それぞれのアクターが、`const ramActor &actor`の形で
		    // 引数として渡されます。
		}

		void drawRigid(const ramRigidBody &rigid)
		{
		    // OSCで受信しているramRigidBodyの個数の分だけ呼ばれます。
		    // それぞれのアクターが、`const ramRigidBody &rigid`の形で
		    // 引数として渡されます。
		}
	
		void onActorSetup(const ramActor &actor)
		{
		    // 新しいramActorが入ってきた時に呼ばれます。  
		    // 新しく入ってきたアクターは`const ramActor &actor`の形で
		    // 引数として渡されます。
		}

		void onActorExit(const ramActor &actor)
		{
		    // `const ramActor &actor`のデータが更新されなくなった時に呼ばれます。
		    // ramConstants.hのRAM_OUTDATED_DURATION定数に、
		    // デフォルトのデータ更新のタイムリミットとして1.0秒が設定されています。
		}

		void onRigidSetup(const ramRigidBody &rigid)
		{
		    // 新しいramRigidBodyが入ってきた時に呼ばれます。  
		    // 新しく入ってきたリジッドボディは、
		    // `const ramRigidBody &rigid`の形で引数として渡されます。
		}

		void onRigidExit(const ramRigidBody &rigid)
		{
		    // `const ramRigidBody &rigid`のデータが更新されなくなった時に呼ばれます。
		    // ramConstants.hのRAM_OUTDATED_DURATION定数に、
		    // デフォルトのデータ更新のタイムリミットとして1.0秒が設定されています。
		}
	};


また、`{RAM_ROOT}/examples/example-emptyScene`がシンプルなシーン実装のサンプルプロジェクトになっているので、参考にしてください。

[[Images/Introduction/fig-scene-1.png]]


### シーンの名前を決める

getName()はシーン管理用に、シーン名を登録するためのメソッドです。
シーン名は同じプロジェクト内の他のシーンと重複しないようにしてください。

	string getName() const { return "My new scene"; }


### GUIの初期化

setupControlPanel()でGUIのパーツを加える事ができます。
シーンごとのGUIパネルとしてofxUICanvasを使う事が出来ます。詳細は[ofxUI](https://github.com/rezaali/ofxUI)か、RAMDanceToolkit内の他のExampleを参照してください。

		void setupControlPanel()
		{
			// シーンごとのパネルを取得します。 
			ofxUICanvas* panel = ramGetGUI().getCurrentUIContext();
			
			// パネルの設定をします...
		}


### シーンのコードを書く

ステージ上に簡単なテキストを書くサンプルコードは下記のようになります。

	void draw()
	{
		ofSetColor(255);
		
		ramBeginCamera();
		ofDrawBitmapString("Hello, "+getName()+ "!", ofVec3f(0,200,0) );
		ramEndCamera();
	}

シーンを書くコードには、ramBaseAppでサポートされているRAMDanceToolkitの機能のほかに、openFrameworksの機能もすべて使用する事が出来ます。RAMDanceToolkitでサポートされている機能に関しては[RAM API Reference Core](RAM-API-Reference-Core)を参照してください。

<hr>
<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="http://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">This Document</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://interlab.ycam.jp/projects/ram" property="cc:attributionName" rel="cc:attributionURL">YCAM InterLab, Yoshito Onishi, Satoru Higa, Motoi Shimizu, and Kyle McDonald</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
