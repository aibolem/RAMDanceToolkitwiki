## Downloads

To start using RAMDanceToolkit, you can download [compiled application, whole source code zip](Overview#downloads), or clone [RAMDanceTookit repository](https://github.com/YCAMInterlab/RAMDanceToolkit).

## Compiled Application

Unzip the downloaded file and launch your RAMDanceToolkit app.  

[[/Images/Introduction/fig-setup-1.png]]

The recorded motion data `Ando_1` appears only at the first time launching of RAMDanceToolkit. The other motion datas `Ando`, `Cyril`, `Richi` are placed in `RAMDanceTookit/resources/MotionData`.  To start playback, click "Load file" button on Actors panel or drag and drop the motion data file to the application.

[[/Images/Introduction/fig-setup-3.png]]

Note that you can playback four motion data at the same time. If you are sending one ramActor OSC message from MOTIONER or other motion capture system to RAMDanceToolkit, you can playback three motion data.

[[/Images/Introduction/fig-setup-2.png]]


## Source code zip

If you are a developer, you can modify RAMDanceTookit source code which is placed at `RAMDanceToolkit/apps/RAMDanceToolkit`. See also RAM API Reference on this wiki.


### addons 

ofxAddons which are load from core libs.  
If you want to add other addons, we recommend to add it to `{OF_ROOT}/addons`.

### apps

RAMDanceToolkit and OpenNIOSC.
You can use OpenNIOSC instead of MOTIONER or other sensors as simple mocap test if you have Microsoft Kinect.

### examples

Sample codes to understand API.


### libs

RAMDanceToolkit core library.

### resources

Fonts, Images, Default Setting files, MotionData, Sound files.  
As noted at Compiled Application section, recorded motion data is in the `MotionData`. 
