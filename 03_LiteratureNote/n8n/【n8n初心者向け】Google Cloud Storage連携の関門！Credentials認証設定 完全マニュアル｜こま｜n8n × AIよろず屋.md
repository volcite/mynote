---
articleTitle: "【n8n初心者向け】Google Cloud Storage連携の関門！Credentials認証設定 完全マニュアル"
posted_at: 2025-12-09
posted_by: "こま｜n8n × AIよろず屋"
tags:
  - n8n
  - GoogleCloudPlatform
  - GoogleCloudStorage
  - 自動化
  - 認証設定
  - マニュアル
aliases:
  - n8nとGCPの連携手順
  - Google Cloud StorageのCredentials設定
  - OAuth同意画面の設定方法
  - n8nのOAuth認証設定
  - GCPバケット作成と権限設定
---
## Transcript by AI
<details>
  <summary>文字起こし</summary>
  
---
title: "【n8n初心者向け】Google Cloud Storage連携の関門！Credentials認証設定 完全マニュアル｜こま｜n8n × AIよろず屋"
source: "https://note.com/ai_yorozuya/n/n24ead1a8783d"
author:
  - "[[こま｜n8n × AIよろず屋]]"
published: 2025-12-09
created: 2026-01-21
description: "n8nで自動化ワークフローを組もうとした時、多くの人が最初に直面する難しい関門が「Credentials（認証情報）の設定」です。  特にGoogle Cloud Platform (GCP) の画面は機能が多く複雑で、「OAuth同意画面」や「リダイレクトURI」といった専門用語に戸惑い、設定を諦めてしまうケースも少なくありません。  この記事では、n8nでGoogle Cloud Storageを使うためのGCP設定の手順を、何も知らない初心者でも0からできるように、画像や専門用語の意味を補いながら、超具体的に解説します。     【はじめに】GCPの前提条件とプロジェクトの確認"
tags:
  - "clippings"
---
![見出し画像](https://assets.st-note.com/production/uploads/images/235164720/rectangle_large_type_2_b2f037705ce554aaab03d728c504eef6.png?width=1280)

## 【n8n初心者向け】Google Cloud Storage連携の関門！Credentials認証設定 完全マニュアル

[こま｜n8n × AIよろず屋](https://note.com/ai_yorozuya)

n8nで自動化ワークフローを組もうとした時、多くの人が最初に直面する難しい関門が「Credentials（認証情報）の設定」です。

特にGoogle Cloud Platform (GCP) の画面は機能が多く複雑で、「OAuth同意画面」や「リダイレクトURI」といった専門用語に戸惑い、設定を諦めてしまうケースも少なくありません。

この記事では、n8nでGoogle Cloud Storageを使うためのGCP設定の手順を、何も知らない初心者でも0からできるように、画像や専門用語の意味を補いながら、超具体的に解説します。

  

## 【はじめに】GCPの前提条件とプロジェクトの確認

このマニュアルは、Google Cloud Platform (GCP)のアカウント登録と、基本的なプロジェクトの作成が完了していることを前提としています。 まだGCPのアカウント作成やプロジェクト作成が完了していない場合は、先にそれらの初期設定を済ませてください。

[**Google Cloud Platform** *Google Cloud Platform lets you build, deploy, and scale appli* *console.cloud.google.com*](https://console.cloud.google.com/welcome)

## 【ステップ1】Google Cloud Storageを有効化する

まず、GCPで「Google Cloud Storageを操作する機能」を使えるように許可を出します。

GCPダッシュボードの左上にあるサイドメニュー（三本線のアイコン）から「APIとサービス」 **にカーソルを合わせ、** 「ライブラリ」を選択します。

![画像](https://assets.st-note.com/img/1765271849-ukrJG6cgjdCz04aTvAFmlNSp.png?width=1200)

APIライブラリの検索窓に「Google Cloud Storage」と入力して検索します。

![画像](https://assets.st-note.com/img/1765272000-hPSTXH0U1fzZVMq8kWg76Go3.png?width=1200)

検索結果から「Google Cloud Storage」を見つけてクリックします。

![画像](https://assets.st-note.com/img/1765272041-tp1cBs7PZ9M3O50lAdGXUFhb.png?width=1200)

次の画面で、青い「有効にする」ボタンをクリックします。  
※下記の画像は有効後の状態です

![画像](https://assets.st-note.com/img/1765272067-3C2jHk8d5aeg0VuDMULNwPi7.png?width=1200)

「APIが有効です」という趣旨の管理画面に遷移すれば、有効化は完了です。

## 【ステップ2】OAuth同意画面を設定する（最重要）

次に、「n8nという外部のアプリが、あなたのGoogleアカウントにアクセスすることを許可しますよ」という同意画面の「型」を作成します。 **この設定、特に「テストユーザー」の登録は、認証を成功させるために最も重要です。**

> ※すでに他のアプリ連携などで一度「OAuth同意画面」を設定したことがある方は、この手順を飛ばせる場合があります。

左側のメニューから「APIとサービス」 **の中にある** 「OAuth同意画面」を選択します。

  

![画像](https://assets.st-note.com/img/1765271850-lvt1FCSxrQ4K5ajPXL3guJq9.png?width=1200)

「開始」ボタンをクリックします

![画像](https://assets.st-note.com/img/1765271849-MlURTmHEBay5rNQsD2FfSnGp.png?width=1200)

アプリ名は任意のアプリ名（ここでは「n8n-integration」とします）を入力して、ユーザーサポートメールはプルダウンで選択できるメールを選択します。次へボタンを押下します。

![画像](https://assets.st-note.com/img/1765271849-1r6JDzXfSCmpAWHPRMsxh2dt.png)

「User Type」で「 **外部** 」を選択し、「次へ」をクリックします。 （※Google Workspaceアカウントを利用している場合は「内部」も選択できますが、個人利用の場合は「外部」で問題ありません。）

![画像](https://assets.st-note.com/img/1765271849-R1koYmanIj8SEKpX0HQyBvVg.png?width=1200)

Googleからの連絡を受け取るメールアドレスを入力して、「次へ」ボタンを押下します。

![画像](https://assets.st-note.com/img/1765271849-qeQsApoj3uk0bgncCWX6OZz4.png?width=1200)

ポリシーに同意して作成ボタンを押下します。

![画像](https://assets.st-note.com/img/1765271849-erA579c3u4DW0pUwsCyBIXaL.png?width=1200)

## 【ステップ3】n8n用の「OAuthクライアントID」を作成する

次に、n8nだけがGCPと通信するために必要な「専用の鍵（クライアントIDとシークレット）」を作成します。 このステップでは、 **GCPとn8nの画面を両方開いて作業します。**

GCPの左側メニューから「APIとサービス」 **の中の** 「認証情報」をクリックします。

![画像](https://assets.st-note.com/img/1765271849-UaMfkBXlnCh54g1LVZWISKsO.png?width=1200)

画面上部にある「+ 認証情報を作成」をクリックし、

![画像](https://assets.st-note.com/img/1765271850-Es3OK1qm4huAzdyCkwISL7DW.png?width=1200)

OAuthクライアントIDをクリックします  
（※httpリクエストなどで使用するTokenはAPIキーを選択して作成してください。）

![画像](https://assets.st-note.com/img/1765271850-Bz5PfOsldjAQm71qZJCSW09p.png?width=1200)

アプリケーションの種類から「webアプリケーション」を選択します。名前は適当な名前を付けます。

![画像](https://assets.st-note.com/img/1765271849-RzEyYnPUIgrhwfZ3FlupckqG.png?width=1200)

「承認済みのリダイレクト URI」の項目

ここに、Googleでの認証後にn8nへ戻ってくるための「n8n側の住所（URL）」を登録します。

ここでn8nのダッシュボードに戻って、右上の「Create Workflow」の右の下矢印から「Create Credential」を選択。

![画像](https://assets.st-note.com/img/1765271850-aVPvdALMKnqEi6Ypre8gC4H0.png?width=1200)

「Google Cloud Storage」を検索して選択し、「Continue」をクリックします。

![画像](https://assets.st-note.com/img/1765272157-HUrNcKuESGRnJhet6zmBZf9p.png?width=1200)

OAuth Redirect URLをコピーしてします。  
URLは **「https://oauth.n8n.cloud/oauth2/callback」** のようになっています。

![画像](https://assets.st-note.com/img/1765272201-ElViAzW5XQyx9K0ZNIpqg24m.png?width=1200)

GCPの「承認済みのリダイレクト URI」の項目にある「+ URI を追加」をクリックします。表示された入力欄に、今n8nでコピーした「OAuth Redirect URL」をそのまま貼り付けます。

![画像](https://assets.st-note.com/img/1765271849-NxdnEewSKfo192BmUszvp0ZV.png?width=1200)

## 【ステップ4】n8nに「クライアントID」と「シークレット」を設定する

  

ステップ3で「作成」ボタンを押すと、GCPの画面に2つの重要な情報が表示されます。「クライアント ID」 **と** 「クライアント シークレット」がポップアップで表示されます。これがn8nに必要な「鍵」です。

![画像](https://assets.st-note.com/img/1765271849-o726SWAlre5mHiwMdgFG3YQR.png)

**この2つの文字列を、それぞれ「コピー」ボタンでコピーし、メモ帳などに安全に貼り付けてください。** （「OK」を押して閉じても、後から認証情報画面で確認できます）

n8nに戻って

- **Client ID** の欄に、先ほどGCPでコピーした「クライアントID」を貼り付けます。
- **Client Secret** の欄に、「クライアントシークレット」を貼り付けます。
![画像](https://assets.st-note.com/img/1765272263-JnqcQdRG8huPD41gMI5eAwNo.png?width=1200)

## 【ステップ5】Googleアカウントで認証を完了する

n8nでClient ID/Secretを保存すると、画面に「Sign in with Google」というボタンが表示されます。これをクリックします。

Googleのログイン画面がポップアップで表示されます。

**【重要】** ここで、 **ステップ2で「テストユーザー」として登録したご自身のGoogleアカウント** を選択してください。

![画像](https://assets.st-note.com/img/1765272319-czqgkjyN71f3Ob6pw04mPIQG.png?width=1200)

下記手順は一度実施している人は実施しなくて問題ないです  
ログインすると下記画面が表示されます。アクセスがブロックされますが、慌てないでください。

![画像](https://assets.st-note.com/img/1765271849-CPrEORsHB18D4S0Zf7KatAvM.png?width=1200)

## 【ステップ6】 テストユーザーを登録する

> ※すでに他のアプリ連携などで一度「テストユーザー」を設定したことがある方は、この手順を飛ばせる場合があります。

ナビゲーションメニューから **「APIとサービス」 > 「OAuth同意画面」** を選択

![画像](https://assets.st-note.com/img/1765271849-fCspM031r4DhRGZgwKPOUacA.png?width=1200)

右のメニューの **「対象」** をクリックします

  

![画像](https://assets.st-note.com/img/1765271849-2aVjJDU5nf9uC3LgpKhAIzGb.png?width=1200)

テストユーザーを追加します。

![画像](https://assets.st-note.com/img/1765271849-DFMTNxguwa2b1KVGdB9SL6YE.png?width=1200)

アカウント連携するGoogleのメアドを登録し「保存」をクリックします。

![画像](https://assets.st-note.com/img/1765271849-XBsKqgFNWTJAQDz2ipduebGR.png?width=1200)

再度n8nで「 **Sign in with Google** 」をクリックすると…下記画面で「続行」をクリックします。

  

![画像](https://assets.st-note.com/img/1765271849-wVYyqtb3J0268TSgFUzQnjGc.png)

どの権限を渡すか確認されるので、選択します。（基本すべて選択して問題ありません。）

![画像](https://assets.st-note.com/img/1765271849-ZyOkoxUmLDgP6rSB0Hv5d9EI.png)

「Connection successful」と表示されれば、すべての連携は完了です！

![画像](https://assets.st-note.com/img/1765271849-thQDIby3xwZd5aoLfNHrAizm.png)

「Connection successful」と表示されれば、連携は完了です！

## 【ステップ7】Google Cloud Storageの追加設定

まずはGCPのコンソール画面を開きます。  
上の検索窓に「Cloud Storage」と入力してCloud Storageをクリックします。  

![画像](https://assets.st-note.com/img/1765272440-Zw4B8HtyzAclFnNsJKU1gWdT.png?width=1200)

バケットの作成をクリックします。

![画像](https://assets.st-note.com/img/1765272487-12wQZWTIY6jaAUByolDrzdp5.png?width=1200)

任意の名前を入力してバケットという名の箱を入力して続行をクリックします。

![画像](https://assets.st-note.com/img/1765272571-1eun6biU9o4hFmOjsfVAg8X2.png?width=1200)

そのまま続行をクリックします。

![画像](https://assets.st-note.com/img/1765272658-n3KINsckOpWbjFmQoGD91Hah.png?width=1200)

次もそのまま続行で大丈夫です

![画像](https://assets.st-note.com/img/1765272693-VZ2mH37JtXpLIGjkcNPduhow.png?width=1200)

「このバケットに対する公開アクセス禁止を適用する」のチェックを外して続行をクリックします。（世界中の人からアクセスできるような設定ですので、アップロードする画像やコンテンツは注意してください）

![画像](https://assets.st-note.com/img/1765272753-fTVjvHYWtE4k5izsNMgQm8bJ.png?width=1200)

カスタム保持期間を設定にチェックを入れて、30日とします。（30日間コンテンツが保存されます）

![画像](https://assets.st-note.com/img/1765272813-Psc2TyDZLMot5F9BEh0VJxur.png?width=1200)

作成をクリックすると、下記画面に遷移してバケットが完成します。

![画像](https://assets.st-note.com/img/1765272845-ew02IRuUh3avDWlFNB45nCV8.png?width=1200)

権限のタブをクリックします

![画像](https://assets.st-note.com/img/1765272981-s1PEI3vFUpxmhC2lLW8b6zke.png?width=1200)

アクセス許可をクリックします

![画像](https://assets.st-note.com/img/1765273035-1wtvk3ISgjA5dyTN2PQGJxRD.png?width=1200)

allUsersと入力してクリックします。

![画像](https://assets.st-note.com/img/1765273084-fcgT97MhvRzr3WBNqYHkxjI1.png?width=1200)

Cloud Storage > Storageオブジェクト閲覧者 の権限を付与して、保存ボタンをクリックします。

![画像](https://assets.st-note.com/img/1765273179-s9StIgTbZEqXRaYGuroA6dlk.png?width=1200)

一般公開アクセスを許可します。  
こうするとAPIで画像を渡したい時などに、リンクを送るだけでアクセスできるような設定にできます。

![画像](https://assets.st-note.com/img/1765273237-oRYS48sbfIij7NvzOAJEuGrc.png?width=1200)

### 【おわりに】接続完了と次のステップ

あなたはGCPという複雑な迷宮を突破し、n8nとGoogle Cloud Storageを正しく接続できました。

これで、n8nのワークフロー内で「Google Cloud Storage」ノードを自由に使い、新着動画の取得や動画情報の検索など、様々な自動化を構築する準備が整いました。

【n8n初心者向け】Google Cloud Storage連携の関門！Credentials認証設定 完全マニュアル｜こま｜n8n × AIよろず屋
</details>

## Summary
n8nでGoogle Cloud Storageを利用するために不可欠な「Credentials（認証情報）」の設定手順を、初心者向けに詳細に解説した完全マニュアルです。Google Cloud Platform (GCP) の複雑な設定画面における「APIの有効化」「OAuth同意画面の作成」「OAuthクライアントIDの発行」「n8nへのリダイレクトURI登録」といった一連の流れを、専門用語を補いながらステップバイステップで説明しています。また、認証後のCloud Storageバケット作成や公開アクセス設定についても網羅しており、この手順に従うことでn8nとGCSの連携を完了させることができます。

## Key Learning Points
*   **Google Cloud Storage APIの有効化**: GCPの「APIとサービス」から「Google Cloud Storage」を検索し、有効化する必要がある。
*   **OAuth同意画面の設定**: アプリ作成時にUser Typeを「外部」に設定し、アプリ名やユーザーサポートメールなどの必須情報を入力する。
*   **OAuthクライアントIDの作成**: アプリケーションの種類を「webアプリケーション」とし、n8n側で取得した「OAuth Redirect URL」をGCPの「承認済みのリダイレクト URI」に追加する。
*   **Credentialsの設定**: GCPで生成された「クライアントID」と「クライアントシークレット」をn8nのCredentials設定画面に入力する。
*   **テストユーザーの登録**: アプリがテスト段階の場合、認証時のアクセスブロックを防ぐために自身のGoogleアカウントを「テストユーザー」として追加する。
*   **バケットの公開設定**: Cloud Storageでバケット作成時に「公開アクセス禁止」を外し、権限で「allUsers」に「Storageオブジェクト閲覧者」を付与することで一般公開アクセスが可能になる。

## Key Message
GCPの認証設定は機能が多く複雑で専門用語も多いため、多くの人がn8n連携時のCredentials設定で挫折してしまいますが、このマニュアルの手順通りに進めることで、初心者でも迷わずにn8nとGoogle Cloud Storageを正しく接続し、自動化ワークフロー構築の準備を整えることができます。