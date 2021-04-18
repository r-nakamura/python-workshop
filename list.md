# Python のデータ構造

これまでは **スカラ変数** を紹介したが、以降では Python のデータ構造を
紹介する。Python では、以下のデータ構造が用意されている。

- **リスト**
- タプル
- **辞書**
- 集合

本資料では、リストと辞書を主に説明する。ただし、タプルと集合も非常に強
力なデータ構造であるので、ぜひ自身で学んでほしい。

# リスト
## リストの宣言

リストを活用することにより、複数の要素を単一の変数で管理することができ
る。

Python では、以下のように、リストを宣言することができる。

```python
alist = [1, 2, 3]
print(alist) # [1, 2, 3]
```

また、空のリストは以下のように宣言することができる。

```python
alist = []
alist = list()
```

C 言語における配列の宣言に相当すると考えてもよい。

```c
int
main()
{
  int array[3] = {1, 2, 3};
  return 0;
}
```

ただし、C 言語とは異なり、

- 要素数を宣言する必要はない
- 同一の型の値を格納する必要はない (つまり、型が異なる値を格納することができる)

## リストにおける要素の取り出し

各リストの値を取り出すためには、**オフセット** を指定する。この時に、
リストにおける先頭の要素がゼロ番目であることに注意する。

```python
alist = [1, 2, 3]
print(alist[0]) # 1
print(alist[1]) # 2
print(alist[2]) # 3
```

また、負のインデックスを使用すれば、末尾から逆順に要素を辿ることができ
る。

```python
alist = [1, 2, 3]
print(alist[-1]) # 3
print(alist[-2]) # 2
print(alist[-3]) # 1
```

このため、リストの大きさが不明である場合にも、リストにおける末尾の要素
は容易に取り出すことができる。

## リストにおける要素の書き換え

リストの要素を別の値に書き換えるには、書き換える要素をインデックスによ
り指定した上で値を代入すればよい。

```python
alist = [1, 2, 3]
alist[1] = 200
print(alist) # [1, 200, 3]
```

## スライスによる要素の取り出し

スライスを利用することにより、リストにおける特定の範囲の要素を取り出す
ことができる。

```python
alist = [1, 2, 3, 4, 5]
print(alist[3:]) # [4, 5]
print(alist[:2]) # [1, 2]
print(alist[2:4]) # [3, 4]
print(alist[::2]) # [1, 3, 5]
print(alist[::-1]) # [5, 4, 3, 2, 1]
```

上記の例はそれぞれ以下の操作を表す。
- `alist[3:]`: 3 番目から末尾の要素を取り出す
- `alist[:2]`: 先頭から 2 番目までの要素を取り出す
- `alist[2:4]`: 2 番目から 4 番目までの要素を取り出す
- `alist[::2]`: 先頭から末尾までの要素を一つ置きに取り出す
- `alist[::-1]`: リストを逆順にした要素を取り出す

## リストへの要素の追加と削除

リストに新たに要素を追加する場合に、以下のような操作を実行するとエラー
となる。

```python
alist = [1, 2, 3]
alist[3] = 4
# Traceback (most recent call last):
#   File "list.py", line 25, in <module>
#     alist[3] = 4
# IndexError: list assignment index out of range
```

Python では、リストに新たに要素を追加する場合には以下の関数を使用する。
  - `append` 関数
  - `insert` 関数

一方、リストに存在する要素を削除する場合には以下の関数を使用する。
  - `pop` 関数
  - `del` 関数

## append/insert 関数

`append` 関数は、リストの末尾に値を新たに追加する。

```python
alist = ['Alice', 'Bob']
alist.append('Chris')
print(alist) # ['Alice', 'Bob', 'Chris']
```

`insert` 関数は、指定したオフセットに要素を追加する。下記の例では、リ
ストの 1 番目に値を新たに追加している。

```python
alist = ['Alice', 'Bob']
alist.insert(1, 'Chris')
print(alist) # ['Alice', 'Chris', 'Bob']
```

## pop 関数

`pop` 関数は、引数を指定しない場合には、リストにおける末尾の要素を削除
する。

```python
alist = ['Alice', 'Bob', 'Chris']
alist.pop()
print(alist) # ['Alice', 'Bob']
```

また、`pop` 関数における引数にオフセットを与えることにより、当該オフセッ
トに位置する値を削除することができる。

```python
alist = ['Alice', 'Bob', 'Chris']
alist.pop(1)
print(alist) # ['Alice', 'Chris']
```

## リストにおける要素の追加/削除のまとめ

筆者の独断ではあるが、特に以下の操作はしっかり把握しておくとよい。

- リストにおける末尾への要素の追加: `alist.append()`
- リストにおける末尾の要素の取り出し: `alist.pop()`
- リストにおける先頭の要素の取り出し: `alist.pop(0)`

これらの操作を利用すれば、規律が FIFO (First-In First-Out) であるキュー
は下記のように簡易的に実現できる。

```python
queue = []

queue.append(1)
print(queue) # [1]

queue.append(2)
print(queue) # [1, 2]

queue.append(3)
print(queue) # [1, 2, 3]

queue.pop(0)
print(queue) # [2, 3]

queue.append(4)
print(queue) # [2, 3, 4]
```

ちなみに、キューを使用するのであれば、`collection.deque` オブジェクト
を使用するのがよい ([https://docs.python.org/3/library/collections.html#collections.deque](https://docs.python.org/3/library/collections.html#collections.deque) 参照)。

## リストの大きさの取得

リストの大きさを取得するには `len` 関数を使用すればよい。

```python
alist = [1, 2, 3]
print(len(alist)) # 3
```

## リストから文字列の変換

`join` 関数により、与えられた区切り文字でリストの要素を結合した文字列
を取得することができる。

```python
alist = ['A', 'B', 'C']
astr = '_'.join(alist)
print(astr) # A_B_C

astr = ','.join(alist)
print(astr) # A,B,C
```

`join` 関数を活用することにより、CSV や TSV などのフォーマットに (ある
程度) 従う文字列を簡単に作成することができる。

## 練習問題: list_append.py

リストを利用し、以下の処理を実装せよ。

1. `['Alice', 'Bob', 'Chris']` というリスト `alist` を宣言せよ
2. リスト `alist` の末尾に Diana を追加し、 `['Alice', 'Bob', 'Chris', 'Diana']` というリストを作成せよ
3. リスト `array` の先頭に Eve を追加し、 `['Eve', 'Alice', 'Bob', 'Chris', 'Diana']` というリストを作成せよ

## 練習問題: list_pop.py

リストを利用し、以下の処理を実装せよ。

1. `['Alice', 'Bob', 'Chris']` というリスト `alist` を宣言せよ
2. リスト `alist` から 'Chris' を取り出した後のリストを出力せよ
3. リスト `alist` から 'Alice' を取り出した後のリストを出力せよ

## 練習問題: join.py

`join` 関数を利用し、以下の処理を実装せよ。

1. `["0120", "123", "XXX"]` というリストを宣言せよ
2. 宣言したリストを `join` 関数を利用して `-` で連結して出力せよ

