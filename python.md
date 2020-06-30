# pandas

## DataFrameの相関関係を取得する

```
import pandas as pd
import numpy as np

data = np.random.randn(3,30)
df = pd.DataFrame(data)
print(df.corr())
```

## 相関関係をヒートマップで表示する

```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

data = np.random.randn(3,4)
df = pd.DataFrame(data)
print(df.corr())

sns.heatmap(df.corr(),
            cmap='Blues',
            annot=True,
            annot_kws={'size': 20},
            fmt='1.1f',
            xticklabels=df.columns,
            yticklabels=df.columns)
plt.show()
```

## matplotlibのヒートマップ一覧
https://matplotlib.org/examples/color/colormaps_reference.html

```
cmaps = [('Perceptually Uniform Sequential', [
            'viridis', 'plasma', 'inferno', 'magma']),
         ('Sequential', [
            'Greys', 'Purples', 'Blues', 'Greens', 'Oranges', 'Reds',
            'YlOrBr', 'YlOrRd', 'OrRd', 'PuRd', 'RdPu', 'BuPu',
            'GnBu', 'PuBu', 'YlGnBu', 'PuBuGn', 'BuGn', 'YlGn']),
         ('Sequential (2)', [
            'binary', 'gist_yarg', 'gist_gray', 'gray', 'bone', 'pink',
            'spring', 'summer', 'autumn', 'winter', 'cool', 'Wistia',
            'hot', 'afmhot', 'gist_heat', 'copper']),
         ('Diverging', [
            'PiYG', 'PRGn', 'BrBG', 'PuOr', 'RdGy', 'RdBu',
            'RdYlBu', 'RdYlGn', 'Spectral', 'coolwarm', 'bwr', 'seismic']),
         ('Qualitative', [
            'Pastel1', 'Pastel2', 'Paired', 'Accent',
            'Dark2', 'Set1', 'Set2', 'Set3',
            'tab10', 'tab20', 'tab20b', 'tab20c']),
         ('Miscellaneous', [
            'flag', 'prism', 'ocean', 'gist_earth', 'terrain', 'gist_stern',
            'gnuplot', 'gnuplot2', 'CMRmap', 'cubehelix', 'brg', 'hsv',
            'gist_rainbow', 'rainbow', 'jet', 'nipy_spectral', 'gist_ncar'])]
```

# numpy

## 次元の追加方法
```
import numpy as np
data = np.arange(12)

print(data.shape)
# 12,
print(data[:,None])
print(data[:,None].shape)
# 12,1
print(data[None,:])
print(data[None,:].shape)
# 1,12
print(data.reshape(-1,1))
print(data.reshape(-1,1).shape)
# 12,1
print(data.reshape(1,-1))
print(data.reshape(1,-1).shape)
# 1,12
```

## 1次元化
```
import numpy as np
data = np.arange(12).reshape(-1,3)

# ravel reshapeは可能な限りviewを返すため、操作を行うと元のnp.ndarrayも影響を受ける
print(np.ravel(data))
print(np.reshape(data, -1))
# flattenは常にコピーを返すため、返却値に対して操作をしても元のnp.ndarrayは影響を受けない
print(data.flatten())
```