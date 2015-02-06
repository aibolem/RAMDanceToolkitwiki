## about Hakoniwa

Hakoniwa is a kind of small laboratries that react to dancers' movement. This works with the same concept as RAM scenes, but physical. Using motors, fans, electromagnets to create physical phenomenon to react to motion data, and show the reaction to dancers, so dansers can use this feedbacks as a part of their environment.

Examples for Hakoniwas

- ServoPendulum
Double pendulum is attached on a servo motor. Dancer can control this servo motor's freqency controling distance between chosen 2 nodes.

* movie link comes

- MagnetPendulum
hang magnet on a string from the high place (get higher, move slower), dancer can control on/off of electromagnets on the floor, then dancer can affect the movement of the hanged magnet.

* movie link comes

- Tornado
put a watertank and voporizer(in the watertank) and fan(on the ceiling) in a box, and make a tornado. Dancer can control tornado through controlling the fan on the ceiling.

* movie link comes

### system map

RDTK    -----> Arduino -----> Hakoniwa
machine	<-----         <-----    ↓
        <--------------------- Camera

Change here to an image file.


### Hakoniwa & HakoViz

2 Example projects for Hakoniwa & HakoViz are in `RAM-Root/examples/`.

`example_Hakoniwa_HakoVis_MagPendulum`
`example_Hakoniwa_HakoVis_ServoPendulum`

Each has project files for OSX/Windows development, Arduino source code, and a schematic file.

RAMDanceToolkit assume 2 scenes for a hakoniwa.
first one is for controlling a hakoniwa, which we call Hakoniwa. this scene Analyze motion data and use specific movement of bodies, and control Hakoniwa. in example projects, this scene show a realtime visualization for dancers to understand how their motion can affect hakoniwa.

Second one is for showing a visualization using data from Hakoniwa via OSC from Arduino/Sensors or Video analysis, which we call HakoViz. HakoViz is not always needed to use Hakoniwa.


### Video analysis and sensors

To obserb Hakoniwa, there're mainly 2 ways. one is using Camera, the other is using other sensers. CameraUnit in `RAM-Root/apps/` is for video analysis to analyze Hakoniwa. Please check `ram-root/apps/CameraUnit/readme.md` for the usage.

data from sensers on hakoniwas go in Arduino and is sent via OSC message to a computer where RAMDanceToolkit is running. Port number can be the same as the number you set in ramInitialize(int port) in setup() in testApp.cpp. and you can use ramOscReceiveTag to get OSC message with registered address in your scene.

for example, in .h & .cpp files for a scene,

.h file

    ramOscReceiveTag mReceiver;

.cpp file and in setup()

    ramOscManager::instance().addReceiverTag(&mReceiver);
    mReceiver.addAddress("/dp/cameraUnit/MagPendulum/contour/boundingRect");

then you can get OSC messages with the address "/dp/cameraUnit/MagPendulum/contour/boundingRect" in this scene.

You can check actual implementations in 2 example projects, so please check HakoViz source codes in them.


