
# Filter


### Summary

This page shows how to use ramFilters.  
Each of the filters RAMDanceToolkit includes inherits from ramBaseFilter. If you create own filter, we strongly recommend that the filter also inherits ramBaseFilter to integrate with other factor in RAMDanceToolkit.


### table of contents
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

ramBaseFilter is a base class of all filters. This class provides common interface for filtering, and getting result.

Here is a minimum example of new filter class "MyFilter".

	class MyFilter : public ramBaseFilter
	{
		
	public:
		
		MyFilter() {}
		
		void setupControlPanel()
		{
			// GUI parts implementation here...
		}
		
		
		const ramNodeArray& update(ramNodeArray& src)
		{
			// do something...
			
			return src;
		}
		
		const string getName() { return "MyFilter"; }
	};

For filtering ramNodeArray, `const ramNodeArray& update(const ramNodeArray& src)` should be called because ramBaseFilter create a cache of update result on each frame to keep the result correct. 

For getting result, you can use the returned value from update(). Or simply call `const ramNodeArray& ramBaseFilter::get(size_t index)` after updating.


Therefore MyFilter is used like:

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

---


