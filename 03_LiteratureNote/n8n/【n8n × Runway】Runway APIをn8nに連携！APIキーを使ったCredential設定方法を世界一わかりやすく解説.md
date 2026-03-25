---
articleTitle: "【n8n × Runway】Runway APIをn8nに連携！APIキーを使ったCredential設定方法を世界一わかりやすく解説｜こま｜n8n × AIよろず屋"
posted_at: 2025-12-13
posted_by: "こま｜n8n × AIよろず屋"
tags:
  - n8n
  - Runway
  - API連携
  - 自動化
  - 生成AI
aliases:
  - Runway APIキー取得手順
  - n8n Bearer Auth設定
  - Runwayとn8nの連携方法
  - 動画生成AI自動化
---
## Transcript by AI
<details>
  <summary>文字起こし</summary>
---
title: "【n8n × Runway】Runway APIをn8nに連携！APIキーを使ったCredential設定方法を世界一わかりやすく解説｜こま｜n8n × AIよろず屋"
source: "https://note.com/ai_yorozuya/n/nd3409944dc07"
author:
  - "[[こま｜n8n × AIよろず屋]]"
published: 2025-12-13
created: 2026-01-21
description: "いつものショート動画作成、もっと「簡単に」してみませんか？  もし自動化の仕組みに、動画生成AIである「Runway」を組み込めたとしたら、あなたのワークフローは一体どれほど進化するでしょうか。  これまで「スキル」が必要があった工程さえも、自動化の領域に組み込むことができるのです。   「でも、AIとの連携なんて、専門知識がないと無理なのでは…」   ご安心ください。n8nとRunwayの連携は、あなたが思っているよりもずっと簡単です。   この記事では、その連携に必要不可欠な「Credential（クレデンシャル）設定」、つまりn8nにRunwayを使ってもらうための合鍵を発行し、"
tags:
  - "clippings"
---
![見出し画像](https://assets.st-note.com/production/uploads/images/235951448/rectangle_large_type_2_f51b8bddf4c7210cc6fb8c97188c19e0.png?width=1280)

## 【n8n × Runway】Runway APIをn8nに連携！APIキーを使ったCredential設定方法を世界一わかりやすく解説

[こま｜n8n × AIよろず屋](https://note.com/ai_yorozuya)

いつものショート動画作成、もっと「簡単に」してみませんか？

もし自動化の仕組みに、動画生成AIである「Runway」を組み込めたとしたら、あなたのワークフローは一体どれほど進化するでしょうか。

これまで「スキル」が必要があった工程さえも、自動化の領域に組み込むことができるのです。

> **「でも、AIとの連携なんて、専門知識がないと無理なのでは…」**

ご安心ください。n8nとRunwayの連携は、あなたが思っているよりもずっと簡単です。

この記事では、その連携に必要不可欠な「Credential（クレデンシャル）設定」 **、つまりn8nにRunwayを使ってもらうための** 合鍵を発行し、登録する手順を、どこよりも丁寧に、一つ一つの画面に沿って解説します。

この記事を読み終えれば、あなたのn8nは、強力な「頭脳」を手に入れているはずです。 さあ、あなたの自動化を進化させましょう！

## 今回のゴール「RunwayのAPIキーを取得し、n8nに登録する」までの全ルートを把握しよう

今回のミッションは非常にシンプルです。

1. **Runwayのサイトで、n8n用の”合鍵（APIキー）”をもらう**
2. **n8nに戻り、もらった”合鍵”を設定する**

たったこれだけです。一つずつ手順を追っていけば、誰でも必ず完了できますので、リラックスして進めていきましょう。

## 第1章 Rnwayの”合鍵”！APIキーを取得しよう

まずは、連携に必要不可欠なAPIキーをGoogleから発行してもらいます。

### STEP 1Runwayに登録する

まずはRunwayのサイトにアクセスします。

[**Runway Developer Portal** *dev.runwayml.com*](https://dev.runwayml.com/)

右上のLoginボタンをクリックします。

![画像](https://assets.st-note.com/img/1765575571-L6Ulyx8HYJ4TPRwkopgBaZf9.png?width=1200)

アカウントを持ってる方はそのままログインしてください。  
アカウントを持ってない方は下のSign upをクリックしてください。

![画像](https://assets.st-note.com/img/1765575796-AaTnoJdktQ4Zp6zCNWR5PceS.png)

Googleアカウントでの登録が一番簡単です。

ログインが完了すると下記画面に遷移します。API Keysをクリックします。

![画像](https://assets.st-note.com/img/1765576015-kDGdjiBYWVxHtzIK9r4QFfJO.png?width=1200)

＋New API key をクリックします。

![画像](https://assets.st-note.com/img/1765576060-S9sREWzPb4iNY7wvO1DhqQXH.png?width=1200)

わかりやすい名前を入力してCreateをクリック

![画像](https://assets.st-note.com/img/1765576108-qdecbkaOZpGXWIvno8P1wKAU.png?width=1200)

APIキーが発行されるので、コピーしておきます。

![画像](https://assets.st-note.com/img/1765576144-sgUvmdqrYiZPt83Xxf26Bo7j.png)

## 第2章 【n8n側の設定】取得したAPIキーをn8nに登録する手順

さて、無事に”合鍵”を手に入れたので、今度はn8nに戻って、その合鍵を登録していきましょう。

### STEP 1 n8nのダッシュボードから「Credentials」画面へ

n8nにログインし、ダッシュボードを開きます。 画面右上の「Create workflow」の右の下矢印から「Create Credential」をクリックします。

![画像](https://assets.st-note.com/img/1765575217-hQmt1eDG9wP8KxJT6CnOdXk2.png?width=1200)

### STEP 2 「Bearer Auth」を検索し、設定画面を開く

下記画面で「Bearer Auth」と入力して、表示されたものを選択して「Continue」をクリックします。

![画像](https://assets.st-note.com/img/1765576207-jMyq6FOZowzVp49kH8BJY570.png?width=1200)

  

### STEP2でコピーしたAPIキーを貼り付けて保存する

「Bearer Token」という入力欄に、先ほどコピーしたAPIキーを貼り付けます。 貼り付けたら、画面右上にある「 **Save** 」ボタンをクリックします。

![画像](https://assets.st-note.com/img/1765576326-YIJUN9iER0QMuLeGAHg46thO.png?width=1200)

右上の名前もわかりやすくRunway APIなどに変更しておくといいと思います。

![画像](https://assets.st-note.com/img/1765576310-LAXdGzE6IoshDx2S9yru85YB.png?width=1200)

一覧画面に戻り、「Runway」のCredentialが追加されていれば、設定はすべて完了です！お疲れ様でした。

## ようこそ、AI動画生成自動化の世界へ

おめでとうございます！ これで、あなたのn8nはRunwayの動画生成の力をワークフローに組み込む準備が整いました。

今回あなたが設定したCredentialは、いわばAIの世界へのパスポートです。 このパスポートがあれば、単純な作業の自動化だけでなく、文章の生成、要約、翻訳、分析といった、より高度で知的なタスクの自動化にも挑戦できます。

ぜひ、様々なワークフローにRunwayを組み込んで、あなたのアイデアを形にしてみてください。 あなたのn8nライフが、今日からもっと刺激的で創造的なものになることを願っています。

  

【n8n × Runway】Runway APIをn8nに連携！APIキーを使ったCredential設定方法を世界一わかりやすく解説｜こま｜n8n × AIよろず屋
</details>

## Summary
この記事は、動画生成AI「Runway」をノーコード自動化ツール「n8n」と連携させるためのAPI連携手順を解説しています。主な内容は、Runway Developer PortalでのAPIキー取得方法と、n8nでのCredential（Bearer Auth）設定方法の2ステップです。専門知識がなくても、これらの手順を実行することで動画生成などのタスクを自動化ワークフローに組み込むことが可能になります。

## Key Learning Points
*   **Runway APIキーの取得手順**
    *   Runway Developer Portalにアクセスし、ログイン（またはGoogleアカウントでSign up）する。
    *   メニューの「API Keys」を選択し、「+New API key」をクリックする。
    *   キーに名前を付けて「Create」し、発行されたAPIキーをコピーする。
*   **n8nでのCredential設定手順**
    *   n8nダッシュボードの「Create Credential」から設定を開始する。
    *   「Bearer Auth」を検索して選択する。
    *   「Bearer Token」入力欄にRunwayで取得したAPIキーを貼り付け、「Save」をクリックする。
*   **連携の意義**
    *   このCredential設定により、n8nのワークフロー内でRunwayの動画生成機能を自動的に利用できるようになる。

## Key Message
n8nとRunwayの連携は、「RunwayでAPIキー（合鍵）を取得」し、「n8nのBearer Authに登録する」というシンプルな手順のみで完了し、これによって動画生成を含む高度な自動化が可能になります。