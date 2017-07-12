## Charts

+++

なんと、GitPitchでは簡単なグラフをコードで記述することが出来るのです！

GitPitchではマークダウンの中にHTMLを記述することが出来るのですが、HTMLでCanvasタグを記述し、その中にグラフのためのコードを記述することでグラフを作ることが出来ます。

+++

GitPitchはスライドの機能のために[reveal.js](http://lab.hakim.se/reveal-js/)というライブラリを利用しているのでうが、グラフ自体はこのreveal.jsの[プラグイン](https://github.com/rajgoel/reveal.js-plugins/tree/master/chart)を利用して描画されます。

どのようなコードを書けばいいかは、プラグインの設定を確認してください。

+++

以下に簡単なサンプルを示します。

以下のようなコードを書くと…

```
<canvas data-chart="line">
Month, January, February, March, April, May, June, July
First dataset, 65, 59, 80, 81, 56, 55, 40
Second dataset, 28, 48, 40, 19, 86, 27, 90
</canvas>
```

+++

このようにグラグを表示出来ます。

<canvas data-chart="line">
Month, January, February, March, April, May, June, July
First dataset, 65, 59, 80, 81, 56, 55, 40
Second dataset, 28, 48, 40, 19, 86, 27, 90
</canvas>

+++

この機能を利用するには__PITCHME.yaml__というファイルに設定を記述する必要があります。

__PITCHME.yaml__については後述します。
