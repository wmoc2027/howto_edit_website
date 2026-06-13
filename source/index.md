# WMOC2027 オリエンテーリング大会公式WEBサイト編集マニュアル

## 概要

このサイトは静的サイトジェネレータ[Hugo](https://gohugo.io/)により構築された [wmoc2027の公式WEBサイト](https://wmoc2027.jp/)の編集方法について説明するドキュメントです。
静的サイトジェネレータとは、あらかじめ用意したソースファイル（命令言語でWEBサイトのデザインを定義する専用のテキストファイル）に基づいて、WEBサイトを生成するシステムです。Hugoはいくつかある方式の一種で、次のサイトにあるように同じソースファイルからさまざまなデザインのWEBサイトを生成することができます。

```{note}
[Hugoのテーマ一覧](https://themes.gohugo.io/)
```

WMOC2027では、この中から[Hinode](https://gethinode.com/)テーマを使ってサイトを構築しています。本サイトでは、このHinodeテーマを使ったWEBサイト記述方法、管理方法について説明し、WMOC2027のイベント運営に即したユースケースに基づいたマニュアルを紹介します。

## 準備

WEBサイトを編集するためには、いくつかの環境準備が必要となります。

### GithubとGithub pages の扱い方

前述のとおり、あらかじめマークアップ言語 Markdown で作成したHugoのプロジェクトをHTMLへ変換してWEB公開します。元となるHugoのプロジェクトは以下のWMOC2027のGithubリポジトリに格納しています。

[https://github.com/wmoc2027/public_website](https://github.com/wmoc2027/public_website)

リポジトリとは、Git上で扱われるファイル構成の管理単位です。Githubではアカウント毎に[複数のリポジトリを保持することができます](https://github.com/orgs/wmoc2027/repositories)。公式WEBサイトのリポジトリは、`wmoc2027` アカウント内に、 `public_website` という名前のリポジトリとして管理されていることがわかります。

このリポジトリのファイル構成が元となり、hugoのビルドシステムによってHTML変換が行われ、公式WEBサイトとして公開されます。この一連の変換動作は、Github Actions という仕組みで自動実行されます。リポジトリ上のファイルの変更を検出すると、Github Actionsの定義ファイルに基づいて自動変換とWEBサイトへの反映が行われます。

```{admonition} Gihub pagesを生成する仕組み
:class: tip

Github Actionsは、プロジェクトファイル中の `.github` フォルダ以下に格納された[Github Actions定義yamlファイル](https://github.com/wmoc2027/public_website/blob/main/.github/workflows/hugo.yml) のとおり、次のセクションで定義したジョブが実行されます。ジョブの実行状態や実行結果は[こちら](https://github.com/wmoc2027/public_website/actions) で確認できます。

`Jobs.build` セクション
    : Ubuntu Linuxコンテナ上にHugoをインストールしたコンテナが起動し、リポジトリ上のプロジェクトファイルを処理してHTMLに変換します。変換されたHTMLファイルは、 [upload-pages-artifact](https://github.com/actions/upload-pages-artifact) アクションを通じてパッケージ化されます。


`Jobs.deploy` セクション
    : `jobs.build` が終了したことを確認した上で作成したアーティファクトパッケージをGithubが提供するホスティングサービス [Github pages](https://docs.github.com/ja/pages/getting-started-with-github-pages/what-is-github-pages) 上にデプロイ（配置）します。ここで使用されるアクションは、[deploy-pages](https://github.com/actions/deploy-pages) アクションを通じて行います。さらに、ホスティングされたWEBサーバは、ドメインネームシステムにより "wmoc2027.jp" に解決することで [https://wmoc2027.jp/](https://wmoc2027.jp/) で公開されます。

[参考](https://docs.github.com/ja/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site#%E3%82%AB%E3%82%B9%E3%82%BF%E3%83%A0-github-actions-%E3%83%AF%E3%83%BC%E3%82%AF%E3%83%95%E3%83%AD%E3%83%BC%E3%81%AB%E3%82%88%E3%82%8B%E5%85%AC%E9%96%8B) 
```

#### GithubリポジトリのForkとプルリクエスト

前項のとおりリポジトリ [https://github.com/wmoc2027/public_website](https://github.com/wmoc2027/public_website) の内容を変更すると、自動的にhugoによるビルドが始まり、この内容がWEBサイトへ反映されます。このままでは何らレビューされることなく編集者の編集内容が直接公開されてしまいます。

これを防ぐため、編集者となる皆さんは、まず Gihub のアカウントを作成し、このアカウント上に[フォーク](https://docs.github.com/ja/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo)した `public_website` を編集します。

![](assets/fork_pullreq.svg){align=center}

図の例では、editor1, editor2の各アカウントにおいて、 `wmoc2027` アカウントの `public_website` リポジトリからそれぞれフォークを行うと `editor1/public_website`, `editor2/public_website` が生成されます。

これらのフォークしたリポジトリでも Github Actions による Github pages の設定を有効にします。これにより独自のURLで生成されたHTMLをプレビューすることができます。

```{code-block}
:caption: Github pagesでホスティングされるURL

https://<アカウント名>.github.io/<リポジトリ名>
```

このURLを関係者内にシェアしてレビューを行い、問題なければ、`wmoc2027` アカウントに反映を行います。フォーク元であるwmoc2027アカウントに編集内容を反映することを、 **プルリクエスト** と言います。

全体の編集の流れは以上の通りとなります。次節から、Gitのインストールや初期設定、編集ツールなど個々の設定手順について説明します。

```{toctree}
:maxdepth: 3
:numbered: 2
:caption: 目次

environment/index.md
contents_edit/index.md
```
