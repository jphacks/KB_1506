# MESH オリジナルソフトウェタグ
* MESH アプリ上で動作するオリジナルのソフトウェアタグを開発しました．
  * 開発には [MESH SDK](https://meshprj.com/sdk/) を使用しています．
  * マニュアルは [こちら](https://meshprj.com/sdk/doc/)
* 開発したソフトウェアタグは，[こちら](/Promotion/developLog_Software_Web_API.md) の Web API から取得できるオープンデータによって，その後の振る舞いを変更することができます．

# 実装したソフトウェアタグのソースコード
* ソフトウェアタグを開発するプロセスは，Initialize, Receive, Execute, Result となっています．
* この各プロセスをプログラミングすることで，オリジナルのソフトウェアタグを開発することができます．
* また，別のタグからのデータの受け取り (Input) や，結果別の振る舞いの分岐(Output)などを行うことができます．
* 以下に，実装したソフトウェアタグの Input と Output, およびソースコードを掲載します．

## Input および Output
![タグの Input と Output](/Promotion/Images/Dev_Software/mesh%20originaltag_input_output.png "タグの Input と Output")


## Initialize
```javascript
return {
	runtimeValues : {
		outputIndex : 0
	},
	resultType : "continue"
};
```

## Receive
* 今回，Receive 部分は実装していません．

## Execute
```javascript
var apiURL = "https://okanneru.dotcloudapp.com/";

ajax ({
	url : apiURL,
	type : "get",
	timeout : 5000,
	success : function ( contents ) {
		log(contents);

		switch(contents) {
			case "月":
				runtimeValues.outputIndex = 0;
				break;
			case "火":
				runtimeValues.outputIndex = 1;
				break;
			case "水":
				runtimeValues.outputIndex = 2;
				break;
			case "木":
				runtimeValues.outputIndex = 3;
				break;
			case "金":
				runtimeValues.outputIndex = 4;
				break;
			case "土":
				runtimeValues.outputIndex = 5;
				break;
			case "日":
				runtimeValues.outputIndex = 6;
				break;
			default:
				runtimeValues.outputIndex = -1;
				break;
		}

		callbackSuccess( {
			resultType : "continue",
			runtimeValues : runtimeValues
		} );
	},
	error : function ( request, errorMessage ) {
		log("Day : Network error");
		runtimeValues.outputIndex = -1;

		callbackSuccess( {
			resultType : "continue",
			runtimeValues : runtimeValues
		} );
	}
});

return {
	resultType : "pause"
};
```

## Result
```javascript
return {
	indexes : [ runtimeValues.outputIndex ],
	resultType : "continue"
};
```
