---
articleTitle: "【n8n × AI】Google Geminiをn8nに連携！APIキーを使ったCredential設定方法を世界一わかりやすく解説｜こま｜n8n × AIよろず屋"
posted_at: 2025-10-09
posted_by: "[[こま｜n8n × AIよろず屋]]"
tags:
  - n8n
  - AI
  - GoogleGemini
  - 自動化
  - API
  - Credential
aliases:
  - n8n Gemini 連携手順
  - Google AI Studio APIキー取得方法
  - n8n Credential設定
---
## Transcript by AI
<details>
  <summary>文字起こし</summary>
  
---
title: "【n8n × AI】Google Geminiをn8nに連携！APIキーを使ったCredential設定方法を世界一わかりやすく解説｜こま｜n8n × AIよろず屋"
source: "https://note.com/ai_yorozuya/n/n3702e3f17ecc"
author:
  - "[[こま｜n8n × AIよろず屋]]"
published: 2025-10-09
created: 2026-01-21
description: "いつもの業務自動化、もっと「賢く」してみませんか？   もし自動化の仕組みに、Googleの最新AIである「Gemini」の頭脳を組み込めたとしたら、あなたのワークフローは一体どれほど進化するでしょうか。    問い合わせメールの内容をAIが自動で要約し、担当者へ通知する    Webから収集した情報を基に、SNS投稿文のドラフトをAIが自動生成する    顧客からのフィードバックをAIが分析し、ポジティブかネガティブかを自動でタグ付けする    これまで「人間が読んで判断する」必要があった工程さえも、自動化の領域に組み込むことができるのです。   「でも、AIとの連携なんて、専門知識"
tags:
  - "clippings"
---
![見出し画像](https://assets.st-note.com/production/uploads/images/221018235/rectangle_large_type_2_5681f211396b6c6b092f2af900d02db2.png?width=1280)

## 【n8n × AI】Google Geminiをn8nに連携！APIキーを使ったCredential設定方法を世界一わかりやすく解説

[こま｜n8n × AIよろず屋](https://note.com/ai_yorozuya)

いつもの業務自動化、もっと「賢く」してみませんか？

もし自動化の仕組みに、Googleの **最新AIである「Gemini」の頭脳** を組み込めたとしたら、あなたのワークフローは一体どれほど進化するでしょうか。

- **問い合わせメールの内容をAIが自動で要約し、担当者へ通知する**
- **Webから収集した情報を基に、SNS投稿文のドラフトをAIが自動生成する**
- **顧客からのフィードバックをAIが分析し、ポジティブかネガティブかを自動でタグ付けする**

これまで「人間が読んで判断する」必要があった工程さえも、自動化の領域に組み込むことができるのです。

> **「でも、AIとの連携なんて、専門知識がないと無理なのでは…」**

ご安心ください。n8nとGeminiの連携は、あなたが思っているよりもずっと簡単です。 この記事では、その連携に必要不可欠な「Credential（クレデンシャル）設定」 **、つまりn8nにGeminiを使ってもらうための** 合鍵を発行し、登録する手順を、どこよりも丁寧に、一つ一つの画面に沿って解説します。

この記事を読み終えれば、あなたのn8nは、強力な「頭脳」を手に入れているはずです。 さあ、あなたの自動化を進化させましょう！

## 序章 Gemini連携で、あなたのn8nは「賢い相棒」に進化する

### Credential（クレデンシャル）とは？ なぜ”合鍵”が必要なのか

本題に入る前に、今回の最重要キーワードである「Credential」について簡単にお話しします。 Credential（クレデンシャル）とは、一言でいうと「認証情報」のことです。

n8nがあなたの代わりにGoogle Geminiの機能を使おうとするとき、Google側は **「本当にあなたからの指示ですか？」「誰でも自由に使っていいわけではありませんよ」** と確認する必要があります。

そこで登場するのが、あなた専用の”合鍵”である **「APIキー」** です。 この”合鍵”をn8nに預けておくことで、n8nは「〇〇さんから許可を得ていますよ」という証明書を持って、堂々とGeminiの機能を利用できるのです。この”合鍵”をn8nに登録する作業、それがCredential設定です。

### 今回のゴール「GeminiのAPIキーを取得し、n8nに登録する」までの全ルートを把握しよう

今回のミッションは非常にシンプルです。

1. **Googleのサイトで、Gemini用の”合鍵（APIキー）”をもらう**
2. **n8nに戻り、もらった”合鍵”を設定する**

たったこれだけです。一つずつ手順を追っていけば、誰でも必ず完了できますので、リラックスして進めていきましょう。

## 第1章 Geminiの”合鍵”！APIキーを取得しよう

まずは、連携に必要不可欠なAPIキーをGoogleから発行してもらいます。

### STEP 1GCPコンソールへログインし、新しいプロジェクトを作成する

まだGCPの登録やプロジェクトの作成をしたことがない方は下記記事を参考に、GCPのセットアップを行ってください。（５分程度で終わります。）

### STEP 2 「Google AI Studio」へアクセスする

お使いのブラウザで、「Google AI Studio」の公式サイトへアクセスし、お持ちのGoogleアカウントでログインしてください。

[**Google AI Studio** *The fastest path from prompt to production with Gemini* *aistudio.google.com*](https://aistudio.google.com/welcome)

右上の「Get started」をクリックして、GCPに登録しているGoogleアカウントでログインする。

![画像](https://assets.st-note.com/img/1759973453-cuoRkdGntAbIMjE58D3l4BmQ.png?width=1200)

セキュリティ診断の画面が表示されたら、「続行」をクリック

![画像](https://assets.st-note.com/img/1759974003-HGpNviM4ePjBOaF8mql0dDAY.png?width=1200)

### STEP 2 「APIキーを取得」をクリック

ログインすると、開発用の画面が表示されます。 画面の左側にあるメニューの中から、 **「Get API key」** という項目をクリックします。

![画像](https://assets.st-note.com/img/1759974104-kcGFxwEgWv384uDqjsHJClnI.png?width=1200)

### STEP 3 新しいAPIキーを作成し、忘れずにコピーする【超重要】

「API キー」画面が表示されたら、右上の「 **APIキーを作成** 」というボタンをクリックしてください。

![画像](https://assets.st-note.com/img/1759974180-MrNARd2QS3DqHkyhcbpaWBlF.png?width=1200)

キーの名前を好きな名前に設定します。（今回は「n8n-integration」としておきます。）インポートしたプロジェクトを選択から「import project」を選択します。

![画像](https://assets.st-note.com/img/1759974303-Hfhgrd9Z0amcxIyoqGT5NUQW.png)

右側にプロジェクトをインポートするという画面が出てきますので、GCPで作成したプロジェクトを選択して、インポートをクリックします。

![画像](https://assets.st-note.com/img/1759974358-lphEb4vgPyumxioCwcRYSAkK.png?width=1200)

![画像](https://assets.st-note.com/img/1759974388-QaotSCR7LOiwen05vFUYmxsD.png?width=1200)

右下のキーを作成をクリックします。

![画像](https://assets.st-note.com/img/1759974497-HnCBobcOZW0SxN4Y3ILTMV9K.png)

新しいキーが発行されたので、右側のコピーボタンをクリックします

![画像](https://assets.st-note.com/img/1759974558-re8LcR0x5BYuDJjawniESKHb.png?width=1200)

無事にAPIキーをコピーできたら、第1章はクリアです！

## 第2章 【n8n側の設定】取得したAPIキーをn8nに登録する手順

さて、無事に”合鍵”を手に入れたので、今度はn8nに戻って、その合鍵を登録していきましょう。

### STEP 1 n8nのダッシュボードから「Credentials」画面へ

n8nにログインし、ダッシュボードを開きます。 画面右上の「Create workflow」の右の下矢印から「Create Credential」をクリックします。

![画像](https://assets.st-note.com/img/1759974673-MG4dEfSqzTw0PV7uJkW6p9sA.png?width=1200)

### STEP 2 「Gemini」を検索し、設定画面を開く

下記画面で「Gemini」と入力して、表示されたものを選択して「Continue」をクリックします。

![画像](https://assets.st-note.com/img/1759974753-kJ2cq4YiSdsLyUr3EhWFN67D.png)

  

![画像](https://assets.st-note.com/img/1759974790-uLyhir6sep0FHGIx3Ul8c5EQ.png)

### STEP 4 コピーしたAPIキーを貼り付けて保存する

Gemini用のCredential設定画面が開きます。 やることは一つだけです。

「API Key」という入力欄に、先ほどGoogle AI StudioでコピーしたAPIキーを貼り付けます。 貼り付けたら、画面右上にある「 **Save** 」ボタンをクリックします。

![画像](https://assets.st-note.com/img/1759974857-01Zkyp3xPlEJs52OgFNuDeKQ.png?width=1200)

一覧画面に戻り、「Google Gemini」のCredentialが追加されていれば、設定はすべて完了です！お疲れ様でした。

## 第3章【動作確認】実際にGeminiノードを使ってみよう

設定が正しくできたか、簡単なワークフローで確認してみましょう。

### 簡単なワークフローで接続テスト

1, n8nで新しいワークフローを作成します。

![画像](https://assets.st-note.com/img/1759976839-T2RYwELc4zpxA6F9rBX7b1dl.png?width=1200)

2, Add first stepをクリックし、最初のトリガーは手動で実行できる「Trigger Manualy」でOKです。

![画像](https://assets.st-note.com/img/1759976913-FY2XAbQzjDUcKOWmRrTyug10.png?width=1200)

![画像](https://assets.st-note.com/img/1759976986-d4JXBQwpmP5Ezv0Ta6R8A73F.png?width=1200)

3, 「＋」ボタンをクリックします。

![画像](https://assets.st-note.com/img/1759977047-afydcDshz14ImBjA8Xb0ERqt.png?width=1200)

4, ノード検索で「 **Gemini** 」と入力して、Geminiノードをクリックします。

![画像](https://assets.st-note.com/img/1759977119-UGClfJkaBOdSq2FtepTz0oZX.png?width=1200)

5, AIの種類をします。今回はチャットボットのようなやり取りにしたいので、「Message a model」をクリックします。

![画像](https://assets.st-note.com/img/1759977214-YGwt5pDSi6CL71XyKREAvOmV.png?width=1200)

6, Credentialの欄は、先ほど作成したものが自動で選択されているはずです。

![画像](https://assets.st-note.com/img/1759977300-8DfNaAFtigZm7LEHxbzh4Jsk.png?width=1200)

7, Modelから任意のモデルを選びます。GeminiはFlashのモデルが無料で使えるので今回はFlashのモデルを選びます。

![画像](https://assets.st-note.com/img/1759977413-fBSoNOZFzh7vnPpdxaVX4yq5.png?width=1200)

8, 「Text」の欄に、Geminiへの簡単な質問（例「日本の首都はどこですか？」）を入力します。

![画像](https://assets.st-note.com/img/1759977519-MRKw75EazFBfikQh3Jen64It.png?width=1200)

9, 右上の「Execute step」ボタンをクリックして実行します。

![画像](https://assets.st-note.com/img/1759978058-hsSKkLYT9xy2EU1tbA8P7FDw.png?width=1200)

### Credentialが正しく設定されていることを確認

実行後、Geminiノードの出力（Output）に、質問に対する正しい答え（例「東京です。」）が返ってきていれば、接続は成功です！ もしエラーが出た場合は、APIキーが正しくコピー＆ペーストできているか、再度確認してみてください。

![画像](https://assets.st-note.com/img/1759978094-lMQIJNRGcvViuemAh0kSyZpU.png?width=1200)

## ようこそ、AI自動化の世界へ

おめでとうございます！ これで、あなたのn8nはGoogleの最新AI「Gemini」と会話し、その”知性”をワークフローに組み込む準備が整いました。

今回あなたが設定したCredentialは、いわばAIの世界へのパスポートです。 このパスポートがあれば、単純な作業の自動化だけでなく、文章の生成、要約、翻訳、分析といった、より高度で知的なタスクの自動化にも挑戦できます。

ぜひ、様々なワークフローにGeminiノードを組み込んで、あなたのアイデアを形にしてみてください。 あなたのn8nライフが、今日からもっと刺激的で創造的なものになることを願っています。

【n8n × AI】Google Geminiをn8nに連携！APIキーを使ったCredential設定方法を世界一わかりやすく解説｜こま｜n8n × AIよろず屋
</details>

## Summary
n8nとGoogleの最新AI「Gemini」を連携させることで、業務自動化の高度化（メール要約、SNS投稿生成、分析など）を実現する方法を解説した記事です。連携に必須となる「Credential（認証情報）」の概念から、Google AI Studioを使用したAPIキーの発行手順、n8n側での設定方法、そして簡単なワークフロー作成による動作確認までをステップバイステップで詳しく説明しています。

## Key Learning Points
*   **Credentialの重要性**: n8nがGoogle Geminiの機能を利用するには、認証情報として「APIキー（合鍵）」の設定が必要である。
*   **APIキーの取得手順 (Google AI Studio)**:
    1.  GCPプロジェクトを作成後、「Google AI Studio」にログインする。
    2.  左メニューの「Get API key」から「APIキーを作成」をクリックする。
    3.  GCPプロジェクトをインポートし、新しいキーを作成してコピーする。
*   **n8nでの設定手順**:
    1.  ダッシュボード右上の「Create Credential」を選択する。
    2.  「Gemini」を検索して選択し、取得したAPIキーを貼り付けて保存する。
*   **動作確認方法**:
    1.  「Trigger Manualy」と「Gemini」ノードを接続したワークフローを作成する。
    2.  Geminiノードの設定で「Message a model」を選択し、任意のモデル（Flashなど）と先ほど作成したCredentialを指定する。
    3.  簡単な質問を入力して実行し、正しい回答が出力されれば連携成功である。

## Key Message
専門知識がなくても、簡単なステップで「Credential設定（APIキーの登録）」を行えば、n8nとGeminiを連携させることが可能であり、これによって自動化のワークフローに強力なAIの「頭脳」を組み込むことができる。