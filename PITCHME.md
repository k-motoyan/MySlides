# First time GitPitch

---

## GitPitch Overview

+++

GitPichはGitのホスティングサービスに置かれたマークダウンファイルからSlideを作成してくれるサービスです。

+++

現在、以下のホスティングサービスで利用することが出来ます。

- Github.com
- Gitlab.com
- Bitbucket.org
- Gitea.io
- Gogs.io

> OSS版のGitlabについてはよく分かりません。

+++

使い方は簡単！

Gitのホスティングサービスにリポジトリを作成し、__PITCHME.md__というマークダウンファイルをコミットしてリポジトリにPushすればいいだけです。

あとは

__https://gitpitch.com/your-name/project__

という形式のURLにアクセスするとスライドが表示されます。

---

## Markdown

+++

基本的には普通のマークダウンの形式で書けば問題ありません。

+++

ページの分割方法がちょっと特殊です。

__---__、__+++__というマークダウンでは水平線となる記述がページ分割の記号として取り扱われます。

+++

__---__は横方向へのページ分割となり、__+++__は縦方向へのページ分割となります。

__+++__は通常のスライドには無い概念なので、このスライドで感覚を掴んでください。

---

## Code Presenting

+++

GitPitchではコードを強調させながらスライドを展開することが出来ます。

+++

```
print("コードが")

print("強調")
print("されている！！")

print("なんと…")
```

@[1]
@[3-4]
@[6](注釈もつけられます！)

+++

この機能はコードブロックの下の行に__@[強調したい行数]__を記述することで利用することが出来ます。

複数の行数をまとめて指定したい場合には__@[n-m]__のような形式で記述することで対応出来ます。

+++

また、__@[行数]\(注釈\)__のように記述することで、コードブロック下部に注釈テキストを表示することも出来ます。

---

## Flagment

+++

GitPitchではテキストを順次表示していくような機能が提供されています。

- このように |
- 少しずつ |
- 表示することが出来ます。 |

+++

リストの末尾に__|__を付与することで機能を利用することが出来ます。

この機能は残念ながら、リスト表記に対してしか利用することは出来ません。

---

## Charts

なんと、GitPitchでは簡単なグラフをコードで記述することが出来るのです！

GitPitchではマークダウンの中にHTMLを記述することが出来るのですが、HTMLでCanvasタグを記述し、その中にグラフのためのコードを記述することでグラフを作ることが出来ます。

+++

GitPitchはスライドの機能のために[reveal.js](http://lab.hakim.se/reveal-js/)というライブラリを利用しているのでうが、グラフ自体はこのreveal.jsの[プラグイン](https://github.com/rajgoel/reveal.js-plugins/tree/master/chart)を利用して描画されます。

どのようなコードを書けばいいかは、プラグインの設定を確認してください。

+++

以下に簡単なサンプルを示します。

```
<canvas data-chart="line">
Month, January, February, March, April, May, June, July
First dataset, 65, 59, 80, 81, 56, 55, 40
Second dataset, 28, 48, 40, 19, 86, 27, 90
</canvas>
```

+++

<canvas data-chart="line">
Month, January, February, March, April, May, June, July
First dataset, 65, 59, 80, 81, 56, 55, 40
Second dataset, 28, 48, 40, 19, 86, 27, 90
</canvas>

---

## Settings

it works.
