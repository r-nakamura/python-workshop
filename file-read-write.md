# ファイル読み込み/書き込み
## C 言語を用いた場合の外部ファイル読み込み

まず、C 言語で外部ファイルを読み込む方法を確認しよう。いくつかの方法が
存在するが、典型的な例は以下の手順である。

  1. `fopen` 関数により、ファイル名からファイルストリームを開く
  2. 例えば、`fscanf` 関数により、各行を読み込む
  3. `fclose` 関数により、ファイルストリームを閉じる

上記の手順をコードで書くと以下のようになる。

```c
#include <stdio.h>

int
main()
{
  FILE *fp;
  int val1, val2;
  fp = fopen("sample.txt", "r");

  while (fscanf(fp, "%d %d", &val1, &val2) != EOF) {
    printf("val1: %d, val2: %d\n", val1, val2);
  }

  fclose(fp);
  return 0;
}
```

## 外部ファイルの読み込み (1/2)

次に、C 言語で外部ファイルを読み込む方法を説明する。Python においても
様々な方法でファイルを読み込むことができるが、まずは `open` 関数と
`read` 関数を用いたコードの例を示す。

```python
with open("sample.txt") as f:
    print(f.read())
```

以下では、上記のコードを詳細に説明する。

- `open` 関数の引数には、読み込む対象であるファイル名を指定する。`open` 関数の返り値としてファイルオブジェクトが得られる。
- `with` を利用することにより、`with` のスコープから外れた時に**自動的に**ファイルストリームが閉じられる。
  - `close` 関数により明示的にファイルストリームを閉じることはできるが、`with` を使う方が望ましい。
- `read` 関数によりファイル全体のテキストを取得する。

## 外部ファイルの読み込み (2/2)

`read` 関数ではファイル全体の文字列が得られるが、`readlines` 関数と
`for` を利用することにより、行単位で文字列を処理することができる。

```python
with open("sample.txt") as f:
    for line in f.readlines():
        print(line)
```

上記の処理は、ファイルオブジェクトを `for` により繰り返し処理すること
で、以下のように簡潔に書くこともできる。

```python
with open("sample.txt") as f:
    for line in f:
        print(line)
```

## 補足: rstrip 関数による改行文字の処理

上記の方法では、入力ファイルにおける各行の末尾には改行文字 (`\n`) が付
与されているため、`print` 関数で文字列を出力した際に余分な改行が表示さ
れる。このような場合において、文字列の末尾の改行文字を取り除くためには、
`rstrip` 関数を使用すればよい。

```python
with open("sample.txt") as f:
    for line in f:
        line = line.rstrip() # 末尾の改行文字を取り除く
        print(line)
```

シミュレーションにより得られた数値データを処理する場合には、上記のよう
なコードを書くことが多いので、テンプレートとして覚えておいてもよい。

## 外部ファイルの書き込み (1/2)

外部ファイルに文字列を書き込む場合は `write` 関数を使えばよい。

```python
lines = [
    "line 1",
    "line 2",
    "line 3"
]

with open("sample1.txt", "w") as f:
    for line in lines:
        f.write(line + "\n")
```

ただし、ファイルに書き込む場合は、`open` 関数の引数に `w` を与える必要
がある (`w` は write の略称)。

## モジュールを利用したファイルの読み込み

上記では、`open` 関数を利用したファイルの読み込みを紹介したが、**モジュー
ル**によりファイルを読み込みことができる。以下では、`fileinput` モジュー
ルを利用した例を紹介する。

```python
import fileinput

for line in fileinput.input("sample.txt"):
    print(line)
```

まず、モジュールを利用する場合には、`import` によりモジュールを読み込
む。その後は、モジュールのお作法に従ってコードを記述する。今回利用する
`fileinput` では `input` 関数にファイル名を与えることで、ファイルを読
み込むことができる。

## 標準入力からの読み込み

上述した `fileinput` を利用すれば、標準入力からも文字列を読み込むこと
ができる。その場合は、`input` 関数の引数を空にすればよい。

```python
import fileinput

for line in fileinput.input():
    print(line)
```

モジュールを利用しない場合には、`sys.stdin` を利用すればよい。ただ、筆
者自身は、標準入力や外部ファイルからの読み込みは `fileinput` で統一し
ている。

また、筆者は、(余程のことがない限りは) 標準入力からデータを読み込み、
標準出力に処理したデータを出力するようなプログラムを書く。なので、
`fileinput` と `print` 関数を併用した下記のようなコードを用意し、

```python
import fileinput

for line in fileinput.input():
    # 何かしらの処理

    print(line)
```

下記のように実行することが多い。

```sh
python3 code.py <input.txt >output.txt
```

## 練習問題: cat.py

何かしらのテキストファイルを自身で用意し、そのファイルの中身を Python
で読み込み、その中身を標準出力に出力せよ。

## よくある例: csv ファイルのデータ処理

まず、下記のような、簡単な csv ファイルが存在するものとする。

```
1,2
3.5,4.2
5,6
```

上記の csv ファイルにおいて、行毎の値の平均値を出力するコードは以下の
ようになる。

```python
import fileinput

for line in fileinput.input():
    line = line.rstrip() 
    fields = line.split(",")
    fields = list(map(float, fields))
    print(sum(fields) / len(fields))
```

以下では、上記のコードを詳細に説明する。
  - まず、`rstrip` 関数により末尾の改行文字を取り除く
  - 次に、csv は区切り文字が「,」であるため、「,」でフィールド毎に分割できることから、`split` 関数により分割した要素をリストに格納
    - ただし、これは、各フィールドに「,」場合のみにしか適用できない。
  - リストにおける各要素は `str` 型であるため、`map` 関数により `float` 型に変換
  - `sum` 関数によるリストにおける値の総和と、`len` 関数によるリストの要素数から平均値を計算