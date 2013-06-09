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

RAMDanceToolkitアプリケーション最新版（v1.0.0）、ソースコードを以下のリンクからダウンロードする事が出来ます。
使用方法に関しては、上記リンク先の動画や、[RAMDanceToolkitのセットアップ](How-to-setup-RAMDanceToolkit_Jp)をご覧下さい。

### RAMDanceToolkit アプリケーション

- [RAM-app_osx_v1_0_1.zip](https://raw.github.com/wiki/YCAMInterlab/RAMDanceToolkit/releases/app/RAM-app_osx_v1_0_1.zip) (Mac OS 10.7+, 79.8MB)
- [RAM-app_win_v1_0_0.zip](https://raw.github.com/wiki/YCAMInterlab/RAMDanceToolkit/releases/app/RAM-app_win_v1_0_0.zip) (Windows 7+, 86.1MB)

### モーションデータ OSCサーバー

MOTIONER等のモーションキャプチャーシステムから送られてくるOSCメッセージと同じものをを送信する為のアプリケーションです。
同梱のモーションデータxmlファイルをアプリケーションにドラッグアンドドロップをすると再生が始まります。
RAMDanceToolkitのテスト用にお使いください。

- [RAM-OSCServer_mac-v1_0_1.zip](https://raw.github.com/wiki/YCAMInterlab/RAMDanceToolkit/releases/osc_server/RAM-OSCServer_mac-v1_0_1.zip) (Mac OS 10.7+, 34.1MB)
- [RAM-OSCServer_win-v1_0_0.zip](https://raw.github.com/wiki/YCAMInterlab/RAMDanceToolkit/releases/osc_server/RAM-OSCServer_win-v1_0_0.zip) (Windows7+, 46.1MB)

### ソースコード

RAMDanceToolkit, OSCサーバーやその他ソースコード、 モーションデータ等の全てが入っています。
ご自身のプロジェクトの開発にお使いください。

- [RAM_Release_v1_0_1.zip](https://raw.github.com/wiki/YCAMInterlab/RAMDanceToolkit/releases/source_zip/RAM-release-v1_0_1.zip) (Mac OS 10.7+, Windows7+, OF0.7.4+, 117.6MB)

### サウンドファイル, モーションデータ

RAMDanceToolkitのリポジトリをcloneした場合に必要なファイルです。
上記のアプリケーション・ソースコードのzipファイルに含まれていますので、ダウンロードする必要はありません。

- [RAM-Sound_MotionData_v1_0_0.zip](https://raw.github.com/wiki/YCAMInterlab/RAMDanceToolkit/releases/resources/RAM-Sound_MotionData_v1_0_0.zip) (104.7MB)

<!--
### Other versions
Download links are available on [YCAM InterLab server]().
-->



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
    