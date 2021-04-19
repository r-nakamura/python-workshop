# リストや辞書を組み合わせたデータ構造
## リストとリストの組み合わせ

C 言語における多次元配列と同様に、Python ではリストとリストを組み合わ
せることができる。これにより、例えば、行列などのデータ構造を表現するこ
とができる。

```python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9],
]
print(matrix) # [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
```

リストを `[1, 2, 3]` という風に定義することから、リストの要素の中に
`[1, 2, 3]` と記述することで、リストの中にリストを格納することができる。

上記のリストにおいて、ゼロ番目のリスト `[1, 2, 3]` を参照するには、
```python
matrix[0] # [1, 2, 3]
```
とすればよい。

また、例えば、1 番目のリスト `[4, 5, 6]` における 2 番目の要素 `6` を
参照するには、
```python
matrix[1][2] # 6
```
とすればよい。

ちなみに、ベクトルや行列の演算をするのであれば、NumPy
([https://numpy.org/](https://numpy.org/)) を使うとよい。

## 辞書と辞書の組み合わせ

同様に、辞書における値に辞書を格納することができる。

```python
adict = {
    'dog': {
        'name': 'Taro',
        'color': 'brown',
    },
    'cat': {
        'name': 'Tama',
        'color': 'white',
    },
}
print(adict) # {'dog': {'name': 'Taro', 'color': 'brown'}, 'cat': {'name': 'Tama', 'color': 'white'}}
```

以下のように、各要素にアクセスすることができる。

```python
adict['dog'] # {'name': 'Taro', 'color': 'brown'}
adict['dog']['name'] # Taro'
```

## 辞書とリストの組み合わせ

さらに、辞書における値にリストを格納することで、様々なデータ構造を表現
することができる。

```python
adict = {
    'os': ['Windows', 'Linux', 'Mac'],
    'editor': ['Vim', 'Emacs', 'VSCode'],
}
print(adict['os']) # ['Windows', 'Linux', 'Mac']
print(adict['os'][1]) # Linux
```

本資料では、辞書にリストを格納する方法を述べたが、当然ながら、リストに
複数の辞書を格納することもできる。
