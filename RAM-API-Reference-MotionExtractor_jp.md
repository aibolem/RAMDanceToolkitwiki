# ramMotionExtractor

　ramMotionExtractorは、RAMDanceToolKitのシーンにおけるノード選択の支援クラスです。シーン作成の際にこのクラスを使用することで、ツールキット実行中にスムーズなノードの切り替えが行えます。

## 実装
実装する際には、ramBaseScene継承クラス内でインスタンスを保持し、**3つのメソッド**を呼ぶ必要があります。以下はRAMDanceToolKitのサンプル**example-ramMotionExtractor**からの抜粋です。
~~~
void ramMotionExtractorExampleScene::setupControlPanel(){
	
	/*=== register ===*/
	motionExtractor.setupControlPanel(this);
	
}

void ramMotionExtractorExampleScene::update(){

	/*=== update ===*/
	motionExtractor.update();

}

void ramMotionExtractorExampleScene::draw(){

	ramBeginCamera();
	
	/*=== Preview selected nodes ===*/
	motionExtractor.draw();
	
	ramEndCamera();
	
}
~~~

## 使用
ramMotionExtractorを実装したシーンを実行すると、パネルの右側にmotionExtractor用のUIが追加されます。

[[/Images/API-motionExtractor/pic-preview.png]]

### ノードの追加
　選択したいノードをクリックすると、クリックしたノード上に赤い円が表示されます。円が表示されているのを確認したら、**PushPortボタン**を押して、ノードをMotionExtractorに登録してください。登録が成功すると、選択したノードにワイヤーのボックスとXYZ軸が表示されます。追加されたボックスは”ポート”と呼びます。
　
### ノードの削除
追加したポートを削除したい場合、追加時と同じように対象のノードをクリックした後、**PopPortボタン**を押してノードを削除します。

全てのポートを削除したい場合は、Clearボタンを押して全てを削除します。
### 情報の保存及び読み込み
保存はSaveボタン、読み込みはLoadボタンで実行することができます。
デフォルトでは**motionExt_シーン名.xml**という名前で保存されますが、プログラム内で**ramMotionExtractor::Save(string file)**及び**ramMotionExtractor::Load(string file)**を実行する事で任意のファイル名で保存することができます。


## シーンとの連携
GUI上で追加したポートをプログラムと連携させるためには、以下のような方法で可能です。
### 例：選択した3点で三角形を描く

	ofVec3f vec_a = motionExtractor.getPositionAt(0);
	ofVec3f vec_b = motionExtractor.getPositionAt(1);
	ofVec3f vec_c = motionExtractor.getPositionAt(2);

	ofSetLineWidth(3.0);
	ofNoFill();
	ofTriangle(vec_a, vec_b, vec_c);
	ofFill();
	ofSetLineWidth(1.0);

[[/Images/API-motionExtractor/pic-triangle.png]]

**ramMotionExtractor::getPositionAtメソッド**では、選択したノードの位置座標が取得できます。
ノードがどこにも選択されていない場合、原点(0,0,0)が値として返されます。

主なゲッター(情報を取得するためのメソッド)は以下の通りです。

	int				getNumPort();　/* 選択されているノードの総数 */
	bool			getIsExist(int port); /*指定のポートが選択されているかどうか*/

	ramNode			getNodeAt(int port); /*指定したポートのramNodeデータ*/
	string			getActorNameAt(int port);/*指定したポートを持つアクターの名前*/
	string			getJointNameAt(int port);/*指定したポートの関節の名前*/
	int				getJointIdAt(int port);/*指定したポートのジョイントID*/

	ofVec3f			getPositionAt(int port,bool fixPosition = false);/*指定したポートのグローバル座標*/
	ofQuaternion	getRotationAt(int port);/*指定したポートの回転角度*/

	ofVec3f			getVelocityAt(int port);/*指定したポートの速度ベクトル*/
	float			getVelocitySpeedAt(int port);/*指定したポートの速度ベクトルの長さ*/
	ofQuaternion	getRotateVelocityAt(int port);/*指定したポートの回転速度*/
	float			getDistanceAt(int port_A, int port_B);/*指定した2ポート間の距離*/
	float			getAreaAt(int port_A, int port_B, int port_C);/*指定した3ポートが作る三角形の面積*/
