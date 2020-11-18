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
