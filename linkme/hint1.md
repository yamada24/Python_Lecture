# 課題１（計算機プログラム）のヒント

## 計算機プログラムの流れ
まず，計算機プログラムのゴールを想像してみよう．私はここでは，以下のような計算機プログラムを想定してみます．

```
>>> 数字を入力してください：21
>>> 数字を入力してください：32
>>> 計算方法を選択してください（1. + , 2. - , 3. * , 4. / , 5. % ）：1
>>> 21 + 32 = 35
>>> end
```
こうなってくれたら嬉しいなをまず考えましょう．

次に，これを上から順番にプログラムにしていきます．まずは必要な変数を考えましょう．（変数は無駄のないように最小にしようとすると，より成長が早まりますが無理はしないように．．．）

今回は２数の演算なので２つの変数が必要になります．他に何の変数が必要か考えてみてください．その際に，変数の名前は見てわかるような変数名にしましょう．

演算の選択にはこの場合はこの計算をするというように条件で処理を分けたいです．これに合う文法を探して当てはめてみましょう．

あとは，エラー分との睨めっこです！


## 計算機プログラムの探究
計算機は本来，複数の数字を計算することができますよね？では，複数の数字を入力してそれらをすべて計算できれば嬉しいですね．私のおすすめは複数の数字の足し算からやってみるといいと思います．

配列を使うと，複数の数字の扱いが楽になりそうですね．

他にも，世の中には，関数電卓というものが存在するらしい．関数電卓は理系の学生の親友とも呼ばれる常に共に学生生活を送るパートナーだそうです．これもプログラミングで計算されているらしいですね．ぜひ．．．

