---
description: n8nワークフローJSONを自然言語の要望から自動生成する
---

# n8n ワークフロー生成スキル

このスキルは、ユーザーの「やりたいこと」をヒアリングし、n8nで動作するワークフローJSONを自動生成します。

## 使用方法

1. ユーザーに以下の質問を順番に行い、要件を明確にする
2. 要件に基づいてワークフローを設計
3. JSONを生成して `10_n8njson` フォルダに保存

---

# ★★★ 使用するSkills ★★★

このワークフローを実行する際は、以下のSkillsを**必ず**読み込んで適用してください。

| タイミング | Skill | 読み込む対象 |
|---|---|---|
| STEP 5（JSON出力後） | `n8n-workflow-validator` | `resources/n8n_best_practices.md` でJSON検証・ベストプラクティス確認 |

---

## STEP 1: ヒアリング質問

### 必須質問（必ず確認）

1. **ワークフローの目的**
   - 何を自動化したいですか？（例：SNS投稿、記事作成、データ収集、通知）

2. **トリガー（きっかけ）**
   - どのタイミングで実行しますか？
     - スケジュール実行（毎日〇時、毎週〇曜日）
     - フォーム入力時
     - スプレッドシート更新時
     - 新規ファイル追加時
     - 手動実行

3. **入力データ**
   - 何をインプットにしますか？（例：URL、テキスト、ファイル、スプレッドシートデータ）

4. **出力先**
   - 結果をどこに出力しますか？（例：スプレッドシート、SNS、メール、Drive）

### 任意質問（必要に応じて）

5. **AI処理の有無**
   - AIを使った処理は必要ですか？（文章生成、要約、翻訳、画像生成など）

6. **条件分岐**
   - 特定の条件で処理を分けたいですか？

7. **ループ処理**
   - 複数のアイテムを繰り返し処理しますか？

---

## STEP 2: ワークフロー設計パターン

### パターン1: コンテンツ生成型
```
トリガー → データ取得 → AI処理 → 画像生成 → 保存/投稿
```
用途: 記事作成、SNS投稿、メルマガ作成

### パターン2: 情報収集・分析型
```
スケジュールトリガー → Web検索/API取得 → AI分析 → レポート作成 → 通知
```
用途: 競合調査、ニュース収集、トレンド分析

### パターン3: 通知・連携型
```
イベントトリガー → データ抽出 → 通知/記録
```
用途: 問い合わせ通知、在庫アラート、タスク連携

### パターン4: バッチ処理型
```
トリガー → データ取得 → ループ処理 → 個別処理 → 集約・保存
```
用途: 一括データ処理、複数アイテム操作

---

## STEP 3: 使用可能なノード一覧

### トリガーノード
| ノード名 | 用途 | typeVersion |
|---------|------|------------|
| `n8n-nodes-base.scheduleTrigger` | 定時実行 | 1.2 |
| `n8n-nodes-base.googleSheetsTrigger` | スプシ更新検知 | 1 |
| `n8n-nodes-base.googleDriveTrigger` | Drive更新検知 | 1 |
| `n8n-nodes-base.formTrigger` | フォーム入力 | 2.4 |
| `n8n-nodes-base.manualTrigger` | 手動実行 | 1 |

### AI処理ノード
| ノード名 | 用途 | typeVersion |
|---------|------|------------|
| `@n8n/n8n-nodes-langchain.agent` | AIエージェント | 2.2 / 3.1 |
| `@n8n/n8n-nodes-langchain.googleGemini` | Gemini API | 1 / 1.1 |
| `@n8n/n8n-nodes-langchain.lmChatGoogleGemini` | Gemini Chat Model | 1 |
| `@n8n/n8n-nodes-langchain.lmChatOpenAi` | OpenAI Chat Model | 1.2 |
| `@n8n/n8n-nodes-langchain.outputParserStructured` | 構造化出力 | 1.3 |

### データ処理ノード
| ノード名 | 用途 | typeVersion |
|---------|------|------------|
| `n8n-nodes-base.set` | フィールド編集 | 3.4 |
| `n8n-nodes-base.splitOut` | 配列分割 | 1 |
| `n8n-nodes-base.splitInBatches` | バッチ分割ループ | 3 |
| `n8n-nodes-base.aggregate` | データ集約 | 1 |
| `n8n-nodes-base.if` | 条件分岐 | 2.2 |
| `n8n-nodes-base.merge` | データ結合 | 3.2 |
| `n8n-nodes-base.code` | JavaScriptコード | 2 |
| `n8n-nodes-base.wait` | 待機 | 1.1 |

### 外部サービスノード
| ノード名 | 用途 | typeVersion |
|---------|------|------------|
| `n8n-nodes-base.googleSheets` | スプレッドシート操作 | 4.7 |
| `n8n-nodes-base.googleDrive` | Googleドライブ操作 | 3 |
| `n8n-nodes-base.googleDocs` | Googleドキュメント操作 | 2 |
| `n8n-nodes-base.gmail` | Gmail操作 | 2.2 |
| `n8n-nodes-base.twitter` | X投稿 | 2 |
| `n8n-nodes-base.httpRequest` | HTTP API呼び出し | 4.2 |
| `n8n-nodes-base.googleCloudStorage` | GCS操作 | 1 |

### 補助ノード
| ノード名 | 用途 | typeVersion |
|---------|------|------------|
| `n8n-nodes-base.stickyNote` | コメント・説明 | 1 |

---

## STEP 4: JSON生成ルール

### 基本構造
```json
{
  "name": "ワークフロー名",
  "nodes": [...],
  "pinData": {},
  "connections": {...},
  "active": false,
  "settings": {
    "executionOrder": "v1"
  },
  "versionId": "生成したUUID",
  "meta": {
    "templateCredsSetupCompleted": true,
    "instanceId": "placeholder"
  },
  "id": "生成したID",
  "tags": []
}
```

### ノード構造
```json
{
  "parameters": {...},
  "type": "ノードタイプ",
  "typeVersion": バージョン数値,
  "position": [x座標, y座標],
  "id": "一意のUUID",
  "name": "ノード表示名",
  "credentials": {
    "credentialType": {
      "id": "YOUR_CREDENTIAL_ID",
      "name": "YOUR_CREDENTIAL_NAME"
    }
  }
}
```

### Credentials プレースホルダー規則
```json
{
  "googleSheetsOAuth2Api": {
    "id": "YOUR_GOOGLE_SHEETS_CREDENTIAL_ID",
    "name": "YOUR_GOOGLE_SHEETS_CREDENTIAL_NAME"
  },
  "googleDriveOAuth2Api": {
    "id": "YOUR_GOOGLE_DRIVE_CREDENTIAL_ID",
    "name": "YOUR_GOOGLE_DRIVE_CREDENTIAL_NAME"
  },
  "googlePalmApi": {
    "id": "YOUR_GEMINI_API_CREDENTIAL_ID",
    "name": "YOUR_GEMINI_API_CREDENTIAL_NAME"
  },
  "openAiApi": {
    "id": "YOUR_OPENAI_API_CREDENTIAL_ID",
    "name": "YOUR_OPENAI_API_CREDENTIAL_NAME"
  },
  "twitterOAuth2Api": {
    "id": "YOUR_X_API_CREDENTIAL_ID",
    "name": "YOUR_X_API_CREDENTIAL_NAME"
  }
}
```

### 座標配置ルール
- 横方向: 200px間隔（左から右へ）
- 縦方向: 分岐時は150px間隔
- Sticky Noteは関連ノードの上部に配置

### Connections構造
```json
{
  "ノード名": {
    "main": [
      [
        {
          "node": "接続先ノード名",
          "type": "main",
          "index": 0
        }
      ]
    ]
  }
}
```

### AI系の特殊接続
```json
{
  "Google Gemini Chat Model": {
    "ai_languageModel": [
      [
        {
          "node": "AI Agent",
          "type": "ai_languageModel",
          "index": 0
        }
      ]
    ]
  }
}
```

---

## STEP 5: 出力

生成したJSONを以下のパスに保存:
```
g:\マイドライブ\AI\MyNote\10_n8njson\[ワークフロー名].json
```

ファイル名は日本語でOK。内容を端的に表す名前にする。

---

## 参考: よく使うプロンプトテンプレート

### 文章生成用
```
あなたは優秀なライターです。
[タスク内容]

## 手順
1. [手順1]
2. [手順2]

## 注意事項
- [注意1]
- [注意2]

## 出力形式
[出力形式の指定]
```

### SNS投稿作成用
```
あなたはSNSマーケティングのプロフェッショナルです。
以下の[テーマ]をもとに、[プラットフォーム]で最もエンゲージメントが期待できる投稿を作成してください。

# テーマ
{{ $json['テーマ'] }}

# 制約条件
- 文字数: [X]文字程度
- トーン: [カジュアル/フォーマル]
- ハッシュタグ: [あり/なし]

# 出力形式
投稿本文のみテキストで出力してください。
```
