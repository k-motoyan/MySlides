## 使ってみる

+++

llbuildは次の３つから利用方法を選択することが出来ます。

+++

### llbuild Command Line Tool

llbuildの機能をコマンドラインから扱うためのツールです。

主に、Ninjaでビルドを行っていたプロダクトをllbuildがホストするために使うようです。

Note:
llbuildのcoreがninjaと差し替え可能であるということを実現することで、自身のcoreシステムの妥当性の証明に利用できること、また、ninjaとllbuildの性能比較に使うことができるというメリットがあるようです。

+++

### swift-build-tool (Command Line Tool)

SwiftPackageManagerで利用されるビルドシステムのコマンドラインツールです。

これはCLIツールの`swiftc`をプログラミング可能なレベルに抽象化したツールであり、これを更にSwiftPackageManagerが抽象化して利用することになります。

Note:
SwiftPackageManagerの開発に携わらないかぎり、この存在は意識する必要がなさそうです。

+++

### libllbuild Library

llbuildのC APIです。

C言語のAPIを呼び出す他に、Swift、Pythonの言語バインディングが用意されておりこれらの言語からllbuildの機能を呼び出すことも可能です。

Note:
Xcode9で新たに追加されたビルドシステムはこのlibllbuildを利用して構築されているとのことです。
Swift、Pythonともに提供されるのはCoreコンポーネントの機能だけで、BuildSystemへのバインディングは現時点では提供されていません。

+++

### Xcodeプロジェクトでllbuildを使ってみる

+++

以下の手順でllbuildを利用するためのプロジェクトを作成します。

1. llbuildプロジェクトのコードをgithubから取得
2. Xcodeプロジェクトを開いて、llbuild.frameworkターゲットをビルド
3. Xcodeで適当なプロジェクトを作成
4. 2でビルドしたllbuild.frameworkをプロジェクトに配置
5. llbuiildプロジェクトの`products/swift-bindings/llbuild.swift`をプロジェクトの中にコピー

Note:
書いてあるとおりなので、説明は省略してもいい。

+++

### コードを書く前にビルドに必要な機能を確認

+++

#### Task

計算処理の進行の管理を行う。

+++

```
final class MyTask: Task {
    func start(_ engine: TaskBuildEngine) {
        // タスクの開始処理
    }

    func provideValue(_ engine: TaskBuildEngine, inputID: Int, value: Value) {
        // 依存入力の出力を解決する処理
    }

    func inputsAvailable(_ engine: TaskBuildEngine) {
        // メイン入力の完了処理
    }
}
```

@[1](Taskプロトコルに準拠させます)
@[2-4](タスクの開始、依存する入力がある場合ビルドエンジンに入力を処理するよう登録する)
@[6-8](各入力の出力を処理します)
@[10-12](入力の完了処理、ここで依存入力の出力を元にRuleから渡された計算処理を行います)

+++

#### Rule

実行可能な計算の要素。

+++

```
final class MyRule: Rule {
    func createTask() -> Task {
        return MyTask()
    }
}
```

@[1](Ruleプロトコルに準拠させます)
@[2-4](タスクを生成します)

+++

#### BuildEngineDelegate

ビルドに関するルールを登録し、ビルドを実行する。

+++

```
final class MyBuildEngineDelegate: BuildEngineDelegate {
    func lookupRule(_ key: Key) -> Rule {
        switch key.toString() {
        case "initialize":
            return MyRule([]) { /* 処理 */ }
        case "compile":
            return MyRule([Key("initialize")]) { /* 処理 */ }
        case "run":
            return MyRule([Key("initialize"), Key("compile")]) { /* 処理 */ }
        default:
            fatalError("unexpected key.")
        }
    }
}
```

@[1](BuildEngineDelegateプロトコルに準拠させます)
@[3-12](Keyに対するビルドルールを実行します)

+++

これらの処理は以下のようにして起動します。

```
let delegate = MyBuildEngineDelegate()
let engine = BuildEngine(delegate: delegate)

let key = Key("run")
let result = engine.build(key: key)
```

@[1-2](ビルドエンジンを生成します)
@[4](実行するビルドルールを指定します)
@[5](ビルドを実行し、結果を受け取ります)

+++

実際に動かしてみましょう

Note:
ここでXcodeに画面を変えて、ビルドしてみる。

+++

このコードはGithubにアップされているので興味のある方は確認してみてください。

https://github.com/k-motoyan/llbuild-sample
