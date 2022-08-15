# matplotlib

## 解决中文乱码

```python
plt.rcParams[‘font.sans-serif’]=[‘SimHei’]
plt.rcParams[‘axes.unicode_minus’]=False
```

## 散点图绘制
```python
matplotlib.pyplot.scatter(x, y, s=None, c=None, marker=None, cmap=None, 
                          norm=None, vmin=None, vmax=None, alpha=None,
                          linewidths=None, *, edgecolors=None, 
                          plotnonfinite=False, data=None, **kwargs)
```
**参数说明**：

* `x，y`：`float or array-like`数据位置

* `s`：`loat or array-like`散点大小

* `c`：`array-like or list of colors or color`，标记颜色

  可能的值为：

  1. 要使用cmap和norm映射到颜色的n个数字的标量或序列
  2. 一个二维数组，其中的行是RGB
  3. 长度为n的颜色序列
  4. 单一颜色格式字符串

* `marker`：**default:** `'o'`，标记样式

  | marker                  | symbol                                                | description                   |
  | ----------------------- | ----------------------------------------------------- | ----------------------------- |
  | `"."`                   | ![m00](https://matplotlib.org/stable/_images/m00.png) | point                         |
  | `","`                   | ![m01](https://matplotlib.org/stable/_images/m01.png) | pixel                         |
  | `"o"`                   | ![m02](https://matplotlib.org/stable/_images/m02.png) | circle                        |
  | `"v"`                   | ![m03](https://matplotlib.org/stable/_images/m03.png) | triangle_down                 |
  | `"^"`                   | ![m04](https://matplotlib.org/stable/_images/m04.png) | triangle_up                   |
  | `"<"`                   | ![m05](https://matplotlib.org/stable/_images/m05.png) | triangle_left                 |
  | `">"`                   | ![m06](https://matplotlib.org/stable/_images/m06.png) | triangle_right                |
  | `"1"`                   | ![m07](https://matplotlib.org/stable/_images/m07.png) | tri_down                      |
  | `"2"`                   | ![m08](https://matplotlib.org/stable/_images/m08.png) | tri_up                        |
  | `"3"`                   | ![m09](https://matplotlib.org/stable/_images/m09.png) | tri_left                      |
  | `"4"`                   | ![m10](https://matplotlib.org/stable/_images/m10.png) | tri_right                     |
  | `"8"`                   | ![m11](https://matplotlib.org/stable/_images/m11.png) | octagon                       |
  | `"s"`                   | ![m12](https://matplotlib.org/stable/_images/m12.png) | square                        |
  | `"p"`                   | ![m13](https://matplotlib.org/stable/_images/m13.png) | pentagon                      |
  | `"P"`                   | ![m23](https://matplotlib.org/stable/_images/m23.png) | plus (filled)                 |
  | `"*"`                   | ![m14](https://matplotlib.org/stable/_images/m14.png) | star                          |
  | `"h"`                   | ![m15](https://matplotlib.org/stable/_images/m15.png) | hexagon1                      |
  | `"H"`                   | ![m16](https://matplotlib.org/stable/_images/m16.png) | hexagon2                      |
  | `"+"`                   | ![m17](https://matplotlib.org/stable/_images/m17.png) | plus                          |
  | `"x"`                   | ![m18](https://matplotlib.org/stable/_images/m18.png) | x                             |
  | `"X"`                   | ![m24](https://matplotlib.org/stable/_images/m24.png) | x (filled)                    |
  | `"D"`                   | ![m19](https://matplotlib.org/stable/_images/m19.png) | diamond                       |
  | `"d"`                   | ![m20](https://matplotlib.org/stable/_images/m20.png) | thin_diamond                  |
  | `"|"`                   | ![m21](https://matplotlib.org/stable/_images/m21.png) | vline                         |
  | `"_"`                   | ![m22](https://matplotlib.org/stable/_images/m22.png) | hline                         |
  | `0` (`TICKLEFT`)        | ![m25](https://matplotlib.org/stable/_images/m25.png) | tickleft                      |
  | `1` (`TICKRIGHT`)       | ![m26](https://matplotlib.org/stable/_images/m26.png) | tickright                     |
  | `2` (`TICKUP`)          | ![m27](https://matplotlib.org/stable/_images/m27.png) | tickup                        |
  | `3` (`TICKDOWN`)        | ![m28](https://matplotlib.org/stable/_images/m28.png) | tickdown                      |
  | `4` (`CARETLEFT`)       | ![m29](https://matplotlib.org/stable/_images/m29.png) | caretleft                     |
  | `5` (`CARETRIGHT`)      | ![m30](https://matplotlib.org/stable/_images/m30.png) | caretright                    |
  | `6` (`CARETUP`)         | ![m31](https://matplotlib.org/stable/_images/m31.png) | caretup                       |
  | `7` (`CARETDOWN`)       | ![m32](https://matplotlib.org/stable/_images/m32.png) | caretdown                     |
  | `8` (`CARETLEFTBASE`)   | ![m33](https://matplotlib.org/stable/_images/m33.png) | caretleft (centered at base)  |
  | `9` (`CARETRIGHTBASE`)  | ![m34](https://matplotlib.org/stable/_images/m34.png) | caretright (centered at base) |
  | `10` (`CARETUPBASE`)    | ![m35](https://matplotlib.org/stable/_images/m35.png) | caretup (centered at base)    |
  | `11` (`CARETDOWNBASE`)  | ![m36](https://matplotlib.org/stable/_images/m36.png) | caretdown (centered at base)  |
  | `"None"`, `" "` or `""` |                                                       | nothing                       |

* `alpha`：`float`，透明度。0-1。
