#node.jsチートシート
##ノンブロッキングな書き方
処理に時間がかかりそうなコマンドは次の命令をブロックしないようにしないといけない。そのためには、時間がかかりそうな処理は**コールバック関数**で処理するようにする。

```javascript
setTimeout(function() {
	console.log("hello");
}, 1000);
console.log("world");
```

##サーバを建てる

とりあえず覚えるしかないかな。
200はhttpのステータスコード（
うまくいったよという意味）。
200の後に書いている`Content-Type`は、これから渡すコンテンツのタイプを入力。`html`とか`ejs`とか。

```javascript
var server = http.createServer();
server.on('request', function(req, res){
	res.writeHead(200, {'Content-Type': 'text/plain'});
	res.end();
});
server.listen(1337, '192.168.0.15');
console.log("server listening . . .");
```



##モジュールの作り方

```javascript
export.message = "Hello jscafe";
```

`export`でモジュールを作成し、別ファイルで`require`することで使用することができる。


```javascript
var hoge = require('./上のファイル名');  //この時ファイル名に.jsは付けなくて良い。
cosole.log(hoge.message);  
```



