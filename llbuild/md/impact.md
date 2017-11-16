## iOSエンジニアへの影響

+++

llbuildはSwiftPackageManagerやXcode9のビルドシステムに搭載されていますが、iOSエンジニアにはどの程度影響があるのでしょうか？

+++

### ビルドパフォーマンスの向上

Xcode9のリリースに合わせて追加されたビルドシステムはパフォーマンスが向上しているという御触が出ました。

llbuildの哲学を考えると依存関係の多いプロジェクト（コードの中でimportの記述が多いプロジェクトと考えるといいかもしれません）、あるいは差分ビルドに対して大きなアドバンテージがあると推測出来ます。

Note:
Swiftのコンパイラが速くなったわけではないので、ライブラリ等を使わない純粋なコードのクリーンビルドには影響しないと思われます。

+++

### 切り替えのコスト

Xcodeのオプションで変更すればすぐに使えるので、コストはほぼ０と言っていいでしょう。

また、SwiftPackageMangerを使う場合、コマンドの裏側ではllbuildが動作しているので切り替え自体が必要ありません。