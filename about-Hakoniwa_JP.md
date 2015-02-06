## 箱庭に関して

箱庭はRAMDanceToolkitのシーンを物理世界にまで拡張した物です。モーターや電磁石、ファンなどのアクチュエーターをダンサーの動きに連動させて動かし、観測データをダンサーに伝える事で、現実の世界での様々な現象を組み合わせ、ダンサーの環境の一部として利用します。

箱庭の例として：

- ServoPendulum
二重振り子をサーボモーターに取り付け、揺らします。ダンサーは選択された部位の間の距離でサーボモーターが揺れる周期をコントロールする事が出来ます。

*movie link

- MagnetPendulum
磁石の振り子を天井から吊るし、振り子の下に電磁石を配置します。ダンサーは選択した部位の間の距離で、電磁石の入切をコントロールし、吊るされた磁石の動きに影響を与える事ができます。

*movie link

- Tornado
箱の中で超音波の霧発生装置を用いて水蒸気を発生させ、天井に取り付けたファンで竜巻を発生させます。ダンサーは選択された3点が作る円の大きさで竜巻の発生をコントロールする事が出来ます。

*movie link


### システム図

*画像で差し替え

RDTK    -----> Arduino -----> Hakoniwa
machine	<-----         <-----    ↓
        <--------------------- Camera



### HakoniwaとHakoVizに関して

HakoniwaとHakoVizのサンプルプロジェクトとしてRAM-root/examples/の中に

example_Hakoniwa_HakoVis_MagPendulum
example_Hakoniwa_HakoVis_ServoPendulum

の2つがあり、それぞれの中にはOSX/Windowsの開発環境で使用するプロジェクトと、Arduinoのソースコード、動作させるための回路図が入っています。

RAMDanceToolkitでは1つの箱庭の連動に対して2つのシーンを想定しています。
1つめは箱庭をコントロールするためのシーンです。これをHakoniwa（ハコニワ）と呼んでいます。モーションデータを解析し、特定の動作や身体の動きのパラメータを使って箱庭を動作させます。サンプルプロジェクトでは、ここで箱庭を動かす条件が分かりやすくなるようなビジュアルを画面に表示しています。

2つめは箱庭の画像解析結果を受けて、もしくは箱庭に取り付けたセンサーからの値をArduinoを介して取得し、そのデータをさらにビジュアル化するものです。これをHakoviz（ハコビズ）と呼んでいます。どのような箱庭か、また使用方法にもよりますが、このHakovizは必ず使わなければ成立しないという物ではありません。


### カメラでの観測とセンサーでの観測
箱庭からのデータの取得方法として、カメラを使用する方法と、それ以外のセンサーを用いて観測を行う方法があります。Appsフォルダに入っているCameraUnitはカメラを用いて箱庭の状況を観測するためのソフトウェアです。使用方法に関してはram-root/apps/CameraUnit/readme_jp.mdを参照してください。

センサーでの観測データはArduinoで取得し、OSCを使ってRAMDanceToolkitの起動しているコンピュータに送信します。ポートはモーションデータを受信している、ramInitialize(int port)で指定したポートを使用できます。ramOscReceiveTagを使用して、アドレスごとに振り分けられたOSCメッセージを各シーンで受信することができます。

例えば、

.hファイル

    ramOscReceiveTag mReceiver;

.cppファイルのsetup()内

    ramOscManager::instance().addReceiverTag(&mReceiver);
    mReceiver.addAddress("/dp/cameraUnit/MagPendulum/contour/boundingRect");

とすることで、"/dp/cameraUnit/MagPendulum/contour/boundingRect"というアドレスを持ったメッセージをこのシーンで受け取る事ができます。

実際にサンプルプロジェクトを開き、HakoVizのソースコードで実装されていますので参考にしてみてください。
