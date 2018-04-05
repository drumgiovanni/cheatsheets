***Jqueryチートシート***
---
**基本**

	$('idなりclassなり').メソッド();	
最後にセミコロン忘れないように注意。


<br></br>
**よく使うメソッド**

**clickメソッド*
		
	$('idなりclassなり').click(function(){処理});
		
<br></br>
**hoverメソッド*

	$('idなりclassなり').hover(function(){カーソルを乗せたときの処理}, function(){カーソルを外した時の処理});
		
<br></br>

**animateメソッド*

hoverメソッドと組み合わせることが多い。

	$('idなりclassなり').hover(function(){
	  $(this).animated({'font-sizeとか':'どう変化させたいのか'}, アニメーションの表示速度300とかslowとか);
	  }, function(){
	  上に同じ}, なんちゃら);
	  
clickメソッドと合わせた場合↓
	
	$('').click(function(){
   		$('html, body').animate({
    	'scrollTop':0}, 500);
    	
<br></br>

**offsetメソッド*
