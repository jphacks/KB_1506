# 神戸市のゴミ収集API for MESH
* [神戸市のごみの排出区分、排出曜日、住所地](http://www.city.kobe.lg.jp/information/opendata/catalogue.html) のオープンデータを使用したAPIです．

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

    print "test"

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
'''
