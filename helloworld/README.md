# helloworld

A new Flutter project.

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.

## ここまでの流れ

任意の作業フォルダの中にVSCodeでFlutterプロジェクトを作成する。
作業フォルダについては、後述の環境構築のとこに書いている。

参考サイト

[05.HelloWorld｜Flutter実践入門](https://zenn.dev/kazutxt/books/flutter_practice_introduction/viewer/07_chapter1_helloworld)

作成されたサンプルアプリはブラウザでも動作する、カウンターアプリ。
ここからは、githubへコミットして、単体テストも実行できるように環境を構築していく。

## 環境構築

以下のコマンドをインストールする
- scoop
- hub
- gibo

参考サイト

[GitHub のコマンドラインツール「hub」の基本と便利な使い方のまとめ | DevelopersIO](https://dev.classmethod.jp/articles/hub/)  
[github/hub: A command-line tool that makes git easier to use with GitHub.](https://github.com/github/hub)  
[ScoopInstaller/Scoop: A command-line installer for Windows.](https://github.com/ScoopInstaller/Scoop)  

```powershell
Invoke-Expression (New-Object System.Net.WebClient).DownloadString('https://get.scoop.sh')
scoop --version
scoop update
scoop install hub
hub --version
scoop install gibo
gibo version
```

PowerShellでhubをgitのエイリアスに設定するのが公式だけど、明確にhubコマンドを利用する方針とするー

```powershell
Set-Alias git hub
```

## リポジトリ作成

作業フォルダを用意する(フォルダ名は任意、リポジトリ名になる)

```powershell
mkdir project-name
cd project-name
git config --global user.name ryohei-ochi-fr
git config user.name
git config --global user.email ryohei.ochi@futurerays.biz
git config user.email
git init
gibo update
gibo dump Node VisualStudioCode > .gitignore
echo "# github accesstoken file" >> .gitignore
echo ".accesstoken.ini" >> .gitignore

# これはやめた
echo "token = hogefuga" > .accesstoken
code .
```

githubで取得したアクセストークンを .accesstoken の token に書く(個人的なメモとして)

github に、リポジトリ(remote)を作成する

```powershell
hub create
```

`github.com username` メアドじゃないユーザ名 ryohei-ochi-fr
`github.com password` アクセストークン

```powershell
Error creating repository: Unauthorized (HTTP 401)
Bad credentials
```

認証エラーとなる場合はhubの設定ファイルを確認する

```powershell
type ~/.config/hub
```

エラーになっているけど、リポジトリは作成されているのでとりあえずヨシ

```powershell
github.com username: ryohei.ochi@futurerays.biz
github.com password for ryohei.ochi@futurerays.biz (never stored): 
Updating origin
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
error: Could not fetch origin
```

エラーが出なかったらヨシ

```powershell
PS > git remote -v
origin  https://github.com/ryohei-ochi-fr/helloworld.git (fetch)
origin  https://github.com/ryohei-ochi-fr/helloworld.git (push)
```

ブラウザでgithubにリモートリポジトリを確認する

```powershell
hub browse
````

## first commit

```powershell
git add .
git commit -m "first commit"
git status

git branch

git branch -m master
git push -u origin master
```



エラーの修正、urlを整える

```powershell
git remote set-url origin https://ryohei-ochi-fr@github.com/ryohei-ochi-fr/project-name.git
```




ブラウザでリモートリポジトリを確認する
```powershell
hub browse
```



