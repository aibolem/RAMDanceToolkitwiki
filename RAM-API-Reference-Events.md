# Events


### Summary

This page describes how to use ramEvents.

ramEvents are not to be confused with ofEvents, which work differently. A ramEvent has a boolean state, which is set to true when it is fired.

### Table of Contents
- [Introduction to ramBaseEvent](https://github.com/YCAMInterlab/RAMDanceToolkit/wiki/RAM-API-Reference-Events#introduction-to-rambaseevent)
- [ramCollisionEvent](https://github.com/YCAMInterlab/RAMDanceToolkit/wiki/RAM-API-Reference-Events#ramcollisionevent)
- [ramScheduledTimerEvent](https://github.com/YCAMInterlab/RAMDanceToolkit/wiki/RAM-API-Reference-Events#ramscheduledtimerevent)
- [ramRandomTimerEvent](https://github.com/YCAMInterlab/RAMDanceToolkit/wiki/RAM-API-Reference-Events#ramrandomtimerevent)


# Introduction to ramBaseEvent

ramBaseEvent is a base class for all RAMDanceToolkit events.
Here is a small example of a new event class called "MyEvent".

	class MyEvent : public ramBaseEvent
	{
	
	protected:
		bool tick()
		{
			// do something...
		}
	};

When you call update() as implemented in ramBaseEvent, the boolean returned by tick() is returned to a caller. The cached value will be returned if you call update() many times in same frame.

	// testApp.h
	MyEvent event;
	
	// testApp.cpp 
	void testApp::update()
	{
		if (event.update())
		{
			// do something...		
		}
	}



# ramCollisionEvent

ramCollisionEvent observes collision between `ramPrimitive` objects that are set to respond to a ramCollisionEvent. Other objects which also have collision detection include `ramBox`, `ramLine` etc.

Three trigger timings can be set to a ramCollisionEvent.

	enum ramTriggerTiming
	{
		RAM_TRIGGER_UP,
		RAM_TRIGGER_DOWN,
		RAM_TRIGGER_BOTH
	};





# ramScheduledTimerEvent

ramScheduledTimerEvent changes its state once per interval duration. 


# ramRandomTimerEvent

ramRandomTimerEvent changes its state once per interval duration, which is set randomly between `min` and `max`.

<hr>
<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="http://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">This Document</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://interlab.ycam.jp/projects/ram" property="cc:attributionName" rel="cc:attributionURL">YCAM InterLab, Yoshito Onishi, Satoru Higa, Motoi Shimizu, and Kyle McDonald</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
