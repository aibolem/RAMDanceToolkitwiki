## ramBaseApp

[[/Images/API-Structure/fig-inheritence.png]]

In a normal openFrameworks application, your `testApp` is inherited from `ofBaseApp`. However, with the RAMDanceToolkit, your `testApp` inherits from `ramBaseApp`, which itself inherits from `ofBaseApp`. The image above illustrates this relationship.

Because of this, you can still do all of your normal openFrameworks coding within your `testApp`. In addition, the `ramBaseApp` from which `testApp` inherits provides you with additional methods and events to manipulate the data sent in from [MOTIONER](https://github.com/YCAMInterlab/Motioner) or another motion capture system. 

The RAMDanceToolkit kicks off via one line of code in your testApp::setup():

	void testApp::setup()
	{
		// do something…
		
		ramInitialize(10000); // osc port
	}


<br>


## OSC data format
	
RAMDanceToolkit can receive Skeleton data as explained below.

The structure of each OSC message is:

**Key**: s: string,  i: int,  f: float

1. `s`: the actor name.
2. `i`: the number of nodes in the message.
3. Array of nodes.
4. `f`: the message timestamp. The unit is in seconds.

The arguments for each node are:

1. `s`: name of the node.
2. `fff`: (x, y, z) position of the node.
3. `ffff`: angle-axis orientation of the node, stored as (angle, x, y, z). The unit for the angle is degrees.

### Address

The data for ramActor will come into:

    /ram/skeleton  

The data for ramRigidBody will come into:

	/ram/rigid_body

### Messages

An example OSC message might look like the following:

	"Cyril" 23 "Hips" -134.158005 94.602600 -113.970001 110.832001 0.526926 -0.671370 -0.521163 "Adbomen" -134.207001 104.348999 -106.655998 91.804497 -0.056078 0.996729 -0.058192 "Chest" -134.246994 108.658997 -107.821999 92.454498 -0.010825 0.999559 -0.027652 "Neck" -133.548004 143.860992 -106.059998 90.029297 0.049690 0.997769 0.044593 "Head" -133.554993 150.345001 -105.623001 84.570602 0.121813 0.984545 0.125828 "LeftHip" -141.544006 88.343803 -107.088997 178.479996 -0.642011 0.064949 0.763939 "LeftKnee" -145.653000 48.290199 -103.302002 179.240005 0.640059 -0.081635 -0.763977 "LeftAnkle" -148.789993 15.491300 -98.873001 174.432999 0.642616 -0.109263 -0.758357 "LeftToe" -151.300003 9.696490 -108.139999 103.278999 -0.994862 0.092970 0.040074 "RightHip" -126.377998 88.619102 -107.279999 171.507996 0.740300 -0.026556 -0.671752 "RightKnee" -123.816002 45.709202 -100.458000 170.074005 0.740422 -0.040390 -0.670927 "RightAnkle" -121.940002 12.993000 -94.412003 171.091995 0.742070 -0.027796 -0.669746 "RightToe" -120.042999 7.877160 -104.221001 98.821404 -0.997675 -0.065811 -0.017722 "LeftCollar" -136.449005 136.802002 -109.265999 153.891998 -0.630623 0.734379 0.251004 "LeftShoulder" -150.138000 140.856003 -108.894997 119.434998 -0.512346 0.657398 0.552566 "LeftElbow" -154.035004 108.620003 -107.651001 163.992004 -0.792702 -0.091116 0.602761 "LeftWrist" -158.363007 87.962799 -117.723999 167.427994 -0.935610 -0.305578 -0.176792 "LeftHand" -156.645004 85.710098 -117.999001 159.007004 -0.934149 -0.321990 -0.153910 "RightCollar" -131.164001 136.707001 -109.487999 91.634697 0.229410 0.255104 -0.939305 "RightShoulder" -117.195999 139.391006 -110.776001 115.863998 0.515374 0.637759 -0.572411 "RightElbow" -113.127998 107.455002 -109.375000 170.673996 -0.539455 -0.115717 0.834025 "RightWrist" -110.157997 86.682297 -118.761002 147.880005 0.264177 -0.062961 0.962417 "RightHand" -111.675003 84.333099 -118.681000 154.839005 0.313359 0.136381 0.939790 3902.675049

<br>


## Scene
 
 
[[/Images/API-Structure/fig-structure.png]]

The above image shows the general flow of the RAMDanceToolkit.

1. RAMDanceToolkit receives motion data from MOTIONER or another kind of sensor
2. Update phase:
	- Converts motion data using a `Filter`
	- Analyses data using a `Recognizer`
	- Updates an `Object` interaction with the dancer
3. Draw phase
 	- Uses a `Vizualizer` with the results of the update phase
 	- Draws `Objects`
4. Outputs visuals to screen, projector, or other expressive environment (physical interface, sound etc.) This mediated expression is expected to be used by the dances as feedback, generating new ideas for movement.

We call a virtual environment made by this sequence a `Scene`.
 

### Filter example

Adding +180 degree rotation to the actor data

[[/Images/API-Structure/pic-filter.png]]


### Recognizer example

Circle tracking

[[/Images/API-Structure/pic-recognizer.png]]


### Events

Triggering when actor touches some objects

[[/Images/API-Structure/pic-event.png]]


### Visualizer

Visualizing the relation between nodes as a line. 

[[/Images/API-Structure/pic-visualizer.png]]


### Object

Putting a visual "chain" on a joint.

[[/Images/API-Structure/pic-object.png]]


The easiest way to implement a `scene` is by creating your own! Using the `ramBaseScene` and `ramSceneManager` is the recommended way to manage many scenes in one project.

`ramBaseFilter`, `ramBaseRecognizer` and `ramBaseEvents` are available to create your own filters, recognizers, events etc. Please check out [How to create scene](How-to-create-Scene), and the other RAM API References, for more information.

<hr>
<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="http://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">This Document</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://interlab.ycam.jp/projects/ram" property="cc:attributionName" rel="cc:attributionURL">YCAM InterLab, Yoshito Onishi, Satoru Higa, Motoi Shimizu, and Kyle McDonald</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
