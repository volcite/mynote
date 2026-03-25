---
articleTitle: "【画像解説】もう挫折しない！n8n×Threadsの「最初の壁」をぶち破るAPI設定マニュアル｜こま｜n8n × AIよろず屋"
posted_at: 2025-12-04
posted_by: "こま｜n8n × AIよろず屋"
tags:
  - n8n
  - Threads
  - API
  - Meta
  - 自動化
  - SNSマーケティング
aliases:
  - Threads Graph API
  - Meta for Developers
  - アクセストークン
  - Bearer Auth
  - アプリ設定
---
## Transcript by AI
<details>
  <summary>文字起こし</summary>

![見出し画像](https://assets.st-note.com/production/uploads/images/234029225/rectangle_large_type_2_70000fa24691f1c52e94e8a51ad1870f.png?width=1280)

## 【画像解説】もう挫折しない！n8n×Threadsの「最初の壁」をぶち破るAPI設定マニュアル

[こま｜n8n × AIよろず屋](https://note.com/ai_yorozuya)

n8nという「自動化の魔法」を知ったのに、threadsに繋ごうとした瞬間、絶望していませんか？

> **「APIって何？」  
> 「アクセストークン？意味が分からない…」  
> 「Metaの開発者ページが地獄の迷宮すぎて、5分でそっとブラウザを閉じた」**

そんな悩みをお持ちではありませんか？

私自身、多くのクライアントの自動化支援を行っていますが、ほぼ全員がこの「Threads Graph API」の設定で脱落していきます。

n8nのポテンシャルは無限大なのに、その力を解放する「最初の鍵」で挫折している方が本当に多いのです。

しかし、正直に言います。  
Threads自動化を使えないという状態は、私には理解しがたい。  
なぜなら、 **API連携は「手順」さえ知っていれば、高度なスキルや知識は一切不要** だからです。

SNSマーケティングが当たり前の今、 **手動での投稿や分析に時間を奪われ** ている経営者やフリーランスが多すぎます。

その横で、一部の **「知っている人間」だけ** が、n8nとAPIを使って自動でフォロワーを分析し、最適な時間に投稿を予約し、空いた時間でさらに収益を上げています。

その差は、いったい何でしょうか？

実は、自動化を使いこなす人間が必ず乗り越える **「最初の儀式」** があるのです。  
  
それが今回のテーマである **「API設定」** です。

この記事を読み終えたあなたは、  
**「n8nとThreadsが繋がった！これで何でもできる！」**  
と、API設定を完了させることができるでしょう。

このマニュアルを手にすることで、あなたは自分のSNS業務にn8nを即座に取り入れ、あんなに億劫だった反復作業から解放され、人から **「どうやってるの？」と驚かれる** ようになり、あなたの貴重な人生の時間を大幅に増やし、最高の自動化ライフを手に入れることができます。

それでは早速、APIの設定を始めましょう。

---

### 「Meta開発者ページ」完全攻略マップ

まず、私たちがn8nとThreadsを接続するために乗り越えるべき最初の関門。それが「Meta for Developers」（Meta開発者ページ）です。

### なぜ私たちはFacebook（Meta）の設定画面で迷子になるのか？

答えは簡単です。  
あのページは「私たち（マーケターや一般ユーザー）」のために作られていないからです。  
あれは「開発者」のための場所であり、用語は専門的、UI（画面デザイン）は複雑怪奇、おまけに頻繁にデザインが変わります。

「ビジネス設定」と「開発者設定」と「アプリ設定」…一体どれが正解なのか！  
多くの人がここで迷子になり、「自分には無理だ」と諦めてしまいます。

しかし、安心してください。  
このマニュアルは、その迷宮を突破するための「完全な地図」です。  
あなたは、ただこの地図に書かれた「赤い印」だけを辿ればいいのです。

### 事前に準備するもの

下記のものを用意して進めてください。

- **Facebookアカウント**
- **Threadsアカウント**

### 「Meta for Developers」への第一歩

まず、Meta for Developersのページにアクセスし、あなたのFacebookアカウントでログインしてください。

[**Meta for Business (formerly Facebook for Business)** *developers.facebook.com*](https://developers.facebook.com/apps/)

### 「新しいアプリ」の作成

ログインしたら、右上の「利用を開始」ボタンをクリックします。

![画像](https://assets.st-note.com/img/1764849237-sZmowblM5A8VgdCFUO71Nxnq.png?width=1200)

Meta for Developers アカウントを作成します。「次へ」ボタンをくリクしてください。

![画像](https://assets.st-note.com/img/1764849237-d7icrERJk4WONxgDoht9senL.png?width=1200)

次に電話番号を入力して、アカウントの認証を行います。SMSで6桁の数字が送られてきますので入力して認証を行ってください。

![画像](https://assets.st-note.com/img/1764849237-ZeaqBM26xJ1RWpk9gb4HurPs.png?width=1200)

次にメールの認証を行います。任意のメールアドレスを入力して認証を行ってください。

![画像](https://assets.st-note.com/img/1764849239-l29AjpX7CR5Ir4S0K3znJbmN.png?width=1200)

あなたの役割を選択してください。（どれを選択しても同じです。）  
右下の登録完了をクリックします。

![画像](https://assets.st-note.com/img/1764849237-9MahEzIkxv1nfuRUYNZHpQF5.png?width=1200)

この画面に遷移すれば登録は完了です。

![画像](https://assets.st-note.com/img/1764849239-p5sXyLTv1DKtmcYA4Zk2l8oI.png?width=1200)

アプリを作成をクリックします。

![画像](https://assets.st-note.com/img/1764849239-3mNOFL2dv97Y8hZXeDcJI0WP.png?width=1200)

アプリ名とメールアドレスを入力して、次へボタンをクリックします。

![画像](https://assets.st-note.com/img/1764849434-7MTbeC2GpA9rL8BHKQqZu0lW.png?width=1200)

ユースケースを追加の画面で、「Threads APIにアクセス」を選び次へをクリックしてください。

![画像](https://assets.st-note.com/img/1764849646-v3ZOwK5imAYXVou6HDIP1RCF.png?width=1200)

「ビジネスポートフォリオをリンクしない」を選択して次へをクリックします。もちろんリンクしてもOKです。

![画像](https://assets.st-note.com/img/1764849693-61b7ECQnsmMyeiUDxATBhYzK.png?width=1200)

下記画面で、次へをクリックします。

![画像](https://assets.st-note.com/img/1764849722-K1kSlqomI2rFTewvgZnf7CuU.png?width=1200)

次の画面で「ダッシュボードに移動」をクリックします。

![画像](https://assets.st-note.com/img/1764849804-IX6gRdpxHujn1ZUM9OY5KyTQ.png?width=1200)

下記画面に遷移して、左上が先ほど設定したアプリ名になっていればOKです！

![画像](https://assets.st-note.com/img/1764849874-NzJkusD4Z0aF8TrnY21Cx7vR.png?width=1200)

このダッシュボードで、「「Threads APIへのアクセス」ユースケースをカスタマイズ」を選択してください。

![画像](https://assets.st-note.com/img/1764849882-KnH198dNvTMa4kJpq5sLoVYy.png?width=1200)

threads\_content\_publishを追加します。

- **threads\_basic** （すべてのThreadsエンドポイントで必須）
- **threads\_content\_publish** （投稿エンドポイント用）
![画像](https://assets.st-note.com/img/1764849963-vy61tr0DYdsn9mCuwQXV5g2H.png?width=1200)

左のメニューを開いて、アプリの役割 > 役割 をクリックします。

![画像](https://assets.st-note.com/img/1764850054-eOPm3A6gN2d891ExC5shqBLn.png?width=1200)

メンバーを追加するをクリックします。

![画像](https://assets.st-note.com/img/1764849240-nEduVWg5vI2kwo6yTAzO8BJU.png?width=1200)

Threadsテスターを選択します。

![画像](https://assets.st-note.com/img/1764850148-qS3sZu2QehcHrObAP4JRg0Tt.png)

一番下の入力欄に、APIで投稿したいThreadsアカウントのユーザーネームを入力します。

![画像](https://assets.st-note.com/img/1764850247-IrbRGxU2X1Lu6NBcwWTP0QaA.png)

ユーザーを選択したら、追加ボタンをクリックします。

![画像](https://assets.st-note.com/img/1764850279-Mu76zORaldhGLAS4pgY3D80F.png?width=1200)

そうすると承認待ちステータスになるので、「アプリとウェブサイト」のテキストリンクをクリックします。

![画像](https://assets.st-note.com/img/1764850349-M0pWwvl2HC6Bh1LtaSmxNA5u.png?width=1200)

指定したThreadsアカウントでログインすると下記画面が表示されます。

![画像](https://assets.st-note.com/img/1764850367-GJhV3mw6CtQSfBMpqlZLFeEc.png?width=1200)

ウェブサイトのアクセス許可をクリック

![画像](https://assets.st-note.com/img/1764850406-7g19qDsE2JIyWmhj3AQorYOi.png?width=1200)

招待をクリックして、先ほど作ったアカウントの招待に同意してください。

![画像](https://assets.st-note.com/img/1764850456-nevji7mWwTIBz6c12JgCEYtR.png?width=1200)

アプリの設定 > ベーシック をクリックします。

![画像](https://assets.st-note.com/img/1764850695-Cfcn5YRp1gLwkMehIQ3Hd9b7.png?width=1200)

アプリIDとapp secretをメモ帳などにコピーしておきます。

![画像](https://assets.st-note.com/img/1764850745-f94xnFJBevwRZpmbAG1utdK5.png?width=1200)

ダッシュボードに戻ります。

![画像](https://assets.st-note.com/img/1764851037-wjQUEIxqrsm5L8JcF9g6eiPk.png?width=1200)

ユースケースをテストするをクリックします。

![画像](https://assets.st-note.com/img/1764851082-eq72FdpY6DEgMWvwAlk1CzBH.png?width=1200)

「グラフAPIエクスプローラを開く」をクリックします。

![画像](https://assets.st-note.com/img/1764851127-CGuzieBqXymrvlnoRLt45DTb.png?width=1200)

左上の接続先を「.facebook.com/」から **「.threads.net/」に変更** します。  
その後、右側の **「Generate Threads Access Token」** をクリックしてください。

![画像](https://assets.st-note.com/img/1764851196-8UxQhyBWDeTEHN6pA4C7ucOX.png?width=1200)

別タブが開きますので、続行をクリックします。

![画像](https://assets.st-note.com/img/1764851227-qzuRGBUTApI0SQZ35Debtnhg.png?width=1200)

アクセストークンが生成されたらOKです。

![画像](https://assets.st-note.com/img/1764851286-8nTklhOA2iHKgpEPZe9z5cRr.png?width=1200)

次に長期トークンを生成します。

左のメニューから「ダッシュボード」をクリックします。  
このダッシュボードで、「「Threads APIへのアクセス」ユースケースをカスタマイズ」を選択してください。

設定をクリックします。

![画像](https://assets.st-note.com/img/1764915309-vQ5PAoFCxm1erVJGgaOSlyM8.png?width=1200)

画面下の「アクセストークンを生成」をクリックすると、アクセストークンが生成されますので、threadsのAPIを使うときはこれを利用します。

![画像](https://assets.st-note.com/img/1764915141-KuWxatoBc6iGrUAhIjQSCgfp.png?width=1200)

### n8nにアクセスキーを連携させる

n8nのCreate Credentialsをクリックします。

![画像](https://assets.st-note.com/img/1764849238-0c6svlAm15HBFVObS2C8NiGY.png?width=1200)

「Bearer Auth」をクリックします。

![画像](https://assets.st-note.com/img/1764852633-ViX6zdnPqQ7pCexZ4RutaUjl.png?width=1200)

先ほどコピーしたアクセストークンを入力して、右上のSaveボタンをクリックすれば設定は完了です！

![画像](https://assets.st-note.com/img/1764852671-GOXJ3l6tcLTsfnB954SpNZuw.png?width=1200)

ちなみにThreads APIを実行するときに使うuser\_idは、グラフAPIエクスプローラーでアクセストークンを生成して、送信ボタンをクリックして表示されたの赤枠の部分の数字です。

![画像](https://assets.st-note.com/img/1764903208-uhsvib72cTeComX5zHZPV0Ff.png?width=1200)

![画像](https://assets.st-note.com/img/1764852756-wTHNs3aZolL5VjnIEUGXvRtS.png?width=1200)

### 自動化のその先へ…接続は「始まり」にすぎない

このマニュアルをここまで読み切り、実行した猛者であるあなたに、私は敬意を表します。  
あなたは「自動化」の本当のスタートラインに立ちました。

そう、API接続はゴールではありません。  
車を手に入れるために、自動車学校（Meta開発者ページ）で面倒な手続き（API設定）をして、ようやく「鍵（トークン）」を手に入れたにすぎないのです。

- Googleスプレッドシートに書いた文章を、毎日決まった時間に「自動で」Threadsに投稿する
- 競合アカウントの投稿を「自動で」監視し、インサイトを分析する
- 特定のハッシュタグが付いた投稿を「自動で」収集し、データベース化する

これらはすべて、あなたが今日手に入れた「n8n」と「Threads API」で実現可能な「魔法」です。

### 次の自動化マニュアルで会いましょう

面倒な作業はすべてn8nに任せ、あなたにしかできない「創造的な仕事」に時間を使ってください。  
このマニュアルが、あなたの「最強のAIライフ」の第一歩となることを願っています。

さあ、次はどんな「魔法」を自動化しますか？  
次の自動化マニュアルで、またお会いしましょう。
</details>

## Summary
本記事は、n8nとThreadsを連携させるための最大の難関である「Threads Graph API」の設定手順を徹底解説したマニュアルです。開発者向けの複雑なMeta for Developersページにおけるアプリ作成、権限設定、テスター登録、アクセストークン生成までの一連の流れを、画像付きでステップバイステップで説明しています。最後にn8n側でのCredentials設定（Bearer Auth）を行うことで、Threadsへの自動投稿やデータ収集が可能になる手順を示しています。

## Key Learning Points
- **Meta for Developersでのアプリ作成**: Facebookアカウントでログインし、「Threads APIにアクセス」するユースケースでアプリを作成する。
- **権限の設定**: アプリに`threads_basic`（基本）と`threads_content_publish`（投稿用）の2つの権限を追加する。
- **テスター登録と承認**: アプリの「役割」で自分のThreadsアカウントをテスターとして追加し、Threads側の設定画面で招待を承認する。
- **アクセストークンの生成**: 「グラフAPIエクスプローラ」を使用し、接続先を`.facebook.com`から`.threads.net`に変更してからトークンを生成する。
- **長期トークンの取得**: ダッシュボードのユースケース設定画面から、長期間使用可能なアクセストークンを生成する。
- **n8n連携**: n8nのCredentialsで「Bearer Auth」を選択し、取得したアクセストークンを入力して接続を完了させる。

## Key Message
API連携は高度なスキルが必要なものではなく、正しい「手順」さえ知っていれば誰でも実現可能である。この設定という「最初の壁」を乗り越えることで、SNS運用の自動化による時間の創出と生産性向上を手に入れることができる。