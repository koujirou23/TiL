## echo
```
<?php echo 5 + 7; ?> //5+7の結果が出力 → 12 
<?php echo "5 + 7"; ?> //5+7が文字列として出力 →5+7
```

## 変数
```
<?php
  $fruit = "りんご";
  echo $fruit;      //"りんご"が出力
?>

<?php
  $sum = 8 + 9;
  echo $sum;      //17が出力
?>
```

## 文字の連結
```
<?php
  $name = "taro";
  echo "こんにちは".$name;  //"こんにちはtaro"と出力
?>

.=　とすることで連結することも可能  
  
<?php
  $name = "taro";
  $name .= "こんにちは";
  echo $name;           //"taroこんにちは"と出力
?>
```

## 変数展開
```
<?php
  $name = "taro";
  echo "こんにちは、{$name}さん";   //"こんにちは、taroさん"と出力
?>
```

## if
```
<?php

$age = 20;
if ($age >= 30){
  echo "あなたは30歳以上です。";
}elseif ($age >= 20 && $age < 30){
  echo "あなたは20歳以上です。";
}else{
  echo "あなたは10代以下です。";
}

?>
```
#### 条件の否定(条件式のtrueとfalseが逆になる)
!を使えば式が真であれば偽に、偽であれば真になる
```
<?php

$num = 10;
if(!($num == 30)){
  echo "numは30ではない";  //$num==30ではない「偽」のため echoが出力される
}
```
