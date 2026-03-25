---
articleTitle: "【n8n × Google】もう連携で迷わない！Google OAuthクレデンシャル設定の完全手順書｜こま｜n8n × AIよろず屋"
posted_at: 2025-10-09
posted_by: こま｜n8n × AIよろず屋
tags:
  - n8n
  - Google
  - OAuth
  - GCP
  - 自動化
aliases:
  - Google OAuth設定
  - GCPプロジェクト作成
  - n8n連携
  - API有効化
  - クライアントID
  - テストユーザー登録
---
## Transcript by AI
<details>
  <summary>文字起こし</summary>

---
title: "【n8n × Google】もう連携で迷わない！Google OAuthクレデンシャル設定の完全手順書｜こま｜n8n × AIよろず屋"
source: "https://note.com/ai_yorozuya/n/nf0ab777a6f59"
author:
  - "[[こま｜n8n × AIよろず屋]]"
published: 2025-10-09
created: 2026-01-21
description: "n8nで連携させたくなるのは、きっとGoogleスプレッドシートやGmail、Googleカレンダーといった、普段使いのGoogleツールではないでしょうか。  しかし、これらのツールと連携しようとすると、必ず「OAuth」という認証の壁が立ちはだかります。 「GCPって何？」「APIを有効化？」 見慣れない単語の数々に、そっと画面を閉じてしまった経験はありませんか？  ご安心ください。 この記事では、n8nとGoogleツールを連携させるための最重要プロセスである「Google OAuth Credential設定」の手順を、Google Cloud Platform (GCP) で"
tags:
  - "clippings"
---
![見出し画像](https://assets.st-note.com/production/uploads/images/221001478/rectangle_large_type_2_aa5aebeffa4d6dbcb0c58101ecdbb674.png?width=1280)

## 【n8n × Google】もう連携で迷わない！Google OAuthクレデンシャル設定の完全手順書

[こま｜n8n × AIよろず屋](https://note.com/ai_yorozuya)

n8nで連携させたくなるのは、きっとGoogleスプレッドシートやGmail、Googleカレンダーといった、普段使いのGoogleツールではないでしょうか。

しかし、これらのツールと連携しようとすると、必ず **「OAuth」** という認証の壁が立ちはだかります。 「GCPって何？」「APIを有効化？」 見慣れない単語の数々に、そっと画面を閉じてしまった経験はありませんか？

ご安心ください。 この記事では、n8nとGoogleツールを連携させるための最重要プロセスである「Google OAuth Credential設定」の手順を、 **Google Cloud Platform (GCP) でのプロジェクト作成** という一番最初のステップから、一つも漏らすことなく、どこよりも丁寧に解説します。

この記事は、あなたのn8nがGoogleの各種サービスとやりとりし、データをやり取りするための「許可証」を発行するまでの完全ガイドです。

読み終える頃には、安全で強力なGoogle連携ワークフローを自在に構築できるようになっているはずです。

## 序章 なぜ「OAuth」が必要なの？ APIキーとの違いを知る

### OAuthは「代理人への委任状」。安全に権限を渡す仕組み

今回設定する「OAuth」は「代理人への委任状」のようなものです。

OAuthでは、「スプレッドシートの読み書きは許可しますが、メールの削除は許可しません」といったように、 **n8n（代理人）に許可する権限（できること）を細かく指定** できます。

ユーザー本人がログインして許可を与えない限り、n8nは **勝手にあなたのデータにアクセスできません** 。この安全な仕組みのおかげで、私たちは安心してサービス連携ができるのです。

### 今回のゴール「GCPでOAuthクライアントIDを作成し、n8nに登録する」までの全ルート

今回の手順は少し長丁場ですが、やっていることは以下の通りです。

1. **GCPでn8n専用のプロジェクトを作る**
2. **プロジェクトで使いたいGoogleサービス（ドライブ等）の機能をONにする**
3. **ユーザーに許可を求めるための同意画面を作る**
4. **n8nに渡すための正式なIDとパスワード（クライアントIDとシークレット）を発行する**
5. **発行されたIDとパスワードをn8nに登録し、最終的な連携を完了させる**

一つずつ進めていきましょう。

## 第1章 すべてはここから！Google Cloud Platform (GCP) でのプロジェクト準備

### STEP 1 GCPコンソールへログインし、新しいプロジェクトを作成する

まだGCPの登録やプロジェクトの作成をしたことがない方は下記記事を参考に、GCPのセットアップを行ってください。（５分程度で終わります。）

### STEP 2 連携したいGoogleサービスのAPIを有効にする

プロジェクトを作成したら、次にそのプロジェクトで利用したいGoogleサービスの機能を有効化します。

左上のナビゲーションメニューから **「APIとサービス」 > 「ライブラリ」** を選択します。

![画像](https://assets.st-note.com/img/1759931587-AaeNT3McSbgt0lonU4sq6KIW.png?width=1200)

![画像](https://assets.st-note.com/img/1759931695-i3UkQ5lR0VMOCsfPvAjTaGNe.png?width=1200)

APIライブラリの検索窓で、連携したいサービス名（例 「Google Drive API」）を検索します。

![画像](https://assets.st-note.com/img/1759931742-nkx56Uolrh0DLcBaIYVpdbZ9.png?width=1200)

目的のAPIを選択し、「有効にする」ボタンをクリックします。  
今回はGoogleDriveを選択しますが、連携したいサービス（Gmail API, Google Calendar API, Google Sheet APIなど）ごとに行います。

![画像](https://assets.st-note.com/img/1759931792-DhJ5isRdkz1VULxmp8aHWcIS.png?width=1200)

  

![画像](https://assets.st-note.com/img/1759931818-TZI1OH0wF2q5Pvk63SbxNC8s.png?width=1200)

## 第2章 ユーザーに許可を求める「同意画面」を設定しよう

次に、n8nがあなたのデータにアクセスする際に表示される「許可しますか？」の確認画面（同意画面）を作成します。

### STEP 1 「OAuth同意画面」へ移動する

ナビゲーションメニューから「APIとサービス」 > 「OAuth同意画面」を選択します。

  

![画像](https://assets.st-note.com/img/1759931911-V3avkQqmCJrHf9RgXxiDAwly.png?width=1200)

### STEP 3 アプリケーション情報を入力する

「開始」ボタンをクリックします

![画像](https://assets.st-note.com/img/1759932033-WV1evRDL7NmsAISPutrkfQB3.png?width=1200)

アプリ名は任意のアプリ名（ここでは「n8n-integration」とします）を入力して、ユーザーサポートメールはプルダウンで選択できるメールを選択します。次へボタンを押下します。

![画像](https://assets.st-note.com/img/1759971673-iQL3JW2hAdVv0IkeMGXKjoEY.png)

「User Type」で「 **外部** 」を選択し、「次へ」をクリックします。 （※Google Workspaceアカウントを利用している場合は「内部」も選択できますが、個人利用の場合は「外部」で問題ありません。）  

![画像](https://assets.st-note.com/img/1759932116-BFLfv4QI2MVqDoEN9ZrJRjdl.png?width=1200)

Googleからの連絡を受け取るメールアドレスを入力して、「次へ」ボタンを押下します。

![画像](https://assets.st-note.com/img/1759932176-542RsniPC8Bp0ogNLmXDQ3vc.png?width=1200)

ポリシーに同意して作成ボタンを押下します。

![画像](https://assets.st-note.com/img/1759932220-UHShsplde0RV7qZFnA9aLyDJ.png?width=1200)

  

## 第3章 n8nに渡す”IDとパスワード”！ OAuth 2.0 クライアントIDを作成する

「スコープ」は、n8nに許可する権限の範囲です。「スコープを追加または削除」ボタンを押し、先ほど有効化したAPIに関連するスコープを選択します。

### STEP 1 「認証情報」ページで「認証情報を作成」をクリック

ナビゲーションメニューから「APIとサービス」 > 「認証情報」を選択

![画像](https://assets.st-note.com/img/1759932408-UOSCVwMdr2nlZiFKu5zeyDLh.png?width=1200)

  

![画像](https://assets.st-note.com/img/1759932530-M6bs1QwZh7T4BgGYc0fWkvit.png?width=1200)

画面上部にある「＋認証情報を作成」をクリックします。

![画像](https://assets.st-note.com/img/1759971763-PRAw1t5m6Nyp3kbWaFqBIcn7.png?width=1200)

### STEP 2「OAuth 2.0 クライアントID」を選択する

表示された選択肢の中から、「 **OAuth 2.0 クライアント ID** 」をクリックします。

![画像](https://assets.st-note.com/img/1759932626-RASW2cLkbEsvYpl7OutdBHax.png?width=1200)

### STEP 3アプリケーションの種類で「ウェブ アプリケーション」を選択

「アプリケーションの種類」のプルダウンメニューから「 **ウェブ アプリケーション** 」を選択します。

![画像](https://assets.st-note.com/img/1759932723-LUVxKr4E6397DXwt8JH0vk5g.png?width=1200)

名前に「n8n-integration」などと入力しておきましょう。

![画像](https://assets.st-note.com/img/1759932820-NBbLChW3fRYmKjJn1H9Vco6u.png?width=1200)

**STEP 4  
n8nの「リダイレクトURL」を追加する**

「承認済みのリダイレクト URI」の項目が最も重要です。 ここに、Googleでの認証後に戻ってくるn8nのページのURLを登録します。

ここでn8nのダッシュボードに戻って、右上の「Create Workflow」の右の下矢印から「Create Credential」を選択。

![画像](https://assets.st-note.com/img/1759932940-E0nur7ishvdSkmxoTB6q83b5.png?width=1200)

Google Drive OAuth2 APIを選択して、「Continue」ボタンをクリック

![画像](https://assets.st-note.com/img/1759933063-o0fTbgUetWk4Ocu9DiMvFRjy.png)

OAuth Redirect URLをコピーしてします。  
URLは **「https://oauth.n8n.cloud/oauth2/callback」** のようになっています。

![画像](https://assets.st-note.com/img/1759933141-uyjzWYGM3A4T6pfc1DoFOnKi.png?width=1200)

入力したら、右上の「Save」ボタンをクリックして一旦保存します。

![画像](https://assets.st-note.com/img/1759933226-3txIg1GofNMiC2ecLqwS8ObA.png?width=1200)

### STEP 5 発行された「クライアントID」と「クライアントシークレット」をコピーする

作成が完了すると、「クライアント ID」と「クライアント シークレット」が表示されます。これがn8nに登録する最終的な認証情報です。 必ず両方ともコピーして、メモ帳などに安全に保管してください。

![画像](https://assets.st-note.com/img/1760838114-EdlGv5KWfDZrgoq2wXaAsJHm.png)

先ほどリダイレクトURIを取得した画面の２か所にそれぞれコピペする。

- **Client ID** の欄に、先ほどGCPでコピーした「クライアントID」を貼り付けます。
- **Client Secret** の欄に、「クライアントシークレット」を貼り付けます。
![画像](https://assets.st-note.com/img/1759933592-9OcHUyFSlMz5ZVrWfs6Yubi2.png?width=1200)

### STEP 4 「Sign in with Google」でアカウントを連携させる

保存後、画面に「 **Sign in with Google** 」というボタンが表示されます。 これをクリックすると、先ほど作成したGCPの同意画面がポップアップで表示されます。

![画像](https://assets.st-note.com/img/1759933979-SuIO76epkjM9zARlrBCcY14t.png?width=1200)

ログインすると下記画面が表示されます。アクセスがブロックされますが、慌てないでください。

![画像](https://assets.st-note.com/img/1759934026-TFKDZcztAdQRGmePyrMY86EW.png?width=1200)

### STEP 5 テストユーザーを登録する

ナビゲーションメニューから **「APIとサービス」 > 「OAuth同意画面」** を選択

![画像](https://assets.st-note.com/img/1759934232-1iMc8BYLV5hNgKv67ExtryFq.png?width=1200)

右のメニューの **「対象」** をクリックします

  

![画像](https://assets.st-note.com/img/1759934261-NhqbZJjFgSLkueP0O75Vs3TB.png?width=1200)

テストユーザーを追加します。

![画像](https://assets.st-note.com/img/1759934302-MtaJXUnQ2dRsY9lf3AHpBeF7.png?width=1200)

アカウント連携するGoogleのメアドを登録し「保存」をクリックします。

![画像](https://assets.st-note.com/img/1759934352-Xd8nu30rFVN2MLKfO1CtShjP.png?width=1200)

再度n8nで「 **Sign in with Google** 」をクリックすると…下記画面で「続行」をクリックします。

  

![画像](https://assets.st-note.com/img/1759934444-6tw2Sqp0uhCzNbA5VEQr7TjM.png)

どの権限を渡すか確認されるので、選択します。（基本すべて選択して問題ありません。）  

![画像](https://assets.st-note.com/img/1759934487-ejRPgFNhWQZYaqudiCrTz85y.png)

「Connection successful」と表示されれば、すべての連携は完了です！  

![画像](https://assets.st-note.com/img/1759934517-FV1Zl7OHPhNpLCY5aeKudSs6.png)

## 終章 解き放たれた自動化の世界へ

おめでとうございます！ これであなたのn8nは、Googleの各種サービスと安全に、そして自由に連携するための「公式な通行許可証」を手に入れました。

この設定さえ乗り越えれば、 「スプレッドシートの特定セルを監視し、変更があったらGmailを送る」 「Googleカレンダーの予定をトリガーにして、自動でドキュメントを作成する」 といった、あなたの日常業務に深く根差した、強力な自動化ワークフローを構築できるようになります。

スプレッドシートやメール、カレンダーそれぞれのAPIも必要に応じて連携してください。

基本的なやり方は同じです。「連携したいGoogleサービスのAPIを有効にする」でスプレッドシートやGmail、カレンダーのAPIを選択してください。

ぜひ、日々の業務を快適にさせていきましょう！

【n8n × Google】もう連携で迷わない！Google OAuthクレデンシャル設定の完全手順書｜こま｜n8n × AIよろず屋
</details>

## Summary
この記事は、n8nとGoogleツール（スプレッドシート、Gmail、Googleカレンダーなど）を連携させるために必須となる「Google OAuth Credential設定」の完全ガイドです。OAuth認証の仕組みを「代理人への委任状」と解説した上で、Google Cloud Platform (GCP) でのプロジェクト作成、APIの有効化、OAuth同意画面の設定、認証情報の発行手順をステップバイステップで説明しています。さらに、n8n側でのリダイレクトURLの取得と登録、そしてテストユーザーを追加して最終的な接続確認を行うまでの全工程を網羅しており、読者が安全かつ強力なGoogle連携ワークフローを構築できるようにサポートしています。

## Key Learning Points
*   **OAuthの役割**: n8nにGoogleデータへのアクセス権限を安全に委任する仕組み。
*   **GCPプロジェクトの準備**: n8n連携用のプロジェクトをGCPで作成し、Google Drive APIなどの必要なAPIを「APIとサービス > ライブラリ」から有効化する。
*   **OAuth同意画面の設定**: User Typeを「外部」に設定し、アプリ名やユーザーサポートメールを入力して作成する。
*   **クライアントIDの作成**: 「APIとサービス > 認証情報」から「OAuth 2.0 クライアント ID」を作成し、アプリケーションの種類を「ウェブ アプリケーション」にする。
*   **リダイレクトURLの設定**: n8nのCredential画面に表示されるURL（例: `https://oauth.n8n.cloud/oauth2/callback`）を、GCPの「承認済みのリダイレクト URI」に追加する。
*   **n8nへの登録**: GCPで発行された「クライアントID」と「クライアントシークレット」をn8nのCredential設定画面に入力する。
*   **テストユーザーの追加**: 認証エラーを防ぐため、GCPのOAuth同意画面設定で、連携するGoogleアカウントを「テストユーザー」として追加する。

## Key Message
Google OAuth設定は一見複雑な「認証の壁」に見えますが、正しい手順で「許可証」を発行すれば、n8nを通じてGoogleの各種サービスを自在に操り、業務効率を劇的に向上させる自動化ワークフローを構築できるようになります。