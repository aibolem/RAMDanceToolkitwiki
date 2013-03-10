
## ramBaseApp

[[/Images/Home/inheritence.png]]

Regularly testApp is inherited from ofBaseApp but all of testApp in RAMDanceToolkit projects are inherited from `ramBaseApp` which is inherited from ofBaseApp. The regular methods in testApp can be used as your usual hacking. ramBaseApp provides additional methods and events to testApp to manipulate the data sent from [MOTIONER](https://github.com/YCAMInterlab/Motioner) or other motion capture system. 

RAMDanceToolkit starts running from writing one line code in your testApp::setup() like:

	void testApp::setup()
	{
		// do something…
		
		ramInitialize(10000); // osc port
	}


<br>


## OSC data format
	

Skeleton data is sent as a series of nodes in a single OSC message.

The structure of each OSC message is:

1. `s`: the actor name.
2. `i`: the number of nodes in the message.
3. Array of nodes.
4. `f`: the message timestamp. The unit is seconds.

The arguments for each node are:

1. `s`: name of the node.
2. `fff`: (x, y, z) position of the node.
3. `ffff`: angle-axis orientation of the node, stored as (angle, x, y, z).

Actual OSC message is like the following.  

### Address

The data for ramActor will come into:

    /ram/skeleton  

The data for ramRigidBody will come into:

	/ram/rigid_body

### Messages

	"Cyril" 23 "Hips" -134.158005 94.602600 -113.970001 110.832001 0.526926 -0.671370 -0.521163 "Adbomen" -134.207001 104.348999 -106.655998 91.804497 -0.056078 0.996729 -0.058192 "Chest" -134.246994 108.658997 -107.821999 92.454498 -0.010825 0.999559 -0.027652 "Neck" -133.548004 143.860992 -106.059998 90.029297 0.049690 0.997769 0.044593 "Head" -133.554993 150.345001 -105.623001 84.570602 0.121813 0.984545 0.125828 "LeftHip" -141.544006 88.343803 -107.088997 178.479996 -0.642011 0.064949 0.763939 "LeftKnee" -145.653000 48.290199 -103.302002 179.240005 0.640059 -0.081635 -0.763977 "LeftAnkle" -148.789993 15.491300 -98.873001 174.432999 0.642616 -0.109263 -0.758357 "LeftToe" -151.300003 9.696490 -108.139999 103.278999 -0.994862 0.092970 0.040074 "RightHip" -126.377998 88.619102 -107.279999 171.507996 0.740300 -0.026556 -0.671752 "RightKnee" -123.816002 45.709202 -100.458000 170.074005 0.740422 -0.040390 -0.670927 "RightAnkle" -121.940002 12.993000 -94.412003 171.091995 0.742070 -0.027796 -0.669746 "RightToe" -120.042999 7.877160 -104.221001 98.821404 -0.997675 -0.065811 -0.017722 "LeftCollar" -136.449005 136.802002 -109.265999 153.891998 -0.630623 0.734379 0.251004 "LeftShoulder" -150.138000 140.856003 -108.894997 119.434998 -0.512346 0.657398 0.552566 "LeftElbow" -154.035004 108.620003 -107.651001 163.992004 -0.792702 -0.091116 0.602761 "LeftWrist" -158.363007 87.962799 -117.723999 167.427994 -0.935610 -0.305578 -0.176792 "LeftHand" -156.645004 85.710098 -117.999001 159.007004 -0.934149 -0.321990 -0.153910 "RightCollar" -131.164001 136.707001 -109.487999 91.634697 0.229410 0.255104 -0.939305 "RightShoulder" -117.195999 139.391006 -110.776001 115.863998 0.515374 0.637759 -0.572411 "RightElbow" -113.127998 107.455002 -109.375000 170.673996 -0.539455 -0.115717 0.834025 "RightWrist" -110.157997 86.682297 -118.761002 147.880005 0.264177 -0.062961 0.962417 "RightHand" -111.675003 84.333099 -118.681000 154.839005 0.313359 0.136381 0.939790 3902.675049

<br>


## Scene
 
 
[[/Images/Home/structure.png]]

This image shows an abstract sequence of signal processing flow.  

1. Recieive motion data from MOTIONER or other sencer
2. In update phase, 
3. In draw phase, 
4. Output visuals to screen, projector, or 

We call this sequence as `Scene`.  


### Filter
	- フィルタの概念:
### Recognizer
	- レコグナイザの概念: 
### Events
	- イベントの概念
### Visualizer
	- ヴィジュアライザの概念:








