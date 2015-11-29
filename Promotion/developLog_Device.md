# オカンネル~Mamanel~ / ハードウェア製作
## 1.駆動部のMESHとの連携
### MESHのGPIOタグとブレッドボードで回路を製作

* MESHのGPIOタグにブレッドボードで組んだLEDを光らせる回路を連動させ動作を確認

![GPIOTAG_TEST1](/Promotion/Images/Dev_Device/%E5%86%99%E7%9C%9F%202015-11-28%2014%2037%2059.jpg "Mamanel01")

![GPIOTAG_TEST2](/Promotion/Images/Dev_Device/%E5%86%99%E7%9C%9F%202015-11-28%2014%2038%2003.jpg "Mamanel02")

![GPIOTAG_TEST3](/Promotion/Images/Dev_Device/%E5%86%99%E7%9C%9F%202015-11-28%2014%2038%2010.jpg "Mamanel03")

### DCモーターの動作を確認
* DCモーターの回転を制御するコードを書いて動作を確認

```Arduino:motor_sample.ino
// サンプルコード
// 出力ピンの定義
const int motor1A = 7;
const int motor1B = 8;
const int motor1P = 9;

// 初期設定
void setup(){
pinMode(motor1A,OUTPUT); // 信号用ピン
pinMode(motor1B,OUTPUT); // 信号用ピン
}

// 繰り返し
void loop(){
// 回転
digitalWrite(motor1A,HIGH);
digitalWrite(motor1B,LOW);
analogWrite(motor1P,100);
delay(2000);
// 静止
digitalWrite(motor1A,LOW);
digitalWrite(motor1B,LOW);
delay(2000);

}
```


### MESHのGPIOタグを使った回路でDCモーターを制御
* MESHのGPIOタグにブレッドボードとArduinoを組み合わせた回路を製作

![GPIOMOTOR_1](/Promotion/Images/Dev_Device/%E5%86%99%E7%9C%9F%202015-11-28%2016%2026%2027.jpg "Mamanel04")

![GPIOMOTOR_2](/Promotion/Images/Dev_Device/%E5%86%99%E7%9C%9F%202015-11-28%2016%2024%2039.jpg "Mamanel05")

![GPIOMOTOR_3](/Promotion/Images/Dev_Device/%E5%86%99%E7%9C%9F%202015-11-28%2016%2026%2052.jpg "Mamanel06")

*　回路図

![GPIOFRITZING_1](/Promotion/Images/Dev_Device/MESH_回路.png)


##MESHのアプリケーション上でMESH同士を制御
* MESHのアプリケーションを使ってGPIOタグとMotionタグとBrightnessタグを連携

![GPIOMOTOR_4](/Promotion/Images/Dev_Device/%E5%86%99%E7%9C%9F%202015-11-28%2016%2021%2031.png "Mamanel07")

![GPIOMOTOR_5](/Promotion/Images/Dev_Device/%E5%86%99%E7%9C%9F%202015-11-28%2016%2021%2037.png "Mamanel08")

![GPIOMOTOR_6](/Promotion/Images/Dev_Device/%E5%86%99%E7%9C%9F%202015-11-28%2016%2021%2057.png "Mamanel09")

![GPIOMOTOR_7](/Promotion/Images/Dev_Device/%E5%86%99%E7%9C%9F%202015-11-28%2016%2022%2004.png "Mamanel10")

![GPIOMOTOR_8](/Promotion/Images/Dev_Device/%E5%86%99%E7%9C%9F%202015-11-28%2016%2022%2014.png "Mamanel11")

![GPIOMOTOR_9](/Promotion/Images/Dev_Device/%E5%86%99%E7%9C%9F%202015-11-28%2016%2023%2053.png "Mamanel12")

## 2.ボディの製作
###デザインの経緯
　　　* ファンネルというからには浮遊させたい

　　　* ファンネル数機が使用者の周りを浮遊するイメージでスタート

![DESIGN_1](/Promotion/Images/Dev_Device/IMG_20151130_0001.jpg "Design1")

　　　* 使用者の腰にアーチを着ける案も出たが、前進させる方向にシフト
　　　* 尖った形状のものが多かったが、往復のためシンメトリーに

![DESIGN_2](/Promotion/Images/Dev_Device/IMG_20151130_0002.jpg "Design2")

　　　* 買い揃えられるものや、製作難度を加味し、形状よりも表面のデザインに注力する方向へ

![DESIGN_3](/Promotion/Images/Dev_Device/IMG_20151130_0003.jpg "Design3")

### 制作部分のこだわり
* シンメトリーな形状

   前進と後退が可能な特性を活かすために、前後どちらの向きで進んでも違和感が生じない形状を採用

* 赤・青・白・銀を基調にしたカラー

   宇宙船やロケットのような色を使い、近未来的な模様でファンネルを思わせる雰囲気を演出。銀シールを絵具で塗り、パーツパーツを丁寧に切り貼りし、細部にも装飾を施した

* プラスチックやアクリルの材質
   硬さと透明感を両立するためにプラスチックやアクリルの材質を使用
   特に支柱は、ファンネルを支える強度と、あくまで浮いているように見える透明さの両立を簡単な素材で可能にするため、接着方法と素材を厳選した


### MESHのタグとiPodTouchが入る「ファンネル」部分を製作

   * 筒状のプラスチックで製作

![MESHBODY_1](/Promotion/Images/Dev_Device/DSC01637.JPG "Mamanel13")

![MESHBODY_2](/Promotion/Images/Dev_Device/DSC01638.JPG "Mamanel14")

![MESHBODY_3](/Promotion/Images/Dev_Device/DSC01639.JPG "Mamanel15")

![MESHBODY_4](/Promotion/Images/Dev_Device/DSC01640.JPG "Mamanel16")

* 塗装

![MESHBODY_5](/Promotion/Images/Dev_Device/DSC01643.JPG "Mamanel17")

### 「ファンネル」を浮かせるための部分を製作

   * ボックス状のプラスチックで製作

![MESHBODY_6](/Promotion/Images/Dev_Device/DSC01634.JPG "Mamanel18")

##　3. 駆動部の製作
   * 使用したパーツの情報
      [タミヤ タンク工作基本セット](http://www.tamiya.com/japan/products/70108tracked_vehicle/)
      [東芝セミコンダクターモータードライバー](http://akizukidenshi.com/catalog/g/gI-02001/)
   ** タンク工作キットを改造し、モータドライバーを用いてモータの回転の方向を前後制御できるようにした