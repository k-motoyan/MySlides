## Web Components

カスタムエレメントというのはHTMLで独自の機能を持つタグのことです。

Note:
Polymerの話をする前に、Web Componentsについて概要を知っておいたほうがPolymerを理解する大きな手助けになります。

+++

## Web Componentsとは何？

> Web Componentsとは、HTMLの要素をカプセル化して再利用可能なパーツにするための**ブラウザのAPI群**です。
> <small>[cacoo blog web-components](https://nulab-inc.com/ja/blog/cacoo/web-components/) </small>

+++

## Web Componentsの構成技術

* CustomElement
* ShadowDom
* HTML imports
* HTML Template

Note:
Web Componentsはカスタムエレメント、シャドウドム、HTMLインポート、HTMLテンプレートの４つの機能から構成されています。

+++

## CustomElement
 
新しいDOM要素を生成するためのAPI

Note:
冒頭の例で出た、my-elementというタグを定義するAPI

+++

## ShadowDom

カスタムエレメントのスタイルをカプセル化するAPI

Note:
カスタムエレメントの内部のみに有効なスタイルを定義できるようにするAPI

+++

## HTML imports

外部のスクリプトなどを読み込むAPI

+++

## HTML Template

ページ読み込み時は利用されず、何らかの処理実行時に利用されるHTMLのタグ
