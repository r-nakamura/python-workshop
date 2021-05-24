# if/elif/else による条件分岐
## if による条件比較

`if` と `else` による、単純な条件分岐は下記のように書くことができる。

```python
if True:
    print('True') # True
else:
    print('False')
```

`if` の後には、**条件**を記述する。この条件が真である場合には、`if` のブロッ
クに含まれるコードが実行される。

```python
if False:
    print('True')
else:
    print('False') # False
```

一方、この条件が偽である場合には、`else` のブロックに含まれるコードが
実行される。

## 条件比較

条件には、変数だけでなく、比較演算子を利用した条件文を記述することがで
きる。

例えば、値の比較を行うためには、以下のように記述する。

```python
val = 1
if val == 1:
    print('val: 1') # val: 1
else:
    print('val: unknown')
```

## 比較演算子

Python では、以下の比較演算子が定義されている。

```python
== # 等しい
!= # 等しくない

< # り小さい
> # より大きい

<= # 以下
>= # 以上
```

文字列が等しいかどうかを比較する時も、`==` や `!=` を利用する。

```python
astr = 'hoge'
if astr == 'hoge':
    print('hoge') # hoge
```

C 言語において、文字列が等しいかどうかを照合する場合には、`strcmp()`
を利用するが、Python では上記のように書けばよい。

## in を利用したリストや辞書における要素の確認

リストや辞書における説明では述べなかったが、`if` と `in` を組み合わせ
ることにより、リストや辞書において、特定の要素が含まれているかどうかを
確認することができる。

```python
alist = ['Alice', 'Bob', 'Chris']
if 'Alice' in alist:
    print('Alice') # Alice

adict = {
    'name': 'dummy',
    'age': 20,
}
if 'age' in adict: # キーが存在するかどうかを確認
    print('age:', adict['age']) # age: 20

if 'dummy' in adict:
    pass
else:
    print('not exist') # not exist
```

辞書の場合は、値ではなくキーが当該の辞書に含まれているかどうかを確認す
ることができる。

ここで、`pass` は「何も実行しない」ことを表す。

## ブール演算子

ブール演算子である `and` (かつ)、`or` (または) を利用して、条件式を組
み合わせることができる。

例えば、「ある値が 1 以上であり、5 以下であるかどうか」のような条件は、
`and` を用いて以下のように記述できる。

```python
x = 3
if 1 <= x and x <= 5:
    print("1 <= x <= 5")
```

ただし、一つの変数に対する比較を行う場合は、以下のように書くこともでき
る。
```python
x = 3
if 1 <= x <= 5:
    print("1 <= x <= 5")
```

また、「ある値が 1 以下であるか、もしくは、5 以上であるか」という条件
は、`or` を用いて以下のように記述できる。

```python
x = 3
if x <= 1 or 5 <= x:
    print("x <= 1 or 5 <= x")
```

もう一つのブール演算子である `not` の説明は後述する。

## Python における真偽値

Python では、`True` と `False` 以外にも、例えば、下記のデータは
`False` とみなされる。

  - `False`
  - `None`
  - ゼロ: `0` や `0.0`
  - 空文字列: `''`
  - 空リスト: `[]`

このため、変数が空でないかどうかは以下のように確認することができる。

```python
alist = []
if alist:
    print("list is not empty.")
else:
    print("list is empty.")
```

さらに、`not` を利用すれば、「変数が空である場合には、...」というロジッ
クを以下のように書くことができる。

```python
alist = []
if not alist:
    print("list is empty.")
else:
    print("list is not empty.")
```

変数を初期化する処理は上記のような手順で書くことが多い。

また、`not` と `in` を組み合わせることで、例えば、辞書における特定のキー
に対する値の初期化もできる。

```python
adict = {}
if not 'key' in adict:
    adict['key'] = {}
```

## 複数の条件分岐

ここまでは `if` と `else` による 2 通りの条件分岐を紹介したが、以降で
は、`if` と `elif` と `else` を利用した複数の条件分岐を説明する。複数
の条件分岐を書くには、C 言語では `else if` を利用するが、Python では
`elif` を利用する。

```python
val = 1
if val == 1:
    print('1')
elif val == 2:
    print('2')
elif val == 3:
    print('3')
else:
    print('unknown')
```

構文こそは異なるが、動作は C 言語における `if` や `else if` を利用した
条件分岐と同様である。

ちなみに、Python では、C 言語における `switch` は存在しない。

## 練習問題: fizzbuzz.py

以下の規則に従い、ある任意の自然数に対応する出力を表示せよ。規則は下記
の通りである。

- ある自然数が 3 で割り切れるなら Fizz と表示する
- ある自然数が 5 で割り切れるなら Buzz と表示する
- ある自然数が 3 でも 5 でも割り切れるなら FizzBuzz と表示する
- ある自然数が 3 でも 5 でも割り切れないならその数を表示する
