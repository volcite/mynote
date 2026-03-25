---
articleTitle: "【禁断の動画錬金術】n8nで動画生成から編集までを「完全無人化」する方法｜こま｜n8n × AIよろず屋"
posted_at: 2025-12-20
posted_by: "[[こま｜n8n × AIよろず屋]]"
tags:
  - clippings
  - n8n
  - 動画生成AI
  - 自動化
  - Creatomate
  - Gemini
  - GoogleCloud
aliases:
  - 動画自動生成システム
  - n8n動画編集自動化
  - Creatomate活用法
  - Gemini Veo 2.0
  - 完全無人化動画制作
---
## Transcript by AI
<details>
  <summary>文字起こし</summary>

## 【禁断の動画錬金術】n8nで動画生成から編集までを「完全無人化」する方法

[こま｜n8n × AIよろず屋](https://note.com/ai_yorozuya)

  
あなたはまだ、Premiere Proを開いてカット編集をしているのですか？  
あるいは、動画生成AIで作った素材を、いちいちダウンロードして編集ソフトに並べているのですか？

今回公開するのは、動画制作の概念を破壊する自動化システムです。  
あなたがやることはたった一つ。「どんな動画が見たいか」をフォームに入力するだけ。

あとは勝手に裏側で

1. Googleの最新AI「Veo」が動画素材を撮影し
2. **Google Cloud** がデータを高速転送し
3. **Creatomate** がプロのクオリティで編集し
4. **Google Drive** に完成品が届く

この魔法のような仕組みを、n8nという最強のツールで実現します。  
この構築法を知ってしまえば、あなたは寝ている間に数百本の動画を作る「動画工場長」になることでしょう。

脳汁が出る準備はできましたか？  
それでは、始めましょう。

## なぜ「Creatomate」なのか？動画革命の正体

多くの人が勘違いしています。  
「動画生成AI」があれば動画が作れると。  
しかし、生成された動画はただの「素材」に過ぎません。それを繋ぎ、エフェクトをかけ、BGMを入れる「編集」こそが最も面倒な作業なのです。

今回のシステムの肝はここにあります。

- **Gemini Veo 2.0**  
	Googleが発表したばかりの動画生成モデル。指示理解能力が圧倒的に高く、高品質な動画を数秒で生成します。
- **Creatomate**  
	APIで動く動画編集クラウド。コードベースで動画を編集できるため、テンプレートさえあれば無限に量産が可能になります。

この2つをn8nで繋ぐこと。それはつまり、 **「撮影」と「編集」という2つの巨大な工程を、たった一つのボタンに集約すること** を意味します。

## 【設計図公開】完全自動化ワークフローの全貌

まずは、今回構築するシステムの全体像を頭に叩き込んでください。  
データの流れを理解していると、構築が簡単です。

今回は概要をつかんでもらうために簡単に動画を結合するワークフローを作ります。

![画像](https://assets.st-note.com/img/1766209735-apK81HcJLv6VfWTosuPrRhOz.png?width=1200)

## 事前準備：ワークフローを操るための3つの鍵

n8nを触る前に、以下の3つのアカウントと設定を済ませておいてください。これが「鍵」です。

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

- **Creatomate**

CreatomateのAPIを使えるように設定します。

これらの設定が完了していることを前提に、ワークフローを作成していきます。 n8nのダッシュボードで新しいワークフローを作成し、早速始めましょう！

### GoogleDriveにフォルダを作成

GoogleDriveに任意の名前のフォルダを作成します。（例：n8n動画編集）

### Creatomateでテンプレートを作成する

Creatomateのダッシュボードを開いて、Templateをクリックします。

![画像](https://assets.st-note.com/img/1766195065-Lpq8DsGhebP7KwR4SAWNlvIo.png?width=1200)

右上のNewをクリックします。

![画像](https://assets.st-note.com/img/1766195129-MDx5O2TmWqEAiN0vsjb4dJGS.png?width=1200)

ここでテンプレートを選択するんですが、今回は簡単なものを作ってみます。Start from scratchをクリックします。

![画像](https://assets.st-note.com/img/1766195190-lXEPu7sJweRyOxaqtb5jFHcZ.png?width=1200)

16:9のサイズを選択します。

![画像](https://assets.st-note.com/img/1766195263-PsjBayl5Im8HETc9zAGQMYUZ.png?width=1200)

図形のボタンをクリックします。

![画像](https://assets.st-note.com/img/1766195330-tON2jdocsZuLaFVlAQrSKBxI.png?width=1200)

何か自分のPCに保存されてる動画をドラッグ＆ドロップで配置します。。

右側のDurationを5に変えます。（5秒という意味です）

![画像](https://assets.st-note.com/img/1766209525-pJ0PdwTSl9t4o6LmYqhDbC75.png?width=1200)

次に名前を変更します。右クリックして、Renameをクリックします。名前をVideo-1に変更します。

![画像](https://assets.st-note.com/img/1766209570-QMcfhLE79dtnPv1G52X4sNAT.png?width=1200)

Video-1をコピーして複製してVideo-2という名前にします。Durationも5に変更します。

![画像](https://assets.st-note.com/img/1766209588-gcof3ZdFk6lPnXLhWVp2C5Km.png?width=1200)

これでテンプレートの設定は完了です。  
テンプレートIDを取得してメモ帳にコピーしておいてください。

動画のテンプレート画面の右上の「Use Template」をクリックします。

![画像](https://assets.st-note.com/img/1766195836-ZIRloqenTYcVhPtvirpUja5Q.png?width=1200)

API Integrationをクリックします。

![画像](https://assets.st-note.com/img/1766195835-n6OXPkSGZ8BKcYdVtgx70vHj.png?width=1200)

APIで変えられる要素とテンプレートIDが表示されます。赤枠で囲った項目がテンプレートIDです。これをコピーしてメモ帳に保存しておいてください。（これはテンプレートごとに異なります）

![画像](https://assets.st-note.com/img/1766195835-N0wpAyTLh23xuPqZcFUIoYzv.png)

## 【実践】n8n構築のステップバイステップ

ここからは具体的な設定です。  
初心者が必ず引っかかるポイントを潰しながら解説します。

### ステップ1 司令塔を作る（Form Trigger）

まず、動画生成の「命令」を出す場所です。

**①On form submission**

**設定**

- Form Title 動画のテーマを入力してください。
- Form Fields
- Text Field テーマ1
- Text Field テーマ2
![画像](https://assets.st-note.com/img/1766191349-rH0Ok549mRzDyENBQK86iwbg.png?width=1200)

![画像](https://assets.st-note.com/img/1766191374-EkZOA7grlQpyNcBR13z9Jdix.png)

ここで入力された言葉が、全ての始まりになります。「猫が走っている」「犬が寝ている」など、好きな言葉を入力するための窓口です。

### ステップ2 動画の素材の自動生成機能を実装する

動画生成と保存のルートは2つ作成します。  
このステップ2で作るものを2つ作って線でつなげます。

![画像](https://assets.st-note.com/img/1766191943-lcIt4R1CFAek3XfOvWSdDTQy.png)

**①Generate a video**

- Resource：Video を選択。
- Operation：Generate a Video
- Model：models/veo-2.0-generate-001
- Prompt

> 下記テーマに沿った動画を生成してください。  
> {{ $json\['テーマ1'\] }}

※もう一つのノードでは「{{ $json\['テーマ2'\] }}」にしてください。

![画像](https://assets.st-note.com/img/1766191639-P0Adf6bGU5HLvrj9w2Jx3VZE.png?width=1200)

**②Create an object**

AIが作った動画は、そのままではCreatomateに渡せません。一度ネット上の「URL」を持たせる必要があります。

- Resource：Object
- Operation：Create
- Bucket Name ：ここはあなたが作成したバケット名にしてください
- Object Name：movie1
- Use Input Binary Field：チェックを入れる
- Input Binary Field：data

※ObjectNameはもう一つのノードではmovie2にしてください。

![画像](https://assets.st-note.com/img/1766192100-XICoqORPigchs051pWaGfJTA.png?width=1200)

このノードが動くと、GCS上にファイルが保存されます。

**③Edit Fields**

**設定**

- Mode：Manual Mapping
- Field to Set
	- movie1
	- string
	- {{ $json.mediaLink }}

※もう一つのノードはmovie2にしてください。

![画像](https://assets.st-note.com/img/1766192344-9Si41OhRtZf0u2DrQLB7dPnY.png?width=1200)

### ステップ4 最強の編集ロボットを呼ぶ（Creatomate）

ここが最難関であり、最も強力な部分です。  
2つの動画URLを束ねて、Creatomateに編集指示を出します。

**①Merge**

**設定**

- Mode：Combine
- Combine By：Position
- Numper of Inputs：2
![画像](https://assets.st-note.com/img/1766192567-RiKzJ2lcTg1Z3oy0QjYS5Xma.png?width=1200)

**②HTTP Request**

2つのルートで生成された動画情報を一つにまとめます。

**設定**

- Method：POST
- URL ： [https://api.creatomate.com/v1/renders](https://api.creatomate.com/v1/renders%60)
- Authentication：Generic Credential Type
- Generic Auth Type：Bearer Auth
- Bearer Auth：CreatomateのCredentialsを先手くしてください。
- Send Body：チェックを入れる
- Body Content Type：JSON
- Specify Body：Using JSON
- JSON

```javascript
{
  "template_id": "あなたのテンプレートID",
  "modifications": {
    "Video-1": "{{ $json.movie1 }}",
    "Video-2": "{{ $json.movie2 }}"
  }
}
```

  

![画像](https://assets.st-note.com/img/1766192652-56vm8MLuCWxg2UpIQFKtnd01.png?width=1200)

![画像](https://assets.st-note.com/img/1766192710-wsj1MRJXEU97Vxz8o0bQqZGc.png?width=1200)

\`template\_id\`は、Creatomateの管理画面から取得したものに書き換えてください。  
また、\`modifications\`の中にあるキー（"Video-1"など）は、Creatomateのテンプレート内で設定した「要素名」と一致している必要があります。ここがズレていると、画面がデフォルトの動画が出来上がります。

### ステップ5 納品口を作る

最後は動画の回収です。

**①Wait  
**レンダリングには時間がかかります。15秒〜30秒ほど待機させます。

**設定**

- Resume：After Time Interval
- Wait Amount：15.00
- Wait Unit：Seconds
![画像](https://assets.st-note.com/img/1766193196-IvVUqoO39Sx8E6FubtPJABc1.png?width=1200)

**②HTTP Request**

生成した動画をダウンロードします

**設定**

- Method：GET
- URL ：
- Response
	- Response Format：File
	- Put Output in Field：data
![画像](https://assets.st-note.com/img/1766208777-klEB9Js4dONKMFP6QYo52XvW.png?width=1200)

![画像](https://assets.st-note.com/img/1766208791-ABsqpn3WZYOEGMc2uohlRtXQ.png?width=1200)

**③Google Drive（Upload file）**

Creatomateから返ってきた動画ファイルのURLを元に、Google Driveへアップロードします。

**設定**

- Resource：File
- Operation：Upload
- Input Data Field Name：data
- File Name：好きな名前にしてください。
- Parent Drive：My Drive
- Parent Folder：事前準備で作ったフォルダを選択
![画像](https://assets.st-note.com/img/1766193309-Gdp7mlvtVS8sBrxQJZFMqguK.png?width=1200)

## Creatomate追加解説

Creatomateを攻略すればかなりショート動画の制作が簡単になると思います。

  

## まとめ：動画編集はもう、人間の仕事ではない

いかがでしたか。  
これが、最先端のAI自動化の姿です。

あなたがキーボードで「テーマ」を打ち込み、コーヒーを一口飲んでいる間に、GoogleのAIが撮影し、クラウドが運び、APIが編集し、完成品が手元に届く。

これを体験してしまうと、もう自分でタイムラインを操作するのが馬鹿らしくなるはずです。

今回のワークフローは、まさに「未来へのチケット」です。  
ただし、設定箇所（バケット名、テンプレートID）だけは、あなたの環境に合わせて書き換える必要があります。

さあ、今すぐn8nを開いてください。  
そして、動画制作の常識をあなたの手で葬り去ってください。

![画像](https://assets.st-note.com/img/1766193514-G04TxDZnmMUYFiL2dVHe6uSl.jpg?width=1200)

## 【公開後48時間以内限定】最後に、あなたへ誰でも簡単にこの自動化が実現できるファイルをお渡しします

ここまで、この長く、しかし熱量の高いマニュアルを読み切ってくれたあなたへ。 心からの感謝と敬意を表します。

あなたはもう、コンテンツが自動で生まれる世界の理論と構造を完全に理解しました。 しかし、理論を実践に移すには、まだ少しだけ「作業」が必要です。

…私としたことが、まだあなたに「楽」をさせきれていませんでした。

そこで、この記事を最後まで読んでくれた本気のあなただけに、最後のプレゼントを用意しました。 **構築の時間すらショートカットし、今日この瞬間から「全自動コンテンツ制作」** が可能です。

これは単なるテンプレートではありません。 私の思考が詰め込まれた「魔法の設計図」そのものです。

あなたがやることは、たった一つ。 このファイルをダウンロードし、あなたのn8nにインポートするだけ。 面倒なノード設定やプロンプト入力をすべて飛び越え、クリック一つで、あなたのPCに私と同じコンテンツ工場が姿を現します。

> **【魔法を手に入れるための参加条件】**  
> **この記事の感想（「こんな自動化はヤバすぎる！」「これで睡眠時間が増える！」など一言でもOK！）を添えて、下記の投稿を「引用リツイート」してください。**

  

確認でき次第、「設計図」をお届けします。  
さあ、最後の行動です。 このチャンスを掴み取り、あなたの貴重な時間を未来のために使い始めましょう。

あなたの熱い感想を、Xで待っています。

![画像](https://assets.st-note.com/img/1766196209-nLfUETm2o04SyNFXBAczpCOM.jpg?width=1200)

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

【禁断の動画錬金術】n8nで動画生成から編集までを「完全無人化」する方法｜こま｜n8n × AIよろず屋
</details>

## Summary
n8n、Google Veo 2.0、Creatomate、Google Cloudを組み合わせることで、動画の生成から編集、納品までを完全自動化する「動画錬金術」の構築方法を解説しています。ユーザーはフォームに「見たい動画のテーマ」を入力するだけで、裏側でAIが素材を生成し、クラウド上で編集され、完成品がGoogle Driveに届くシステムを実現できます。具体的なn8nのワークフロー設定やCreatomateのテンプレート作成手順もステップバイステップで公開されています。

## Key Learning Points
*   **動画制作の自動化フロー**: 「撮影（Gemini Veo 2.0）」→「転送（Google Cloud Storage）」→「編集（Creatomate）」→「納品（Google Drive）」という一連の流れをn8nで統合・自動化できる。
*   **Creatomateの役割**: APIで動作する動画編集クラウドであり、テンプレートを作成してAPI経由で素材やテキストを差し替えることで、動画の無限量産を可能にする。
*   **必要なツールと事前準備**:
    *   **n8n**: ワークフローの司令塔。
    *   **Gemini Veo 2.0**: 高品質な動画生成モデル。
    *   **Google Cloud (GCP)**: データの高速転送や一時保存（バケット作成）に利用。
    *   **各種API/認証設定**: Google OAuth、Gemini API、Creatomate APIの設定が必須。
*   **n8n構築の主要ステップ**:
    1.  **Form Trigger**: 動画のテーマを入力する窓口を作成。
    2.  **Generate a video (Gemini)**: テーマに基づき動画を生成。
    3.  **GCSへのアップロード**: 生成された動画をURL化するためにGoogle Cloud Storageに保存。
    4.  **Merge & HTTP Request (Creatomate)**: 複数の動画素材URLをまとめ、Creatomate APIへ編集指示（JSON形式）を送信。
    5.  **Wait & Download**: レンダリング完了まで待機し、完成動画をダウンロードしてGoogle Driveへ保存。

## Key Message
動画生成AIで作られた素材を人間が手作業で編集するのは非効率であり、n8nとCreatomateを活用することで「撮影」と「編集」の工程をボタン一つに集約できる。この自動化システムを構築すれば、寝ている間に数百本の動画を生み出す「動画工場長」になることが可能である。