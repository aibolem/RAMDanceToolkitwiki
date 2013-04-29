## ダウンロード

[アプリケーション、モーションデータOSCサーバー、ソースコード一式のzip](Overview#downloads)をダウンロード出来ます。
または、[RAMDanceTookit repository](https://github.com/YCAMInterlab/RAMDanceToolkit)をcloneする事が出来ます。

## アプリケーション

ダウンロードしたzipファイルを解凍し、RAMDanceToolkitアプリケーションを起動してください。

[[/Images/Introduction/fig-setup-1.png]]

### モーションデータのプレイバック
MOTIONER等からのモーションデータをOSCで受け取らずに、レコーディング済みのデータを再生してRAMDanceToolkitをテストする事が出来ます。　　
**※RAMDanceToolkit バージョン1.0.0 では、Mac OSのみこの機能に対応しています。**

初回起動時のみ、`Ando_1`というダンサーがステージに現れます。
次回からの起動は、`RAMDanceTookit/resources/MotionData`ディレクトリにある `Ando`, `Cyril`, `Richi`のデータを"Load File"ボタンから読み込み・またはファイルをアプリケーションへドラッグ&ドロップする事でモーションデータの再生が始まります。

[[/Images/Introduction/fig-setup-3.png]]

一度に再生出来るプレイバックデータの最大数は4人までです。
（もしMOTIONERやその他のモーションキャプチャーシステムから一人分のOSCメッセージを受け取って再生をしている場合、プレイバックできる最大数は3人までです。）

[[/Images/Introduction/fig-setup-2.png]]


## モーションデータ OSCサーバー

[[/Images/Introduction/fig-setup-osc1.png]]

同梱の`MotionData-OSCServer`ディレクトリ内のxmlファイルをドラッグアンドドロップすると、アプリケーション内で指定したIP, portへMOTIONERから送られてくるOSC messageと同じmessageを送信し始めます。
MOTIONER等が手元に無い場合のRAMDanceToolkitのテストに役立ちます。


## ソースコード一式のzip

ソースコード一式をダウンロードして、本Wiki内のRAM API Referenceを参考にRAMDanceToolkitを編集する事が出来ます。
ダウンロードしたファイルは、openFrameworks (version 0.7.4+) ディレクトリの直下に置いてください。

[[/Images/Introduction/fig-setup-of.png]]


RAMDanceTookitアプリケーションのソースコードは、`RAMDanceToolkit/apps/RAMDanceToolkit`にあります。


### addons 

RAMコアライブラリから読まれるofxAddonsが入っています。
もし別のaddonsを追加したい場合は、このディレクトリではなく `{OF_ROOT}/addons` に追加する事をお勧めします。

### apps

RAMDanceToolkit、OpenNIOSCが入っています。
もしMicrosoft Kinectをお持ちであれば、MOTIONERや他のモーションキャプチャーシステムの代替えとしてOpenNIOSCを使用する事が出来ます。

### examples

RAM APIに慣れる為のサンプルコードがあります。

### libs

RAMDanceToolkit core libraryが入っています。

### resources

画像やフォント等、全てのアプリケーションから読まれる共有リソースが入っています。 各アプリケーションからは、`ramToRecourcePath(...)`でこのディレクトリへの相対パスを作る事が出来ます。
前述の通り、レコーディング済みのモーションデータは `resources/MotionData` に入っています。


## RAMDanceTookit repositoryをCloneする

openFrameworks (version 0.7.4+) ディレクトリの直下にcloneしてください。

[[/Images/Introduction/fig-setup-of.png]]

RAMリポジトリをcloneする場合、コードを書き始める前に2つやる事があります。

### 1. Submodules checkout, ofxUI編集パッチのapply

このリポジトリ内のaddonsは、submoduleとして管理されています。
RAMルートディレクトリにある `submodules.sh`を実行して、addonsの入手とパッチの実行を行います。

	$ cd {RAM_ROOT}
	$ ./submodules.sh

#### submodules.sh

このスクリプトは、submoduleとして管理をしているaddonsの入手、ofxUI.patchの実行を行います。
ofxUI.hはデフォルトの状態で、`GUI/NewMedia Fett.ttf`というパスのフォントを読みにきます。このままだと全てのアプリケーション配下にある `bin/data`ディレクトリにフォントを複製しなければならないので、ofxUIがRAMDanceToolkit内のresourcesディレクトリ内のFontを読みに行く様に編集を行っています。


### 2. 追加resourcesのダウンロード

このリポジトリは、サウンドファイル、モーションデータのファイル等の大きいサイズのディレクトリを含んでいません。
以下のサウンドファイル、モーションデータをダウンロードする必要があります。

- [RAM-Sound_MotionData_v1_0_0.zip](https://raw.github.com/wiki/YCAMInterlab/RAMDanceToolkit/releases/resources/RAM-Sound_MotionData_v1_0_0.zip) (29.5MB)

ダウンロード・解凍後、`Sounds` `MotionData` ディレクトリを `{RAM_ROOT}/resources`に追加してください。

[[/Images/Introduction/fig-setup-4.png]]