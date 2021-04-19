# for や while による繰り返し
## for による繰り返し

Python では、`for` を利用することにより、シーケンスに対して繰り返し処
理を行うことができる。シーケンスは iterable なオブジェクトを差す。以下
では、シーケンスの典型的な例であるリストを用いて、`for` の使い方を説明
する。

```python
alist = ['Alice', 'Bob', 'Chris']
for name in alist:
    print(name)

# Alice
# Bob
# Chris
```

for による繰り返しを行う場合には、`for 変数名 in リスト` という風に書
く。for のブロック内において、宣言した変数にリストの値が一時的に格納さ
れる。

## enumerate 

リストを走査する時に、要素番号を一緒に取得する場合には、`enumerate` 関
数を利用する。

```python
alist = ['Alice', 'Bob', 'Chris']
for idx, name in enumerate(alist):
    print(idx, name)

# 0 Alice
# 1 Bob
# 2 Chris
```

`enumerate` によって返される要素番号の初期値は、`start` 引数により任意
に設定することができる。初期値のデフォルトはゼロである。

```python
lines = [
    'Return an enumerate object. iterable must be a sequence, an iterator, or some other object which supports',
    'iteration. The __next__() method of the iterator returned by enumerate() returns a tuple containing a count',
    '(from start which defaults to 0) and the values obtained from iterating over iterable.',
]

for lineno, line in enumerate(lines, start=1):
    print(lineno, line)

# 1 Return an enumerate object. iterable must be a sequence, an iterator, or some other object which supports
# 2 iteration. The __next__() method of the iterator returned by enumerate() returns a tuple containing a count
# 3 (from start which defaults to 0) and the values obtained from iterating over iterable.
```

## range を利用した繰り返し

C 言語では、100 回繰り返すという操作を下記のように書くが、

```c
int i = 0;
for (i = 0; i < 100; i++) {
    printf("%d\n", i);
}
```

Python では、`range` 関数を利用する。

```python
for val in range(0, 100):
    print(val)
# 0
# 1
# 2
# ...
```

上記の例では、`range` 関数により、0 から 100 までの値を一つ刻みに出力
している。ここで、`range` が対象とする値の範囲は、0 **から** 100 **ま
で** の値であることに注意すること。

## for と辞書の組み合わせ

「辞書」の項では、`keys` 関数や `values` 関数や `items` 関数を紹介した。
これらの関数は `for` と組み合わせて利用することが多い。以下では、その
例を紹介する。

```python
adict = {
    'name': 'dummy',
    'age': 20,
}

for key in adict.keys():
    print(key, adict[key])

for value in adict.values():
    print(value)

for k, v in adict.items():
    print(k, v)
```

上記の例では、

- `keys` 関数を利用し、辞書における全てのキーを走査している
- `values` 関数を利用し、辞書における全ての値を走査している
- `items` 関数を利用し、辞書における全てのキーと値を走査している

## 練習問題: fizzbuzz.py

「[if/elif/else による条件分岐](https://github.com/r-nakamura/python-workshop/blob/master/if-elif-else.md)」
で作成した fizzbuzz.py を拡張して、任意の値ではなく、1 から 100 の整数
に対して fizzbuzz を判定するようにせよ。

## break

C 言語と同じように、`break` 文を挿入することにより、処理を打ち切ること
ができる。

```python
alist = [1, 2, 3]
for val in alist:
    if val == 2:
        break
```

上記の例では、変数 `val` が 2 である時にループが打ち切られるため、変数
`val` が 3 である時はループの中の処理は実行されない。

## continue

`continue` 文を挿入することにより、以降の処理を行わず、次のイテレーショ
ンを開始することができる。

```python
alist = [1, 2, 3]
for val in alist:
    if val == 2:
        continue
    print(val)
```

`break` と `continue` の双方の例を実際に動かしてみることで、`break` と
`continue` の違いがわかるだろう。

## while による繰り返し

while による繰り返しは C 言語と同様であり、与えられた条件が真 (`True`)
である限り、ブロック内の処理を繰り返し実行する。

```python
while True:
    print(1)
```

例えば、空でないリストは `True` と判定される、また、空のリストは
`False` と判定されることを利用して、リストから (先頭の) 要素を取り出す
ような操作は下記のように書くことができる。

```python
queue = [1, 2, 3, 4, 5]
while queue:
    queue.pop(0)
```