---
articleTitle: 【n8n × ChatGPT】OpenAI連携 完全ガイド！APIキー取得からCredential設定まで徹底解説｜こま｜n8n × AIよろず屋
posted_at: 2025-10-14
posted_by: こま｜n8n × AIよろず屋
tags:
  - n8n
  - OpenAI
  - ChatGPT
  - API連携
  - 自動化
aliases:
  - n8n OpenAI連携手順
  - OpenAI APIキー取得方法
  - n8n Credential登録
  - OpenAI API利用制限解除
  - n8n AI連携
---
## Transcript by AI
<details>
  <summary>文字起こし</summary>
  
![見出し画像](https://assets.st-note.com/production/uploads/images/222156220/rectangle_large_type_2_8f602c8494dfaba6adc12b4ad78b4fa9.png?width=1280)

## 【n8n × ChatGPT】OpenAI連携 完全ガイド！APIキー取得からCredential設定まで徹底解説

[こま｜n8n × AIよろず屋](https://note.com/ai_yorozuya)

n8nでの自動化で挑戦したくなるのが「AIとの連携」ではないでしょうか。 特に、ChatGPTやDALL-Eで知られるOpenAIの強力なAIモデルをn8nに組み込むことができれば、あなたのワークフローは単なる自動化ツールから、 **自ら思考し、創造する「賢い相棒」へと進化** します。

> **「でも、API連携って設定が複雑そう…」  
> 「英語のサイトで、どこをどう設定すればいいか分からない」**

ご安心ください。 この記事では、n8nとOpenAIを連携させるための最重要プロセスである「APIキーの取得」 **から** 「n8nへのCredential（クレデンシャル）登録」 **、そして多くの人がつまずく** 「APIの利用制限解除」まで、

全てのステップを実際の画面に沿って、一つも漏らさず丁寧に解説します。

この記事を読み終える頃には、あなたはAIの力を自在に操るための、最も重要な”鍵”を手に入れているはずです。

## 第1章：OpenAIアカウントの準備とAPIキーの取得

まずは、n8nに渡すための”合鍵”となる「APIキー」をOpenAIから発行してもらいます。

### STEP 1: OpenAI公式サイトへアクセスし、APIプラットフォームに登録する

まず、OpenAIの公式サイト（ [https://openai.com/ja-JP/](https://openai.com/ja-JP/) ）にアクセスします。

![画像](https://assets.st-note.com/img/1760183019-TyhNYbtimB7C0RuMK9152SI3.png?width=1200)

画面右上の「ログイン」にマウスカーソルを合わせると表示されるメニューから、「 **APIプラットフォーム** 」をクリックします。 ここからアカウント登録を進めていきましょう。Googleアカウント、またはメールアドレスで登録が可能です。

![画像](https://assets.st-note.com/img/1760183134-mMf2UgBCiZsayWRzweAdqVnr.png?width=1200)

初めてログインする際は、名前や生年月日の入力を求められますので、指示に従って入力してください。組織情報の入力を求められた場合も同様です。

![画像](https://assets.st-note.com/img/1760183366-O2DshgrfUiwpTFLckXHKVCx6.png)

### STEP 2: プロジェクトを作成し、APIキーを発行する

登録が完了してダッシュボードに移動したら、いよいよAPIキーを作成します。

![画像](https://assets.st-note.com/img/1760182800-HQR6T2rcDCJnx5E7XPia9G4O.png?width=1200)

「 **Start building** 」をクリックして、プロジェクト作成画面へ進みます。

![画像](https://assets.st-note.com/img/1760183922-fiApuXmeZ65dJTo0lrM1gYRx.png?width=1200)

「Organization name」には任意のプロジェクトの名前（今回は「n8n integration」としておきます）  
「What best describes you?」には利用目的（なんでもよい）を選択してください。

![画像](https://assets.st-note.com/img/1760183852-Rgi4F5TnowxObUkVB1N2hzcp.png)

「Create organization」のボタンをクリックすると、メンバーを招待されるか聞かれます。今回はスキップしたいので、下の「I\`ll invite my team later」をクリックします。

![画像](https://assets.st-note.com/img/1760184021-Hhdv8lsbNQCE1Uuq2pmV0GiI.png)

API key nameとProject nameを聞かれるので、今回は両方とも「n8n integration」にしておきます。（自分で管理しやすい、わかりやすい名前を付けてください）

![画像](https://assets.st-note.com/img/1760184132-X85BNuzlgnPsSe97vbOWocYL.png)

「 **Generate API Key** 」ボタンをクリックすると、英数字の長い文字列が表示されます。これがあなた専用のAPIキーです。

**【超重要】**  
このAPIキーは、一度この画面を閉じると二度と表示されません。必ず表示された瞬間に「コピー」ボタンを押し、メモ帳などの安全な場所に貼り付けて保管してください。

![画像](https://assets.st-note.com/img/1760184192-EI6lpMuTX0Gf2ykwF9ZPhDNJ.png)

APIキーをコピーしたら、「Continue」ボタンを押します。 クレジットの購入を促されますが、ここでは一旦「I'll buy credits later」をクリックして先に進みましょう。

![画像](https://assets.st-note.com/img/1760184296-o9JwaXmpuhk0Ibq7eFvZC6VH.png)

これでAPIキーの発行は完了です。

## 第2章：n8nへのCredential登録

次に、n8nに戻り、先ほど取得したAPIキーを登録します。

### STEP 1: n8nでCredential作成画面を開く

まずはn8n（ [https://volcite.app.n8n.cloud/home/workflows](https://volcite.app.n8n.cloud/home/workflows) ）ダッシュボードを開きます。

![画像](https://assets.st-note.com/img/1760184640-83ICGAbWRPn52cN69sSDqH1F.png?width=1200)

画面右上の「Create Workflow」ボタンの右にある下向き矢印（▼）をクリックし、表示されたメニューから「 **Create Credential** 」を選択します。

![画像](https://assets.st-note.com/img/1760184709-LQUtrHIMgVC7zifW4PSBK50l.png?width=1200)

### STEP 2: OpenAIのCredentialを設定する

下記画面で検索窓に「 **OpenAI** 」と入力し、表示されたOpenAIをクリックします。

![画像](https://assets.st-note.com/img/1760184761-lNXomd3YyhSLZ1cRqrMpKvDT.png)

右下の「Continue」ボタンをクリックします。

![画像](https://assets.st-note.com/img/1760184803-ozgvn1QaP6LrFeNkCY4GlXHt.png)

「API Key」と表示されている入力欄に、先ほどコピーしておいたOpenAIのAPIキーを貼り付けます。

![画像](https://assets.st-note.com/img/1760184864-NOcrgKUymIwEVXtfGDLaPz28.png?width=1200)

右上の「Save」を押して問題なく保存できればn8nとOpenAIのAPIの連携は完了です！

![画像](https://assets.st-note.com/img/1760184923-YNiIpX0oGcevEQKAW5mgOPfk.png?width=1200)

![画像](https://assets.st-note.com/img/1760184935-CFOs0L6zMqkSoUjmGbuHlTrI.png?width=1200)

## 第3章：OpenAI APIの利用制限解除（本人確認と支払い設定）

現在の状態では、まだOpenAIのAPIを自由に使うことができません。APIを本格的に利用可能にするため、本人確認と支払い情報の登録を完了させましょう。

### STEP 1: 支払い方法を追加する

OpenAIのAPIプラットフォームに再度アクセスし、画面右上の歯車アイコン（Settings）をクリックします。

![画像](https://assets.st-note.com/img/1760343600-4qQaW10NwHxABMvXiZptks5O.png?width=1200)

「Verify Organization」のボタンをクリックします

![画像](https://assets.st-note.com/img/1760343644-hoGN8AZFqL9tiJvK4IWkdVcP.png?width=1200)

支払い方法が未登録の場合、「 **Add payment method** 」をクリックして、クレジットカード情報を登録してください。

![画像](https://assets.st-note.com/img/1760343730-4EQniroM1Ify0wmDPuFbK9jv.png)

### STEP 2: クレジットをチャージする

左側メニューの「 **Overview** 」などをクリックし、支払い設定画面へ進みます。

![画像](https://assets.st-note.com/img/1760343824-pIMLORXTj8rAiJl3PWynsfzF.png?width=1200)

「 **Add payment details** 」をクリックし、請求先の情報を入力します。

![画像](https://assets.st-note.com/img/1760343863-rYP4EDhzTOejq8owIK5U9ckS.png?width=1200)

クレジットカードや請求先の情報を入力して、右下の「Continue」をクリックします。

![画像](https://assets.st-note.com/img/1760344044-5LpcYnIH6k91OdB8KSz7DFqR.png)

OpenAIのAPIは課金しないと利用できないため、5ドルだけチャージしておきます。

**【注意】** クレジットが少なくなった際に自動でチャージする「Auto-recharge」のチェックは、意図しない高額請求を防ぐために外しておくことを推奨します。

内容を確認してチャージを完了させます。

![画像](https://assets.st-note.com/img/1760344139-xJPq4j8OpQFXCdUf0KHSNrgV.png)

### STEP 3: 本人確認（ID Check）を完了させる

右上の歯車ボタンをクリックします。

![画像](https://assets.st-note.com/img/1760343600-4qQaW10NwHxABMvXiZptks5O.png?width=1200)

再度「Verify Organization」をクリックします

![画像](https://assets.st-note.com/img/1760344291-zxI146bkeuUDaSPsRjyJHhWt.png?width=1200)

「Start ID Check」をクリックします

![画像](https://assets.st-note.com/img/1760344339-VmyXTiOGWaJIqfC0MUls7Q2E.png)

本人確認が始まるので、同意にチェックを入れて、今すぐ始めるボタンをクリックしてください。（マイナンバーカード、運転免許証、パスポートで実施できます）

![画像](https://assets.st-note.com/img/1760344397-PhoB1fdYjMr2EwbCgmDvqtGN.png)

PCで実施している方はスマホでQRを読み取って本人確認を実施しましょう。

![画像](https://assets.st-note.com/img/1760344466-MKXJ5wiHhbf9Rd7njUFyluYx.png)

「Verified」という表示が出れば、すべての手続きは完了です！ これで、あなたはn8nからOpenAIのAPIを自由に呼び出すことができるようになりました。

![画像](https://assets.st-note.com/img/1760344800-V8NQROyenx7qiUDvckAWPwKf.png?width=1200)

## 終章：ようこそ、AI自動化の世界へ

お疲れ様でした！ これで、あなたのn8nはOpenAIという強力な頭脳を手に入れました。

文字起こし、文章の要約や生成、画像の作成など、これまで人間の手と思考が必要だったタスクを、これからはワークフローの中に自由に組み込むことができます。

ぜひ、この新しい力を使って、あなたの創造性を最大限に発揮してください。

【n8n × ChatGPT】OpenAI連携 完全ガイド！APIキー取得からCredential設定まで徹底解説｜こま｜n8n × AIよろず屋
</details>

## Summary
この記事は、ノーコード自動化ツール「n8n」とOpenAI（ChatGPTなど）を連携させる手順をステップバイステップで解説したガイドです。n8nにOpenAIの機能を組み込むことで、ワークフローを「賢い相棒」へと進化させる方法を紹介しています。主な内容は、OpenAIのAPIキーを取得する方法、n8n上でそのキーを使ってCredential（クレデンシャル）を登録する手順、そしてAPIを実際に利用可能にするための支払い設定（クレジットチャージ）と本人確認（ID Check）のプロセスです。

## Key Learning Points
*   **APIキーの取得手順**: OpenAI公式サイトのAPIプラットフォームに登録し、プロジェクトを作成してAPIキーを発行する。発行されたキーは一度しか表示されないため、即座に保存する必要がある。
*   **n8nでのCredential登録**: n8nダッシュボードの「Create Credential」から「OpenAI」を検索し、取得したAPIキーを入力・保存することで連携設定が完了する。
*   **API利用制限の解除**:
    *   API利用にはクレジットカード情報の登録と、事前のクレジットチャージ（最低5ドルなど）が必要。
    *   「Auto-recharge」機能は意図しない高額請求を防ぐためにオフにすることが推奨される。
    *   「Verify Organization」から本人確認（ID Check）を行い、「Verified」ステータスにする必要がある。

## Key Message
n8nとOpenAIを連携させることで、これまで人間が行っていた思考や創造が必要なタスクをワークフローに組み込み、自動化ツールを「賢い相棒」へと進化させることができる。