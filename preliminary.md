# 準備
## Python のバージョンの確認

本資料では Python のバージョン 3 を対象とするので、まず、Python のバー
ジョンを確認しよう。

```
$ python -V
Python 2.7.16

$ python3 -V
Python 3.8.0
```

以降では、Python のバージョンが 3 である方のコマンドを実行しよう。上記
の場合には、`python3` を使用する。

## Python の対話型インタプリタ

端末で `python3` を実行すると、以下のように **対話型インタプリタ** が
起動する。1 行ずつコマンドを実行すると、その結果が表示される。

```
$ python3
Python 3.8.0 (default, Jan  9 2021, 18:52:56) 
[GCC 8.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 1 + 1
2
>>> 2 * 3
6
>>> 
```

終了する場合には、`Ctrl-d` を入力する (`Ctrl` キーを押しながら、`d`キー
を入力する)。

## Python ファイルの実行方法

`python3` により、Python が記述されたファイルを実行する場合には、以下
のように、`python3` の引数にファイル名を指定する。

```
$ python3 hello.py
```

通常、Python が記述されたファイルの名前における拡張子は `.py` である。
これにより、ファイルの中身を開かなくても、ファイルが Python のためのも
のであることがわかる。

## Hello, World の表示

早速、テキストエディタにより、以下のように記述した `hello.py` ファイル
を作成しよう。

```python
print('Hello, World!')
```

そして、以下のようなコマンドを端末で実行することにより、`Hello,
World!` と表示されるかを確認しよう。

```
$ python3 hello.py
Hello, World!
```

Python において標準出力に文字列を出力するには、`print` 関数を使用する。
`print` 関数のデフォルト機能により、末尾には改行 (`\n`) が付与されてい
る。

## shebang

Python のプログラムの冒頭には、**shebang** として、

```python
#!/usr/bin/env python3
```

と必ず記入するようにしよう。

これにより、スクリプトを実行する際に、どのインタプリタを利用するかを明
示できる。このため、(スクリプトの実行権限を付与した上すれば、) スクリ
プトを直接実行することができる。

```
$ cat hello.py
#!/usr/bin/env python3
print('Hello, World!')
$ chmod +x hello.py
$ ./hello.py
```

読みやすさのために、本資料におけるサンプルコードでは shebang は書かな
いものとする。
