## 複数の
## プレゼンテーション

+++

GitPitchでは１つのGitリポジトリに１つのSlideURLが付与されるように出来ています。

しかし、１つのリポジトリで複数のスライドを管理したいこともあるかと思います。

GitPitchではこういった問題に対して幾つかの解決方法を提供しています。

+++

### Branch / Tag によるURL追加

+++

GitPitchではGitのBranchやTagに対してURLを付与する機能が備わっています。

例えば、__foo__というブランチがある場合、下記のURLでスライドのページへアクセスすることが出来るようになります。

__https://gitpitch.com/your-name/project/foo__

+++

### クエリによるスライドの切り替え

+++

GitPitchではリポジトリの下にディレクトリを作成すると、URLクエリ__"p"__に指定したディレクトリに作成された__PITCHME.md__を表示することが出来ます。

+++

例えば、下記のような構造のリポジトリだった場合…

<pre>
repository
  ├ slide1
  │ ├ PITCHME.md
  │ └ PITCHME.yaml
  └ slide2
    └ PITCHME.md
</pre>

+++

下記のURLでアクセスすることで、それぞれslide1、slide2のディレクトリ配下にあるPITCHME.mdのスライドページを表示することが出来ます。

- https://gitpitch.com/your-name/project?p=slide1
- https://gitpitch.com/your-name/project?p=slide2

> URLクエリpの前に __/__ を付与すると動作しなくなるので注意が必要です。
