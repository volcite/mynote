---
articleTitle: 【n8n初心者向け】YouTube API連携の関門！Credentials認証設定 完全マニュアル｜こま｜n8n × AIよろず屋
posted_at: 2025-10-19
posted_by: [[こま｜n8n × AIよろず屋]]
tags:
  - n8n
  - YouTubeAPI
  - GCP
  - 自動化
  - OAuth
aliases:
  - n8n YouTube連携
  - GCP Credentials設定
  - OAuth同意画面設定
  - YouTube Data API有効化
  - n8n認証エラー対策
---
## Transcript by AI
<details>
  <summary>文字起こし</summary>
---
title: "【n8n初心者向け】YouTube API連携の関門！Credentials認証設定 完全マニュアル｜こま｜n8n × AIよろず屋"
source: "https://note.com/ai_yorozuya/n/n48fc083ebfaf"
author:
  - "[[こま｜n8n × AIよろず屋]]"
published: 2025-10-19
created: 2026-01-21
description: "n8nでYouTubeの自動化ワークフローを組もうとした時、多くの人が最初に直面する難しい関門が「Credentials（認証情報）の設定」です。  特にGoogle Cloud Platform (GCP) の画面は機能が多く複雑で、「OAuth同意画面」や「リダイレクトURI」といった専門用語に戸惑い、設定を諦めてしまうケースも少なくありません。  この記事では、n8nでYouTube APIを使うためのGCP設定の手順を、何も知らない初心者でも0からできるように、画像や専門用語の意味を補いながら、超具体的に解説します。     【はじめに】GCPの前提条件とプロジェクトの確認"
tags:
  - "clippings"
---
![見出し画像](https://assets.st-note.com/production/uploads/images/223403385/rectangle_large_type_2_3d08a2de5e24486d80b3fe908eb9ed1d.png?width=1280)

## 【n8n初心者向け】YouTube API連携の関門！Credentials認証設定 完全マニュアル

[こま｜n8n × AIよろず屋](https://note.com/ai_yorozuya)

n8nでYouTubeの自動化ワークフローを組もうとした時、多くの人が最初に直面する難しい関門が「Credentials（認証情報）の設定」です。

特にGoogle Cloud Platform (GCP) の画面は機能が多く複雑で、「OAuth同意画面」や「リダイレクトURI」といった専門用語に戸惑い、設定を諦めてしまうケースも少なくありません。

この記事では、n8nでYouTube APIを使うためのGCP設定の手順を、何も知らない初心者でも0からできるように、画像や専門用語の意味を補いながら、超具体的に解説します。

  

## 【はじめに】GCPの前提条件とプロジェクトの確認

このマニュアルは、Google Cloud Platform (GCP)のアカウント登録と、基本的なプロジェクトの作成が完了していることを前提としています。 まだGCPのアカウント作成やプロジェクト作成が完了していない場合は、先にそれらの初期設定を済ませてください。

[**Google Cloud Platform** *Google Cloud Platform lets you build, deploy, and scale appli* *console.cloud.google.com*](https://console.cloud.google.com/welcome)

## 【ステップ1】YouTube Data APIを有効化する

まず、GCPで「YouTubeのデータを操作する機能」を使えるように許可を出します。

GCPダッシュボードの左上にあるサイドメニュー（三本線のアイコン）から「APIとサービス」 **にカーソルを合わせ、** 「ライブラリ」を選択します。

![画像](https://assets.st-note.com/img/1760836703-iQM5EHG3th9fY2RWyj8KubND.png?width=1200)

APIライブラリの検索窓に「Youtube」と入力して検索します。

![画像](https://assets.st-note.com/img/1760836766-N41zIYArEZymsoaBGwt3i728.png?width=1200)

検索結果から「YouTube Data API v3」を見つけてクリックします。

![画像](https://assets.st-note.com/img/1760836832-YM8mS4PNGaiTDOXuBAFgtpkl.png?width=1200)

次の画面で、青い「有効にする」ボタンをクリックします。

![画像](https://assets.st-note.com/img/1760836866-6aFik70RqoLptjxDUmnfMlIA.png?width=1200)

「APIが有効です」という趣旨の管理画面に遷移すれば、有効化は完了です。

![画像](https://assets.st-note.com/img/1760836934-U3GhJVMrgzWCAxmQI0oB24eE.png?width=1200)

## 【ステップ2】OAuth同意画面を設定する（最重要）

次に、「n8nという外部のアプリが、あなたのGoogleアカウントにアクセスすることを許可しますよ」という同意画面の「型」を作成します。 **この設定、特に「テストユーザー」の登録は、認証を成功させるために最も重要です。**

> ※すでに他のアプリ連携などで一度「OAuth同意画面」を設定したことがある方は、この手順を飛ばせる場合があります。

左側のメニューから「APIとサービス」 **の中にある** 「OAuth同意画面」を選択します。

  

![画像](https://assets.st-note.com/img/1760837219-BY4yjn9sMagv6CcdmRw5bxpZ.png?width=1200)

「開始」ボタンをクリックします

![画像](https://assets.st-note.com/img/1760837219-Ddu3xWmyte6UQh2kCJ1N9TPg.png?width=1200)

アプリ名は任意のアプリ名（ここでは「n8n-integration」とします）を入力して、ユーザーサポートメールはプルダウンで選択できるメールを選択します。次へボタンを押下します。

![画像](https://assets.st-note.com/img/1760837219-VYir18JCMETKD5dLytbe0Pmf.png)

「User Type」で「 **外部** 」を選択し、「次へ」をクリックします。 （※Google Workspaceアカウントを利用している場合は「内部」も選択できますが、個人利用の場合は「外部」で問題ありません。）

![画像](https://assets.st-note.com/img/1760837219-aiLRDTpeqKX8nOfZywgPtEIk.png?width=1200)

Googleからの連絡を受け取るメールアドレスを入力して、「次へ」ボタンを押下します。

![画像](https://assets.st-note.com/img/1760837219-z3QsDh8LUNORbFYf59mJvunq.png?width=1200)

ポリシーに同意して作成ボタンを押下します。

![画像](https://assets.st-note.com/img/1760837219-6utpUgksyKLR35fSB14N9VmI.png?width=1200)

## 【ステップ3】n8n用の「OAuthクライアントID」を作成する

次に、n8nだけがGCPと通信するために必要な「専用の鍵（クライアントIDとシークレット）」を作成します。 このステップでは、 **GCPとn8nの画面を両方開いて作業します。**

GCPの左側メニューから「APIとサービス」 **の中の** 「認証情報」をクリックします。

![画像](https://assets.st-note.com/img/1760837313-jV3MuT47DsgF9PbiIrx1ce5p.png?width=1200)

画面上部にある「+ 認証情報を作成」をクリックし、

![画像](https://assets.st-note.com/img/1760837348-pisKdo8xwJZT3mU01DWcke5R.png?width=1200)

OAuthクライアントIDをクリックします  
（※httpリクエストなどで使用するTokenはAPIキーを選択して作成してください。）

![画像](https://assets.st-note.com/img/1760837400-QRSduomEAHVbx3UItajhg0re.png?width=1200)

アプリケーションの種類から「webアプリケーション」を選択します。名前は適当な名前を付けます。

![画像](https://assets.st-note.com/img/1760837779-2v75XLxQq9Cz3ylHecmthWbN.png?width=1200)

「承認済みのリダイレクト URI」の項目

ここに、Googleでの認証後にn8nへ戻ってくるための「n8n側の住所（URL）」を登録します。

ここでn8nのダッシュボードに戻って、右上の「Create Workflow」の右の下矢印から「Create Credential」を選択。

![画像](https://assets.st-note.com/img/1760837735-CuQZhvsAdxOHTMVFRywt7J5S.png?width=1200)

「Youtube OAuth2 API」を検索して選択し、「Continue」をクリックします。

![画像](https://assets.st-note.com/img/1760837830-Epzqd7QlkUht5K3fMDX1NmO4.png?width=1200)

OAuth Redirect URLをコピーしてします。  
URLは **「https://oauth.n8n.cloud/oauth2/callback」** のようになっています。

![画像](https://assets.st-note.com/img/1760837883-1oCwURsq8rZ7n5EahLSmV2Hu.png?width=1200)

GCPの「承認済みのリダイレクト URI」の項目にある「+ URI を追加」をクリックします。表示された入力欄に、今n8nでコピーした「OAuth Redirect URL」をそのまま貼り付けます。

![画像](https://assets.st-note.com/img/1760837984-UbcdET2HG3V1Nl8Zmk4PfYCn.png?width=1200)

## 【ステップ4】n8nに「クライアントID」と「シークレット」を設定する

  

ステップ3で「作成」ボタンを押すと、GCPの画面に2つの重要な情報が表示されます。「クライアント ID」 **と** 「クライアント シークレット」がポップアップで表示されます。これがn8nに必要な「鍵」です。

![画像](https://assets.st-note.com/img/1760838122-EkshYSptGX4eTruLKbx6df2H.png)

**この2つの文字列を、それぞれ「コピー」ボタンでコピーし、メモ帳などに安全に貼り付けてください。** （「OK」を押して閉じても、後から認証情報画面で確認できます）

n8nに戻って

- **Client ID** の欄に、先ほどGCPでコピーした「クライアントID」を貼り付けます。
- **Client Secret** の欄に、「クライアントシークレット」を貼り付けます。
![画像](https://assets.st-note.com/img/1760838161-MZSJHOEeBVhw6aivIo4C3Xk9.png?width=1200)

## 【ステップ5】Googleアカウントで認証を完了する

n8nでClient ID/Secretを保存すると、画面に「Sign in with Google」というボタンが表示されます。これをクリックします。

Googleのログイン画面がポップアップで表示されます。

**【重要】** ここで、 **ステップ2で「テストユーザー」として登録したご自身のGoogleアカウント** を選択してください。

![画像](https://assets.st-note.com/img/1760838206-XLvijqm5xpKWdOE1VrTaHRfw.png?width=1200)

下記手順は一度実施している人は実施しなくて問題ないです  
ログインすると下記画面が表示されます。アクセスがブロックされますが、慌てないでください。

![画像](https://assets.st-note.com/img/1760838280-cxuyfdwrjY47TpgECSDkq8l3.png?width=1200)

## 【ステップ6】 テストユーザーを登録する

> ※すでに他のアプリ連携などで一度「テストユーザー」を設定したことがある方は、この手順を飛ばせる場合があります。

ナビゲーションメニューから **「APIとサービス」 > 「OAuth同意画面」** を選択

![画像](https://assets.st-note.com/img/1760838280-e4cvtiM7ZyK3UwnxOXafubjq.png?width=1200)

右のメニューの **「対象」** をクリックします

  

![画像](https://assets.st-note.com/img/1760838280-JrA2Mx6vFDt1agnC0T7ZsYQ8.png?width=1200)

テストユーザーを追加します。

![画像](https://assets.st-note.com/img/1760838280-mwarHMdGfcszCyU6AlEoe80Q.png?width=1200)

アカウント連携するGoogleのメアドを登録し「保存」をクリックします。

![画像](https://assets.st-note.com/img/1760838280-ljyV4FJfoTQYwCDE9pN6SPdq.png?width=1200)

再度n8nで「 **Sign in with Google** 」をクリックすると…下記画面で「続行」をクリックします。

  

![画像](https://assets.st-note.com/img/1760838279-eUOHXPksM1halJWxIdSb4AzQ.png)

どの権限を渡すか確認されるので、選択します。（基本すべて選択して問題ありません。）

![画像](https://assets.st-note.com/img/1760838280-kmZKShJCoqYTsz4jE7PpHXtW.png)

「Connection successful」と表示されれば、すべての連携は完了です！

![画像](https://assets.st-note.com/img/1760838279-bCVe2HsQycY1MAOz6ohBn3jG.png)

### 【おわりに】接続完了と次のステップ

「Connection successful」と表示されれば、すべての連携は完了です！

あなたはGCPという複雑な迷宮を突破し、n8nとYouTube APIを正しく接続できました。

これで、n8nのワークフロー内で「YouTube」ノードを自由に使い、新着動画の取得や動画情報の検索など、様々な自動化を構築する準備が整いました。

【n8n初心者向け】YouTube API連携の関門！Credentials認証設定 完全マニュアル｜こま｜n8n × AIよろず屋
</details>

## Summary
n8nでYouTubeの自動化ワークフローを構築する際、最大の難関となるGoogle Cloud Platform (GCP) での「Credentials（認証情報）」の設定手順を解説したマニュアルです。初心者がつまずきやすい専門用語や複雑な画面操作について、前提条件の確認から、「YouTube Data API v3」の有効化、OAuth同意画面の設定、クライアントIDとシークレットの取得、そしてn8n側への設定までをステップバイステップで説明しています。特に、認証を成功させるために不可欠な「テストユーザー」の登録手順についても詳しく触れています。

## Key Learning Points
*   **YouTube Data APIの有効化**: GCPの「APIとサービス」>「ライブラリ」から「YouTube Data API v3」を検索し、有効化する必要がある。
*   **OAuth同意画面の設定**: User Typeは個人利用の場合「外部」を選択する。
*   **n8nのリダイレクトURL設定**: n8nのCredentials作成画面で表示される「OAuth Redirect URL」を、GCPのOAuthクライアントID作成画面の「承認済みのリダイレクトURI」に正確にコピペする。
*   **クライアントIDとシークレット**: GCPで発行された2つの情報をn8nのCredentials設定に入力する。
*   **テストユーザーの登録**: 認証時のブロックを防ぐため、OAuth同意画面の設定で、自身のGoogleアカウントをテストユーザーとして追加することが最重要である。

## Key Message
n8nとYouTube APIの連携において、GCPの設定は複雑で諦めてしまう人も多いですが、手順通りに行えば初心者でも可能です。特に「OAuth同意画面」における「テストユーザー」の登録は認証成功の鍵となるため、忘れずに実施してください。