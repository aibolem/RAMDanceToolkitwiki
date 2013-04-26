## ダウンロード

[アプリケーション、またはソースコード一式のzip](Overview#downloads)をダウンロード出来ます。
または、[RAMDanceTookit repository](https://github.com/YCAMInterlab/RAMDanceToolkit)をcloneしてください。

## アプリケーション

Unzip the downloaded file and launch your RAMDanceToolkit app.  
ダウンロードしたzipファイルを解凍し、RAMDanceToolkitアプリケーションを起動してください。

[[/Images/Introduction/fig-setup-1.png]]

初回起動時のみ、`Ando_1`というダンサーがステージに現れます。
次回からの起動は、`RAMDanceTookit/resources/MotionData`ディレクトリにある `Ando`, `Cyril`, `Richi`のデータを"Load File"ボタンから読み込み・またはファイルをアプリケーションへドラッグ&ドロップする事でモーションデータの再生が始まります。

[[/Images/Introduction/fig-setup-3.png]]

一度に再生出来るプレイバックデータの最大数は4人までです。
（もしMOTIONERやその他のモーションキャプチャーシステムから一人分のOSCメッセージを受け取って再生をしている場合、プレイバックできる最大数は3人までです。）

[[/Images/Introduction/fig-setup-2.png]]


## ソースコード一式のzip

If you are a developer, you can modify RAMDanceTookit source code which is placed at `RAMDanceToolkit/apps/RAMDanceToolkit`. See also RAM API Reference on this wiki.

ソースコード一式をダウンロードして、本Wiki内のRAM API Referenceを参考にRAMDanceToolkitを編集する事が出来ます。
RAMDanceTookitアプリケーションのソースコードは、`RAMDanceToolkit/apps/RAMDanceToolkit`にあります。


### addons 

RAMコアライブラリから読まれるofxAddonsが入っています。
もし別のaddonsを追加したい場合は、このディレクトリではなく `{OF_ROOT}/addons` に追加する事をお勧めします。

### apps

RAMDanceToolkit and OpenNIOSC.
You can use OpenNIOSC instead of MOTIONER or other sensors as simple mocap test if you have Microsoft Kinect.
RAMDanceToolkit、OpenNIOSCが入っています。
もしMicrosoft Kinectをお持ちであれば、MOTIONERや他のモーションキャプチャーシステムの代替えとしてOpenNIOSCを使用する事が出来ます。

### examples

RAM APIに慣れる為のサンプルコードがあります。


### libs

RAMDanceToolkit core libraryが入っています。.

### resources

Shared resources which are load from each application. You can use `ramToRecourcePath(...)` in your code to get the path to directory.

As noted at Compiled Application section, recorded motion data is in the `MotionData`. 


## Clone RAMDanceTookit repository

If you clone the RAM repo, you should do two tasks before writing code.

### 1. Submodules checkout and applying patch to modify ofxUI

This repo doesn't include the addons in `RAMDanceToolkit/addons` which are managed as submodules.

Run this shell script after cloning the repo.

	$ cd {RAM_ROOT}
	$ ./submodules.sh


#### tasks of submodules.sh

This script simply checkout the submodules, and apply ofxUI.patch at ofxUI directory.  
ofxUI requires `GUI/NewMedia Fett.ttf` font file which is placed at `bin/data` so we have to duplicate the font to every project. After applying this patch, the path to font file will be changed to `{RAM_ROOT}/resources/Fonts/FreeUniversal-Regular.ttf`.


### 2. download resources

This repo doesn't include some big size files e.g. Sounds, MotionData so you have to download it manually.

- [RAM-Sound_MotionData_v1_0_0.zip](https://raw.github.com/wiki/YCAMInterlab/RAMDanceToolkit/releases/resources/RAM-Sound_MotionData_v1_0_0.zip)

After download, add `Sounds` and `MotionData` directories into `{RAM_ROOT}/resources`.

[[/Images/Introduction/fig-setup-4.png]]