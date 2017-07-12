## Moduler

+++

GitPitchでは外部のマークダウンファイルを読み込む機能が提供されています。

この機能のおかげで、多くのスライドページを作り込む時に一つのPITCHME.mdファイルが肥大化するのを防ぎ、
また、文書の構造化を手助けします。

+++

この機能は以下のように記述することで利用出来ます。

```
\---?include=path/to/any.md
```

+++

PATHはPITCHME.mdファイルをRootとして、そこからの相対パスで記述します。

たとえば下記のような構造だった場合、

<pre>
PITCHME.md
  └ md/
    ├ foo.md
    └ bar.md
</pre>

+++

下記のように読み込むことが出来ます。

```
# Title

\---?include=md/foo.md
\---?include=md/bar.md
```
