# expressチートシート



##基本の使い方
最初にexpressモジュールを読み込む

```javascript
var express = require('express');
	app = express();
```

パラメータと同じファイル名を表示する用にする（middleware）

```javascript
app.use(express.static(__dirname + '/public'));
```

パラメータを取得し、処理を変える

- テキストを表示
    
    ```javascript
    app.get('/url名', function(req, res) {
    	res.send('表示したいテキスト');
    });
    ```
    
- ファイルの中身を表示

    ```javascript
    app.get('/url名', function(req, res) {
    	res.sendfile(__dirname + '表示したいファイル名');
    });
    ```

- パラメータの値で出力を変える（app.paramを使用）

    ```javascript
    app.param('id', function(req, res, next, id){
  	var users = ['taguchi', 'fkoji', 'dotinstall'];
  	req.params.name = users[id];
  	next();
	});
	```

    これをapp.getとres.sendを用いて出力することでパラメータの値で出力を変化させることができる。
    
##実践編  
        
###nodemonを使う  
これでいちいちサーバを再起動しなくて済むようになる。

```
nodemon hoge.js
```


###ejsを使う（テンプレートエンジン）

```
npm install ejs
```

```javascript
//最初に設定してあげる
app.set('views', __dirname + '/views');
app.set('view engine', 'ejs');
//urlに応じてejsを表示するためにはrenderを使う
app.get('/', function(req, res) {
	res.render('index'); //これでindex.ejsの内容を表示する
});
```
値を埋め込む

```javascript
app.get('/', function(req, res) {
  res.render('index', {title: 'title'});
});
```
↑このようにオブジェクトにして値を渡す


