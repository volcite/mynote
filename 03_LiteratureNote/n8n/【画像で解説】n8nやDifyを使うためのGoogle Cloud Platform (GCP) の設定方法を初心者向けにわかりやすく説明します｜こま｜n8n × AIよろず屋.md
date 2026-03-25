---
articleTitle: 【画像で解説】n8nやDifyを使うためのGoogle Cloud Platform (GCP) の設定方法を初心者向けにわかりやすく説明します｜こま｜n8n × AIよろず屋
posted_at: 2025-10-09
posted_by: こま｜n8n × AIよろず屋
tags:
  - GCP
  - GoogleCloudPlatform
  - n8n
  - Dify
  - 初心者ガイド
aliases:
  - GCPプロジェクト作成
  - Google Cloud Platform設定手順
  - n8n連携設定
  - Dify連携設定
---
## Transcript by AI
<details>
  <summary>文字起こし</summary>
---
title: "【画像で解説】n8nやDifyを使うためのGoogle Cloud Platform (GCP) の設定方法を初心者向けにわかりやすく説明します｜こま｜n8n × AIよろず屋"
source: "https://note.com/ai_yorozuya/n/nc312b9c68d3f"
author:
  - "[[こま｜n8n × AIよろず屋]]"
published: 2025-10-09
created: 2026-01-21
description: "n8nやDifyとGoogleサービスを連携させたい、そのためにGCP（Google Cloud Platform）の設定が必要になったけれど、どこから手をつければいいか分からない…    そんなお悩みをお持ちではありませんか？  こんにちは、こまです。  GCPでの作業は、すべて「プロジェクト」という単位で行われます。 プロジェクトとは、あなたの作業内容をまとめておくための、いわば専用の「部屋」のようなものです。APIを有効にしたり、認証情報を作成したりといった設定は、すべてこの「プロジェクト」の中で行います。  この記事では、GCPを利用する上で一番最初に、そして必ず必要になる「新"
tags:
  - "clippings"
---
![見出し画像](https://assets.st-note.com/production/uploads/images/220995843/rectangle_large_type_2_0179a3a5d79b9c625afc683e4ea8ce7b.png?width=1280)

## 【画像で解説】n8nやDifyを使うためのGoogle Cloud Platform (GCP) の設定方法を初心者向けにわかりやすく説明します

[こま｜n8n × AIよろず屋](https://note.com/ai_yorozuya)

> n8nやDifyとGoogleサービスを連携させたい、そのために **GCP（Google Cloud Platform）** の設定が必要になったけれど、どこから手をつければいいか分からない…

そんなお悩みをお持ちではありませんか？

こんにちは、こまです。

GCPでの作業は、すべて「プロジェクト」という単位で行われます。 **プロジェクトとは、あなたの作業内容をまとめておくための、いわば専用の「部屋」のようなものです。** APIを有効にしたり、認証情報を作成したりといった設定は、すべてこの「プロジェクト」の中で行います。

この記事では、GCPを利用する上で一番最初に、そして必ず必要になる「新しいプロジェクトの作成方法」を、 **実際の画面に沿って、一つ一つのステップを丁寧に解説していきます** 。

この記事を読み終えれば、あなたはn8nやDify連携の準備を始めるための、 **自分専用のプロジェクトをGCP上に用意できている** はずです。

## Google Cloud Platform (GCP) でのプロジェクト準備

それでは早速、GCPにログインして、あなたの最初のプロジェクトを作成していきましょう。

### STEP 1 GCPコンソールへログインし、新しいプロジェクトを作成する

まず、お使いのブラウザで「Google Cloud Platform」の公式サイト（ [https://cloud.google.com/](https://cloud.google.com/) ）にアクセスし、お手持ちのGoogleアカウント（Gmailアカウント）でログインします。

![画像](https://assets.st-note.com/img/1759969690-apb9YLig7reAE0w2x8lqZ5MC.png?width=1200)

ログイン後、セキュリティに関する画面が表示された場合は、内容を確認して一番下の「続行」ボタンを押してください。

![画像](https://assets.st-note.com/img/1759969700-WZGs6zAgjwQuipoc7LOI4DFK.png?width=1200)

最初のトップページに戻ってきたら、画面右上にある「 **コンソール** 」というボタンをクリックします。

![画像](https://assets.st-note.com/img/1759969711-W2u9y8Hvgj4cmOVbECFXxa6R.png?width=1200)

初めてコンソールにアクセスする際は、利用規約の同意を求められることがあります。内容を確認し、チェックボックスにチェックを入れて「同意して続行」をクリックしてください。

![画像](https://assets.st-note.com/img/1759969717-Kju5oaYiGcq2Ix6h7ULzSVPZ.png)

### STEP 2 新しいプロジェクトを作成する

コンソール画面が開きます。 画面の上部（ヘッダー部分）に、現在のプロジェクト名が表示されている箇所があります。（初めての場合は「プロジェクトを選択」となっているかもしれません） ここをクリックしてください。

![画像](https://assets.st-note.com/img/1759969727-3TVqP4iysDoZOa1cLYRQMABz.png?width=1200)

プロジェクトを選択するポップアップ画面が表示されますので、その右上にある「 **新しいプロジェクト** 」をクリックします。

![画像](https://assets.st-note.com/img/1759969734-X43ub7iqBmrRAOwY92LaQ5zD.png?width=1200)

### STEP 3 プロジェクトに名前を付けて作成する

「新しいプロジェクト」の作成画面に切り替わります。

「プロジェクト名」の入力欄に、これから作成するプロジェクトの名前を入力します。今回はn8nとの連携で利用することが目的なので、「 **n8n-integration** 」のような、後から見ても分かりやすい名前を付けるのがおすすめです。

名前を入力したら、画面左下にある「 **作成** 」ボタンをクリックします。

![画像](https://assets.st-note.com/img/1759969747-E1CnBsxGpRFID60faJNboSiU.png?width=1200)

### STEP 4 作成したプロジェクトを選択する

プロジェクトが作成されると、右上に通知が表示されます。 これでプロジェクトはできましたが、まだそのプロジェクトを使う状態になっていません。

もう一度、画面上部のプロジェクト名が表示されている部分をクリックしてください。 すると、先ほど作成した「n8n-integration」が一覧に表示されているはずですので、それをクリックして選択します。

![画像](https://assets.st-note.com/img/1759969780-KlHgGIiLuOmqZC958rTDw4W7.png?width=1200)

最後に、画面上部の表示が「 **n8n-integration** 」に切り替わっていることを確認してください。 これが、今あなたがいる「作業するプロジェクト」の名前です。

![画像](https://assets.st-note.com/img/1759969811-8qRTHOBEjZ3g4SAVxPtKbJLo.png?width=1200)

## これで準備完了！

おめでとうございます！ これで、あなたがGCP上で作業を行うための基盤となる、最初のプロジェクトを作成することができました。

今後、GoogleスプレッドシートやGmailのAPIを有効にしたり、n8nやDifyと連携するための認証情報（クレデンシャル）を作成したりする作業は、すべてこの「n8n-integration」プロジェクトの中で行っていくことになります。

【画像で解説】n8nやDifyを使うためのGoogle Cloud Platform (GCP) の設定方法を初心者向けにわかりやすく説明します｜こま｜n8n × AIよろず屋
</details>

## Summary
n8nやDifyとGoogleサービスを連携させる際に必須となる、Google Cloud Platform (GCP) の「プロジェクト」作成方法を初心者向けに解説しています。GCPにおける作業の基本単位である「プロジェクト」の概念説明から、ログイン、新規プロジェクトの作成、そして作業対象としてのプロジェクト選択までの具体的な手順をステップバイステップで紹介しています。

## Key Learning Points
*   **GCPの「プロジェクト」とは**
    *   APIの有効化や認証情報の作成など、すべての作業を行うための専用の「部屋」のような単位。
*   **プロジェクト作成のステップ**
    1.  **コンソールへのアクセス**: GCP公式サイトにGoogleアカウントでログインし、右上の「コンソール」をクリックする。
    2.  **新規作成の開始**: コンソール画面上部のプロジェクト名表示部分をクリックし、ポップアップ内の「新しいプロジェクト」を選択する。
    3.  **名前の設定**: プロジェクト名（例：`n8n-integration`）を入力し、「作成」をクリックする。
*   **プロジェクトの切り替え**
    *   作成後は必ず、画面上部のプロジェクト名部分をクリックし、作成したプロジェクトを選択して作業対象を切り替える必要がある。

## Key Message
n8nやDifyとGoogleサービスを連携させるための第一歩は、GCP上で自分専用の「プロジェクト」を作成し、その中で設定作業を行うことです。