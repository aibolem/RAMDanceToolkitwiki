
# Graphics

RAMDanceToolkit has some global method to draw shapes defined at _ramGraphics.h_.


### table of contents

- [ramGraphics](#wiki-ramGraphics)
- [ramSimpleShadow](#wiki-ramNodeArray)
- [ramColor](#wiki-ramNode)
- [ramGraphView](#wiki-ramActorManager)
- [ramNodeLine](#wiki-ramNodeLine)


<br>


<h1 id="wiki-ramGraphics">ramGraphics</h1>

---

##### void ramBox(const ramNode& o, float size)

Same to ofBox but has collision detection.  
Example of collision detection is available on _SoundCube.h_ scene in RAMDanceToolkit.

---

##### void ramSphere(const ramNode& o, float radius)

Same to ofSphere but has collision detection.  
Example of collision detection is available on _SoundCube.h_ scene in RAMDanceToolkit.

---

##### void ramSphere(const ramNode& o, float radius)

Same to ofSphere but has collision detection.

---

##### void ramDrawBasicActor(const ramActor& actor)

Draws ramActor using simple shape.

---

##### void ramDrawBasicRigid(const ramRigidBody& rigid)

Draws ramRigidBody using simple shape.

----

##### void ramDrawNodes(const ramNodeArray& nodeArray)

Draws ramNodeArray using simple shape.  
Use this method When you need to check is the ramNodeArray ramActor or ramRigidBody.

----

##### void ramDrawNodeCorresponds(const ramNodeArray &a, const ramNodeArray &b)

Draws lines between correspond nodes. Two ramNodeArrays must have same number of nodes.

----

##### void ramStripe(...)

Draws plane using passed ramNode.  
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

To draw shadow on the floor, wrap your code to draw something using ramBeginShadow(), ramEndShadow().

---

##### void ramBeginShadow()

Starts drawing shadow.

---

##### void ramBeginShadow()

Ends drawing shadow.

---

##### void ramSetShadowAlpha(float alpha)

Sets shadow alpha.

---

##### void ramSetShadowAlpha(float alpha)

Sets shadow alpha.

---

##### void ramEnableShadow(bool v = true)

Sets shadow alpha.



---

<br>


<h1 id="wiki-ramColor">ramColor</h1>


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
are available as preset. 
	
	// ramColor::RED_NORMAL returns ofColor::fromHex(0xff6666)
	ofSerColor( ramColor::RED_NORMAL );

---

<br>


<h1 id="wiki-ramGraphView">ramGraphView</h1>


---

<br>


<h1 id="wiki-ramNodeLine">ramNodeLine</h1>


