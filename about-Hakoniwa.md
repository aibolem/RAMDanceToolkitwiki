## About Hakoniwa

Hakoniwa are small "laboratories" that respond to the movement of dancers. They can be thought of as RAM scenes, but, instead of being virtual or digital, they are physical manifestations of reactive environments. By using motors, fans, electromagnets, hakoniwa embody physical environments that react to motion data. The actions that happen within a hakoniwa are fedback to the dancers, and the dancers can use this information as inspiration for new movement.

Hakoniwa Examples:

- ServoPendulum
ServoPendulum is a double pendulum attached on a servo motor. A dancer can control this servo motor's frequency by changing the distance between chosen 2 nodes on the dancer's body.

** movie link to come **

- MagnetPendulum
MagnetPendulum comprises of a magnet hung on a string above a set of electromagnets. The dancer can control which electromagnets turn on and off, affecting the position and movement of the hanging magnet.

** movie link to come **

- Tornado
Tornado is made up of a fog machine in a water tank, with a fan in the ceiling. When the fog machine and fan are turned on, it creates a simulated tornado. A dancer can control the creation of the tornado by controlling the fan on the ceiling.

** movie link to come **

### System Map

RDTK    -----> Arduino -----> Hakoniwa
machine	<-----         <-----    ↓
        <--------------------- Camera

Change here to an image file.


### Hakoniwa & HakoViz

You can find two example projects for Hakoniwa and HakoViz in `{RAM_Root}/examples/`:

`example_Hakoniwa_HakoVis_MagPendulum`
`example_Hakoniwa_HakoVis_ServoPendulum`

Each example has project files for OSX/Windows development, as well as the Arduino source code and schematic file for the Hakoniwa.

The RAMDanceToolkit assume two scenes for a Hakoniwa.

1. Hakoniwa: This scene is used to control the Hakoniwa, as well as to analyze the incoming motion data of specific body movements to control the Hakoniwa. In the example projects, the Hakoniwa scene shows a realtime visualization, so that the dancers can understand how their movements affect the Hakoniwa.

2. HakoViz: This scene shows a visualization of the data coming in from the Hakoniwa, either via OSC from a sensor or through video analysis. HakoViz is not always needed to use Hakoniwa.

### Video analysis and sensors

There are two main ways to "observe" a Hakoniwa. One is though a video camera. The other is through sensors. Please refer to the CameraUnit example in `RAM-Root/apps/` for an example of how to apply video analysis techniques to analyze Hakoniwa. Also please refer to `ram-root/apps/CameraUnit/readme.md` for more documentation on its usage.

You can also use data from sensors attached to a Hakoniwa to produce visualizations. In your Arduino program, send values via OSC to your RAMDanceToolkit application. Use the same port number that you use in your ramInitialize(int port) function in the setup() function of testApp.cpp. You can also use a ramOscReceiveTag to get the specific OSC message with a registered address in your scene.

Dor example, in the .h and .cpp files for a scene,

.h file

    ramOscReceiveTag mReceiver;

.cpp file, in setup()

    ramOscManager::instance().addReceiverTag(&mReceiver);
    mReceiver.addAddress("/dp/cameraUnit/MagPendulum/contour/boundingRect");

From there you can get OSC messages with the address "/dp/cameraUnit/MagPendulum/contour/boundingRect" in this scene.

Please refer to the two example projects for more specific details about implementation.
