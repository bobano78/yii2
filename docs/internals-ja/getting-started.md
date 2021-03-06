Yii2 の開発を始めよう
=====================

1. yii2 のフォークをクローンします `git clone git@github.com:<yourname>/yii2.git`.
2. レポジトリのフォルダに入ります `cd yii2`.
3. `./build/build app/link basic` を実行して、ベーシックアプリケーションのための composer 依存パッケージをインストールします。
  このコマンドは外部 Comopser パッケージを通常通りインストールしますが、yii2 のレポジトリは、現在チェックアウトされているレポジトリにリンクさせます。
  従って、全てのコードの一つのインスタンスをインストールしたことになります。
4. 必要であれば、アドバンストアプリケーションのためにも同様にします。
  `./build/build app/link advanced`
  このコマンドは、依存パッケージを更新するためにも使用することが出来ます。
  このコマンドは内部的に `composer update` を実行します。
5. 以上で、Yii 2 をハックするための作業用環境が手に入りました。

最新の変更を pull するために yii2 の upstream レポジトリを追加することが出来ます。

```
git remote add upstream https://github.com/yiisoft/yii2.git
```

プルリクエストの作成に関する詳細は、[Yii 2 寄稿者のための Git ワークフロー](git-workflow.md) を参照してください。

単体テスト
----------

単体テストを走らせるためには、dev-repo のための composer パッケージをインストールする必要があります。
`composer update` をレポジトリのルートディレクトリで実行して、最新のパッケージを取得してください。

そうすれば、`phpunit` を走らせて単体テストを実行することが出来ます。

テストを現在取り組んでいる一群のテストだけに制限することが出来ます。
例えば、バリデータと redis のためだけにテストを実行するには、`phpunit --group=validators,redis` とします。

エクステンション
----------------

エクステンションに対して作業をするためには、それを使用するアプリケーションの中にエクステンションをインストールする必要があります。
通常と同じように `composer.json` にエクステンションを追加します。
例えば、`"yiisoft/yii2-redis": "*"` をベーシックアプリケーションの `require` セクションに追加します。
`./build/build app/link basic` を実行すると、エクステンションとその依存パッケージがインストールされます。
そして `extensions/redis` にシンボリックリンクが作成され、composer の vendor ディレクトリではなく、yii2 レポジトリで直接に作業することが出来るようになります。


アプリケーションの機能テストと承認テスト
----------------------------------------

Codeception のテストを実行する方法について学習するために `apps/advanced/tests/README.md` および `apps/basic/tests/README.md` を参照してください。
