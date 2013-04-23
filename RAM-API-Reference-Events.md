# Events


### Summary

This page shows how to use ramEvents.
These are not Event Object like ofEvent, but has boolean state  which is set true when it fires.



### table of contents
- Introduction to ramBaseEvent
- ramCollisionEvent
- ramScheduledTimerEvent
- ramRandomTimerEvent


# Introduction to ramBaseEvent

ramBaseEvent is a base class of all RAM events. 
Here is a minimum example of new filter class "MyFilter".

	class MyEvent : public ramBaseEvent
	{
	
	protected:
		bool tick()
		{
			// do something...
		}
	};

When you call update() implemented in ramBaseFilter, boolean which is returned by tick() is returned to a caller. Cached value will be returned if you call update() many time in same frame.

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

ramCollisionEvent observes collision between `ramPremitive` set to ramCollisionEvent and other objects which also have collision detection e.g. `ramBox`, `ramLine`.

Three trigger timing can be set to ramCollisionEvent.

	enum ramTriggerTiming
	{
		RAM_TRIGGER_UP,
		RAM_TRIGGER_DOWN,
		RAM_TRIGGER_BOTH
	};





# ramScheduledTimerEvent

ramScheduledTimerEvent changes its state once per interval duration. 


# ramRandomTimerEvent

ramRandomTimerEvent changes its state once per interval duration which set randomly between `min` and `max`.

