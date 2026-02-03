# PCへのGITのインストール

[https://git-scm.com/install/windows](https://git-scm.com/install/windows) からインストーラをダウンロードしてインストールするか、管理者権限でターミナルを起動し、Wingetを使ったインストールを行ってください。

```{admonition} 参考サイト
:class: tip

[https://note.com/yamato1220/n/n415b54947795](https://note.com/yamato1220/n/n415b54947795)
```

```{code} powershell
winget install --id Git.Git -e --source winget
```

## 初期設定

Gitのインストールが終わったら初期設定を行います。

まず、あなたの著者としてユーザ名とメールアドレスを設定します。これは、gitの変更履歴に記録される変更を行った開発者の名前として使用されます。

```{code} powershell
git config --global user.name "あなたの名前（ニックネームも可）"
```

```{code} powershell
git config --global user.email "あなたのメールアドレス"
```

新規作成するリポジトリの既定ブランチ名を main に設定します。公開リポジトリも幹は `main` ブランチですので、`main` と設定します。

```{code} powershell
git config --global init.defaultBranch main
```

## SSHの秘密鍵と公開鍵の作成

email　"email@example.com"　の部分はgithubに登録するメールアドレスとして次のコマンドを実行

```{code-block} powershell
ssh-keygen -t ed25519 -C "email@example.com"
```

```{code} powershell
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/????/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
```