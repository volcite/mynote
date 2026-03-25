---
articleTitle: 動画/音声をGoogle Driveに置くだけ！n8nがnote記事・画像・X投稿を全自動で生成する魔法のワークフロー構築術｜こま｜n8n × AIよろず屋
posted_at: 2025-10-16
posted_by: こま｜n8n × AIよろず屋
tags:
  - n8n
  - 生成AI
  - 自動化
  - 業務効率化
  - Gemini
  - ChatGPT
  - DALL-E
  - GoogleDrive
aliases:
  - コンテンツ制作自動化
  - 動画から記事作成
  - n8nワークフロー
  - AI文字起こし
  - SNS自動投稿作成
---
## Transcript by AI
<details>
  <summary>文字起こし</summary>
  
---
title: "動画/音声をGoogle Driveに置くだけ！n8nがnote記事・画像・X投稿を全自動で生成する魔法のワークフロー構築術｜こま｜n8n × AIよろず屋"
source: "https://note.com/ai_yorozuya/n/n500f0e7675df"
author:
  - "[[こま｜n8n × AIよろず屋]]"
published: 2025-10-16
created: 2026-01-21
description: "「この動画の内容、ブログ記事にもしたいけど時間がない…」  「アイキャッチ画像やSNSでの告知文を考えるのが面倒…」   「この動画の内容を記事にして、画像を付けて、SNSで告知して…」  この地獄のループ、今日で終わりにしましょう。 私はこれまで製造業から経理まで、3社の社内業務をDXし、非効率な作業を徹底的に自動化してきました。その経験から断言します。現代のコンテンツ制作は、その9割を自動化できます。  今回お伝えするのは、動画を1本Google Driveに放り込むだけで、  1. 高精度な「note記事」  2. 記事の内容に合った「画像」  3. 読者の興味を引く「Xでの告知"
tags:
  - "clippings"
---
![見出し画像](https://assets.st-note.com/production/uploads/images/222182292/rectangle_large_type_2_602d2b0f0c6086f7707553ad5cf814b5.png?width=1280)

## 動画/音声をGoogle Driveに置くだけ！n8nがnote記事・画像・X投稿を全自動で生成する魔法のワークフロー構築術

[こま｜n8n × AIよろず屋](https://note.com/ai_yorozuya)

¥2,980

> **「この動画の内容、ブログ記事にもしたいけど時間がない…」  
> 「アイキャッチ画像やSNSでの告知文を考えるのが面倒…」**

「この動画の内容を記事にして、画像を付けて、SNSで告知して…」

この地獄のループ、今日で終わりにしましょう。 私はこれまで製造業から経理まで、3社の社内業務をDXし、非効率な作業を徹底的に自動化してきました。その経験から断言します。現代のコンテンツ制作は、その9割を自動化できます。

今回お伝えするのは、動画を1本Google Driveに放り込むだけで、

**1\. 高精度な「note記事」**  
**2\. 記事の内容に合った「画像」**  
**3\. 読者の興味を引く「Xでの告知投稿」**

これら全てが、あなたの手を一切煩わせることなく、全自動で生成される **「コンテンツ工場」の構築マニュアル** です。

![画像](https://assets.st-note.com/img/1760411210-Cg1vbotmSUqNBPsJ6KlIEWT7.png?width=1200)

プログラミング？ 小難しい知識？ 一切不要です。

この記事を読み終える頃には、あなたは単純作業から解放され、AIを奴隷のように使う「魔法使い」へと覚醒しているでしょう。

ちなみに今回のワークフローを少し変えるだけで、 **Youtubeから独自のコンテンツを自動で量産する** ことも可能です！

さあ、あなたの貴重な時間を未来のために使う準備はいいですか？ それでは始めましょう。

> **最後に特別なプレゼントも用意してます！  
> 忙しい方はそれだけでも、ぜひご確認ください**

## 第1章 ワークフロー作成の事前準備

本格的なワークフロー構築に入る前に、いくつかの準備が必要です。

### n8nの基本設定

n8nのアカウント作成がまだの方は、先に済ませておきましょう。

### GCPのアカウント作成と設定

n8nとGoogleのサービスを連携させるのに設定が必要です。

### 各種クレデンシャルの設定

- **Google OAuth**  
	Google Driveやスプレッドシートを読み書きするために必要です。

- **OpenAI** API  
	GPT（文章生成）、DALL-E（画像生成）を利用するためにAPIキーが必要です。

- **Gemini API  
	**Geminiを使って文字起こしをするためにAPIキーが必要です

これらの設定が完了していることを前提に、ワークフローを作成していきます。 n8nのダッシュボードで新しいワークフローを作成し、早速始めましょう！

### GoogleDriveにフォルダを作成

GoogleDriveに任意の名前のフォルダを作成します。（例：動画からnote自動作成フォルダ）

作成したフォルダ内に「動画」という名前のフォルダとスプレッドシートを作成します。名前はわかりやすい名前に変更しておきましょう。（例：note記事一覧）スプシは「タイトル」「本文」「告知文」と記載しておいてください。

![画像](https://assets.st-note.com/img/1760412283-xaqK2O5dAbwsmIFrz1ecQHYh.png)

フォルダの構成はこんな感じです。

![画像](https://assets.st-note.com/img/1760412451-WYy0hpna7TojA2PgRwJOvebs.png?width=1200)

> 動画からnote自動作成フォルダ（フォルダ）  
> L 動画（フォルダ）  
> L note記事一覧（スプシ）

動画フォルダに適当な動画をアップロードしておきましょう。

![画像](https://assets.st-note.com/img/1760577948-K4JvRzI7xNe9DpUGkwQE2Wdf.png?width=1200)

## 第2章：【設計図】これから作るワークフローの全体像！

我々がこれから創り上げる「コンテンツ工場」は、大きく4つの工程で動きます。

このラインより上のエリアが 無料で表示されます。

- **フロー1：文字起こしの儀式（動画から魂のテキストを抽出する）** Google Driveに動画がアップロードされるのを検知し、Gemini APIが超高精度で音声をテキストに変換します。
![画像](https://assets.st-note.com/img/1760411800-0V9aOE18YRJ65SHBNeMq4uvF.png?width=1200)

- **フロー2：目次生成の神託（AI編集者が構成案を授ける）** 抽出されたテキストの塊をChatGPTが読み解き、読者が読みやすいように魅力的な目次を作成します。
![画像](https://assets.st-note.com/img/1760411817-F2M9J86OdfBivocKuRNbkZ5z.png?width=1200)

- **フロー3：画像の召喚（文章からビジュアルを錬成する）** 作成された目次の各項目から、DALL-E 3が読者の理解を助ける画像を生成します。
![画像](https://assets.st-note.com/img/1760412009-b4Py1uQvDX5mOdMjU9inxArG.png?width=1200)

- **フロー4：記事と投稿の爆誕（世界にコンテンツを解き放つ）** 目次、本文、画像を統合し、ChatGPTがnote記事とXの投稿を完成させ、スプレッドシートに記録します。
![画像](https://assets.st-note.com/img/1760412023-lFN5P2Wr30VBzga8f1OEGK9I.png?width=1200)

## 第3章：【実践】コピペでOK！動画コンテンツ自動生成ワークフロー構築マニュアル

お待たせしました。ここからが実践です。n8nの画面を開き、私と一緒に手を動かしていきましょう。

### STEP0：ノードの追加方法

右上のプラスボタンをクリックします

![画像](https://assets.st-note.com/img/1760540564-zDh0IlYZkxNpGUaS6WVLB5R4.png?width=1200)

サイドメニューが出てくるので、検索窓に追加したいノードの名前（例：OpenAI, Gemini など）を入れて検索します。

![画像](https://assets.st-note.com/img/1760540624-6Jium7rPbcZACnRjvhFEad84.png)

追加するノードをクリックすれば追加できます！

![画像](https://assets.st-note.com/img/1760540862-zmbWNZSxLK0Chin92l8f3Tdr.png?width=1200)

追加したノードを編集する場合は、ノードをダブルクリックすると編集画面が開きます。

![画像](https://assets.st-note.com/img/1760577219-9JyF4zCY18AdGHUP7jZfD3iu.png)

![画像](https://assets.st-note.com/img/1760577232-ieE7dgOsBowxY1trRDH0Cjy6.png?width=1200)

左上の「Back to canvas」をクリックすると戻れます。

![画像](https://assets.st-note.com/img/1760578544-gTqVkxQJoYBO39bhwUG5Hztv.png)

### STEP1：【文字起こし編】Google Driveの監視からGeminiによるテキスト化まで

![画像](https://assets.st-note.com/img/1760411800-0V9aOE18YRJ65SHBNeMq4uvF.png?width=1200)

この工程のゴールは「Google Driveにアップされた動画・音声を、Gemini APIが自動で文字起こしする」ことです。

**①Google Drive Trigger  
**特定のGoogle Driveフォルダへのファイルアップロードを監視します。

**設定**

- Credentials：Google OAuthを選択して接続します。
- Trigger when：「File Created」を選択。
- From list：作成した動画という名前のフォルダを選択。
![画像](https://assets.st-note.com/img/1760577254-h0cHWukaAPKMzvxnODt83J41.png?width=1200)

右上の「Fetch Test Event」をクリックしてテストします。右側に実行結果が表示されます。

![画像](https://assets.st-note.com/img/1760578476-rl7mpNQAqfSOjYcKBd1xk9su.png?width=1200)

**②Google Drive (Download file)  
**Triggerが検知したファイルをn8nにダウンロードします。

**設定**

- Resource：「File」
- Operation：「Download」を選択。
- File ID：前のノードから受け取ったファイルのIDをドラッグアンドドロップで設定します。（入力する場合は、入力欄の右側にFixedとExpressionの選択があるので、Expressionを選択して「{{ $json.id }} 」と入力する。）
![画像](https://assets.st-note.com/img/1760578762-UtwsiP8eAQ1yHNnkghf6oFvZ.png?width=1200)

右上の「Execute Step」をクリックしてテストします。右側に実行結果が表示されます。

![画像](https://assets.st-note.com/img/1760578826-KZlyGTBd7VhtqIPS0bAFcg8C.png?width=1200)

**③Gemini API（Upload a file）  
**ダウンロードしたファイルをGemini APIにアップロードします

**設定**

- Resource：fileを選択。
- Operation：Upload File を選択。
- Input Type：Binary File を選択。
- Input Data Field Name：dataと入力。
![画像](https://assets.st-note.com/img/1760578900-CAucXJTiWGQwOEo15l7gmH0V.png?width=1200)

右上の「Execute Step」をクリックしてテストします。右側に実行結果が表示されます。

![画像](https://assets.st-note.com/img/1760578998-K5ZRk6FST8LenAYqHf93ojdp.png?width=1200)

**④Gemini API（Transcribe: audio）**  
Geminiにアップロードしたファイルを文字起こしします。

**設定**

- Resource：Audio を選択。
- Operation：Transcribe a Recording を選択。
- Model：gemini-2.5-flash を選択。（2.5-flashは無料で利用できるため）
- Input Type：Audio URL(s) を選択。
- URL(s)：前のノードから受け取ったファイルのURLをドラッグアンドドロップで設定します。（入力する場合は「{{ $json.fileUri }} 」と入力。）
![画像](https://assets.st-note.com/img/1760580420-1QuE3di7G2glNefHx9mFT460.png?width=1200)

右上の「Execute Step」をクリックしてテストします。右側に実行結果が表示されます。

![画像](https://assets.st-note.com/img/1760581315-UV5asifYu4FJwBZADhLm6lK9.png?width=1200)

これで、動画をDriveに置くだけで、数分後には完璧なテキストデータが手に入るようになります！

### STEP2：【目次作成編】AIエージェントに神がかり的な目次を作らせる呪文

![画像](https://assets.st-note.com/img/1760411817-F2M9J86OdfBivocKuRNbkZ5z.png?width=1200)

ただの文字の羅列では読まれません。ここでAI編集者を投入し、読者が最後まで読みたくなる構成を考えさせます。

**【登場するノード】**

**①AI Agent  
**文字起こし結果を基に、目次や記事構成を考えさせます。

**設定**

- Source for Prompt (User Message)：Define belowを選択。
- System Prompt：下記プロンプトを入力。（「{{ $json.content.parts\[0\].text }}」は入力してもOKですが、前ノードの実行結果からドラッグアンドドロップでも入力可能。）

> あなたは優秀なライターです。私が添付した動画の文字起こしをもとに記事の目次を作成してください。何も知らない初心者でも理解できるように、内容は超具体的に書いて。手順やhow to系なら記事としての完璧なマニュアルへと仕上げてください。出力は記事の目次だけを半角カンマ（,）区切りのテキストで出力してください。目次以外は出力しないでください。  
>   
> #記事構成  
> \- 読者が思わず読み進めてしまうくらいキャッチーで魅力的な目次を作成  
> \- 各セクションタイトルは読者の興味を引く工夫をする  
> \- 誇張表現は使用するが、虚偽の情報は避ける  
> \- 具体的な数字を使用する際は、事実に基づいたものを使用  
>   
> #記事の特徴  
> \- 初心者にもわかりやすい内容  
> \- 禁断、極秘、魔法などの刺激的な表現を適度に使用  
>   
> #注意点  
> \- 数字や成果の表現は事実に基づくこと  
> \- 読者の興味を引きつつ、信頼性を損なわないバランスを保つ  
> 　- 2024年以降の最新情報のみを使う  
> 　- すべての情報を具体的に書く  
> 　- 分かりづらい部分は例えを用いて書く  
>   
> \# 出力例  
> 目次1,目次2,目次3,  
> \# 文字起こし  
> {{ $json.content.parts\[0\].text }}

![画像](https://assets.st-note.com/img/1760581714-jz4I3m8gMidCQ6osDTwYxnGv.png?width=1200)

画面下部のChat Modekを設定します。  

![画像](https://assets.st-note.com/img/1760582944-oFurKjsxAJyviN0tbGRPTVh1.png?width=1200)

OpenAIのモデルを選択し、CredentialとModelを選択します。Modelは今回は4oを選んでます。

![画像](https://assets.st-note.com/img/1760583027-nJWFMpPDO2rSEvRwqYZtT71f.png?width=1200)

AI Agent の右上の「Execute Step」をクリックしてテストします。右側に実行結果が表示されます。

![画像](https://assets.st-note.com/img/1760582637-cCIJmNxbGp65jo1q4PYTV30t.png?width=1200)

**②Google Drive (Create folder)  
**AIが作った記事タイトルで、Google Driveに新しいフォルダを作成します。

**設定**

- Credential to connect with：作成したGoogle OAuth のアカウントを選択。
- Resource：Folder を選択。
- Operation：Create を選択。
- Folder Name：「{{ $json.output.split(",")\[0\] }}」と入力。
- Parent Drive：From list から My Drive を選択。
- Parent Folder：By URLを選択して、作成した「動画からnote自動作成フォルダ」のURLを貼り付けます。
![画像](https://assets.st-note.com/img/1760582585-ZX9vAJBLf4iz7xDalK10Rd6V.png?width=1200)

右上の「Execute Step」をクリックしてテストします。右側に実行結果が表示されます。

![画像](https://assets.st-note.com/img/1760582671-NvYSmaFo0WLu3nU2eMj7E5JR.png?width=1200)

**③Edit Fields (Set)  
**後の工程で使いやすいように、AIが作った目次を編集します。

**設定**

- Mode：JSONを選択。
- JSON：「{{ { item: $('AI Agent').item.json.output.split(",") } }}」と入力。
![画像](https://assets.st-note.com/img/1760582731-MYG1KDBTJwhcP4n3zfOopaxI.png?width=1200)

右上の「Execute Step」をクリックしてテストします。右側に実行結果が表示されます。

![画像](https://assets.st-note.com/img/1760582752-un4WfxHcqkAmdCRBY36yStbU.png?width=1200)

### STEP3：【画像生成編】目次項目をDALL-E 3が「映える画像」に変える秘術

![画像](https://assets.st-note.com/img/1760412009-b4Py1uQvDX5mOdMjU9inxArG.png?width=1200)

記事には適切な画像が不可欠。目次の各項目に入れる画像を、AIで生成しましょう。

**【登場するノード】**

**①Split Out**  
AIが作った目次を、項目ごとに分割します。

**設定**

- Fields To Split Out：「itemcontent.parts\[0\].text, item」と入力。
- Include：No Other Field を選択。
![画像](https://assets.st-note.com/img/1760583788-4gaupyI2JOMjwiefBvhrNmQV.png?width=1200)

右上の「Execute Step」をクリックしてテストします。右側に実行結果が表示されます。

![画像](https://assets.st-note.com/img/1760583827-A5JOdgVany6Ekvwhu79UIqMo.png?width=1200)

  
② **Loop Over Items**  
分割された項目一つひとつに対して、以下の処理を繰り返します。

**設定**

- Batch Size：１を入力
![画像](https://assets.st-note.com/img/1760583877-vNkqzIELa2W0wKRXliegndy9.png?width=1200)

右上の「Execute Step」をクリックしてテストします。（右側に出力結果は出ません。）

![画像](https://assets.st-note.com/img/1760583907-4LvEZkuUoYQTdeNsXChc9mMH.png?width=1200)

loop itemのほうにノードを追加していきます。

![画像](https://assets.st-note.com/img/1760583963-uAwaryoiWMxpZbRhl8En30X5.png?width=1200)

**③OpenAI（Message a model）**  
目次項目を画像生成用のプロンプトに変換させます。

**設定**

- Credential to connect with：OpenAIのCredentialを選択。
- Resource：Textを選択。
- Operation：Mesage a Model を選択。
- Model：From list から4oのモデルを選択。
- Messages
	- Role：Userを選択。
	- Promptは下記を入力。

> あなたは優秀な生成AI画像クリエイターかつ、目次の画像を作成したいです。  
>   
> 下記目次を連想するキーワードを3つ選定して、そのキーワードにあう画像生成プロンプトを作成してください。英文プロンプトのみテキストで出力してください。  
>   
> \# 手順  
> \- 目次を連想するキーワードを3つ選定する  
> \- そのキーワードにあう画像が出力されるプロンプトを作成する  
> \- 作成したプロンプトだけ出力する  
>   
> \# 注意事項  
> \- キーワードは出力しないでください  
> \- ブログにふさわしい画像を出力するプロンプトにしてください  
>   
> \# 出力形式  
> 英語プロンプトのみ  
>   
> \# 目次  
> {{ $json.item }}

  

![画像](https://assets.st-note.com/img/1760584387-9KImQSpxazjEngsPoiqUMDVc.png?width=1200)

右上の「Execute Step」をクリックしてテストします。右側に実行結果が表示されます。

![画像](https://assets.st-note.com/img/1760584705-seGPXAKuLRE06rDkpzmZUMbH.png?width=1200)

④ **OpenAI（Generate image）**  
変換されたプロンプトを基に、DALL-E 3で画像を生成します。

**設定**

- Credential to connect with：OpenAIのCredentialを選択します。
- Resources：Imageを選択。
- Operation：Generate an Imageを選択。
- Model：DALLE-3 を選択。
- Prompt：前ノードの出力したプロンプトをドラッグアンドドロップ
![画像](https://assets.st-note.com/img/1760585127-4yLwJPU7iXb6tKumSAWdThql.png?width=1200)

右上の「Execute Step」をクリックしてテストします。右側に実行結果が表示されます。

![画像](https://assets.st-note.com/img/1760585187-ZgwzJBsmCF91ro6v2NWaEVi3.png?width=1200)

**⑤Google Drive（Upload file）**  
生成された画像を、STEP2で作ったフォルダにアップロードします。

**設定**

- Credential to connect with：Google OAuthのアカウントを選択。
- Resource：Fileを選択。
- Operation：Uploadを選択。
- Input Data Field Name：dataと入力。
- File Name：目次の名前を付けたいので、「{{ $('Loop Over Items').item.json.item }}」と入力。（ドラッグアンドドロップでも入力可能。）
![画像](https://assets.st-note.com/img/1760585822-LMUsI5ZdqFlxV9a6pCRcmzkY.png?width=1200)

- Parent Drive：From listからMy Driveを選択。
- Parent Folder：STEP2で作成したフォルダをドラッグアンドドロップで入力。
![画像](https://assets.st-note.com/img/1760585926-2MAL6GwkZ7IVBupvTO4CtEJ5.png?width=1200)

右上の「Execute Step」をクリックしてテストします。右側に実行結果が表示されます。

![画像](https://assets.st-note.com/img/1760586000-tw37Q1lYLuxPsbNDgRyFhrep.png?width=1200)

⑥Wait  
画像生成して次の画像を生成するのに少し時間を置くため（APIの利用制限に引っ掛からないよう）に設定します。

**設定**

- Resume：After Time Intervalを選択。
- Wait Amount：15.00と入力して15秒待機に設定。
- Wait Unit：Second（秒）を選択
![画像](https://assets.st-note.com/img/1760586105-w3z41DyarTGEQAKMHJlxcvSC.png?width=1200)

右上の「Execute Step」をクリックしてテストします。

これで、記事の各セクションに挿入する画像が自動で揃いました。

### STEP4：【Note＆X投稿編】AIライターが読者の心を鷲掴みにする記事と投稿文を執筆する

![画像](https://assets.st-note.com/img/1760412023-lFN5P2Wr30VBzga8f1OEGK9I.png?width=1200)

いよいよ最終工程です。これまでの素材をすべて統合し、発信するコンテンツを完成させます。

**【登場するノード】**

①Aggregete  
見出しごとに分割したものをまとめるものです。

![画像](https://assets.st-note.com/img/1760586960-NVQxBZPahnyozSGg80H21fY6.png?width=1200)

右上の「Execute Step」をクリックしてテストします。

**②AI Agent  
**文字起こし結果と目次を渡し、読者の心を動かすnote記事の本文を作成させます。

**設定**

- Source for Prompt (User Message)：Define belowを選択。
- System Prompt：下記プロンプトを入力。

> あなたは優秀なライターです。私が添付した動画の文字起こしをもとに記事を作成してください。何も知らない初心者でも理解できるように、句構造文法の枠組みを用いて、理解しやすい文章を作成してください。内容は超具体的に書いて。また、自分の過去や体験談、考えなどを記載したものなら、その人が書いたかのように魅力的な文章に仕上げてください。出力は記事の内容だけをマークダウン形式で出力してください。目次は下記のものを使用してください。  
>   
> #記事構成  
> 　- リード文はセールスライティングを活用して読者の購読・購入意欲を掻き立てるよう意識  
> \- 読者が思わず読み進めてしまうくらいキャッチーで魅力的な目次を作成  
> \- 各セクションタイトルは読者の興味を引く工夫をする  
> \- 【】や！などの記号を適度に使用し、緩急をつける  
> \- 誇張表現は使用するが、虚偽の情報は避ける  
> \- 具体的な数字を使用する際は、事実に基づいたものを使用  
>   
> #記事の特徴  
> \- 初心者にもわかりやすい内容  
> \- 読者が「脳汁を出す」ほど興奮する内容を目指す  
> \- 禁断、極秘、魔法などの刺激的な表現を適度に使用  
>   
> #注意点  
> \- 数字や成果の表現は事実に基づくこと  
> \- 読者の興味を引きつつ、信頼性を損なわないバランスを保つ  
> 　- 2024年以降の最新情報のみを使う  
> 　- すべての情報を具体的に書く  
> 　- 分かりづらい部分は例えを用いて書く  
> 　- 「：」は記事内に使わないで  
> 　- タイトルは出力しないでください  
>   
> \# 目次（「,」で区切っています。最初の一つ目がタイトルです。）  
> {{ $('AI Agent').item.json.output }}  
>   
> \# 文字起こし  
> {{ $('文字起こし').item.json.content.parts\[0\].text }}

![画像](https://assets.st-note.com/img/1760587379-Wv2uaEKBUOzg4HdhXnFGweSD.png?width=1200)

画面下部のChat Modekを設定します。

![画像](https://assets.st-note.com/img/1760582944-oFurKjsxAJyviN0tbGRPTVh1.png?width=1200)

OpenAIのモデルを選択し、CredentialとModelを選択します。Modelは今回は4oを選んでます。

![画像](https://assets.st-note.com/img/1760583027-nJWFMpPDO2rSEvRwqYZtT71f.png?width=1200)

AI Agent の右上の「Execute Step」をクリックしてテストします。右側に実行結果が表示されます。

![画像](https://assets.st-note.com/img/1760587528-aWVzkQLRN5v8CeinUrMuhIgf.png?width=1200)

**③X投稿作成 (OpenAI Chat Model)**

完成した記事の要点を渡し、クリックせずにはいられないXの告知投稿文を作成させます。

**設定**

- Source for Prompt (User Message)：Define belowを選択。
- System Prompt：下記プロンプトを入力。

> 【note告知文 作成プロンプト】  
> あなたは、読者の興味を引きつけ、クリックを促すプロのSNSコピーライターです。  
> 以下の#制約条件と#入力情報を基に、note記事へのアクセスを最大化するための告知文章を作成してください  
>   
> #制約条件  
> \- 読者の注意を引く、キャッチーな書き出しで始めてください。  
> \- 記事のテーマと、それが読者にとってなぜ重要なのかを簡潔に提示してください。  
> \- 記事の本文から、最も興味を引く部分を一部引用または要約して「チラ見せ」してください。  
> \- その「チラ見せ」した部分の重要性や、それが何を意味するのかを軽く解説し、読者の知的好奇心を刺激してください。  
> \- 読者が「その先が知りたい！」と思うように、「しかし、本当に重要なポイントは...」「このテクニックの全貌は...」といった言葉で、note記事への期待感を高めてください。  
> \- 記事の結論や最も重要なノウハウは告知文に含めず、noteで明かす構成にしてください。  
> \- 最後に、明確なCall to Action（行動喚起）として、note記事へのリンクを促す一文を加えてください。（例：「全文はこちらのnoteで」「続きはこちらから👇」）  
> \- 投稿文章だけテキスト形式で出力してください  
> \- 文字数は500文字から1000文字程度で作成してください  
> \- スマホで見やすいように、適宜改行を入れてください  
> \- 最初の１文は対象のユーザーが思っている常識を破壊するような内容にしてください。ただし嘘はダメです。  
>   
> #入力情報  
> タイトル:  
> {{ $('Edit Fields').item.json.item\[0\] }}  
> 本文:  
> {{ $json.output }}

画面下部のChat Modekを設定します。

![画像](https://assets.st-note.com/img/1760582944-oFurKjsxAJyviN0tbGRPTVh1.png?width=1200)

OpenAIのモデルを選択し、CredentialとModelを選択します。Modelは今回は4oを選んでます。

![画像](https://assets.st-note.com/img/1760583027-nJWFMpPDO2rSEvRwqYZtT71f.png?width=1200)

AI Agent の右上の「Execute Step」をクリックしてテストします。右側に実行結果が表示されます。

![画像](https://assets.st-note.com/img/1760587515-NW7AIRLlVEagO68U52oPSZzd.png?width=1200)

**④Google Sheets（append: sheet）**

記事タイトル、本文、X投稿文などをスプレッドシートに追記し、コンテンツ資産を記録します。

**設定**

- Credentials to connect with：Google OAuthのアカウントを選択。
- Resource：Sheet Within Documentを選択。
- Operation：Append Rowを選択。
- Document：From listから作成した「note記事一覧」のスプシを選択。
- Sheet：デフォルトの「シート1」を選択。シート名を変更していればその名前にしてください。
- Mapping Column Mode：Map Each Column Monuallyを選択し、下記項目にそれぞれ入力する。
	- タイトル：{{ $('Edit Fields').item.json.item\[0\] }}
	- 本文：{{ $('note作成').item.json.output }}
	- 告知文：{{ $json.output }}
![画像](https://assets.st-note.com/img/1760593327-XqAQRTkvLh5EPyG9uCBiMHrS.png?width=1200)

右上の「Execute Step」をクリックしてテストします。右側に実行結果が表示されます。

**【仕上げ】** 全てのノードを接続し、設定を確認したら、ワークフロー右上の「Save」と「Active」をONにすることを忘れないでください。

---

## 終章：あなたはもう、手を動かしてはいけない。AIに働かせて生まれた時間で、本当にやるべきことを始めよう

ここまでたどり着いたあなたなら、もう理解しているはずです。 単純作業に時間を奪われる時代は、終わりました。

この自動化された「コンテンツ工場」がもたらすのは、単なる時短ではありません。それは、あなたが本来やるべきだった「新しい企画を考える」「ファンと交流する」「専門性をさらに深める」 **といった、創造的な活動に集中するための** 時間と精神的な余裕です。

さあ、今すぐ最初の動画をGoogle Driveにアップロードしてください。  

あなたの代わりにAIが働き始めるその瞬間から、あなたの新しいクリエイター人生が幕を開けます

---

![画像](https://assets.st-note.com/img/1760594324-ML1ZpGUSHAFTkrde9C5tqlDu.jpg?width=1200)

## 【公開後48時間以内限定】最後に、あなたへ誰でも簡単にこの自動化が実現できるファイルをお渡しします

ここまで、この長く、しかし熱量の高いマニュアルを読み切ってくれたあなたへ。 心からの感謝と敬意を表します。

あなたはもう、コンテンツが自動で生まれる世界の理論と構造を完全に理解しました。 しかし、理論を実践に移すには、まだ少しだけ「作業」が必要です。

…私としたことが、まだあなたに「楽」をさせきれていませんでした。

そこで、この記事を最後まで読んでくれた本気のあなただけに、最後のプレゼントを用意しました。 **構築の時間すらショートカットし、今日この瞬間から「全自動コンテンツ制作」** が可能です。

  

これは単なるテンプレートではありません。 私の思考が詰め込まれた「魔法の設計図」そのものです。

あなたがやることは、たった一つ。 このファイルをダウンロードし、あなたのn8nにインポートするだけ。 面倒なノード設定やプロンプト入力をすべて飛び越え、クリック一つで、あなたのPCに私と同じコンテンツ工場が姿を現します。

## 【限定3名】これだけでは終わりません！さらにあなたを楽にさせるとっておきの特典をご用意しました！

さらに、ここまで本気で読み切ってくれた「未来の魔法使い」であるあなたへ、私から **禁断の提案** です。

**あなたの「今の業務」を** **どうやって「自動化」するか？** **私こまが【完全無料】で個別コンサルします。**

このnoteで学んだのは、あくまで「X運用」という一つの事例にすぎません。

いや、正直に言いましょう。 **このnoteで公開したワークフローですら、まだ「改善の余地」だらけなのです。**

例えば、今回紹介したフローに「AIによるキーワード自動選定・投稿」機能を組み込んだらどうなるでしょう？

AIが勝手にトレンドを分析し、最もバズる可能性のあるキーワードを選び出し、それに基づいた投稿を自動生成し始める… まさに **「思考する永久機関」** の完成です。

これ以外にも、

- 「エンゲージメント（いいね・リプ）をリアルタイムで分析し、AIが自動で投稿内容を最適化していく」 **魔改造**
- 「特定のインフルエンサーの投稿に即座に反応し、関連性の高いコメントを自動生成する」 **戦略的リプライ機能**
- 「画像生成AIと連携させ、投稿内容に最もマッチした画像をAIが自動生成・添付する」 **完全ビジュアル自動化**

など、あなたの目的に合わせた無数の **「禁断の魔改造プラン」** が存在します。

ですが、これらの強力すぎる内容は、さすがにnote全体で公開することはできません。悪用されたら困りますからね。

**だからこそ、この「個別コンサル」を用意しました。**

このnoteの「さらに先」… あなた専用の「自動化設計図」と「禁断の魔改造プラン」を、私自身があなたの業務内容を分析し、その場で提示します。

なぜこんなことをするのか？ 簡単です。私自身が、AIとn8nによって人生が激変する瞬間を、この目で直接見たいからです。 あなたの「脳汁が溢れ出す」瞬間を、私にプロデュースさせてください。

ただし、私の時間も有限です。 一人ひとりに本気で向き合うため、このコンサルを受けられるのは **【先着3名様】** のみとさせていただきます。 （※本気の方の時間を確保するため、冷やかしは固くお断りします）

**【応募方法】**

1. 下記の公式LINEに登録する
2. 「 **無料コンサル希望** 」と、一言だけメッセージを送る

[**Add LINE friend** *dz2knout.autosns.app*](https://dz2knout.autosns.app/line)

たったこれだけです。 私から返信があった方が、当選となります。（定員に達し次第、即座に締め切ります）

このチャンスを掴むか、掴まないか。 「設計する側」への切符は、今あなたの目の前にあります。

行動の速い、先見の明のある方からのご連絡をお待ちしています。

動画/音声をGoogle Driveに置くだけ！n8nがnote記事・画像・X投稿を全自動で生成する魔法のワークフロー構築術｜こま｜n8n × AIよろず屋
</details>

## Summary
n8nを活用し、動画や音声をGoogle Driveにアップロードするだけで、note記事の執筆、見出し画像の生成、X（旧Twitter）用の告知文作成を全自動で行う「コンテンツ工場」の構築手順を解説した記事です。Google Drive、Gemini API、OpenAI API（ChatGPT/DALL-E 3）、Google Sheetsを連携させ、コンテンツ制作の9割を自動化する具体的なワークフロー設定とプロンプトが詳細に紹介されています。

## Key Learning Points
- **ワークフローの全体設計**: 4つの主要工程（文字起こし、目次生成、画像生成、記事・SNS投稿作成）で構成され、動画ファイルから最終的なコンテンツまで一気通貫で生成する仕組み。
- **連携ツールと設定**:
    - **Google Drive**: トリガーとしてファイルのアップロードを監視。
    - **Gemini API**: 動画・音声ファイルの文字起こし（モデル：gemini-2.5-flashを使用）。
    - **OpenAI (ChatGPT)**: 文字起こしデータからの目次構成案作成、および記事本文・SNS告知文の執筆。
    - **OpenAI (DALL-E 3)**: 目次ごとのキーワード抽出と画像生成プロンプト作成を経て、記事用画像を生成。
    - **Google Sheets**: 生成されたタイトル、本文、告知文を自動で保存。
- **具体的な構築テクニック**:
    - **Loop Over Items**: 複数の目次項目に対して個別に画像生成処理を繰り返す設定。
    - **Waitノード**: 画像生成時のAPI制限回避のための待機時間設定。
    - **プロンプトエンジニアリング**: AIに対し「優秀なライター」「SNSコピーライター」などの役割を与え、具体的な出力形式や制約条件を指定することで高品質なアウトプットを得る方法。

## Key Message
現代のコンテンツ制作は9割を自動化可能です。単純作業をAIに任せることで、人間は「企画」「交流」「専門性の深化」といった創造的な活動に時間を割くべきです。