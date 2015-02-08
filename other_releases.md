## v1.2.0

### source code
[RAM-release-v1.2.0.zip]() (Mac OS 10.??+, Windows7+, OF0.8.4, ---MB)

### compiled app
- [RAM-app_osx_v1_2_0.zip]() (Mac OS 10.7+, 106.1MB)
- [RAM-app_win_v1_2_0.zip]() (Windows 7+, 136.7MB)

### change log
- add **ramMotionExtractor** : It makes you easier to edit node selection. check [wiki](https://github.com/YCAMInterlab/RAMDanceToolkit/wiki/RAM-API-Reference-MotionExtractor_jp) how to use it.


## v1.1.0

### source code
- [RAM-release-v1_1_0.zip](https://github.com/YCAMInterlab/RAMDanceToolkit/releases/download/v1.1.0/RAM-release-v1_1_0.zip) (Mac OS 10.7+, Windows7+, OF0.8.3+, 107.1MB)

### compiled app
- [RAM-app_osx_v1_1_0.zip](https://github.com/YCAMInterlab/RAMDanceToolkit/releases/download/v1.1.0/RAM-app_osx_v1_1_0.zip) (Mac OS 10.7+, 106.1MB)
- [RAM-app_win_v1_1_0.zip](https://github.com/YCAMInterlab/RAMDanceToolkit/releases/download/v1.1.0/RAM-app_win_v1_1_0.zip) (Windows 7+, 136.7MB)

### change log

- Compatible with oF0.8.3
- Bugfix:
  - fixed unrepeatable crash problem that happens when ramActor disappear. RAMDanceToolkit have got more stable.
  - ramNode::accelerometer didn't work correctly when you apply ramFilter to ramNodeArray, and use Tsv playbacker
- New features:
  - `ramGetNode(actorIndex, jointName)` - Shorthand of accessing to ramNode
  - `ramCommunicationManager` - OSC interface


---


## v1.0.1

### source code
- [RAM-release-v1_0_1.zip](https://github.com/YCAMInterlab/RAMDanceToolkit/releases/download/v1.0.1/RAM-release-v1_0_1.zip) (Mac OS 10.7+, Windows 7+, 112.1MB)

### compiled app
- [RAM-app_osx_v1_0_1.zip](https://github.com/YCAMInterlab/RAMDanceToolkit/releases/download/v1.0.1/RAM-app_osx_v1_0_1.zip) (Mac OS 10.7+, 76.1MB)
- (no update for windows)

### change log

- added second arg to ramInitialize() which is used as hook of show/hide preset scenes buttons on gui


---


## v1.0.0

### source code
- [RAM-release-v1_0_0.zip](https://github.com/YCAMInterlab/RAMDanceToolkit/releases/download/v1.0.0/RAM-release-v1_0_0.zip) (Mac OS 10.7+, Windows 7+, 125.4MB)

### compiled app
- [RAM-app_osx_v1_0_0.zip](https://github.com/YCAMInterlab/RAMDanceToolkit/releases/download/v1.0.0/RAM-app_osx_v1_0_0.zip) (Mac OS 10.7+, 76.1MB)
- [RAM-app_win_v1_0_0.zip](https://github.com/YCAMInterlab/RAMDanceToolkit/releases/download/v1.0.0/RAM-app_win_v1_0_0.zip) (Windows 7+, 82.2MB)

