# オカンネル~Mamanel~ / ハードウェア製作
## 1.駆動部のMeshとの連携
### MeshのGPIOタグとブレッドボードで回路を製作

* MeshのGPIOにプレッドボードで組んだLEDを光らせる回路を連動させ動作を確認

![GPIOTAG_TEST1](https://github.com/jphacks/KB_06/blob/deploy/Promotion/Images/Dev_Device/%E5%86%99%E7%9C%9F%202015-11-28%2014%2037%2059.jpg "Mamanel01")

![GPIOTAG_TEST2](https://github.com/jphacks/KB_06/blob/deploy/Promotion/Images/Dev_Device/%E5%86%99%E7%9C%9F%202015-11-28%2014%2038%2003.jpg "Mamanel02")

![GPIOTAG_TEST3](https://github.com/jphacks/KB_06/blob/deploy/Promotion/Images/Dev_Device/%E5%86%99%E7%9C%9F%202015-11-28%2014%2038%2010.jpg "Mamanel03")

### MeshのGPIOタグを使った回路でモーターを制御

* MeshのGPIOにプレッドボードとArduinoを組み合わせた回路を製作

![GPIOMOTOR_1](https://github.com/jphacks/KB_06/blob/deploy/Promotion/Images/Dev_Device/%E5%86%99%E7%9C%9F%202015-11-28%2016%2026%2027.jpg "Mamanel04")

![GPIOMOTOR_2](https://github.com/jphacks/KB_06/blob/deploy/Promotion/Images/Dev_Device/%E5%86%99%E7%9C%9F%202015-11-28%2016%2024%2039.jpg "Mamanel05")

![GPIOMOTOR_3](https://github.com/jphacks/KB_06/blob/deploy/Promotion/Images/Dev_Device/%E5%86%99%E7%9C%9F%202015-11-28%2016%2026%2052.jpg "Mamanel06")


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


* Meshのアプリケーションを使ってMotionタグと連携

![GPIOMOTOR_4](https://github.com/jphacks/KB_06/blob/deploy/Promotion/Images/Dev_Device/%E5%86%99%E7%9C%9F%202015-11-28%2016%2021%2031.png "Mamanel07")

![GPIOMOTOR_5](https://github.com/jphacks/KB_06/blob/deploy/Promotion/Images/Dev_Device/%E5%86%99%E7%9C%9F%202015-11-28%2016%2021%2037.png "Mamanel08")

![GPIOMOTOR_6](https://github.com/jphacks/KB_06/blob/deploy/Promotion/Images/Dev_Device/%E5%86%99%E7%9C%9F%202015-11-28%2016%2021%2057.png "Mamanel09")

![GPIOMOTOR_7](https://github.com/jphacks/KB_06/blob/deploy/Promotion/Images/Dev_Device/%E5%86%99%E7%9C%9F%202015-11-28%2016%2022%2004.png "Mamanel10")

![GPIOMOTOR_8](https://github.com/jphacks/KB_06/blob/deploy/Promotion/Images/Dev_Device/%E5%86%99%E7%9C%9F%202015-11-28%2016%2022%2014.png "Mamanel11")

![GPIOMOTOR_9](https://github.com/jphacks/KB_06/blob/deploy/Promotion/Images/Dev_Device/%E5%86%99%E7%9C%9F%202015-11-28%2016%2023%2053.png "Mamanel12")

## 2.ボディの製作
### MeshのタグとiPodTouchが入る「ファンネル」部分を製作

* 筒状のプラスチックで製作

![MESHBODY_1](https://github.com/jphacks/KB_06/blob/deploy/Promotion/Images/Dev_Device/DSC01637.jpg "Mamanel13")

![MESHBODY_2](https://github.com/jphacks/KB_06/blob/deploy/Promotion/Images/Dev_Device/DSC01638.jpg "Mamanel14")

![MESHBODY_3](https://github.com/jphacks/KB_06/blob/deploy/Promotion/Images/Dev_Device/DSC01639.jpg "Mamanel15")

![MESHBODY_4](https://github.com/jphacks/KB_06/blob/deploy/Promotion/Images/Dev_Device/DSC01640.JPG "Mamanel16")

* 塗装

![MESHBODY_5](https://github.com/jphacks/KB_06/blob/deploy/Promotion/Images/Dev_Device/DSC01643.JPG "Mamanel17")

### 「ファンネル」を浮かせるための部分を製作

* ボックス状のプラスチックで製作

![MESHBODY_6](https://github.com/jphacks/KB_06/blob/deploy/Promotion/Images/Dev_Device/DSC01634.jpg "Mamanel18")

