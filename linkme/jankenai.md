# AIの導入

近年注目を集めているのがAI（Artifical Intelligence）で，人工知能とも呼ばれる．人工知能と聞いて，「そんな難しいこと，できるわけないよー」と思う人も少なくない．しかし，人工知能とは知能を人工的に模倣しているに過ぎない．つまり，この課題を取り組んでいるあなたたちにはすでに知能が存在しているということであり，知能を発達させることができているということである．

結論，人工知能は君たちの頭の中のロジック（logic）をプログラムで動かしているということであり，難易度はピンキリである．ここでは，ファーストステップを経験してもらう．

## ジャンケンとAI
初めに思考してもらう．ジャンケンはどういう気持ちで手を決めているかを考えることがAIでの最初のステップである．ここで，一番簡単なジャンケンの思考は「さっき出してきた手は続いて出さないだろう」と考えるロジックを想定する．

さっき出してきた手を出さないようにプログラムを組んでみる．骨格から作ることにする．

ロジック的には，cpuが最初１を出したら次はそれ以外を出すようにしてみる．（なお，ここでは，一回の実行で5回の勝負をすることとする）また，試行回数はこちらで決められるようにする．以下のプログラムで実現できる．

```python
import random

print('How many times ?')
n = int(input())

for i in range(n):
	print(i , '回目')
	# この中にジャンケンの処理を記述するとendまでn回繰り返してくれる
	# この中に先ほど作ったジャンケンのプログラムをそのまま入れてみるとn回処理してくれるのがわかる

print('end')
```

では，早速，AIを構築していく．まずは，ロジックをもとに処理内容を整理してみる

1. 1回目のジャンケンで，cpuは普通に手をだす
1. この手を記憶しておく
1. 2回目のジャンケンでcpuはその前に記憶しておいた手とは違う手を出す
1. この手を記憶しておく
1. この試行を繰り返す

この要件から`if`と`for` `while`をどう使っていくかを考える．

### 1について
1回目は普通に手を出せばいいので`random`を使って手を出してもらう．

```python
# playerの手を決める
print('player input ?')
player = int(input())

# cpuの手を決める
cpu = random.randint(0,2)

```

ちなみに，複雑になればなるほど変数に入っている値がわからなくなってくるので，定期的に確認したい場所に`print(変数)`を追加して変数に何が入っているかを確認すると良い．

今回は`cpu`の手に何が入っているかわからないので確認してみる．

```python
# playerの手を決める
print('player input ?')
player = int(input())

# cpuの手を決める
cpu = random.randint(0,2)

# printで確認してみる
print(cpu)

```

実行結果はランダムなので開発環境のPC内の現在時刻によって生成される（注意：ランダムは基本的にPCの環境内のある規則性に従って生成されるためセキュリティ目的での使用は厳禁！脆弱になってしまうので注意すること！）

これで勝敗を判定させると良い．

### 2について
手を記憶させる方法はいくつかある．変数を１つ用意して比べるのが一般的であるが，今回は勉強のため，リストを使ってみる．リストはもう使えるだろう．一応確認しておく．

リスト（List）は配列とも呼ばれており，値を複数，順番をつけて持たせることができる変数型である．以下のように扱う．

```python
# 空のリストを生成
hensu1 = []

# 1,2,3の要素を持ったリスト
hensu2 = [1,2,3]


```

`print()`してみましょう


```
[]
[1, 2, 3]
```

これでリストは完成した．次に幾つかの操作をしてみる．

#### append()


プログラム

```python
hensu1 = []
hensu2 = [1,2,3]

print(hensu1)
print(hensu2)

# hensu1に12を追加する
hensu1.append(12)
print('------------')
print(hensu1)
print(hensu2)

```

結果

```
[]
[1, 2, 3]
------------
[12]
[1, 2, 3]
```

#### insert()

プログラム

```python
hensu1 = []
hensu2 = [1,2,3]

print(hensu1)
print(hensu2)

# hensu1に12を追加する
hensu1.append(12)
print('------------')
print(hensu1)
print(hensu2)

# hensu2の2番目に13を追加する
# なお，2番目と指定したいときは添え字は1となる（n-1と考える）
hensu2.insert(1,13)
print('------------')
print(hensu1)
print(hensu2)

```

結果

```
[]
[1, 2, 3]
------------
[12]
[1, 2, 3]
------------
[12]
[1, 13, 2, 3]

```

他にも色々な操作ができるが，今回はこの辺で...

本題に戻ると，cpuの手をリストに記憶させる処理をかく．

```
# Listの宣言（初期値はからで用意しておく）
cpuList = []

（中略）

# cpuListにcpuの手をappendする
cpuList.append(cpu)

```

これで`cpuList`を`print()`してみると，しっかり値が入っていることが確認できる．

ここまでのコードを確認してみる（多少違っていてもOK．結果が同じであればうまくいっているはず．）

```pythomn
import random

cpuList = []

for i in range(5):
	print('player input ?')
	player = int(input())

	cpu = random.randint(0,2)
	cpuList.append(cpu)
	
	print(cpu)
	print(cpuList)	
 
```

これで1回目の状態を記録できた．

### 3について
ここから難易度が跳ね上がる．頑張ってついてくるように．

まず，cpuが手を出すときに，前の手を確認して違う手を出すモデルについて考える．

cpuがrandomな数字を受け取って，それが前の手と同じだったらもう一度，違う手
だったらその手を出して記録する．という流れにしてみるとうまくいきそうである．では早速書いてみる．

```python
while True:
	cpu = random.randint(0,2)
	
	if cpuList[0] != cpu :
		break

print(cpu)
```

違う手が出るまで繰り返して，違う手が出たらランダムを終わるようにしてみた．
これで前の手と違う手をcpuが出せるようになった．`print()`で確認してみるとわかるだろう．

ここで重要な問題がある．リストの参照についてだ．

リストの中身を見たいときは`index`（添え字）を指定する必要がある．今回は1回目の手と比べるので`index = 0`である．よって，上記の書き方でリストの中身を指定した．では，これを複数繰り返し処理をさせるにはどうしたらいいのか．毎回`index`の値を変えて書くわけにもいかない．ここで最初の`for`で指定した`i`が役にたつ．この`i`を使って`index`を指定してあげると自動で変わっていく．

```python
import random

cpuList = []

for i in range(5):
	print('player input ?')
	player = int(input())

	while True:
		cpu = random.randint(0,2)
	
		if cpuList[i-1] != cpu :
			break

	
	print(cpu)
	print(cpuList)	
```

これを実行すると，エラーが出たと思う．なぜなら，`index`の範囲がマイナスになるとインデックスの範囲を超えましたと言われる．これを処理してあげないといけない．やってみる．

```python
import random

cpuList = []

for i in range(5):
	print('player input ?')
	player = int(input())

	while True:
		cpu = random.randint(0,2)
	
        	if i <= 0:
        		break
        	elif cpu != cpuList[i-1]:
        		break

	
	print(cpu)
	print(cpuList)	
```

`i`が0以下だったらそのままの手を出すという処理にする．

### 4について
ここまでくると，あとはどのタイミングでリストに記憶させるかを考える．これは簡単で，cpuの手が決まったら`append()`するようにする．

```python
import random

cpuList = []

for i in range(5):
	print('player input ?')
	player = int(input())

	while True:
		cpu = random.randint(0,2)
	
        	if i <= 0:
        		break
        	elif cpu != cpuList[i-1]:
        		break
	cpuList.append(cpu)
	
	print(cpu)
	print(cpuList)	
```

これで，実行すると，今回の目的である「前の手を出さないAIモデル」の完成である．

このモデルをあとはジャンケンの勝負に当てはめていい感じに成形していくとAIの入門を達成できる．

## 補足
ジャンケンに当てはめる場合，関数などを使っていくと綺麗になる．ここでは関数を導入してみる．また，自分で試行回数を決められるようにも改良した．

```
# 自分の前に出した手は出さないようにするAIプログラム
import random


# cpuの手のchoice関数の宣言
def choice(cpuList, i):
    while True:
        cpuChoice = random.randint(0,2)

        if i <= 0:
            break
        elif cpuChoice != cpuList[i-1]:
            break

    return cpuChoice


# cpuの手を記憶しておくListの宣言&初期化
cpuList = []

# 試行回数の指定
print('How many times ?')
n = int(input())

# 試行回数分のループ
for i in range(n):
    print(i, '回目の試行')
    # playerの入力
    print('player input ?')
    player = int(input())

    # cpuの入力
    # 前に出した手を出さないようにする処理を関数で切り分けた
    # するとこの行だけでcpuの手が最適化された状態で格納される
    cpu = choice(cpuList,i)
    print(i)
    cpuList.append(cpu)

    print('player = ',player)
    print('cpu = ',cpu)
    print('cpuList = ',cpuList)



print('end')

```

関数は先に宣言しなければいけない．プログラムは上から処理されていくので，下に記述してしまうとまだ宣言されていない関数が呼び出されていると言って怒ってしまう．

また，5回の試行を考えていたが，その部分を最初に`input()`させてその回数を指定するようにした．なお，最後に，`print()`で状況を確認できるようにした．


## 最後に，
今回のAIモデルはシンプルはモノにしたが，他にも，今までのplayerの手を記憶してその結果最頻な手に勝つような手を出すようにすることも可能である．さらに言えば，相手が負けた後に出しやすい手，相手が勝ったときに出しやすい手，相手があいこになったときに出しやすい手などをリストから分析してそれに勝つような手を出すロジックも実現可能である．こうして，最強のAIが出来上がっていく．つまり，AIとは，データがたくさんあればあるほど正確になっていくのはこういうことをAIの中では考えているからである．自由研究などで，AI同士を戦わせてみるのも面白いかもしれない．

ここまでお疲れ様でした．






