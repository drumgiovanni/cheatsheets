# Herokuチートシート

pythonで構築したアプリをherokuでデプロイする際の手順をまとめます。

## 手順

1. localリポジトリの作成

	```
	git init

	```
	
1. requirements.txtに依存ライブラリを記述
	
	```
	pip freeze > requirements.txt
	```
	
1. runtime.txtに使用しているpythonのバージョンを指定

	```
	echo python-hoge.hoge.hoge > runtime.txt
	```
	
1. ProcfileにWebアプリ起動方法を指定（アプリ指導コマンド)

	よくあるやつ
	
	```
	echo web: gunicorn app:app --log-file=- > Procfile
	```
	
	今回shiftgeneratorで用いたやつ
	
	```
	echo web: python app.py --port=$PORT
	```
	
	なお、ポートがローカルとサーバで異なるとエラーが発生するので注意。今回はtornadoのoptionsを用いて回避した。
	
	```python
	from tornado.options import define, options
	
	define("port", default=8888, help="run on the given port", type=int)
	tornado.options.parse_command_line()
	
	# 〜〜〜（中略）〜〜〜
	
	if __name__ == '__main__':
    application.listen(options.port)
    tornado.ioloop.IOLoop.instance().start()
	```  
1. gitにcommit

	```
	git add -A
	git commit -m "initial commit"
	```
	  
1. Herokuにlogin
	
	```
	heroku login
	
	```
	メールアドレスとパスワードを聞かれるので入力し、ログイン。
	
1. Herokuにアプリを作成

	```
	heroku create hogehoge
	```
1.	Herokuにpush

	```
	git push heroku master
	```
	これでエラーがでなければデプロイ完了。
	
1. 	アプリ起動
	
	```
	heroku ps:scale web=1
	heroku open
	```
	
	これでアプリの画面が立ち上がるはず。
	エラーが発生したら
	
	```
	heroku logs
	```
	
	でログを確認しよう。