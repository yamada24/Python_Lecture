# 課題４（irisのデータ分析）のヒント


## irisのデータをどう扱うの？
まず，この`iris`のデータを詳しくみてみる必要がある．そこで，データを確認するためのPythonライブラリで`seaborn`，`pandas`，`matplotlib`などがあるので，まずは，`iris`のデータについて分析してみましょう．

まず初めに`iris`のデータを可視化してみます．

### コード

```python
import seaborn as sns
from matplotlib import pyplot as plt

sns.set()

print(iris)
```



### 実行結果

```
     sepal_length  sepal_width  petal_length  petal_width    species
0             5.1          3.5           1.4          0.2     setosa
1             4.9          3.0           1.4          0.2     setosa
2             4.7          3.2           1.3          0.2     setosa
3             4.6          3.1           1.5          0.2     setosa
4             5.0          3.6           1.4          0.2     setosa
..            ...          ...           ...          ...        ...
145           6.7          3.0           5.2          2.3  virginica
146           6.3          2.5           5.0          1.9  virginica
147           6.5          3.0           5.2          2.0  virginica
148           6.2          3.4           5.4          2.3  virginica
149           5.9          3.0           5.1          1.8  virginica
```

このデータの中身はこの結果の通りです．縦軸がデータの試料数，横軸は各項目の通りになっています．

`sepal_length`はがく片の長さ，`sepal_width`はがく片の幅，`petal_length`は花弁の長さ，`petal_width`は花弁の幅，`species`は種（`setosa`，`versicolor`，`virginica`）の要素になっている．

このデータをグラフにプロット（描画）してみる．グラフにはいろいろある．

### 散布図

```python
#これでグラフにプロットできる
sns.pairplot(iris)
plt.show()
plt.close()

```

`sns.pairplot(iris)`の部分で，`iris`のデータセットをプロットするための関数に送ってグラフをプロットしてくれる．

実行結果は以下のようになっているはず．

![image1](a)  




```python
#これでグラフにプロットできる
sns.pairplot(iris, hue="species")
plt.show()
plt.close()

```

`sns.pairplot(iris, hue="species")`の部分で，`pairplot`関数の引数にデータセットと`hue="species"`を指定すると，`species`の種類で色分けしてくれる．



この要素の関係性を見ていくのがデータ分析である．



## データ分析入門




## データ分析の探究











































