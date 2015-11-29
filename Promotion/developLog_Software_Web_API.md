# 神戸市のゴミ収集API for MESH
* [神戸市のごみの排出区分、排出曜日、住所地](http://www.city.kobe.lg.jp/information/opendata/catalogue.html) のオープンデータを使用した Web APIです．
* MESH において，その基本機能だけでは外部データと連携することはできません．
* そこで，[MESH SDK](https://meshprj.com/sdk/) というオリジナルのソフトウェアタグ (機能のようなもの) を作成できるサービスを使用すると，外部データとの連携が可能になります．
  * 開発環境は，JavaScript です．
  * ただし，MESH SDK では，外部のローカルデータを直接読み込んで…といったことはできません．外部データと連携するためには，Web API を構築する必要があります．
* この Web API は，MESH SDK の JavaScript 上からオープンデータを取得できるようにします．
* そのため，そのデータを使って MESH の振る舞いを変えることができるオリジナルソフトウェアタグを開発することが可能になります．
  * ___私たちは，オープンデータと連携することにより，MESHにさらに多くの可能性を持たせることができると考えています．___
* 今回開発した MESH アプリ向けのオリジナルソフトウェアタグなどについての詳細は[こちら](http://example.com)

# 使用技術
## 開発言語
* Python
* Flask (Webアプリケーションフレームワーク)
* MySQL-python (Python用MySQLアクセスモジュール)

## データベース
* MySQL
* データベースのテーブルスキーマは次の4カラムで構成される．
  * city ※市町村
    * varchar(128)
  * code ※番地
    * varchar(128)
  * yobi1 ※燃えるゴミの日週初め
    * varchar(30)
  * yobi2 ※燃えるゴミの日週終わり
    * varchar(30)

## サーバ環境
* [dotCloud](https://www.dotcloud.com/)

## APIソースコード
* Web アプリケーションフレームワーク Flask を用いた Web API です．

```python
# -*- coding: utf-8 -*-

import os
from flask import Flask, render_template
from datetime import datetime

import MySQLdb
import json

app = Flask(__name__)

cred_file = open(os.environ['CRED_FILE'])
creds = json.load(cred_file)

db_config = {
    'database': creds['MYSQLS']['MYSQLS_DATABASE'],
    'host': creds['MYSQLS']['MYSQLS_HOSTNAME'],
    'port': creds['MYSQLS']['MYSQLS_PORT'],
    'username': creds['MYSQLS']['MYSQLS_USERNAME'],
    'password': creds['MYSQLS']['MYSQLS_PASSWORD']
}

connection = MySQLdb.connect(host=db_config['host'], port=db_config['port'], db=db_config['database'], user=db_config['username'], passwd=db_config['password'], charset="utf8")

yobi = {
    "Monday": u"月",
    "Thuesday": u"火",
    "Wednesday": u"水",
    "Thursday": u"木",
    "Friday": u"金",
    "Saturday": u"土",
    "Sunday": u"日"
}
# now = datetime.now().strftime('%A')
now = "Thursday" # ハッカソンの発表用
cursor = connection.cursor()

@app.route('/', methods=['GET'])
def getDay():
    flag = False

    query = u'select * from kobe_gomi where city="雲井通" and code="7丁目"'
    # query = u'select * from kobe_gomi'
    cursor.execute(query.encode('utf-8'))
    result = cursor.fetchall()

    for row in result:
        if yobi[now] == row[2] or yobi[now] == row[3]:
            flag = True
            break

    if flag:
        # return json.dumps({"status": "OK", "discharge": yobi[now]})
        return yobi[now]
    else:
        # return json.dumps({"status": "ERROR", "message": "Can not get discharge date."})
        return "Error"


    cursor.close()
    connection.close()

app.debug = True
app.run(host='0.0.0.0', port=int(os.environ['PORT']))
''

## データベース内に格納しているデータ
* 今回使用しているデータは，神戸市のごみ排出曜日です．
  * その中でもお母さんが息子に呼びかけることが多いと考えられる「燃えるごみ」の日に着目し使用しています．
* 以下に，データベースに格納されているデータの一部の画像を掲載します．
[神戸市の燃えるごみの日](image url "神戸市の燃えるごみの日")

## Web API へのアクセスログ
* Web API へは，iPod touch上にインストールしたMESHアプリから___オリジナルソフトウェアタグ___を経由してアクセスしています．
* 以下に Web API へのアクセスログを掲載します．
[Web API へのアクセス](image url "Web API へのアクセス")
