## Structure

### ramBaseApp

[[/Images/Home/inheritence.png]]

Regularly testApp is inherited from ofBaseApp but all of testApp in RAMDanceToolkit projects are inherited from `ramBaseApp` which is inherited from ofBaseApp. The regular methods in testApp can be used as your usual hacking. ramBaseApp provides additional methods and events to testApp to manipulate the data sent from [MOTIONER](https://github.com/YCAMInterlab/Motioner) or other motion capture system. 

RAMDanceToolkit starts running from writing one line code in your testApp::setup() like:

	void testApp::setup()
	{
		// do something…
		
		ramInitialize(10000); // osc port
	}

---


### OSC data format
	
	- インプットのフォーマット : OSCフォーマット(ito3/8)


---

 
### Scene
 
 
[[/Images/Home/structure.png]]

We call the sequence this image shows as `Scene`.  


	- フィルタの概念:
	     - 各フィルタの説明＋スクリーンショット（3/8）
	- レコグナイザの概念: 
	     - 各レコグナイザの説明＋スクリーンショット（3/8）
	- ヴィジュアライザの概念:
	     - 各レコグナイザの説明＋スクリーンショット（3/8）
	- イベントの概念
	    - 各イベントの説明
	- 各シーンごとのスクリーンショット＋パラメータの説明：shmizu







