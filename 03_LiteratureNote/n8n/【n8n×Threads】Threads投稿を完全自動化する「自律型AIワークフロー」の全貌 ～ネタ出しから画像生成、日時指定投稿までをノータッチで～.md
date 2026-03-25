---
articleTitle: 【n8n×Threads】Threads投稿を完全自動化する「自律型AIワークフロー」の全貌 ～ネタ出しから画像生成、日時指定投稿までをノータッチで～
posted_at: 2025-12-09
posted_by: [[こま｜n8n × AIよろず屋]]
tags:
  - n8n
  - Threads
  - 自動化
  - AI
  - Gemini
  - GoogleSheets
  - GoogleCloudPlatform
aliases:
  - Threads完全自動化ワークフロー
  - n8n×AI活用事例
  - SNS投稿自動化
  - Gemini画像生成連携
---
## Transcript by AI
<details>
  <summary>文字起こし</summary>
  
---
title: "【n8n×Threads】Threads投稿を完全自動化する「自律型AIワークフロー」の全貌 ～ネタ出しから画像生成、日時指定投稿までをノータッチで～｜こま｜n8n × AIよろず屋"
source: "https://note.com/ai_yorozuya/n/n77877aff0f31"
author:
  - "[[こま｜n8n × AIよろず屋]]"
published: 2025-12-09
created: 2026-01-21
description: "こまです。 Threads、盛り上がってますね。  でも、毎日スマホに張り付いて、通知を気にしながら手動で投稿していませんか？  はっきり言います。 その時間は、人生の無駄遣いです。  今回は、ノーコードツール「n8n」を使って、Threadsへの投稿を「全自動化」し、さらに「日時指定」まで完璧にコントロールするワークフローを構築します。  経営者や多くのSNSマーケターが驚くレベルの自動化システムを、ド素人のあなたでも組めるように解説します。  これが今回作るワークフローの全貌です  覚悟はいいですか？  あなたのThreads運用が「労働」から「支配」に変わる瞬間を、これからお見せ"
tags:
  - "clippings"
---
![見出し画像](https://assets.st-note.com/production/uploads/images/235093563/rectangle_large_type_2_39254186a8febc43f45054fa942c92c6.png?width=1280)

## 【n8n×Threads】Threads投稿を完全自動化する「自律型AIワークフロー」の全貌 ～ネタ出しから画像生成、日時指定投稿までをノータッチで～

[こま｜n8n × AIよろず屋](https://note.com/ai_yorozuya)

¥2,980

こまです。 Threads、盛り上がってますね。

でも、毎日スマホに張り付いて、通知を気にしながら手動で投稿していませんか？

はっきり言います。 **その時間は、人生の無駄遣いです。**

今回は、ノーコードツール「n8n」を使って、Threadsへの投稿を「全自動化」し、さらに「日時指定」まで完璧にコントロールするワークフローを構築します。

経営者や多くのSNSマーケターが驚くレベルの自動化システムを、ド素人のあなたでも組めるように解説します。

これが今回作るワークフローの全貌です

![画像](https://assets.st-note.com/img/1765245426-yPBE3efs4unIcKazY6ilJhkD.png?width=1200)

覚悟はいいですか？

あなたのThreads運用が「労働」から「支配」に変わる瞬間を、これからお見せします。

## 第1章 ワークフロー作成の事前準備

本格的なワークフロー構築に入る前に、いくつかの準備が必要です。

### n8nの基本設定

n8nのアカウント作成がまだの方は、先に済ませておきましょう。

### GCPのアカウント作成と設定

n8nとGoogleのサービスを連携させるのに設定が必要です。

### 各種クレデンシャルの設定

- **Google OAuth**  
	Google Driveやスプレッドシートを読み書きするために必要です。

- **Google Cloud Storage**

GoogleCloudStorageのシークレットキーも取得しておいてください。

**Google Sheets Account**

スプレッドシートに書き込むために連携が必要です。

まずn8nのダッシュボードの右上の「Create Credential」をクリック。

![画像](https://assets.st-note.com/img/1765245537-96uUtcmy7zfPlvh41J0GqCgo.png?width=1200)

GoogleSheetと入力して、Google Sheets OAuth2 APIをクリック

  

![画像](https://assets.st-note.com/img/1765245537-QejFBT3RrEWaOYwUfZI81HbA.png)

「Sign in with Google」をクリックしてご自身のGoogleアカウントでログインする。

![画像](https://assets.st-note.com/img/1765245537-vhPbqEDiNQyc6deV7pkWAwxa.png?width=1200)

- **Gemini API**  
	文章・画像生成を利用するためにAPIキーが必要です。

- **Threads API**

- スプレッドシート
	- ファイル名：Threads投稿管理
	- シート名：投稿一覧
	- 1行目に下記を記載
		- ステータス
		- 日時
		- 投稿テーマ
		- 投稿内容
		- 画像URL
![画像](https://assets.st-note.com/img/1765252044-jP0G3n6svSkEWBQiMNAVqZpd.png?width=1200)

## 第2章：【設計図】これから作るワークフローの全体像！

これから作りあげるワークフローは2つの工程で動きます。

### フロー1：スプシにテーマを入力するだけで自動で投稿を作成してくれる。

![画像](https://assets.st-note.com/img/1765246151-jzyomP86MDKl4gqfstV0ECRU.png?width=1200)

### フロー2：スプシに記入した日に投稿を実施する

![画像](https://assets.st-note.com/img/1765246211-F5RUgi7lDjCGATKNY9dsatJr.png?width=1200)

## 第3章：【実践】コピペでOK！Threads自動投稿ワークフロー構築マニュアル

お待たせしました。ここからが実践です。n8nの画面を開き、私と一緒に手を動かしていきましょう。

### 【パート1】コンテンツ自動生成フロー（テーマ入力 → AI生成 → 保存）

このラインより上のエリアが 無料で表示されます。

**① Google Sheets Trigger**

スプレッドシートに「投稿テーマ」が入力されたことを検知して起動します。

設定

- Credentials：作成したGoogle Sheets Trigger accountを選択
- Poll Time：Every Minute
- Document：Threads投稿管理
- Sheet：投稿一覧
- Trigger On：Row Added or Updated
- Include in Output：New Version
- Options
	- Columns to Watch：投稿テーマ
![画像](https://assets.st-note.com/img/1765248232-rfQsGyS30nZkNCjeAoqlbw2z.png?width=1200)

**② If (Status Check)**

ステータスが「Todo」の行だけを処理するようにフィルタリングします。

設定

- **Conditions**
	- {{ $json\['ステータス'\] }}
	- Equal to
	- Todo
![画像](https://assets.st-note.com/img/1765249153-OPvxXcpJl8Hhayw1RZ5B37Fz.png?width=1200)

③loop Over Items

作成する投稿の数だけ実行するようにします

設定

- Batch Size：1
![画像](https://assets.st-note.com/img/1765249348-NBi6CRZEzKsqd85LMDwjObhS.png?width=1200)

**④ AI Agent (投稿文作成)**

**設定**

- Source for Prompt (User Message)：Define belowを選択。
- System Prompt：下記プロンプトを入力。

> \# 命令書  
> あなたはSNSマーケティングのプロフェッショナルです。  
> 以下の\[投稿テーマ\]をもとに、Threads（スレッズ）で最もエンゲージメント（いいね・保存・再投稿）が期待できる「至高の1投稿」を作成してください。  
>   
> \# 投稿テーマ  
> {{ $json\['投稿テーマ'\] }}  
>   
> \# 思考プロセス（内部処理）  
> 1\. \*\*キーワード分析\*\*: キーワードの性質（共感、有益、逆説、ストーリー、問いかけ）を分析する。  
> 2\. \*\*型の選定\*\*: 以下のフレームワークの中から、今回のキーワードで最もバズる確率が高い\*\*「ベストな1つの型」\*\*を選定する。  
> 3\. \*\*投稿作成\*\*: 選定した型に特化し、Threads特有のトーンで執筆する。  
>   
> \# バズりフレームワーク（選択肢）  
> \- 【共感・あるある型】（日常のモヤモヤ、失敗談、インサイト）  
> \- 【有益・ノウハウ型】（具体的な解決策、箇条書き、保存推奨）  
> \- 【逆説・本音型】（常識へのアンチテーゼ、鋭い意見、議論喚起）  
> \- 【ストーリー・変化型】（Before/After、具体的な数字とエピソード）  
> \- 【問いかけ・参加型】（リプライ欄への誘導、クイズ、相談）  
>   
> \# 制約条件  
> \- \*\*出力は「最終的な投稿案」の1つのみとする。\*\*  
> \- 1行目はスクロールを止める強力なフック（興味付け）を入れること。  
> \- 堅苦しい表現は避け、距離感の近い「独り言」のような口語体にする。  
> \- 漢字とひらがなのバランスを調整し、視覚的な読みやすさを意識する。  
> \- 140文字〜300文字程度。  
> \- ハッシュタグは原則なし（どうしても必要な場合のみ1つ）。  
>   
> \# 出力形式  
> 投稿本文のみテキストで出力してください。  
>   
> \---  
> それでは、入力キーワードから最適解を導き出し、投稿を作成してください。

![画像](https://assets.st-note.com/img/1765249473-M5HhqNSlXsZ73iRkmz4wBrYx.png?width=1200)

画面下部のChat Modekを設定します。

![画像](https://assets.st-note.com/img/1765249428-6pI18JVzlf9ChNaisWRSMb0e.png?width=1200)

OpenAIのモデルを選択し、CredentialとModelを選択します。Modelは今回はgemini-2.5-flashを選んでます。

![画像](https://assets.st-note.com/img/1765249527-KsJpXxMFVlv8uzbiDjO9Ec2q.png?width=1200)

⑤if

文字数が500文字以内になってるかチェックします

設定

- Conditions
	- {{ $('AI Agent').item.json.output.length }}
	- is less than
	- 500
![画像](https://assets.st-note.com/img/1765249594-KyekWHGRAOPDXwZuMtiVUhbL.png?width=1200)

⑥Gemini（Message a model）

- Credentials：作成したGeminiのCredentialsを選択
- Resource：Text
- Operation：Message a Model
- Model：models/gemini-2.5-flash
- Role：User
- Prompt

> 下記Threadsの投稿に合う画像を生成したいです。  
> 画像生成プロンプトを作成してください  
>   
> \## 注意事項  
> 画像はイラスト風にしてください。  
>   
> \## 出力形式  
> 英文の画像生成プロンプトのみ出力してください。  
>   
> \## 投稿文章  
> {{ $json.output }}

**⑦Gemini（ Generate an image）**

Geminiの画像生成モデルを使用して、前のノードで作成したプロンプトから画像を生成します。

- **設定**
	- **Resource** ：Image
	- Operation：Generate an Image
	- **Model** ：gemini-2.5-flash-image
	- **Prompt** ：{{ $json.content.parts\[0\].text }}  
		（前のノードで生成したプロンプトを参照）
![画像](https://assets.st-note.com/img/1765249843-Owma4uxPW5I3sZV0EfCKbJSk.png?width=1200)

**⑥ Google Cloud Storage (Create an object)**

生成された画像をThreads API経由で投稿するため、一度Google Cloud Storageにアップロードして公開URLを発行します。

設定

- Credentials：作成したCredentialsを設定
- Resource：Object
- Operation：Create
- Bucket Name: n8n-threads
- Object Name: {{ DateTime.now().format("yyyy-MM-dd-HH-mm-ss") }} (現在日時をファイル名にする)
- Orpjection：All Properties
- USe Input Binary Field：オンにする
- Input Binary Field：data
![画像](https://assets.st-note.com/img/1765249963-vQTgrbtlR5PMB4Ahs10VXnEG.png?width=1200)

**⑦ Append or update row in sheet**

生成された「投稿本文」と「画像URL」をスプレッドシートに書き戻し、ステータスを「Ready」に変更します。

設定

- Credentials：作成したGoogle SheetのCredentialsを選択します
- Resource：Sheet Within Document
- Operation：Append or Update Row
- Document：Threads投稿管理
- Sheet：投稿一覧
- Mapping Column Mode：MAp Each Column Manually
- Column to match on：投稿テーマ
- Values to Send
	- 投稿テーマ：{{ $('Google Sheets Trigger').item.json\['投稿テーマ'\] }}
	- ステータス：Ready
	- 投稿内容：{{ $('AI Agent').item.json.output }}
	- 画像URL：{{ $('Create an object').item.json.mediaLink }}
![画像](https://assets.st-note.com/img/1765250148-hnkiGLsPbNgrOue5S4Ztx1Io.png?width=1200)

---

### 【パート2】予約投稿フロー（日時判定 → Threads API投稿）

**①Schedule Trigger**

毎日決まった時間に起動し、投稿すべきデータがあるか確認します。  
指定した日の7時に投稿する設定になっています。

設定

- Trigger Interval：Days
- Days Between Triggers：1
- Trigger at Hour：7am
- Trigger at Minute：0
![画像](https://assets.st-note.com/img/1765250540-W9DldfyA85mYMgTxF0cqkE3o.png)

②Google Sheet（Get row(s) in sheet）

スプレッドシートから、生成済みで未投稿（ステータスが「Ready」）のデータを取得します。

設定

- Credentials to connect with：作成したCredentialsを設定
- Resource：Sheet Within Document
- Operation：Get Row(s)
- Document：Threads投稿管理
- Sheet：投稿一覧
- Filters
	- Column：ステータス
	- Values：Ready
- Combine Filters：AND
- Operations
	- Return only Matching Row：オンにする
![画像](https://assets.st-note.com/img/1765250793-8YmhXSo05GtHjdDUQy3wnBVZ.png?width=1200)

**⑩ If**

取得したデータの「日時」列と「今日の日付」が一致するか判定します。一致する場合のみ投稿に進みます。

- **設定**
	- **Conditions**:
		- {{ $json\['日時'\] }}
		- Equal to
		- {{ DateTime.now().format("yyyy/MM/dd") }}
![画像](https://assets.st-note.com/img/1765250829-g2svp5EBVA9UNbn4xt37DGqP.png?width=1200)

**⑪ Edit Fields**

ThreadsのAPIリクエストに必要なユーザーIDを定義します。

設定

- Fields to Set
	- name：user\_id
	- value：ご自身のThreadsユーザーIDを設定してください
![画像](https://assets.st-note.com/img/1765251117-6heVlZREqbkAm2Yd7H4F0SLn.png?width=1200)

**⑫ HTTP Request**

Threads APIを叩き、画像とテキストを含む「メディアコンテナ」を作成します。

設定

- Method：POST
- URL：https://graph.threads.net/v1.0/{{ $json.user\_id }}/threads
- Authentication：Generic Credential Type
- Generic Auth Type：Bearer Auth
- Bearer Auth：作成したThreadsのCredentialsを設定
- SendBody：オンにする
	- Body Content Type：JSON
	- Specify Body：Using Fields Below
	- Body PArameters
		- Name：media\_type
			- Value：IMAGE
		- Name：image\_url
			- Value：{{ $('Get row(s) in sheet1').item.json\['画像URL'\] }}
		- Name：text
			- Value：{{ $('Get row(s) in sheet1').item.json\['投稿内容'\] }}
![画像](https://assets.st-note.com/img/1765251460-NaAIVFMfqyXZ3LshxO1WKBnj.png?width=1200)

![画像](https://assets.st-note.com/img/1765251469-gcjYhvm16U3epLaWTxOrtDC0.png?width=1200)

**⑬ Wait**

APIの処理待ち時間を確保します。コンテナ作成から公開まで間隔を空けないとエラーになることがあるためです。

設定

- Resource：After Time Interval
- Wait Amount：15.00
- Wait Unit：Seconds
![画像](https://assets.st-note.com/img/1765251439-56uBcZNVvJ3KLnMhpd2tEa8Y.png?width=1200)

**⑭ HTTP Request**

作成したコンテナIDを指定して、実際に投稿を公開（Publish）します。

設定

- Method：POST
- URL：https://graph.threads.net/v1.0/{{ $('Edit Fields').item.json.user\_id }}/threads\_publish
- Authentication：Generic Credential Type
- Generic Auth Type：Bearer Auth
- Bearer Auth：作成したThreadsのCredentialsを設定
- SendBody：オンにする
	- Body Content Type：JSON
	- Specify Body：Using Fields Below
	- Body PArameters
		- Name：creation\_id
			- Value：{{ $json.id }}
![画像](https://assets.st-note.com/img/1765251547-sQHuDNFXvGkUfiWZ0bhRo2zc.png?width=1200)

![画像](https://assets.st-note.com/img/1765251558-4qADQliuhpbOK8yxeLmZC0No.png?width=1200)

**⑮ Append or update row in sheet**

無事に投稿が完了したら、スプレッドシートのステータスを「Done」に更新します。

設定

- Credentials：作成したGoogle SheetのCredentialsを選択します
- Resource：Sheet Within Document
- Operation：Append or Update Row
- Document：Threads投稿管理
- Sheet：投稿一覧
- Mapping Column Mode：MAp Each Column Manually
- Column to match on：投稿テーマ
- Values to Send
	- 投稿テーマ：{{ $('Get row(s) in sheet1').item.json\['投稿テーマ'\] }}
	- ステータス：Done
![画像](https://assets.st-note.com/img/1765251643-3PDVTM4QWIAzCrS6ueOi1YLx.png?width=1200)

## 最後に…自動化の先にある、あなたの本当の仕事

おめでとうございます。 これであなたのThreadsは、あなたが寝ている間も、デートをしている間も、自動でコンテンツを投下し続ける「資産」になりました。

「Botっぽくなるのが怖い？」 安心してください。このワークフローの前にChatGPTノードを挟み、「投稿内容を少し人間らしくリライトして」と指示を出せば、もはや誰もBotとは見抜けません。

浮いた時間で何をするか。 新しいコンテンツを考えるもよし、別のビジネスを立ち上げるもよし。 ツールに使われるな、ツールを使え。 今日からあなたが、支配者です。

![画像](https://assets.st-note.com/img/1765246641-NRGWOCyF8mQlr7Bct0aVDdMS.jpg?width=1200)

## 【特別プレゼント】最後に、あなたへ誰でも簡単にこの自動化が実現できるファイルをお渡しします

ここまで、この長く、しかし熱量の高いマニュアルを読み切ってくれたあなたへ。 心からの感謝と敬意を表します。

あなたはもう、コンテンツが自動で生まれる世界の理論と構造を完全に理解しました。 しかし、理論を実践に移すには、まだ少しだけ「作業」が必要です。

…私としたことが、まだあなたに「楽」をさせきれていませんでした。

そこで、この記事を最後まで読んでくれた本気のあなただけに、最後のプレゼントを用意しました。 **構築の時間すらショートカットし、今日この瞬間から「Xの完全自動運用」** が可能です。

[**【n8n×Threads】Threads投稿を完全自動化する「自律型AIワークフロー」の全貌 ネタ出しから画像生成、日時指定投稿までをノータッチで | Notion** *感想の引用リツイートありがとうございます！* *www.notion.so*](https://www.notion.so/n8n-Threads-Threads-AI-2c477d64cc39802b8b9df8e0e750a5fe)

これは単なるテンプレートではありません。 私の思考が詰め込まれた **「魔法の設計図」** そのものです。

あなたがやることは、たった一つ。 このファイルをダウンロードし、あなたのn8nにインポートするだけ。 面倒なノード設定やプロンプト入力をすべて飛び越え、クリック一つで、あなたのPCに私と同じ魔法のワークフローが姿を現します。

![画像](https://assets.st-note.com/img/1765246620-urw84biVTHBey7aA6kEvgonp.jpg?width=1200)

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

このnoteの「さらに先」… あなた専用の「自動化設計図」と「禁断の魔改造プラン」を、私自身があなたの業務内容を分析し、その場で提示します。

なぜこんなことをするのか？ 簡単です。私自身が、AIとn8nによって人生が激変する瞬間を、この目で直接見たいからです。 あなたの「脳汁が溢れ出す」瞬間を、私にプロデュースさせてください。

ただし、私の時間も有限です。 一人ひとりに本気で向き合うため、このコンサルを受けられるのは【先着3名様】のみとさせていただきます。 （※本気の方の時間を確保するため、冷やかしは固くお断りします）

**【応募方法】**

1. 下記の公式LINEに登録する
2. 「 **無料コンサル希望** 」と、一言だけメッセージを送る

[**Add LINE friend** *dz2knout.autosns.app*](https://dz2knout.autosns.app/line)

たったこれだけです。 私から返信があった方が、当選となります。（定員に達し次第、即座に締め切ります）

このチャンスを掴むか、掴まないか。 「設計する側」への切符は、今あなたの目の前にあります。

行動の速い、先見の明のある方からのご連絡をお待ちしています。

【n8n×Threads】Threads投稿を完全自動化する「自律型AIワークフロー」の全貌 ～ネタ出しから画像生成、日時指定投稿までをノータッチで～｜こま｜n8n × AIよろず屋
</details>

## Summary
本記事は、ノーコードツール「n8n」を活用してThreadsへの投稿を完全自動化し、日時指定までコントロールするワークフローの構築方法を解説しています。ネタ出しからAIによる文章・画像生成、そしてAPIを通じた予約投稿までをノータッチで行うための具体的な手順（事前準備、ノード設定、プロンプト例）が詳述されています。

## Key Learning Points
- **ワークフロー構築の事前準備**
    - n8nの基本設定およびGCP（Google Cloud Platform）との連携設定が必要。
    - 必要なクレデンシャル：Google OAuth（Drive/Sheets用）、Google Cloud Storage、Gemini API、Threads API。
    - 管理用スプレッドシートの作成（ステータス、日時、投稿テーマ、投稿内容、画像URLなどを管理）。
- **コンテンツ自動生成フロー（パート1）**
    - **Google Sheets Trigger**: スプレッドシートへのテーマ入力を検知して起動。
    - **AI Agent (Gemini)**: 指定されたプロンプトに基づき、エンゲージメントが高い投稿文を生成。
    - **画像生成**: 投稿文から画像生成プロンプトを作成し、Geminiで画像を生成。Google Cloud Storageに保存してURLを発行。
    - **データ保存**: 生成された投稿文と画像URLをスプレッドシートに書き戻し、ステータスを更新。
- **予約投稿フロー（パート2）**
    - **Schedule Trigger**: 毎日定時に起動。
    - **条件判定**: スプレッドシートから未投稿データを取得し、投稿日時が「今日」であるか判定。
    - **Threads API利用**: 画像とテキストを含むメディアコンテナを作成し、公開リクエストを送信。
    - **ステータス更新**: 投稿完了後、スプレッドシートのステータスを「Done」に変更。

## Key Message
手動でのSNS投稿に時間を費やすのは人生の無駄遣いであり、自動化によって運用を「労働」から「支配」に変えるべきである。ツールを使いこなし、浮いた時間で新しいコンテンツやビジネスの創造に注力することが重要だ。