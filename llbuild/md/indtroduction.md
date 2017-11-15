## llbuildって何？

Note:
Xcode9のリリースに伴って、従来のビルドシステムのオプションとしてllbuildを利用したビルドが行えるようになりました。


+++

llbuildはビルドシステムを構築するためのライブラリセットです。

> llbuild is a set of libraries for building build systems.
> https://github.com/apple/swift-llbuild#llbuild より抜粋

+++

### ？？？

+++

llbuildはコマンドラインインターフェイスではなくAPIを使用してコンパイラのような外部ツールを統合し、より機能豊富なビルド環境を構築できるように設計されています。

> llbuild is designed to allow construction of more feature rich build environments which integrate external tools -- like the compiler -- using APIs instead of command line interfaces.
> https://github.com/apple/swift-llbuild#motivation より抜粋

+++

### つまり…

<div class="fragment">
llbuildとはプログラマブルなAPIを提供することで、IDEなどのツールにビルドシステムを統合するためのライブラリと捉えることが出来ます。
</div>
