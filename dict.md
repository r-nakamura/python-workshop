# 辞書
## 辞書の概要

辞書は、キーと値のペアによりデータを管理するデータ構造である。辞書によ
り、一意なキーからそのキーに対応する値を参照することができる。通常、キー
には文字列を使用するが、整数などもキーとして使用することができる。

辞書は、**ハッシュ**や**連想配列**とも呼ばれる。例えば、プログラミング
言語 Perl のハッシュが Python の辞書に相当する。

筆者の主観ではあるが、辞書を適切に利用することで、プログラムのロジック
を簡潔に表現できることが多いように思う。

## 辞書の宣言

Python では、以下のように、辞書を宣言することができる。

```python
adict = {
    'name': 'dummy',
    'age': 20,
}
print(adict) # {'name': 'dummy', 'age': 20}
```

辞書を宣言する時は、**キー: 値** をカンマ (,) 区切りで並べ、`{}` で囲
む。

また、空の辞書は以下のように宣言することができる。

```python
adict = {}
adict = dict()
```

## 辞書における値の取り出し

辞書における値を参照するには、リストと同じように `[]` を利用する。ただ
し、辞書とは異なり、参照する要素へのオフセットではなく、参照する要素へ
のキーを与える。

```python
adict = {
    'name': 'dummy',
    'age': 20,
}
print(adict['name']) # dummy
print(adict['age']) # 20
```

## 辞書における値の書き換え

辞書における特定の値を別の値に書き換えるには、書き換える値をキーにより
指定した上で値を代入すればよい。

```python
adict = {
    'name': 'dummy',
    'age': 20,
}
adict['age'] = 30
print(adict['age']) # 30
```

## 辞書への (キー: 値) の追加と削除

既に宣言した辞書に、新たにキーと値のペアを追加する場合には、以下のよう
にすればよい。

```python
adict = {
    'name': 'dummy',
    'age': 20,
}
adict['height'] = 150
print(adict) # {'name': 'dummy', 'age': 20, 'height': 150}
```

一方、辞書からキーと値のペアを削除する場合には、`del` 関数を使用する。

```python
adict = {
    'name': 'dummy',
    'age': 20,
}
del adict['age']
print(adict) # {'name': 'dummy'}
```

## 練習問題: dict.py

次の処理を実装せよ。

1. 辞書を利用して、以下のプロフィールを表現せよ
  - 名前 (`name`): anonymous
  - 年齢 (`age`): 32
  - 言語 (`language`): Python
2. キーである `name`、`age`、`language` を利用して、辞書の値を出力せよ

### 辞書における全てのキーの取得

辞書における全てのキーを取得するには、`keys` 関数を使用する。

```python
adict = {
    'name': 'dummy',
    'age': 20,
}
print(adict.keys()) # dict_keys(['name', 'age'])
print(type(adict.keys())) # <class 'dict_keys'>
print(list(adict.keys())) # ['name', 'age']
```

`kyes` 関数の返り値のデータ型は `dict_keys` である。このため、リスト
として扱うためには、`list` 関数によりリストに変換する必要がある。

### 辞書における全ての値の取得

辞書における全ての値を取得するには、`values()` 関数を使用する。

```python
adict = {
    'name': 'dummy',
    'age': 20,
}
print(list(adict.values())) # ['dummy', 20]
```

`keys` 関数と同様に、`values` 関数の返り値をリストとして扱うために
は、`list` 関数を用いる。

### 辞書における全ての (キー: 値) の取得

辞書における全ての (キー: 値) を取得するには、`items` 関数を使用する。

```python
adict = {
    'name': 'dummy',
    'age': 20,
}
print(list(adict.items())) # [('name', 'dummy'), ('age', 20)]
```

上述した `keys`・`values`・`items` 関数は、関数単体で使用するこ
とも当然あるが、`for` 文と組み合わせて使用することが多い。

## 練習問題: dict.py

上記の練習問題で作成した `dict.py` を拡張して、以下の処理を実装せよ。

1. 以下のキーと値を辞書に追加せよ
  - キー: hobby
  - 値: programming
2. `keys` 関数を利用して、辞書に格納されている全てのキーを表示せよ
3. `del` 関数を利用して、辞書における `age` キーとその値を削除せよ

