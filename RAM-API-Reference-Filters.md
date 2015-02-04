# Filter


### Summary

This page shows how to use ramFilters. Each of these filters inherits from ramBaseFilter. If you create your own filter, we strongly encourage you to start by inheriting from ramBaseFilter, so that your custom filter integrates nicely with RAMDanceToolkit.


### Table of Contents
- [Introduction to ramBaseFilter](Introduction to ramBaseFilter)
- [ramExpansion](ramExpansion)
- [ramLowPassFilter](ramLowPassFilter)
- [ramNodeTransform](ramNodeTransform)
- [ramGhost](ramGhost)
- [ramPendulum](ramPendulum)
- [ramSession](ramSession)
- [ramStamp](ramStamp)
- [ramTimeShifter](ramTimeShifter)
- [ramUpsideDown](ramUpsideDown)


# Introduction to ramBaseFilter

ramBaseFilter is the base class of all filters. This class provides common interfaces for filtering data and getting desired results.

Here is a simple example of a custom filter class called "MyFilter".

	class MyFilter : public ramBaseFilter
	{
		
	public:
		
		MyFilter() {}
		
		void setupControlPanel()
		{
			// GUI implementation goes here...
		}
		
		
		const ramNodeArray& update(ramNodeArray& src)
		{
			// do something...
			
			return src;
		}
		
		const string getName() { return "MyFilter"; }
	};

For filtering a ramNodeArray, `const ramNodeArray& update(const ramNodeArray& src)` should be called. ramBaseFilter will create a cache of update results from  each frame and keep track of the result correctly. 

For getting your filtered results, you can use the returned value from update(). Or simply call `const ramNodeArray& ramBaseFilter::get(size_t index)` after updating.


So you might end up using MyFilter like this:

	// testApp.h
	MyFilter filter;
	
	// testApp.cpp 
	void testApp::drawActor(const ramActor &actor)
	{
		const ramNodeArray& NA = filter.update(actor);
		ramDrawBasicActor(actor);
	}



---

<br>


# ramExpansion

---

<br>

# ramLowPassFilter


---

<br>

# ramNodeTransform

---

<br>

# ramGhost

---

<br>

# ramPendulum

---

<br>

# ramSession

---

<br>

# ramStamp

---

<br>

# ramTimeShifter

---

<br>

# ramUpsideDown



<hr>
<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="http://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">This Document</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://interlab.ycam.jp/projects/ram" property="cc:attributionName" rel="cc:attributionURL">YCAM InterLab, Yoshito Onishi, Satoru Higa, Motoi Shimizu, and Kyle McDonald</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
