## Javaの命名規則
#### クラス名は先頭を大文字に
```
SampleApp
```
#### メソッド名・変数名の先頭は小文字  メソッド名は動詞+名詞
```
getValue
```
#### 定数名はすべて大文字
```
FLAG_ON
```

## Javaの文字出力方法
Javaはコードの最後にセミコロン(;)が必要(数値の場合""はいらない)  
```
System.out.println("Hello World"); 
```

## Javaの計算

``
System.out.println( 5 + 3 );  
``

## 文字の連結

```
System.out.println("Hello" + "World"); 
```

## 変数の定義
数値

```
int number = 3;   
System.out.println(number);
```
文字列

```
String name = "Taro";  
System.out.println(name);
```
※代入の時は変数名のみ
```
name = "Satoshi";   
number = 3;
```

※少数をあつかうとき
```
double number = 3.0;
```

## 自動型変換
文字と数値を組み合わせる時
```
System.out.println("私は"+25+"歳です");
"私は"+ "25"+ "歳ですとString型に自動変換され文字列の結合が行われる。
```

int型とdouble型の計算の場合
```
System.out.println(5/2);      →　2と出力(int型)    
System.out.println(5.0/2.0);  →　2.5と出力(double型)    
System.out.println(5.0/2);    →  2.5と出力(double型に変換される)  
```

int型同士の計算
```
int number1 = 7;
int number2 = 2;
System.out.println(number1 / number2);
```
上記だと3が出力

```
System.out.println((double)number1/number2);
```
とすることでdouble型に変換され3.5と出力
(double)number1とすることでint型からdouble型へ変換。
片方がdouble型であればint型はdouble型へ自動変換されるため、(double)は１つ


## 論旨演算子
じゃないのとき(!)  
()が必要
```
!(x > 5)

if (!((i % 2 == 0) && (i % 3 == 0))) {
				System.out.println(2と3の公倍数ではありません);
			}
```

### 条件分岐
##### if 
```
if(条件式){  
  処理;
 }else if(条件式){
  処理;
 }else{  
  処理;  
 }
 ```
 
 ##### switch
 switch文では(条件の値)とcaseの値が等しい(==)のとき処理が実行される　　
 ```
 switch(x % 2){
  case 0: //コロンが必要  
    System.out.println("偶数です");
    break; //breakが無いと次のcase処理を実行してしまう
  case 1:
    System.out.println("奇数です");
    break;
  default:  
    System.out.println("無効な数字です"); //例
    break;
 }
 ```
 どのcaseとも一致しないときに実行する処理  
 default(if文でいうelse)
 
 
