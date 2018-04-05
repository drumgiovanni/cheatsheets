#MongoDBチートシート
---
###**立ち上げ方法**

ターミナルを立ち上げ、

	mongo
と入力。



**db一覧参照方法**

	show dbs;
	
**db作成方法**

	use hoge;
	
**collection作成**

	db.createCollection('hogehoge');
	
**collection一覧参照**

	show collections;

**collectionリネーム**

	db.hogehoge.renameCollection('HOGE');

**db削除方法**

	db.dropDatabase();

**データ追加方法**

	db.hogehoge.insert(
なお、データ追加はpythonのディクショナリみたいな形で行う。
	
	{name: 'hiroki'}	
みたいな感じ。

**データ確認方法**

	db.hogehoge.find();

**データ抽出方法**
	
	db.hogehoge.find({},{_id: 0});
これで全件表示できる。

	db.hogehoge.find({score: {$gte: 50}});
これはscoreが50以上のデータを抽出している。

	db.hogehoge.distinct("team");

これはteamにどんな値があるのかを参照するコマンド。

*並べ替え*

	db.hogehoge.find({},{}).sort({なんちゃら});
	

**データの更新**

	db.hogehoge.update({name: "hiroki"}, {$set: {score: 80}});
これでhirokiというnameの値を持つデータのscoreを80に更新できる。


**データの削除**
	
	dd.hogehoge.remove({name: "hiroki"});
これでhirokiというnameを持つドキュメントの削除ができる。