# オカンネル~Mamanel~
![OkannelLogo](http://github.com/jphacks/KB_06/blob/Images/Presentation/Mananel_slide_1.png)
## 製品概要
### 背景
* 朝の親子間のやり取りで生まれるストレスを軽減する新しいコミュニケーションツール
![Okannelpresentation1](http://github.com/jphacks/KB_06/blob/Images/Presentation/Mananel_slide_2.png)

   毎朝、お母さんは忙しいです。家事をこなす中でも、子供のことを気にかけて、いろんなことに口出ししてしまうからです。

   例えば、お母さんは「弁当持った？」「傘持った？」と出かける子供に対して言います。それを伝えるときに、大声で怒鳴ったり、お節介なことをついつい言ってしまうことが日常になってしまっています。

   お母さんはあくまでも子供のことを思ってのことですが、子供からしたら、うざったく、返事をする気が失せてしまいます。

   子供に大きい声で怒鳴らないといけないお母さんも、お母さんに怒鳴られてしまう子供も、決していい気分にはなれません。むしろストレスがたまっていく一方です。

   そんな朝のストレスをなくすために私たちは、新しいコミュニケーションツールを開発しました。

### 製品説明
![Okannelpresentation2](http://github.com/jphacks/KB_06/blob/Images/Presentation/Mananel_slide_3.png)
   「オカンネル」はSonyMeshを搭載した浮遊型デバイスです。

   お母さんは言っておかないといけないことを予めオカンネルに入力しておくことができます。

   そして家事に忙しい最中でも手をかざしたり音をならすと、

   お母さんの代わりに「オカンネル」が子供に近づきお母さんが伝えたいことを伝えてくれます。

   メッセージをもらった子供は、お母さんと同じように「オカンネル」に手をかざしたり音を出して返事をすることができて、

   メッセージを無事伝えられた「オカンネル」はちゃんとお母さんのもとに戻ってくれます。

   天気情報やゴミ収集日などの地域のオープンデータを元に、

   普段、「今日寒いから上着持って行き」「燃えるごみ出しといて」などのメッセージを子供に届けてくれます。

### 製品の使用例
![Okannelpresentation3](http://github.com/jphacks/KB_06/blob/Images/Presentation/Mananel_slide_4.png)
![Okannelpresentation4](http://github.com/jphacks/KB_06/blob/Images/Presentation/Mananel_slide_5.png)
![Okannelpresentation5](http://github.com/jphacks/KB_06/blob/Images/Presentation/Mananel_slide_6.png)
![Okannelpresentation6](http://github.com/jphacks/KB_06/blob/Images/Presentation/Mananel_slide_7.png)

### 特長
####1. 伝えたい事をちゃんと伝えられる
   * 大声をあげることなく、メッセージをちゃんと伝えられます。
   * リアルタイムの情報や、オープンデータを使って伝えたいことをもっとたくさん伝えられます。

####2. 簡単に伝えられる
   * どんなに忙しい時でも簡単なモーションで使えます。
   * 家のどこでも伝えられます。

####3. 簡単に返信できる
   * 手をかざしたり、音をならすだけで伝えられたメッセージの返信をすることができます。

####4. 確実に返信してもらう事ができる
   * メッセージを返信するまで「オカンネル」が追いかけてくるので、LINEなどのメッセンジャーを使った場合に起こりうる「既読スル」ーを防止できます。

####5. オープンデータを元にメッセージを選んでくれる
   * サーバからオープンデータを参照し、状況にあったメッセージを伝えることができます。

### 解決出来ること
   * 朝忙しい時間帯などに、親子同士のコミュニケーションのストレスが軽減できる。

### 今後の展望
   * 作成したAPIにより、あらゆるオープンデータをデータベースに取り込むことで、機能を拡張することができる。
   * 「オカンネル」から受け取った情報をデータベースに取り入れることで、「オカンネル」の動向や使用頻度などを元にあらゆる分析が可能になる。

### 注力したこと（こだわり等）
   * 「ファンネル」の再現

      ガンダムシリーズで登場するファンネルという浮遊型兵器の動きを再現すること。

   * MESHでオープンデータを活用するための工夫

      MESH単体ではオープンデータの処理が難しいため、独自でサーバーを作成しオープンデータが活用できるように工夫したこと。
   
![Okannelpresentation7](http://github.com/jphacks/KB_06/blob/Images/Presentation/Mananel_slide_8.png)

## 開発技術
### 活用した技術
#### API・データ
   * [神戸市オープンデータ(ゴミ収集日)](http://www.city.kobe.lg.jp/information/opendata/catalogue.html)
   * [MESH SDK](https://meshprj.com/sdk/) 

#### フレームワーク・ライブラリ・モジュール
   * [dotCloud](https://www.dotcloud.com/)
   * [Flask](http://flask.pocoo.org/)

#### デバイス
   * Sony Mesh
   * iPodTouch
   * Arduino

### 独自技術
#### ハッカソンで開発した独自機能・技術
   * [Meshとオープンデータとの連携](/Promotion/developLog_Software_Web_API.md)

   https://github.com/jphacks/KB_06/blob/edit_README.md/Promotion/Images/Presentation/Mananel_slide_1.png