# Graphics

### Summary

The RAMDanceToolkit has a number of global methods for drawing shapes, as defined in _ramGraphics.h_.

### Table of Contents

- [ramGraphics](#wiki-ramGraphics)
- [ramSimpleShadow](#wiki-ramSimpleShadow)
- [ramColor](#wiki-ramColor)
- [ramGraphView](#wiki-ramGraphView)
- [ramNodeLine](#wiki-ramNodeLine)



<h1 id="wiki-ramGraphics">ramGraphics</h1>

---

##### void ramBox(const ramNode& o, float size)

This method works in much the same way as ofBox, with additional support for collision detection.

An example of how collision detection works is available in the _SoundCube.h_ scene in the RAMDanceToolkit.

---

##### void ramSphere(const ramNode& o, float radius)

This method works in much the same way as ofSphere, with additional support for collision detection.

An example of how collision detection works is available in the _SoundCube.h_ scene in the RAMDanceToolkit.

---

##### void ramDrawBasicActor(const ramActor& actor)

This method draws a ramActor object using simple shapes.

---

##### void ramDrawBasicRigid(const ramRigidBody& rigid)

This method draws a ramRigidBody object using simple shapes.

----

##### void ramDrawNodes(const ramNodeArray& nodeArray)

This method draws a ramNodeArray object using simple shapes.
You can use this method when you need to check whether an object is a ramNodeArray, ramActor or ramRigidBody.

----

##### void ramDrawNodeCorresponds(const ramNodeArray &a, const ramNodeArray &b)

This method draws lines between the corresponding nodes. Two ramNodeArrays must have same number of nodes.

----

##### void ramStripe(...)

This method draws a plane using a vector of ramNode objects.  
`vector<ramNode>` or many `ramNode` can be passed as argument:
	
	// vector
	vector<ramNode> nodes;
	nodes.push_back(some_node1);
	nodes.push_back(some_node2);
	nodes.push_back(some_node3);
	ramStripe(nodes);
	
	// ramNode (min:5, max:12)
	ramStripe(some_node1, some_node2, some_node3, some_node4, some_node5, … some_node12);


---

<br>


<h1 id="wiki-ramSimpleShadow">ramSimpleShadow</h1>

By wrapping your graphics between ramBeginShadow() and ramEndShadow(), you can draw shadows on the floor.

---

##### void ramBeginShadow()

This method starts drawing shadows.

---

##### void ramBeginShadow()

This method ends drawing shadows.

---

##### void ramSetShadowAlpha(float alpha)

This method sets shadow alpha.

---

##### void ramSetShadowAlpha(float alpha)

This method sets shadow alpha.

---

##### void ramEnableShadow(bool v = true)

This method sets shadow alpha.



---

<br>


<h1 id="wiki-ramColor">ramColor</h1>

The following colors are available:

`ramColor::RED_NORMAL`,
`ramColor::RED_DEEP`,
`ramColor::RED_LIGHT`,
`ramColor::GREEN_NORMAL`,
`ramColor::GREEN_DEEP`,
`ramColor::GREEN_LIGHT`,
`ramColor::BLUE_NORMAL`,
`ramColor::BLUE_DEEP`,
`ramColor::BLUE_LIGHT`,
`ramColor::YELLOW_NORMAL`,
`ramColor::YELLOW_DEEP`,
`ramColor::YELLOW_LIGHT`,
`ramColor::BLACK`,
`ramColor::DARK_GRAY`,
`ramColor::GRAY`,
`ramColor::LIGHT_GRAY`,
`ramColor::WHITE`,
`ramColor::DARK_GRAY_ALPHA`,
`ramColor::GRAY_ALPHA`,
`ramColor::LIGHT_GRAY_ALPHA`,
`ramColor::SHADOW`.
	
For example:

	// ramColor::RED_NORMAL returns ofColor::fromHex(0xff6666)
	ofSerColor( ramColor::RED_NORMAL );

---

<br>


<h1 id="wiki-ramGraphView">ramGraphView</h1>


---

<br>


<h1 id="wiki-ramNodeLine">ramNodeLine</h1>


<hr>
<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="http://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">This Document</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://interlab.ycam.jp/projects/ram" property="cc:attributionName" rel="cc:attributionURL">YCAM InterLab, Yoshito Onishi, Satoru Higa, Motoi Shimizu, and Kyle McDonald</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
