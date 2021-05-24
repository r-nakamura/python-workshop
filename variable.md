# 変数
## Python におけるデータ型

Python では、以下のデータ型が存在する。

- ブール値
- 整数
- 不動小数点数
- 文字列

上記のデータ型は、ブール値を除いて、C 言語では以下の型に相当すると言え
る。

- 整数: `int`
- 不動小数点数: `double` や `float`
- 文字列: `char` や `char*`

ブール値は、`True` と `False` という 2 つの予約語により、真偽値を表す。

変数のデータ型は `type` 関数により確認することができる。

## 変数の宣言

Python では、変数の宣言を行うと同時に値を代入する。

```python
hoge = True
foo = 123
bar = 3.14
baz = 'string'
```

上述した `type` 関数を利用して、これらの変数のデータ型を確認しておこう。

```python
print(type(hoge)) # <class 'bool'>
print(type(foo))  # <class 'int'>
print(type(bar))  # <class 'float'>
print(type(baz))  # <class 'str'>
```

`None` を利用すれば、変数を宣言し、その後に変数に代入することができる。

```python
foo = None
foo = 123
```

## 変数の再代入

C 言語では型による制約が存在するため、変数にはその型に一致する値や変数
しか代入できないが、Python における変数の代入では、型による制約はない。

```python
hoge = True
print(hoge)
hoge = 123
print(hoge)
```

ただし、このような代入方法は、プログラムを保守する上では、非常にストレ
スフルとなる。なので、型による制約はないが、型の存在をある程度意識する
こと。

## 四則演算とべき乗

Python では、C 言語と同様に、四則演算とべき乗の演算子が用意されている。

```python
operand1 = 4
operand2 = 2

result = operand1 + operand2
print(f"{operand1} + {operand2} = {result}") # 4 + 2 = 6

result = operand1 - operand2
print(f"{operand1} - {operand2} = {result}") # 4 - 2 = 2

result = operand1 * operand2
print(f"{operand1} * {operand2} = {result}") # 4 * 2 = 8

result = operand1 / operand2
print(f"{operand1} / {operand2} = {result}") # 4 / 2 = 2.0

result = operand1 % operand2
print(f"{operand1} % {operand2} = {result}") # 4 % 2 = 0

result = operand1 ** operand2
print(f"{operand1} ** {operand2} = {result}") # 4 ** 2 = 16
```

上記の `print` 関数における書き方は、`f-String` と呼ばれる Python v3.6
以降において実装されている機能である。上記以外の書き方として、

```python
print(str(operand1) + " + " + str(operand2) + " = " + str(result))
print("{} + {} = {}".format(operand1, operand2, result))
```

が挙げられるが、特にこだわりがなければ、`f-String` の使用を勧める。

## 文字列連結

文字列を連結する場合には、加算の演算子である `+` と同様に、`+` を用い
る。

```python
str1 = 'Hello, '
str2 = 'World!'

result = str1 + str2
print(result) # Hello, World!
```

このため、数値を文字列として連結する場合には、`str` 関数により変数の型
を数値から文字列する必要がある。

```python
str1 = 1
str2 = 2

result = str1 + str2
print(result) # 3 <= 1 と 2 の和

result = str(str1) + str(str2)
print(result) # 12 <= '1' と '2' を連結
```

## 省略記法

Python では、ある変数の値と他の値の演算結果をその変数に直接代入するこ
とができる。

```python
val = 100
val += 10
print(val) # 110

val = 100
val -= 10
print(val) # 90

val = 100
val *= 10
print(val) # 1000

val = 100
val /= 10
print(val) # 10.0
```

ただし、Python では、C 言語のようなインクリメントやデクリメントの演算
子 (`val++` や `val--`) による記法はシンタックスエラーとなることに注意
すること。

## 練習問題: calc1.py

Python の四則演算を利用して、以下の値を求めよ。

- 1 + 2 + 3 + 4 + 5 + 6 + 7 + 8 + 9 + 10
- 100 - 200
- 1,000 円の品物を消費税 8% で買った時の税込価格
- 円周率を 3.14 とした時の、半径が 5 [m] である円の面積

## 練習問題: calc2.py

Python の四則演算を利用して、以下の値を求めよ。ただし、`pizza = 10` と
変数を宣言すること。

- 10 切れのピザを 5 人で分けた時の、一人当たりのピザの切数
- 10 切れのピザを 3 人で分けた時の、余ったピザの切数

