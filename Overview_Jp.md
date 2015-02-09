RAM Dance Tookitはクリエイティブコーディングでダンスのための環境を作り出すC++のツールキットです。GUIと、ダンサーのモーションデータにアクセス、解析・利用するための機能を備え、プログラミングを使って様々な環境条件（「シーン」と呼びます）を設定し、ダンサーに対するリアルタイムのフィードバックをシンプルな手順で作り出す事ができます。このツールキットはアーティストのためのソフトウェア開発環境であるopenFrameworksをベースとして開発されており、ユーザーは両方の機能を使用する事ができます。また、RAM Dance Toolkitはプログラミングを必要としないアプリケーションの形でも公開します。アプリケーションを使って、YCAMで開発された既存のシーンを使って振付やトレーニングをおこなうことが出来ます。

[[/Images/Home/ram.png]]




## リンク

### [Introduction to RAM Dance Toolkit application (vimeo)](http://vimeo.com/64703174) 
Kyle McDonaldによる、 RAMDanceToolkitアプリケーション使用方法の解説ムービー

### [Introduction to coding with RAM Dance Toolkit (vimeo)](http://vimeo.com/64775855)  
Kyle McDonaldによる、 RAMDanceToolkit APIの使い方・開発の流れについての解説ムービー

### [Reactor for Awareness in Motion (RAM) - YCAM InterLab](http://interlab.ycam.jp/projects/ram/) 
YCAM InterLab "Reactor for Awareness in Motion" プロジェクトウェブサイト




## ダウンロード 

RAMDanceToolkitアプリケーションと、ソースコードを以下のリンクからダウンロードする事が出来ます。
使用方法に関しては、上記リンク先の動画や、[RAMDanceToolkitのセットアップ](How-to-setup-RAMDanceToolkit_Jp)をご覧下さい。過去のリリースとchange logに関しては、[Other eleases](Other_Releases)をご覧下さい。

### RAMDanceToolkit アプリケーション

コンパイル済みのアプリケーションは、以下のリンクからダウンロード出来ます。

- [RAM-app_osx_v1_2_1.zip](http://interlab.ycam.jp/wp-content/uploads/2015/02/RAM-app_osx_v1_2_1.zip) (Mac OS 10.7+, 77.0MB, updated on 9 Feb 2015)
- [RAM-app_win_v1_2_1.zip](http://interlab.ycam.jp/wp-content/uploads/2015/02/RAM-app_win_v1_2_1.zip) (Windows 7+, 66.3MB, updated on 9 Feb 2015)

Windowsバージョンをご使用になる場合は、事前に[MS Runtime](https://www.microsoft.com/en-US/download/details.aspx?id=30679)をインストールする必要があります。言語を選択し、x86バージョンのものをインストールしてください。

### モーションデータ OSCサーバー

MOTIONER等のモーションキャプチャーシステムから送られてくるOSCメッセージと同じものをを送信する為のアプリケーションです。
同梱のモーションデータxmlファイルをアプリケーションにドラッグアンドドロップをすると再生が始まります。
RAMDanceToolkitのテスト用にお使いください。

- [RAM-OSCServer_mac-v1_0_0.zip](https://github.com/YCAMInterlab/RAMDanceToolkit/releases/download/v1.0.0/RAM-OSCServer_mac-v1_0_0.zip) (Mac OS 10.7+, 32.6MB)
- [RAM-OSCServer_win-v1_0_0.zip](https://github.com/YCAMInterlab/RAMDanceToolkit/releases/download/v1.0.0/RAM-OSCServer_win-v1_0_0.zip) (Windows7+, 39.7MB)

### ソースコード

RAMDanceToolkit, OSCサーバーやその他ソースコード、 モーションデータ等の全てが入っています。
ご自身のプロジェクトの開発にお使いください。

- [RAM_Release_v1_1_0.zip](https://github.com/YCAMInterlab/RAMDanceToolkit/releases/download/v1.1.0/RAM-release-v1_1_0.zip) (Mac OS 10.7+, Windows7+, OF0.7.4+, 107.1MB)

### サウンドファイル, モーションデータ

RAMDanceToolkitのリポジトリをcloneした場合に必要なファイルです。
上記のアプリケーション・ソースコードのzipファイルに含まれていますので、ダウンロードする必要はありません。

- [RAM-Sound_MotionData_v1_0_0.zip](https://github.com/YCAMInterlab/RAMDanceToolkit/releases/download/v1.0.0/RAM-Sound_MotionData_v1_0_0.zip) (99.9MB)




## ライセンス
RAMDanceToolkit by YCAM InterLab, Yoshito Onishi, Satoru Higa, Motoi Shimizu, and Kyle McDonald is licensed under the [Apache License, Version2.0](http://www.apache.org/licenses/LICENSE-2.0.html)

    Copyright 2012-2013 YCAM InterLab, Yoshito Onishi, Satoru Higa, Motoi Shimizu, and Kyle McDonald

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
    
<hr>
<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="http://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">This Document</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://interlab.ycam.jp/projects/ram" property="cc:attributionName" rel="cc:attributionURL">YCAM InterLab, Yoshito Onishi, Satoru Higa, Motoi Shimizu, and Kyle McDonald</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
