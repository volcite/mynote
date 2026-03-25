---
articleTitle: "【悪用厳禁】YouTube URLを貼るだけ。note記事も画像もX告知も、全自動で生成する「凡人が天才を出し抜く反則的自動化術」｜こま｜n8n × AIよろず屋"
posted_at: 2025-12-02
posted_by: "[[こま｜n8n × AIよろず屋]]"
tags:
  - n8n
  - AI
  - 自動化
  - YouTube
  - note
  - X
  - コンテンツ制作
aliases:
  - 動画のブログ記事化
  - 記事作成自動化ワークフロー
  - Gemini API連携
  - コンテンツのマルチユース
---
## Transcript by AI
<details>
  <summary>文字起こし</summary>
---
title: "【悪用厳禁】YouTube URLを貼るだけ。note記事も画像もX告知も、全自動で生成する「凡人が天才を出し抜く反則的自動化術」｜こま｜n8n × AIよろず屋"
source: "https://note.com/ai_yorozuya/n/n9c1ed4d2f33c"
author:
  - "[[こま｜n8n × AIよろず屋]]"
published: 2025-12-02
created: 2026-01-21
description: "あなたはまだ、動画のURLをコピーして、内容を確認して、手作業で要約して、見出しを作って…なんていう「昭和の作業」を続けているのですか？   正直に言います。 その作業、今日で終わりにしましょう。  私はこの「禁断のワークフロー」を構築してから、コンテンツ作成にかける時間が10分の1になりました。 空いた時間で何をしているか？ さらに新しい知識をインプットし、次の自動化の仕組みを作り、収益の柱を増やしています。  今回は、私が裏でこっそり回している「YouTubeの動画URLを入力するだけで、noteの記事構成、アイキャッチ画像、さらにXの告知ポストまで全自動で生成するn8nワークフロ"
tags:
  - "clippings"
---
![見出し画像](https://assets.st-note.com/production/uploads/images/233361562/rectangle_large_type_2_fd97ae7507c9958071bf367f4b2cdc6f.png?width=1280)

## 【悪用厳禁】YouTube URLを貼るだけ。note記事も画像もX告知も、全自動で生成する「凡人が天才を出し抜く反則的自動化術」

[こま｜n8n × AIよろず屋](https://note.com/ai_yorozuya)

¥2,980

> **あなたはまだ、動画のURLをコピーして、内容を確認して、手作業で要約して、見出しを作って…なんていう「昭和の作業」を続けているのですか？**

正直に言います。 その作業、 **今日で終わりにしましょう** 。

私はこの「禁断のワークフロー」を構築してから、コンテンツ作成にかける **時間が10分の1になりました。** 空いた時間で何をしているか？ さらに新しい知識をインプットし、次の自動化の仕組みを作り、 **収益の柱** を増やしています。

今回は、私が裏でこっそり回している「YouTubeの動画URLを入力するだけで、noteの記事構成、アイキャッチ画像、さらにXの告知ポストまで全自動で生成するn8nワークフロー」の全貌を、 **包み隠さず公開** します。

プログラミング知識ゼロ？ 関係ありません。 これは **「現代の魔術」** ですが、 **プログラムを書く必要はない** のです。 必要なのは、あなたの「やろう」という決断だけ。

それでは、あなたの時間を奪還する旅に出かけましょう。

---

![画像](https://assets.st-note.com/img/1764601877-50avcNCTzY2V43kdFQ9SsjMo.jpg?width=1200)

## 序章 まだ大切な人生の時間を「単純作業」に捨てているのですか？

「動画を作ってアップロードしたら終わり」 そう思っていませんか。

それは大きな間違いです。 現代のWebマーケティングにおいて、1つのコンテンツは「マルチユース（多重利用）」されて初めて真価を発揮します。 YouTube動画は、テキスト化してnoteにし、要約してXで拡散し、音声にしてVoicyに流す。 ここまでやって、 **ようやく「資産」になります** 。

しかし、現実はどうでしょう。 動画編集だけでヘトヘトになり、ブログ記事なんて書く気力が残っていない。 結果、素晴らしい動画もYouTubeという海の中で埋もれていく。

**なぜ、あなたのコンテンツは広まらないのか？** 答えはシンプルです。「手数が足りていないから」です。 そして手数が足りない理由は「全部自分でやろうとしているから」です。

![画像](https://assets.st-note.com/img/1764611430-4JPkURosSQY0uiFXbV2T3HKr.png?width=1200)

今日構築するシステムは、あなたが寝ている間も、ご飯を食べている間も、文句ひとつ言わずに働き続けます。 あなたがやることは一つだけ。 **「URLをペーストして、実行ボタンを押す」** これだけです。

**嬉しい感想もたくさんいただいています。**

> **※記事の最後のほうに今回のJsonファイルをお渡しする手順を記載してます。n8nに慣れてる方は最後までスクロールしてください。**

## 第1章 ワークフロー作成の事前準備

本格的なワークフロー構築に入る前に、いくつかの準備が必要です。

### n8nの基本設定

n8nのアカウント作成がまだの方は、先に済ませておきましょう。

### GCPのアカウント作成と設定

n8nとGoogleのサービスを連携させるのに設定が必要です。

### 各種クレデンシャルの設定

- **Google OAuth**  
	Google Driveやスプレッドシートを読み書きするために必要です。

- **Gemini API  
	**Geminiを使って文字起こしをするためにAPIキーが必要です

これらの設定が完了していることを前提に、ワークフローを作成していきます。 n8nのダッシュボードで新しいワークフローを作成し、早速始めましょう！

- **YouTube Transcript API  
	**Youtubeの文字起こしをするのに必要です。

### GoogleDriveにフォルダを作成

GoogleDriveに任意の名前のフォルダを作成します。（例：Youtube→note&X作成フォルダ）

作成したフォルダ内にスプレッドシートを作成します。名前はわかりやすい名前に変更しておきましょう。（例：Youtube文字起こし）スプシは「URL」「note」「X」と記載しておいてください。

![画像](https://assets.st-note.com/img/1764429556-n9KCGqiIat5g164eUhN0oEL7.png?width=1200)

## 第2章：【設計図】これから作るワークフローの全体像！

我々がこれから創り上げるワークフローは、大きく4つの工程で動きます。

### フロー１：YoutubeのURLから文字起こし

![画像](https://assets.st-note.com/img/1764431651-fXGgaV9lxyvOHdYhW12esbtU.png?width=1200)

### フロー２：記事構成・目次作成

![画像](https://assets.st-note.com/img/1764431682-E8tfApZ6gFeClNB1qT3xG2Hm.png?width=1200)

### フロー３：記事の画像生成

![画像](https://assets.st-note.com/img/1764431759-2qVdCrexkWPwKGlaY3Mo9zvb.png?width=1200)

### フロー４：noteの本文・X投稿文生成

![画像](https://assets.st-note.com/img/1764431800-aTBMUVfL0usIQFO9dW3m2pC8.png?width=1200)

## 第3章：【実践】コピペでOK！YoutubeのURLを入力するだけで完了！自動生成ワークフロー構築マニュアル

お待たせしました。ここからが実践です。n8nの画面を開き、私と一緒に手を動かしていきましょう。

### STEP0：ノードの追加方法

右上のプラスボタンをクリックします

![画像](https://assets.st-note.com/img/1764477792-25NHR8CdPbnVKfv4uZg3QsEB.png?width=1200)

サイドメニューが出てくるので、検索窓に追加したいノードの名前（例：OpenAI, Gemini など）を入れて検索します。

![画像](https://assets.st-note.com/img/1764477792-A2xLgeB56njMyKdNvZhV978R.png)

追加するノードをクリックすれば追加できます！

![画像](https://assets.st-note.com/img/1764477792-BjG5PEQXHga3sMbKux4dioeU.png?width=1200)

追加したノードを編集する場合は、ノードをダブルクリックすると編集画面が開きます。

![画像](https://assets.st-note.com/img/1764477792-udT5YEwKFir9lqN0GOz38Wfb.png?width=1200)

左上の「Back to canvas」をクリックすると戻れます。

![画像](https://assets.st-note.com/img/1764477792-hSJnOr873eQo4FWHIiPVXjqv.png)

### STEP1：Youtube動画の文字起こし

![画像](https://assets.st-note.com/img/1764431651-fXGgaV9lxyvOHdYhW12esbtU.png?width=1200)

このラインより上のエリアが 無料で表示されます。

**①On form submission  
**YoutubeのURLを入力するフォームを作成します

**設定**

- Authentivation：None
- Form Title：YoutubeのURLを入力してください
- Form Elements
	- Field Name：URL
	- Element Type：Text
	- Required Field：チェックを入れる
![画像](https://assets.st-note.com/img/1764485039-mvUOhBKDSj6wW3gINAZC4GFi.png)

実際に動かすときは「Production URL」にアクセスしてワークフローを実行します。

**②Code in Javascript**  
YoutubeのURLからIDを抽出します。

**設定**

- Mode：Run Once for All Items
- Language：Javascript
- Code

```php
// 【設定】前のノードから来るURLの項目名（キー）に合わせて変更してください
// ※今はテスト用に、データがない場合は指定のURLを使うようにしています
const targetUrl = $input.item.json.url || "https://www.youtube.com/watch?v=UPwTsyLYgfo";

// --- ID抽出ロジック ---
function getYouTubeId(url) {
  if (!url) return null;
  const regExp = /^.*(youtu\.be\/|v\/|u\/\w\/|embed\/|watch\?v=|\&v=)([^#\&\?]*).*/;
  const match = url.match(regExp);
  return (match && match[2].length === 11) ? match[2] : null;
}
// --------------------

// IDを取得
const videoId = getYouTubeId(targetUrl);

// 結果を出力データに追加
// "youtube_id" という名前で次のノードに渡されます
return {
  json: {
    original_url: targetUrl,
    youtube_id: videoId
  }
};
```

  

![画像](https://assets.st-note.com/img/1764485218-CLPOdJVhGSklUAun3XZYK4x6.png?width=1200)

**③Edit Field**  
Youtube Transcription APIのAPIキーを入力しておきます。

**設定**

- Mode：Manual Mapping
- Field to Set
	- name：API\_KEY
	- string
	- value：取得したAPIキーを入力する
![画像](https://assets.st-note.com/img/1764487217-xS6UYzNF1cIvKrbCA8TpmWyk.png?width=1200)

**③Http Request}  
**Youtubeの動画を文字起こしするAPIです

**設定**

- Method：POST
- URL： [https://www.youtube-transcript.io/api/transcripts](https://www.youtube-transcript.io/api/transcripts)
- Authentication：None
- Send Headers：チェックを入れる
- Specify Headers：Using Fields Below
- Header Parameters
	- Name：Authorization
	- Value：Basic {{ $json.API\_KEY }}
- Send Body：チェックを入れる
- Body Content Type：JSON
- Specify Body：Using JSON
- JSON

```javascript
{
  "ids": ["{{ $('Code in JavaScript').item.json.youtube_id }}"]
}
```

![画像](https://assets.st-note.com/img/1764488423-S7u3fbcrDz9LYONoaFsZEIkU.png?width=1200)

### STEP2：AIエージェントに神がかり的な目次を作らせる

ただの文字の羅列では読まれません。ここでAI編集者を投入し、読者が最後まで読みたくなる構成を考えさせます。

![画像](https://assets.st-note.com/img/1764431682-E8tfApZ6gFeClNB1qT3xG2Hm.png?width=1200)

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

![画像](https://assets.st-note.com/img/1764483922-iIuAL1Gj3rfSYyp8UcMKWoOx.png?width=1200)

画面下部のChat Modekを設定します。

![画像](https://assets.st-note.com/img/1764483921-zgPqjXBNRYshCALu63ex74Gb.png?width=1200)

Geminiのモデルを選択し、CredentialとModelを選択します。Modelは今回は「models/gemini-3-pro-preview」を選んでます。

![画像](https://assets.st-note.com/img/1764518748-6WlKL1JutFenMSiI4gCfOY53.png?width=1200)

AI Agent の右上の「Execute Step」をクリックしてテストします。右側に実行結果が表示されます。

![画像](https://assets.st-note.com/img/1764483923-32o6SAgHuJ1N7PvLpKRqZVUO.png?width=1200)

**②Google Drive (Create folder)  
**AIが作った記事タイトルで、Google Driveに新しいフォルダを作成します。

**設定**

- Credential to connect with：作成したGoogle OAuth のアカウントを選択。
- Resource：Folder を選択。
- Operation：Create を選択。
- Folder Name：「{{ $json.output.split(",")\[0\] }}」と入力。
- Parent Drive：From list から My Drive を選択。
- Parent Folder：From list から、作成した「Youtube→note&X作成フォルダ」を選択。
![画像](https://assets.st-note.com/img/1764483923-I2aJburqd5hTeLMj6pEVPHCx.png?width=1200)

右上の「Execute Step」をクリックしてテストします。右側に実行結果が表示されます。

![画像](https://assets.st-note.com/img/1764483922-TA2L08c3XVevlqSBOQtxzbuG.png?width=1200)

**③Edit Fields (Set)  
**後の工程で使いやすいように、AIが作った目次を編集します。

**設定**

- Mode：JSONを選択。
- JSON：「{{ { item: $('AI Agent').item.json.output.split(",") } }}」と入力。
![画像](https://assets.st-note.com/img/1764483922-70gRPeiXfY6AKqsMH2JQEu9C.png?width=1200)

右上の「Execute Step」をクリックしてテストします。右側に実行結果が表示されます。

![画像](https://assets.st-note.com/img/1764483922-nFRCLQbVKva9iyONGHISqBW2.png?width=1200)

### STEP3：【画像生成編】目次項目をnanobanana proが「映える画像」に変える

![画像](https://assets.st-note.com/img/1764431759-2qVdCrexkWPwKGlaY3Mo9zvb.png?width=1200)

記事には適切な画像が不可欠。目次の各項目に入れる画像を、AIで生成しましょう。

**【登場するノード】**

**①Split Out**  
AIが作った目次を、項目ごとに分割します。

**設定**

- Fields To Split Out：「itemcontent.parts\[0\].text, item」と入力。
- Include：No Other Field を選択。
![画像](https://assets.st-note.com/img/1764483922-BxGtZV6FKD5AM0aYceqX827H.png?width=1200)

右上の「Execute Step」をクリックしてテストします。右側に実行結果が表示されます。

![画像](https://assets.st-note.com/img/1764483923-jufTavRpQsqxizSkmgV0JrIA.png?width=1200)

  
② **Loop Over Items**  
分割された項目一つひとつに対して、以下の処理を繰り返します。

**設定**

- Batch Size：１を入力
![画像](https://assets.st-note.com/img/1764483922-cDEZ0kWengLTif8N3ayosS9w.png?width=1200)

右上の「Execute Step」をクリックしてテストします。（右側に出力結果は出ません。）

![画像](https://assets.st-note.com/img/1764483923-7p6DCmWlwbEjyK2aGFvMRxhq.png?width=1200)

loop itemのほうにノードを追加していきます。

![画像](https://assets.st-note.com/img/1764519277-1oJXO4NfsxpH6jeSDhaRFrz9.png)

③if  
タイトルの画像の場合と目次画像の場合で分岐させます  
最初の1回目だけ別ルートに分岐させます。

**設定**

- Conditions
	- {{ $runIndex }}
	- is equal to
	- 0
![画像](https://assets.st-note.com/img/1764519387-A6DSFQWM2L1jEIRqzUwJloKH.png?width=1200)

**④Gemini(Generate an image)**  
trueにつないで、タイトルを生成させるノード。

**設定**

- Credential to connect with：GeminiのCredentialを選択。
- Resource：Image
- Operation：Generate an image
- Model：models/gemini-3-pro-image-previewを入力
- prompt

> 視認性の高いサムネイルを作って  
> アスペクト比は16:9。  
>   
> \## タイトル  
> {{ $('If').item.json.item }}

![画像](https://assets.st-note.com/img/1764549823-QsPUktcL3ABIo0zTmGKVwnpi.png?width=1200)

**④Gemini（Message a model）**  
目次項目を画像生成用のプロンプトに変換させます。

**設定**

- Credential to connect with：GeminiのCredentialを選択。
- Resource：Textを選択。
- Operation：Mesage a Model を選択。
- Model：From list から「models/gemini-3-pro-preview」のモデルを選択。
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

![画像](https://assets.st-note.com/img/1764584050-5VvXD2cGurIRF70s9gEOwNqL.png?width=1200)

右上の「Execute Step」をクリックしてテストします。右側に実行結果が表示されます。

**⑥Gemini(Generate an image)**  
変換されたプロンプトを基に、nanobanana proで画像を生成します。

**設定**

- Credential to connect with：GeminiのCredentialを選択します。
- Resources：Imageを選択。
- Operation：Generate an Imageを選択。
- Model：models/gemini-3-pro-image-previewを入力
- Prompt：{{ $json.content.parts\[0\].text }}
![画像](https://assets.st-note.com/img/1764584733-AWFBoEqNd91OPK546lyv8Q2S.png?width=1200)

右上の「Execute Step」をクリックしてテストします。右側に実行結果が表示されます。

**⑤Google Drive（Upload file）**  
生成された画像を、STEP2で作ったフォルダにアップロードします。

**設定**

- Credential to connect with：Google OAuthのアカウントを選択。
- Resource：Fileを選択。
- Operation：Uploadを選択。
- Input Data Field Name：dataと入力。
- File Name：目次の名前を付けたいので、「{{ $('Loop Over Items').item.json.item }}」と入力。（ドラッグアンドドロップでも入力可能。）
![画像](https://assets.st-note.com/img/1764483921-mqOQ0pf6aU2BxLJ4XRsF7tkM.png?width=1200)

- Parent Drive：From listからMy Driveを選択。
- Parent Folder：STEP2で作成したフォルダをドラッグアンドドロップで入力。
![画像](https://assets.st-note.com/img/1764483921-U1qncwBveKElIx8biWz0NZX6.png?width=1200)

右上の「Execute Step」をクリックしてテストします。右側に実行結果が表示されます。

![画像](https://assets.st-note.com/img/1764483922-Jbk1Y2aqhZdVAPIC4Bo6OES3.png?width=1200)

⑥Wait  
画像生成して次の画像を生成するのに少し時間を置くため（APIの利用制限に引っ掛からないよう）に設定します。

**設定**

- Resume：After Time Intervalを選択。
- Wait Amount：15.00と入力して15秒待機に設定。
- Wait Unit：Second（秒）を選択
![画像](https://assets.st-note.com/img/1764483921-oXx1Hkr7ZEjQvAuqM8pfshJw.png?width=1200)

右上の「Execute Step」をクリックしてテストします。

これで、記事の各セクションに挿入する画像が自動で揃いました。

### STEP4：【Note＆X投稿編】AIライターが読者の心を鷲掴みにする記事と投稿文を執筆する

![画像](https://assets.st-note.com/img/1764431800-aTBMUVfL0usIQFO9dW3m2pC8.png?width=1200)

いよいよ最終工程です。これまでの素材をすべて統合し、発信するコンテンツを完成させます。

**【登場するノード】**

①Aggregete  
見出しごとに分割したものをまとめるものです。

![画像](https://assets.st-note.com/img/1764483922-qmcwaPsRYjXiDZbK042BMxrU.png?width=1200)

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

![画像](https://assets.st-note.com/img/1764483921-Pj0xptXkT1eRYOdc4i2bWKrq.png?width=1200)

画面下部のChat Modekを設定します。

![画像](https://assets.st-note.com/img/1764483921-i6uUeyLhOxRIvDY8FsgTdNBJ.png?width=1200)

Geminiのモデルを選択し、CredentialとModelを選択します。Modelは今回は「models/gemini-3-pro-preview」を選んでます。

![画像](https://assets.st-note.com/img/1764586054-zKX9Brncebxas3q7IlPu6WG0.png?width=1200)

AI Agent の右上の「Execute Step」をクリックしてテストします。右側に実行結果が表示されます。

![画像](https://assets.st-note.com/img/1764483923-VioH1ZtF7wExG98fIBg3Y2bK.png?width=1200)

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

![画像](https://assets.st-note.com/img/1764483921-RV3DfB2lXSYjaQnFWpouJeN0.png?width=1200)

Geminiのモデルを選択し、CredentialとModelを選択します。Modelは今回は「models/gemini-3-pro-preview」を選んでます。

![画像](https://assets.st-note.com/img/1764586009-6IvsG9AbrTfmi1NhWEqg2DyC.png?width=1200)

AI Agent の右上の「Execute Step」をクリックしてテストします。右側に実行結果が表示されます。

![画像](https://assets.st-note.com/img/1764483923-yanNZiopGk2rLtzbl1TgURYP.png?width=1200)

**④Google Sheets（append: sheet）**

記事タイトル、本文、X投稿文などをスプレッドシートに追記し、コンテンツ資産を記録します。

**設定**

- Credentials to connect with：Google OAuthのアカウントを選択。
- Resource：Sheet Within Documentを選択。
- Operation：Append Rowを選択。
- Document：From listから作成した「note記事一覧」のスプシを選択。
- Sheet：デフォルトの「シート1」を選択。シート名を変更していればその名前にしてください。
- Mapping Column Mode：Map Each Column Monuallyを選択し、下記項目にそれぞれ入力する。
	- URL：{{ $('Code in JavaScript').item.json.original\_url }}
	- note：{{ $('note作成').item.json.output }}
	- X：{{ $json.output }}
![画像](https://assets.st-note.com/img/1764483922-sx7r6JoqpnkNMy3GCvHK8LZB.png?width=1200)

右上の「Execute Step」をクリックしてテストします。右側に実行結果が表示されます。

**【仕上げ】** 全てのノードを接続し、設定を確認したら、ワークフロー右上の「Save」と「Active」をONにすることを忘れないでください。

## 終章 空いた時間で、あなたは次に何をするか？

おめでとうございます。 これであなたは、コンテンツ制作の「奴隷」から解放され、 **「支配者」** になりました。

このワークフローを実行して、Googleドキュメントに完璧な原稿が生成された瞬間。 きっとあなたの脳内からは、ドーパミンという名の脳汁が溢れ出すはずです。 「今まで苦労していたのは何だったんだ」と。

しかし、勘違いしないでください。 **自動化はゴールではありません** 。スタートラインです。

浮いた時間で、あなたは何をしますか。 さらに質の高い動画ネタを探すもよし。 別の自動化システムを組むもよし。あるいは、 **大切な人とゆっくりコーヒーを飲む** のもよし。

時間は、命そのものです。 n8nという最強の武器を使って、あなたの命を「作業」ではなく **「創造」** に使ってください。

さあ、今すぐn8nを開いてください。 未来は、あなたのクリック一つで変わります。

## 【公開後48時間以内限定】最後に、あなたへ誰でも簡単にこの自動化が実現できるファイルをお渡しします

ここまで、この長く、しかし熱量の高いマニュアルを読み切ってくれたあなたへ。 **心からの感謝と敬意を表します** 。

あなたはもう、コンテンツが自動で生まれる世界の理論と構造を完全に理解しました。 しかし、理論を実践に移すには、まだ少しだけ「作業」が必要です。

そこで、この記事を最後まで読んでくれた本気のあなただけに、最後のプレゼントを用意しました。 **構築の時間すらショートカットし、今日この瞬間から「全自動コンテンツ制作」** が可能です。

[**【悪用厳禁】YouTube URLを貼るだけ。note記事も画像もX告知も、全自動で生成する「凡人が天才を出し抜く反則的自動化術」 | Notion** *感想の引用リツイートありがとうございます！* *www.notion.so*](https://www.notion.so/YouTube-URL-note-X-2bc77d64cc39802d92decc7556355690)

これは単なるテンプレートではありません。 私の思考が詰め込まれた **「魔法の設計図」** そのものです。

あなたがやることは、たった一つ。 このファイルをダウンロードし、あなたのn8nにインポートするだけ。 面倒なノード設定やプロンプト入力をすべて飛び越え、クリック一つで、あなたのPCに私と同じコンテンツ工場が姿を現します。

## 【先着限定3名】これだけでは終わりません！さらにあなたを楽にさせるとっておきの特典をご用意しました！

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

このnoteの「さらに先」… **あなた専用の「自動化設計図」と「禁断の魔改造プラン」** を、私自身があなたの業務内容を分析し、その場で提示します。

なぜこんなことをするのか？ 簡単です。私自身が、AIとn8nによって人生が激変する瞬間を、この目で直接見たいからです。 あなたの「脳汁が溢れ出す」瞬間を、 **私にプロデュースさせてください** 。

ただし、私の時間も有限です。 一人ひとりに本気で向き合うため、このコンサルを受けられるのは **【先着3名様】** のみとさせていただきます。 （※本気の方の時間を確保するため、冷やかしは固くお断りします）

**【応募方法】**

1. 下記の公式LINEに登録する
2. 「 **無料コンサル希望** 」と、一言だけメッセージを送る

[**Add LINE friend** *dz2knout.autosns.app*](https://dz2knout.autosns.app/line)

たったこれだけです。 私から返信があった方が、当選となります。（定員に達し次第、即座に締め切ります）

このチャンスを掴むか、掴まないか。 「設計する側」への切符は、今あなたの目の前にあります。

行動の速い、先見の明のある方からのご連絡をお待ちしています。

【悪用厳禁】YouTube URLを貼るだけ。note記事も画像もX告知も、全自動で生成する「凡人が天才を出し抜く反則的自動化術」｜こま｜n8n × AIよろず屋
</details>

## Summary
YouTube動画のURLを入力するだけで、動画の文字起こしからnote記事の構成、アイキャッチ画像、さらにX（旧Twitter）の告知ポストまでを全自動で生成するn8nワークフローの構築方法を解説した記事。動画コンテンツをテキストや他媒体へ「マルチユース」する際の単純作業を排除し、クリエイティブな時間を確保するための具体的な自動化手順が紹介されている。

## Key Learning Points
- **ワークフローの全体像**: YouTube文字起こし、記事構成・目次作成、画像生成、note本文・X投稿文生成の4工程で構成される。
- **事前準備**: n8nのセットアップに加え、GCP（Google Drive, Sheets, Gemini API）、YouTube Transcript APIの設定が必要。
- **文字起こしとID抽出**: JavaScriptコードを用いてURLから動画IDを抽出し、APIで文字起こしを取得する。
- **AIによる構成・執筆**: AI Agentに特定の役割（ライター、画像クリエイター）とプロンプトを与え、読者を引きつける目次、本文、画像生成プロンプトを作成させる。
- **画像生成の自動化**: 目次項目ごとにループ処理を行い、Geminiでプロンプトを作成してから画像生成（nanobanana pro等を使用）し、Google Driveへ保存する。
- **マルチプラットフォーム展開**: 生成した記事とSNS告知文をGoogleスプレッドシートに自動記録し、資産化する。

## Key Message
動画を作って終わりではなく、マルチユースして初めてコンテンツは資産になる。単純作業に時間を費やす「昭和の作業」は終わりにし、n8nによる自動化で時間を奪還して、空いた時間を新しい知識のインプットや次の仕組み作り、大切な人との時間といった「創造」に充てるべきである。