# 関数
## 関数の定義と呼び出し

他のプログラミング言語と同様に、Python では、関数を定義し、それを呼び
出すことができる。

```python
def hello():
    print("Hello, World")

hello()
```

関数を定義する場合には、`def 関数名(引数):` という風に記述する。また、
関数を呼び出す場合には、`関数名(引数)` という風に記述する。

C 言語とは異なり、返り値や引数の型を記述する必要はない。

## 関数の返り値

関数から値を返すには `return` を利用する。

```python
def func1():
    return 1

val = func1()
print(val) # 1
```

`return` において、カンマ (`,`) 区切りで値を記述することで、複数の値を
返すことができる。

```python
def func2():
    return 1, 2

val1, val2 = func2()
print(val1, val2) # 1 2
```

C 言語と同様に、`return` 以降の文が実行されることはない。

## 位置引数

Python では、**位置引数**と**キーワード引数**があるが、まず、位置引数
を説明する。

C 言語と同様に、位置引数では、先頭から順番に引数として処理されるように
引数を記述することができる。このため、下記の `func` では、1 番目の引数
`"first"` は `arg1` に格納され、2 番目の引数 `"second"` は `arg2` に格
納される。

```python
def func(arg1, arg2):
    print(arg1, arg2)

func1("first", "second")
```

## キーワード引数

一方、キーワード引数は、位置引数とは異なり、キーワードにより任意の位置
に引数を記述することができる。

```python
def func(arg1, arg2):
    print(arg1, arg2)

func(arg1="first", arg2="second")
func(arg2="second", arg1="first")
```

この場合、キーワードは関数宣言における変数名である。キーワード引数を利
用すれば、順序に関係なく、値を引数として関数に渡すことができる。

## 引数のデフォルト値

関数における引数には**デフォルト値**を設定することができる。これにより、
引数に値が与えられない場合は、デフォルト値が自動的に使用される。

```python
def func(arg1="hoge", arg2="foo"):
    print(arg1, arg2)

func() # hoge foo
func(arg2="second") # hoge second
func(arg1="first", arg2="second") # first second
```

## 練習問題: calc.py

以下の関数を実装せよ。ただし、これらの関数が正しく実装できているか (与
えた 2 つの引数に対して、正しい値を返すか) を確認するコードも記述せよ。

- add: 2 つの引数の和 (足し算) を計算する
- min: 2 つの引数の差 (引き算) を計算する
- mul: 2 つの引数の積 (掛け算) を計算する
- div: 2 つの引数の商 (割り算) を計算する
