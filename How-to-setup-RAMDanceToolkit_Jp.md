## ダウンロード

アプリケーション、モーションデータOSCサーバー、ソースコード一式のzipを[ダウンロード](Overview#downloads)出来ます。
または、GitHubからRAMDanceTookit repositoryを[clone](https://github.com/YCAMInterlab/RAMDanceToolkit)する事が出来ます。

## アプリケーション

ダウンロードしたzipファイルを解凍し、RAMDanceToolkitアプリケーションを起動してください。

[[/Images/Introduction/fig-setup-1.png]]



## ソースコード一式のzip

ソースコード一式をダウンロードして、本Wiki内のRAM API Referenceを参考にRAMDanceToolkitを編集する事が出来ます。
ダウンロードしたファイルは、openFrameworks (version 0.8.4) ディレクトリの直下に置いてください。

[[/Images/Introduction/fig-setup-of.png]]


## RAMDanceTookit repositoryをCloneする

openFrameworks (version 0.8.4) ディレクトリの直下にcloneしてください。

[[/Images/Introduction/fig-setup-of.png]]

RAMリポジトリをcloneする場合、コードを書き始める前に2つする事があります。

### 1. Submodules checkout, ofxUI編集パッチのapply

このリポジトリ内のaddonsは、submoduleとして管理されています。
RAMルートディレクトリにある `submodules.sh`を実行して、addonsの入手とパッチの実行を行います。  
*事前に[git](http://git-scm.com/downloads)がインストールされている必要があります。

	$ cd {RAM_ROOT}
	$ ./submodules.sh

#### submodules.sh

このスクリプトは、submoduleとして管理をしているaddonsの入手、ofxUI.patchの実行を行います。
ofxUI.hはデフォルトの状態で、`GUI/NewMedia Fett.ttf`というパスのフォントを読みにきます。このままだと全てのアプリケーション配下にある `bin/data`ディレクトリにフォントを複製しなければならないので、ofxUIがRAMDanceToolkit内のresourcesディレクトリ内のFontを読みに行く様に編集を行っています。


### 2. 追加resourcesのダウンロード

このリポジトリは、サウンドファイル、モーションデータのファイル等の大きいサイズのディレクトリを含んでいません。
以下のサウンドファイル、モーションデータをダウンロードする必要があります。

- [RAM-Sound_MotionData_v1_0_0.zip](https://github.com/YCAMInterlab/RAMDanceToolkit/releases/download/v1.0.0/RAM-Sound_MotionData_v1_0_0.zip) (29.5MB)

ダウンロード・解凍後、`Sounds` `MotionData` ディレクトリを `{RAM_ROOT}/resources`に追加してください。

[[/Images/Introduction/fig-setup-4.png]]


## RAMDanceToolkitのフォルダ構造

RAMDanceTookitアプリケーションのソースコードは、`RAMDanceToolkit/apps/RAMDanceToolkit`にあります。


### addons 

RAMコアライブラリから読まれるofxAddonsが入っています。
もし別のaddonsを追加したい場合は、このディレクトリではなく `{OF_ROOT}/addons` に追加する事をお勧めします。

### apps

RAMDanceToolkit、OpenNIOSCが入っています。
もしMicrosoft Kinectをお持ちであれば、MOTIONERや他のモーションキャプチャーシステムの代替えとしてOpenNIOSCを使用する事が出来ます。Windowsの場合は.slnファイルをVisualC++で、OSXの場合は.xcodeprojファイルをXCodeで開いて使用します。Windowsで新規にダウンロードしたopenFrameworksを使用する場合、<br />
'openFrameworksフォルダ/libs/openFrameworksCompiled/project/vs2010/openframeworksLib.sln' <br />
をVisualC++で開き、あらかじめdebugとreleaseの設定でビルドしておく必要があります。

### examples

RAM APIに慣れる為のサンプルコードがあります。使用するファイル、注意点は上記appsフォルダについて書かれたものをご参照ください。

### libs

RAMDanceToolkit core libraryが入っています。

### resources

画像やフォント等、全てのアプリケーションから読まれる共有リソースが入っています。 各アプリケーションからは、`ramToRecourcePath(...)`でこのディレクトリへの相対パスを作る事が出来ます。
前述の通り、レコーディング済みのモーションデータは `resources/MotionData` に入っています。RAMDanceToolkitはresourcesフォルダをアプリケーションに近いパスから順番に探しだし、最も近い位置にあるresourcesフォルダを用います。コンパイル済みのアプリケーションを人に渡す際などにはアプリケーションと同じフォルダに、それ以外の場合はダウンロード時の位置に置いておくのが良いでしょう。


### モーションデータのプレイバック
MOTIONER等からのモーションデータをOSCで受け取らずに、レコーディング済みのデータを再生してRAMDanceToolkitをテストする事が出来ます。

**※現在、Mac OSのみこの機能に対応しています。**

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


<hr>
<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="http://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">This Document</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://interlab.ycam.jp/projects/ram" property="cc:attributionName" rel="cc:attributionURL">YCAM InterLab, Yoshito Onishi, Satoru Higa, Motoi Shimizu, and Kyle McDonald</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
