# 配色

## viridisカラーマップ

viridisカラーマップは、Stéfan van der Walt ([@stefanv](https://github.com/stefanv)) 氏とNathaniel Smith ([@njsmith](https://github.com/njsmith)) 氏によって開発された[^1]。開発の経緯はSciPy 2015での発表[^2]を動画で確認できる[^3]。viridisカラーマップの定義はCC0ライセンスで [colormap/colormaps.py](https://github.com/BIDS/colormap/blob/master/colormaps.py) で公開されている[^3]。

viridisカラーマップは、Pythonの[Matplotlib](https://matplotlib.org/)においてバージョン1.5から導入され、バージョン2以降からはデフォルトのカラーマップとして設定されている[^3]。Rの[ggplot2](https://ggplot2.tidyverse.org/)には、viridisカラーマップを使うための関数が組み込まれている[^4]。

### 例

<figure markdown="span">
  ![Image title](../assets/tips/color-cmap_viridis.png){ loading=lazy }
  <figcaption>viridis Colormap</figcaption>
</figure>

```python
import numpy as np
import matplotlib
import matplotlib.pyplot as plt

gradient = np.linspace(0, 1, 256)
plt.imshow(
	X=np.vstack((gradient, gradient)),
	aspect=16,
	cmap=matplotlib.colormaps["viridis"],
)
plt.axis("off")
plt.savefig(
	fname="test_viridis_cmap.png",
	bbox_inches="tight",
	transparent=True,
)
```

<figure markdown="span">
  ![Image title](../assets/tips/color-palette_viridis.png){ loading=lazy }
  <figcaption>viridis Color Palette</figcaption>
</figure>

```python
import seaborn as sns
import matplotlib.pyplot as plt

palette = sns.color_palette(
    palette="viridis",
    n_colors=8,
    as_cmap=False,
).as_hex()
sns.palplot(palette)
plt.savefig(
    fname="test_viridis_palette.png",
    bbox_inches="tight",
    transparent=True,
)
```

[^1]: [Introduction to the viridis color maps](https://cran.r-project.org/web/packages/viridis/vignettes/intro-to-viridis.html)
[^3]: [matplotlib colormaps](https://bids.github.io/colormap/)
[^2]: [A Better Default Colormap for Matplotlib | SciPy 2015 | Nathaniel Smith and Stéfan van der Walt](https://www.youtube.com/watch?v=xAoljeRJ3lU)
[^4]: [Viridis colour scales from viridisLite — scale\_colour\_viridis\_d • ggplot2](https://ggplot2.tidyverse.org/reference/scale_viridis.html)

## Okabe-Itoカラーパレット

Okabe-Itoカラーパレットは、岡部正隆氏と伊藤啓氏が提案しているカラーパレットである[^5]。CUD (Color Universal Design) カラーパレットとよばれることもあるようだ。カラーユニバーサルデザイン機構（CUDO）が普及活動を行っており日本国内では良く知られているようだ。書籍『Fundamentals of Data Visualization』のデフォルトのカラースケールとして使用されていたことなどから、海外でも知られているようだ。

Okabe-Itoカラーパレットについて、海外で良く参照されている文献[^5]は最終更新日が2008年となっているが、カラーユニバーサルデザイン機構が公開しているカラーユニバーサルデザイン推奨配色セットは2018年にver.4に改定されており[^6]、若干数値が変わっているようだ。色数も異なるようだ。Matplotlibのチケットへのコメント[^9]などを見るに、英語版の公式の最新版の説明が必要とされているようだ。

Okabe-Itoカラーパレットは、書籍『Fundamentals of Data Visualization』のデフォルトカラースケールとして使用されている[^10]。この書籍は、[CC BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/legalcode)で公開されている[^10]。日本語版は『データビジュアライゼーションの基礎』という書名でオライリージャパンから出版されている[^11]。

Okabe-Itoカラーパレットは、Pythonの[Matplotlib](https://matplotlib.org/)においては、現在のところ自力でカラーマップを作成して使う必要があるようだ。一方、Rではバージョン4.0.0からカラーパレットの1つとしてOkabe-Itoが含まれている[^12]。

### 例

以下に、文献[^5]のカラーパレットを示す。

|No.|Color|Name|HEX[^7]|RGB[^8]|
|---|---|---|---|---|
|1| <span></span> { style='background-color:#000000;' }| Black         |#000000|rgb(0 0 0)      |
|2| <span></span> { style='background-color:#e69f00;' }| Orange        |#e69f00|rgb(230 159 0)  |
|3| <span></span> { style='background-color:#56b4e9;' }| Sky Blue      |#56b4e9|rgb(86 180 233) |
|4| <span></span> { style='background-color:#009e73;' }| Bluish Green  |#009e73|rgb(0 158 115)  |
|5| <span></span> { style='background-color:#f0e442;' }| Yellow        |#f0e442|rgb(240 228 66) |
|6| <span></span> { style='background-color:#0072b2;' }| Blue          |#0072b2|rgb(0 114 178)  |
|7| <span></span> { style='background-color:#d55e00;' }| Vermillion    |#d55e00|rgb(213 94 0)   |
|8| <span></span> { style='background-color:#cc79a7;' }| Reddish Purple|#cc79a7|rgb(204 121 167)|

<figure markdown="span">
  ![Image title](../assets/tips/color-palette_okabeito.png){ loading=lazy }
  <figcaption>Okabe-Ito Color Palette</figcaption>
</figure>

```python
import seaborn as sns
import matplotlib.pyplot as plt

palette = sns.color_palette(
    [
        "#000000",
        "#E69F00",
        "#56B4E9",
        "#009E73",
        "#F0E442",
        "#0072B2",
        "#D55E00",
        "#CC79A7",
    ]
)
sns.palplot(palette)
plt.savefig(
    fname="dest/okabeito_palette.png",
    bbox_inches="tight",
    transparent=True,
)
```


[^5]: [Color Universal Design (CUD) / Colorblind Barrier Free](https://jfly.uni-koeln.de/color/)
[^6]: [カラーユニバーサルデザイン推奨配色セットについて – NPO法人 カラーユニバーサルデザイン機構 CUDO](https://cudo.jp/?page_id=1565)
[^7]: HEX (hexadecimal): [hex-color - CSS: Cascading Style Sheets | MDN](https://developer.mozilla.org/docs/Web/CSS/hex-color)
[^8]: RGB (red-green-blue): [rgb-colors - CSS: Cascading Style Sheets | MDN](https://developer.mozilla.org/docs/Web/CSS/CSS_colors)
[^9]: [[ENH]: Add Universal Color Design categorical palette · Issue #27757 · matplotlib/matplotlib](https://github.com/matplotlib/matplotlib/issues/27757#issuecomment-1947666446)
[^10]: Claus O. Wilke, [Fundamentals of Data Visualization](https://clauswilke.com/dataviz/color-basics.html#color-as-a-tool-to-distinguish), 2019, ISBN:9781492031086.
[^11]: Claus O. Wilke 著、小林 儀匡、瀬戸山 雅人 訳、[データビジュアライゼーションの基礎―明確で、魅力的で、説得力のあるデータの見せ方・伝え方](https://www.oreilly.co.jp/books/9784873119533/)、2022、ISBN: 978-4-87311-953-3.
[^12]: [A New palette() for R - The R Blog](https://developer.r-project.org/Blog/public/2019/11/21/a-new-palette-for-r/)

## 用語の整理

- CVD (Color Vision Deficiency) or Color Blindness
	- [Types of Color Vision Deficiency | National Eye Institute](https://www.nei.nih.gov/learn-about-eye-health/eye-conditions-and-diseases/color-blindness/types-color-vision-deficiency)
	- [Colblindor – All about Color Blindness](https://www.color-blindness.com/)
- CUD (Color Universal Design)
	- [CUDとは – NPO法人 カラーユニバーサルデザイン機構 CUDO](https://cudo.jp/?page_id=74)
		- NPO法人カラーユニバーサルデザイン機構が提唱
		- > 人間の色覚の多様性に対応し、より多くの人に利用しやすい配色を行った製品や施設・建築物、サービス、情報を提供するという考え方を「カラーユニバーサルデザイン（略称CUD）」と呼びます。
	- CUDに基づいた配色
		- [Color Universal Design (CUD) / Colorblind Barrier Free](https://jfly.uni-koeln.de/color/)
		- [カラーユニバーサルデザイン推奨配色セット](https://jfly.uni-koeln.de/colorset/)
    - [色覚の呼称 – NPO法人 カラーユニバーサルデザイン機構 CUDO](https://cudo.jp/?page_id=84)	
		- CUDOは色覚型の5種類（C型、P型、D型、A型、T型）を対等に扱うことを提唱している。その上で、割合が最も多いC型を「一般色覚者」と呼び、C型色覚以外を色の対応の不十分な社会における弱者として「色・弱者（しきじゃくしゃ）」と呼んでいる。
	- CUDの考え方においては、色覚には多様性があり、全ての色覚のタイプはフラットに考える。仮に、特定のタイプの色覚がマイノリティであったとしても、それを異常とはよばない。つまり、CUDにおいては、「色覚異常に配慮した」という表現は誤りである。「色覚多様性に配慮した」と表現する。
- 色覚多様性（Color Vision Variation）
	- 日本遺伝学、[遺伝学用語改訂について](https://gsj3.org/wordpress_v2/wp-content/themes/gsj3/assets/docs/pdf/revisionterm_20170911.pdf)、2017-09-11
		- 色覚多様性は、日本遺伝学会が提案する呼称（概念）である。
		- 英語の「Color Blindness」を日本語では「色覚多様性」と改訂し、改訂後の邦訳を「Color Vision Variation」とする。
		- ここでの改訂は概念的な変更も有するように想像するが、同一の概念を指すものか、異なる概念を指すものかは、この「お知らせ」からは「→」で表現されているだけであり、明確に読み取れない。遺伝単を読むしかまいか。CUDOも色覚多様性という呼称を使用している。
	- 日本人類遺伝学会、[遺伝学用語改定のお知らせ](https://jshg.jp/wp-content/uploads/2017/08/d5fdc84ae83d3a9a6627b7ac249e4db0.pdf)、2017-09-26
		- これまで「彷徨変異」と呼称していた概念を「多様性（バリエーション、variation）」と改定した。
	- CUDOも色覚多様性という呼称を使用している。
		- [色覚多様性とは – NPO法人 カラーユニバーサルデザイン機構 CUDO](https://cudo.jp/?page_id=76)
	- 医学用語としてはどうか？
		- 調査中

## その他のリンク

- [Martin Krzywinski - Color Resources and Tools - Canada's Michael Smith Genome Sciences Centre](https://mk.bcgsc.ca/color/#projecthome)
- [Color blind friendly palettes for data visualizations with categories](https://thenode.biologists.com/data-visualization-with-flying-colors/research/)
- [Choosing color palettes — seaborn documentation](https://seaborn.pydata.org/tutorial/color_palettes.html)
- [Introduction to the viridis color maps](https://cran.r-project.org/web/packages/viridis/vignettes/intro-to-viridis.html)
- [Creating a colormap from a list of colors — Matplotlib documentation](https://matplotlib.org/stable/gallery/color/custom_cmap.html)