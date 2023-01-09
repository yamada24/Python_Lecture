# irisを用いたデータ分析
## irisのデータのimport

irisのデータをPython上で扱うには，`seaborn`というライブラリを使う．`seaborn`では，データを分析しやすいように配列として扱いやすい機能が入っている．

`iris = sns.load_dataset("iris")`でデータを`iris`として持っておくことができる．


```python
import pandas as pd
import seaborn as sns
sns.set()

iris=sns.load_dataset("iris")
print(iris)
```
