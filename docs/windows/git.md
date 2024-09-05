# Git

## インストール

Windowsにおいて、[App Installer](app-installer.md)のwingetを使って、Gitをインストールする方法を以下に示します。

```powershell
PS C:\Users\cat> winget install --id Git.Git
```

なお、インストール時に、「ユーザーアカウント制御: このアプリがデバイスに変更を加えることを許可しますか？」というダイアログが表示された場合、確認済みの発行元が、`winget show --id Git.Git` コマンドで確認した際の作成者と、一致することを確認してから、「はい」を選択します。

## 動作確認

Windows PowerShellを再起動してから、以下のコマンドを実行し、バージョンが表示されれば、インストールは完了しています。

```powershell
PS C:\Users\cat> git --version
git version 2.45.2.windows.1
```

## 設定

使い始める前に、ユーザ名やメールアドレスの設定が必要です。

## グローバル設定

次の例は、Gitのグローバル設定でユーザ名とメールアドレスを設定する方法です。もちろん、"Your Name"や"yourname@example.com"は自分のものに置き換えてください。

```powershell
git config --global user.name "Your Name"
```

```powershell
git config --global user.email "yourname@example.com"
```

グローバル設定は、 `C:\Users\%%\.gitconfig` に保存されています。これはただのテキストファイルです。

グローバル設定は、


## 簡単な使い方

基本的には `git --help` コマンドを頼りに使い方を調べます。

```powershell
PS C:\Users\cat> git --help
```

良く使うコマンド:

- git clone
	- Clone a repository into a new directory
- git init
	- Create an empty Git repository or reinitialize an existing o
- git add
	- Add file contents to the index
- git rm
	- Move or rename a file, a directory, or a symlink
- git log
	- Show commit logs
- git show
	- Show various types of objects
- git status
	- Show the working tree status
- git commit
	- Record changes to the repository
- git pull
	- Fetch from and integrate with another repository or a local branch
- git push
	- Update remote refs along with associated objects
