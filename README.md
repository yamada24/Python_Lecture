# Python_Lecture（try用）
高校生向け　情報Ⅰのプログラミング分野の対策用にお使いください．

## まずはじめに...
このレクチャーは，Pythonの初学者，または高校生での共通テストの対策に向けた基礎がために使います．なお，随時アップデートされますので，ご理解ください．

本書では，この資料を見ながら実際に手を動かしながら学習することができます．インプッっとしたらアウトプットをして，課題に取り組み，フィードバックをする．この繰り返しで効率よく学習を定着させます．

## 環境構築
このレクチャーで使用する機材，アプリについて紹介します．

- PC（Google Chromeが使えるものであれば可）
- Google Chrome（Google Colaboratoryを使用するためのアプリ）
- Google Colaboratory（Pythonのコードを記述して実行するためのアプリ）

基本的にはこれらが動作することが前提です．

## プログラミングとは
プログラミングとは，コンピュータにやってほしいことをコンピュータ用の言語で記述し命令することを指します．我々が普段会話で人に命令や指示をすることは慣れています．しかし，コンピュータに指令を送る場合，人間のようにスムーズにはいきません．そこで，この場では，プログラミングの記述の仕方の基本を学ぶことにします．何事も土台が大切です．一緒に頑張りましょう．


## プログラミングの構造

Pythonに限らず，ほとんどのプログラミングは上から順番に処理されていきます．基本的には指示したい順にコードを書いていきます．また，一回書いたコードは指示がない限り戻ったりすることはできませんし，指示なく覚えておくこともできません．気をつけましょう．


## プログラミングの書き方
数学や英語などと一緒で，処理ごとに綺麗にまとめて書くことがスムーズに理解するためのポイントです．

インデントや空行を使うことで綺麗にまとめることができます．また，メモとしてコメントアウトというものがあります．これは，Pythonのコードの中に説明を書きたい場合や実行させたくないコードを無効化できます．

コード
```

print('この文章は表示されます')

# このようにコメントアウト上で日本語でコメントを書くことができます．
# print('この文章は表示されません')

```

実行結果
```
この文章は表示されます
```



# Pythonの文法について
## 変数の扱い

Pythonでは，変数という箱に値を入れて保持，操作していきます．その箱に入れる値にはいくつかの種類があります．

|型|型の名称|意味|例|  
|---|---|---|---|  
|str|string|文字列型|'yamada'|  
|int|integer|整数型|1124|  
|float|float|浮動小数点|11.24|  
