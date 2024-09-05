# App Installer（アプリインストーラー）

App Installerは、Microsoft Storeで配布されているMicrosoft公式のサイドローディング（sideloading）用ツールです。サイドローディングとは、Microsoft Storeなどの公式のアプリストアを経由せずにアプリをコンピュータにインストールする方法を指します。

Microsoft StoreからApp Installerをインストールすると、Windows PowerShellで `winget` コマンドを使用可能になります。

`winget` コマンドを使うと、Microsoft Storeに掲載されていないアプリを簡単にインストールしたりアップデートしたりできるようになります。

## インストール

1. Microsoft EdgeなどのWebブラウザで https://apps.microsoft.com/detail/9nblggh4nns1 にアクセスします。
2. Installをクリックします。するとMicrosoft Storeが起動し、App Installerのページが開きます。
3. Installをクリックします。指示に従ってインストールを完了させます。

## 動作確認

1. Windows PowerShellを起動します。
2. 以下のコマンドを実行して `winget` コマンドのバージョンが表示されればインストールは完了しています。念の為、補足しますが、ここで入力するのは `>` 以降の部分です。

```powershell
PS C:\Users\cat> winget --version
v1.8.1911
```

## 簡単な使い方

次のコマンドでヘルプを表示します。基本的にはこのヘルプを頼りに使い方を調べます。

```powershell
PS C:\Users\cat> winget --help
```

良く使うサブコマンドを示します。

- winget search - アプリを検索する。
- winget show - アプリの詳細を確認する。
- winget install - アプリをインストールする。
- winget upgrade - アプリをアップグレードする。

## 使用例

Google Chromeを `winget` コマンドでインストールする手順を例示します。

1. まず、Microsoft StoreでGoogle Chromeが掲載されていないか調べます。最初から `winget` コマンドで何でもインストールしようとしないでください。`winget` コマンドはサイドローディングを行うためのコマンドです。Microsoft公式のアプリストアからインストールできるならその方が良いでしょう。もし、目当てのアプリがMicrosoft Storeで配布されているので有れば、Microsoft Storeからインストールして終了です。今回は、Microsoft StoreにGoogle Chromeは掲載されていないので、 `winget` コマンドを使ってインストールすることにします。
2. 次のように `winget search` コマンドでGoogle Chromeを検索します。検索結果で表示されたアプリには、いくつかのバリエーションが存在しますが、ここではIDが `Google.Chrome` のアプリに目星をつけましょう。おっと、まだこの段階でインストールしようとしてはいけません。次のステップで詳細を確認しましょう。

```powershell
PS C:\Users\cat> winget search "Google Chrome"
名前                     ID                     バージョン    一致                       ソース
-----------------------------------------------------------------------------------------------
Google Chrome (EXE)      Google.Chrome.EXE      127.0.6533.73 ProductCode: google chrome winget
Google Chrome            Google.Chrome          127.0.6533.73                            winget
Google Chrome Beta       Google.Chrome.Beta     127.0.6533.57                            winget
Google Chrome Beta (EXE) Google.Chrome.Beta.EXE 127.0.6533.57                            winget
Google Chrome Canary     Google.Chrome.Canary   128.0.6613.0                             winget
Google Chrome Dev        Google.Chrome.Dev      128.0.6601.2                             winget
Google Chrome Dev (EXE)  Google.Chrome.Dev.EXE  128.0.6601.2                             winget
```

3. `winget show` コマンドでIDが `Google.Chrome` のアプリの詳細を確認します。ここで特に注目すべき点は、インストーラのURLです。この場合、URLのドメインが `dl.google.com` となっているので、Googleのドメインで運用されているWebサイトからインストーラがダウンロードされることが分かります。このURLのドメインが、アプリの配布元として正規のものかどうか、良く確認する必要があります。もし、怪しいURLの場合は、インストール作業をやめてください。

```powershell
PS C:\Users\cat> winget show --id Google.Chrome
見つかりました Google Chrome [Google.Chrome]
バージョン: 127.0.6533.73
公開元: Google LLC
発行元 URL: https://www.google.com/
発行元のサポート URL: https://support.google.com/
作成者: Google LLC
モニカー: chrome
説明: Chrome is the official web browser from Google, built to be fast, secure, and customizable.
ホーム ページ: https://www.google.com/chrome/
ライセンス: Freeware
ライセンス URL: https://www.google.com/chrome/terms/
プライバシー URL: https://policies.google.com/privacy
著作権: Copyright 2024 Google LLC. All rights reserved.
Documentation:
  Chrome Web Store: https://chromewebstore.google.com/
  Chrome for Developers: https://developer.chrome.com/
  Chrome Platform Status: https://chromestatus.com/
タグ:
  browser
  chromium
  fast
  internet
  safe
  search
  web
  webpage
インストーラー:
  インストーラーの種類: wix
  インストーラーの URL: https://dl.google.com/dl/chrome/install/googlechromestandaloneenterprise_arm64.msi
  インストーラーの SHA256: 05378ed1baa95427f6eb24aee558120162935993b3a64198ec1fd15ef2246b71
  オフライン配信をサポート: true
```

4. `winget install` コマンドを使って、IDが `Google.Chrome` のアプリをインストールします。以下にコマンドの実行例を示します。途中で「ユーザーアカウント制御」が起動し、「このアプリがデバイスに変更を加えることを許可しますか？」と判断を仰がれます。この時、「確認済みの発行元」が`winget show` コマンドで確認した作成者である「Google LLC」となっていることを確認してください。確認できれば「はい」を選択してインストールを進めます。処理が全て終わればインストールは完了です。

```powershell
PS C:\Users\cat> winget install --id Google.Chrome
```

5. もし、`winget` コマンドでインストールしたアプリをアップグレードしたい場合には、 `winget upgrade` コマンドが使えます。以下にGoogle Chromeをアップグレードする場合の例を示します。アップグレードしたいアプリのIDを指定します。なお、`winget upgrade` コマンドをオプション無しで実行すると、アップグレード可能なアプリの一覧が表示されます。

```powershell
PS C:\Users\cat> winget upgrade --id Google.Chrome
```