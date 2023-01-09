# Pythonの基本文法

## 変数の扱い

Pythonでは，変数という箱に値を入れて保持，操作していきます．その箱に入れる値にはいくつかの種類があります．

|型|型の名称|意味|例|説明|  
|---|---|---|---|---|  
|str|string|文字列型|'hensu'|扱いたい文字を'シングルコーテーションで囲む|  
|int|integer|整数型|1124|小数などは小数点以下が消えて整数のみになる|  
|float|float|浮動小数点|11.24|小数を扱う|  
|bool|boolean|真偽値|True , False|先頭は大文字になるので注意|
|list|list|リスト型（配列）|hensu[a,b,c,d,e]|[]を使って宣言．リストの中の値を上書きすることができる|  
|tuple|tuple|タプル型|hensu(a,b,c,d,e)|タプル型はリストと同じだが，値を上書きすることができない|  

変数という箱は宣言するだけでは何の効果もありません．そこに値を入れることで計算などの処理を行うことができます．まずはコードを見てみましょう．今回の例では `hensu` という変数を用意してそこに `123` という数字を入れてみます．

```
# hensuには123という数字を入れるよ
hensu = 123

# これはだめ
123 = hensu
```

これで `hensu` という箱に `123` が格納されました．これが逆だとPCはよくわからなくなってしまいますので，正しく宣言するようにしましょう．

イメージは右から左に入れるイメージです．

```
hensu　← 123
```


```
hensu1 ← 123
hensu2 ← 234
hensu　← hensu1 + hensu2
```


ここで重要なポイントです．他の言語（C言語，Java言語など）では，変数を宣言する際にデータ型を決める必要がありますが，Pythonは型を指定しなくても自動で認識してくれます．便利にも感じますが，変数の方がわかりにくくなります．ここでいくつか例を挙げます．以下の例はどのようなデータ型になっているでしょうか．

```
hensu1 = 123

hensu2 = 12.5

hensu3 = 'yamada'

hensu4 = True

hensu5 = 0

hensu6 = '123'

hensu7 = yamada
```

ここで注目することは，変数の型は入れるデータの型によって変わるということです．ということは入れるデータの型について考えましょう．

```
# hensu1はint型
hensu1 = 123

# hensu2はfloat型
hensu2 = 12.5

# hensu3はstr型
hensu3 = 'yamada'

# hensu4はbool型
hensu4 = True

# hensu5はint型
hensu5 = 0

# hensu6はstr型
hensu6 = '123'

# これはエラーになる（yamadaは文字のためstr型の書き方で入れる必要がある）
hensu7 = yamada
```

このように，変数に値を入れた後は自動で型が決まります．では，なぜ，型を意識しなければいけないのでしょうか？

それでは，次のコードをみてみましょう．

### コード１

```
hensu1 = 123
hensu2 = 234
hensu3 = hensu1 + hensu2
print(hensu3)
```

### コード２

```
hensu1 = '123'
hensu2 = '234'
hensu3 = hensu1 + hensu2
print(hensu3)
```

ここで問題です．上のコード１とコード２実行するとどうなるでしょうか．予想してみましょう．

結果はこのようになります．

### コード１実行結果

```
357
```

### コード２実行結果

```
123234
```


みなさん正解しましたか？そうです．データ型というのは正しくデータを扱うことができるように設定されたカテゴリーのようなものなのです．コード１の方では， `hensu1`と`hensu2`がint型（整数型）なので加算してくれました．コード２の方は，`hensu1`と`hensu2`がstr型（文字列型）なので，PCが文字列とみなして結合してくれました．こうしてそれぞれの変数が自動でデータ型を割り当ててくれています．

では，下のコードはどうでしょうか．

```
hensu1 = 123
hensu2 = '234'
hensu3 = hensu1 + hensu2
print(hensu3)
```

予想したら実行してみましょう．結果は以下のようになったと思います．

```
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-3-b4eacc80adec> in <module>
      1 hensu1 = 123
      2 hensu2 = '234'
----> 3 hensu3 = hensu1 + hensu2
      4 print(hensu3)

TypeError: unsupported operand type(s) for +: 'int' and 'str'
```

みなさん，英語の時間です．できますよね？

`TypeError`...入力ミスしてませんか？

`Trackback（most recent call last）`...実行した結果（最後に処理を試みた部分）

`<ipython-input-3-b4eacc80adec> in <module>`...実行するための場所（モジュール）内の部分

```
      1 hensu1 = 123
      2 hensu2 = '234'
----> 3 hensu3 = hensu1 + hensu2
      4 print(hensu3)
```











# 参考文献
[初めてでもわかるPython入門](https://camp.trainocate.co.jp/magazine/python-basic/)

