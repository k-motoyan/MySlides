## motivation

+++

定型化した処理をいちいち生成する作業が面倒<br>
<dic class="flagment">→コマンド一発でファイルを自動生成（TargetやGroupも未作成なら生成してくれる）</div>

+++

Xcodeのバージョンによっては、実際のファイルパスとXcodeProjectのファイルの参照関係が壊れやすい<br>
<dic class="flagment">→ツールを通すことで常にファイルパスとXcodeProjectの参照関係が一定に保たれる</div>

+++

プロジェクトの基本的な設計情報の説明コストを下げたい<br>
<dic class="flagment">→`scaffold.yml`を見てもらえれば大体どんなアーキテクチャなのか見当がつく</div>

+++

その他ツール開発のためのユーティリティにも使える
