# 課題５（タートルでの図形絵画）のヒント
## turtleの使い方
ここでは，`turtle`という図形絵画ライブラリを使ってさまざまな図形を書いていきます．これは数学の勉強になります．さらにいうと，プログラミングの基礎が全て入っているツールになるので，これ一つで基礎固めになります．習得スキルは以下の通りです．

* 逐次処理（プログラムは上から処理されていくということ）
* forやifの使い方
* 処理を実現させるための数学的思考（計算式など）
* etc...


基本的にプログラムは見えない動きをするため，不可視化状態で何が間違っているか，どう動いているかを考える．それに対して，turtleはグラフ（図形）として可視化されるため，プログラムの動きが把握しやすい．早速turtleしてみよう．

#### lets turtle :)

注意）pythonのバージョンによっては動作しない（エラーが出てしまう）場合がある．その時はpythonのバージョンを3.8にすると良い．（新しいverでは，内部の処理に異常がある時に止まってしまう処理が働いてしまっている感じ？）

使い方はこんな感じ．

```python
import turtle

# カーソルを亀さんにするコード
turtle.shape('turtle')
# 亀さんのスピード調整
turtle.speed('slowest')

# 前に進む（ms）
turtle.forward(100)

# 時計回りに角度変更（°）
turtle.right(30)
turtle.forward(50)

# 反時計回りに角度変更（°）
turtle.left(90)
turtle.forward(200)

# 後ろに下がる（ms）
turtle.back(100)

# 円の絵画（サイズ指定）
turtle.circle(100)

turtle.done()
```

なんとこれだけでほぼ全ての図形を描画できる．


では，早速図形を絵画していく．

## 図形絵画（初級編）
初級編ですから，どうぞお手柔らかに．

### 正三角形

正三角形は内角が60°なので，亀さんを走らせて120°回転させれば内角60°を再現できる．頭の中のイメージからしましょう．こんな感じでしょうか．

![sasa](https://i.imgur.com/Agh6XDd_d.jpg?maxwidth=520&shape=thumb&fidelity=high)  

このイメージがほんまに大事です．これを一般化という．一般化することで，どうプログラムを処理するのがいいか整理ができます．そしてPCの言語化ができるというわけです．

このイメージを元にコーディングした結果が次にある．

```python
import turtle

turtle.shape('turtle')

turtle.forward(100)
turtle.left(120)
turtle.forward(100)
turtle.left(120)
turtle.forward(100)

turtle.done()
```

結果はこんな感じ．

![njasndn](https://i.imgur.com/j2Hyq7j_d.jpg?maxwidth=520&shape=thumb&fidelity=high)  

これで三角形は完成ですね．コンプリート！！

### 直角三角形

次に直角三角形を試してみます．イメージからしましょう．

![mkasnmaskd](https://i.imgur.com/HunLKAb_d.jpg?maxwidth=520&shape=thumb&fidelity=high)  

注意する点としては代表角の三角形の比を抑えること．長さの比を使って正確に三角形を描画する．ここで，無理数が入っているので，無限小数になるが，小数約7桁で計算してくれるので，多少の誤差はあるものの気にしなくて良い．もし，もっと精度を上げるのであれば，double型で計算してください．今回はfloatで十分です．

では，コーディングすると．


```python
import turtle
import math

turtle.shape('turtle')

turtle.color('red')
turtle.forward(100)
turtle.left(90)
turtle.forward(100 * math.sqrt(3))
turtle.left(150)
print(math.sqrt(3))
turtle.forward(200)

turtle.done()
```

結果は．

![sadsnasjdb](https://i.imgur.com/FGlE5YZ_d.jpg?maxwidth=520&shape=thumb&fidelity=high)  

直角三角形の代表角の三角形を描きました．まあ，こんなもんでしょう．1 : 2 : √3 の比になっているので，それを指定して角度を回転させてあげればOKですね．

四角形に行きます．

### 長方形
長方形を書きます．イメージから．

![imasnd](https://i.imgur.com/T9X7OGc_d.jpg?maxwidth=520&shape=thumb&fidelity=high)  


これを元にコーディングする．コードはこんな感じです．

```python
import turtle as t
import math

t.shape('turtle')

t.forward(100)
t.left(90)
t.forward(200)
t.left(90)
t.forward(100)
t.left(90)
t.forward(200)

t.done()

```

実行するとこんな感じになりましたか？

![jaisdh](https://i.imgur.com/xrbTwAF_d.jpg?maxwidth=520&shape=thumb&fidelity=high)  

シンプルですね．正方形も簡単に書けると思います．

### 平行四辺形

平行四辺形は角度決めてドーン！って感じです．頭の中の計算も合わせて載せておきます．（長さ書いてなくてすみません．）

![sad](https://i.imgur.com/e3A9NpL_d.jpg?maxwidth=520&shape=thumb&fidelity=high)  

コードはこんな感じ

```
import turtle as t
import math

t.shape('turtle')

t.color('red')
t.forward(100)
t.left(60)
t.forward(200)
t.left(120)
t.forward(100)
t.left(60)
t.forward(200)

t.done()
```

結果は．．

![ima](https://i.imgur.com/bkVXPJS_d.jpg?maxwidth=520&shape=thumb&fidelity=high)  

うーん，こんなもんですね．

### 台形

台形なんてのも作れますね．少し計算が必要です．頭の中の計算も載せておきますね．

![das](https://i.imgur.com/NrsvtHL_d.jpg?maxwidth=520&shape=thumb&fidelity=high)    

少し複雑なので，簡単な台形にしました．

コードはこんな感じ．


```
import turtle as t
import math

t.shape('turtle')

t.color('blue')
t.forward(400)
t.left(120)
t.forward(200)
t.left(60)
t.forward(200)
t.left(60)
t.forward(200)

t.done()
```

結果は．．．

![iams](https://i.imgur.com/6lkWvby_d.jpg?maxwidth=520&shape=thumb&fidelity=high)  


台形ってこうみると，四角形と三角形の応用だということがわかりますね．数学が深まっていく感覚がわかりますか？プログラムは単純なことしかできないので，一般化しなくてはいけない．一般化しようとすると，一回バラバラにしてシンプルにすることが必要なんですね．この過程でなぜこうなっていたのかが理解できて，一石二鳥な感じです．いってしまえば，数学と英語の融合科目的な感じですね．

さあ，ここまで順調ですか？まだまだ難易度は初級ですよ！ガンガン行きましょう！

## 図形絵画（中級編）
ここから中級編です．実際にfor文を使って繰り返し処理をさせてみます．

forを使うとどうなるのか，こんな感じの枠組みになります

```python
import turtle as t
import math

# ループ回数をここで決められるようにしてみた
n = 30

t.shape('turtle')

# n回試行する
for i in range(n):
	# ここにturtleの動きを絵画するとループして処理してくれる
    t.forward(100)
    t.left(70)

t.done()
```

これを試しに実行してほしい．

結果は動きで確認してみてくれ．

こんなふうに繰り返される．これを元に，書きたい図形を一般化していく

### 星
星をかくという課題は大学でよく見る課題である．やってみよう．まずはイメージからじゃ！

![nbhdsa](https://i.imgur.com/3Vl7IFA.jpeg)  

角度をしっかり求めてっと．あとは，これをコーディング！


```
import turtle as t

t.shape('turtle')

n = 5

for i in range(n):
    t.forward(100)
    t.left(144)

t.done()
```

なんてこった，シンプルすぎて草超えて森超えて熱帯雨林超えてステップですね．

結果は．．

![sadbsj](https://i.imgur.com/WFMojsP.png)  

このようにstarも完成です．もうここまで来ると書けない図はなさそうな気もしますね．

### おまけ．円のあれこれ
円についても書いてみますか．ループさせてサイズの違う円を書き続けてもらうことにする．

```
import turtle as t

t.speed(100)

for i in range(100):
    t.circle(2*i)

t.done()
```

どんな結果になるか予想してみよう．．

```
予想タイム

結果はこの下にあります．


:)






:)




;)




:)




;)





:(




;)
```

さあ，結果はこちら

![nsjjnd](https://i.imgur.com/tgH6CYi.png)  


面白いですね．
確かに，中心から書いているわけではないので，コンパスみたいに上手くいくわけがありません．でも幻想的ですね．


円をかくメソッドを使わないでぐるぐるしてみたいですね．やってみます．


```
import turtle as t

n = 100000

t.speed(100)

for i in range(n):
    t.forward(i)
    t.left(i)


t.done()
```

さあ，これでどうなるでしょうか．ぐるぐるするために，進む距離と角度を変数にして1からだんだん大きくしてみました．

実際に実行してみてください．

![nbajsbdh](https://i.imgur.com/Hb0YwL5.png)  


あれ，上手く行きませんね．うーん，難しいですね．予想とは全然誓うような感じがします．これもまたプログラミングの醍醐味ってやつですかね？へへ．

では，どうすれば上手くいくのか．


## 図形絵画（上級編）
さて，ここからは難易度をぐんぐん上げていきますね．

まず，この章で書きたい図形はフラクタル図形です．さあ，いきましょう！

### ヒルベルト曲線

