## Sample

Note:
最後にPolymerを利用した場合の簡単なサンプルコードを見てみましょう。

+++

### polymer.json

```json
{
    "moduleResolution": "node"
}
```

Note:
Polymerのビルドを行うための設定ファイルです。
ここで載せた設定はPolymerのビルドを行う際に、npmでインストールしたモジュールのパスを解決する設定となります。

+++

### index.html

```html
<script src="https://cdn.jsdelivr.net/npm/@webcomponents/webcomponentsjs@2.0.2/webcomponents-bundle.min.js"></script>
<script type="module" src="src/components/my-element.js" crossorigin></script>
<my-element mood="happpy"></my-element>
```

@[1](webcomponents-bundle.min.jsは、webcomponentsに非対応ブラウザでもその機能を利用出来るようにするためのpolyfilです。)
@[2](カスタムエレメントを定義しているJavascriptを読み込みます、このときのtypeにはmoduleを指定します。)
@[3](カスタムエレメントを利用することを宣言します。)

Note:
１行目のwebcomponents-bundle.min.jsは、webcomponentsに非対応ブラウザでもその機能を利用出来るようにするためのpolyfilです。
２行目でカスタムエレメントを定義しているJavascriptを読み込みます、このときのtypeにはmoduleを指定します。
３行目でカスタムエレメントを利用することを宣言します。

+++

### my-element.js

```js
import { LitElement, html } from '@polymer/lit-element';

class MyElement extends LitElement {

  static get properties() {
    return {
      mood: String
    }
  }

  _render({ mood }) {
    return html`
      <style>
        .mood { color: green; }
      </style>

      Web Components are <span class="mood">${mood}</span>!
    `;
  }

}

customElements.define('my-element', MyElement);
```

@[3](LitElementというクラスを継承したオブジェクトを定義)
@[5-9](外部から渡ってくるプロパティを定義)
@[11-18](実際に描画されるスタイルやHTMLを定義、HTMLを定義するシンタックス自体はES6のTemplateStringを利用している)
@[23](作成したクラスをカスタムエレメントとしてWindowに登録)

Note:
※コードハイライトの注釈をそのまま話すのみに留める。
