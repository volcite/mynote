# エージェントチーム構成マップ

各スキル・ワークフローで起動するエージェントチームの構成を定義します。

---

## エージェント一覧

### 戦略層（調査・分析・企画）
| エージェント | ファイル | 役割 | モデル |
|-------------|---------|------|--------|
| リサーチャー | `researcher.md` | 市場調査・競合分析・トレンド調査 | sonnet |
| ストラテジスト | `strategist.md` | コンセプト設計・ターゲット分析・差別化戦略 | sonnet |

### 制作層（執筆・コンテンツ制作）
| エージェント | ファイル | 役割 | モデル |
|-------------|---------|------|--------|
| ストーリーテラー | `storyteller.md` | 物語構造設計・感情設計・ストーリー構築 | opus |
| コピーライター | `copywriter.md` | セールスコピー・LP・広告文・CTA設計 | opus |
| こまボイスライター | `koma-writer.md` | こまの文体を完全再現して執筆 | opus |
| Xクリエイター | `x-creator.md` | X投稿・プレゼント企画・エンゲージメント戦略 | sonnet |

### 品質管理層（チェック・検証・実行管理）
| エージェント | ファイル | 役割 | モデル |
|-------------|---------|------|--------|
| エディター | `editor.md` | 品質チェック・構成分析・推敲 | sonnet |
| コンプライアンスガード | `compliance-guard.md` | LINE垢バン防止・法令チェック・NGワード検出 | sonnet |
| n8nエンジニア | `n8n-engineer.md` | n8nワークフロー生成・検証・最適化 | sonnet |
| ローンチディレクター | `launch-director.md` | ローンチ戦略・スケジュール・全体統括 | sonnet |

---

## スキル別チーム編成

### article-structure-analyzer（記事構成分析）
```
[editor] ──── 構成分析・読みやすさチェック（リード）
[storyteller] ─ 物語構造の観点からフィードバック（サポート）
```
- **起動順**: editor → storyteller（並列可）
- **最終出力**: editor がレポートを統合

### concept-designer（コンセプト設計）
```
[researcher] ── 市場・競合調査（Phase 1）
     ↓
[strategist] ── コンセプト設計・USP抽出（Phase 2）
```
- **起動順**: researcher → strategist（逐次）
- **最終出力**: strategist がコンセプトシートを作成

### content-quality-checker（コンテンツ品質チェック）
```
[editor] ──── 品質チェック全般（リード）
[koma-writer] ─ 文体の自然さチェック（サポート）
```
- **起動順**: editor → koma-writer（並列可）
- **最終出力**: editor が品質レポートを作成

### line-ban-prevention-checker（LINE垢バン防止）
```
[compliance-guard] ── リスク判定・改善提案（単独）
```
- **起動順**: compliance-guard 単独起動
- **最終出力**: compliance-guard が診断レポートを作成

### marketing-copy-reviewer（マーケティングコピーレビュー）
```
[copywriter] ────── コピーの改善案作成（リード）
[compliance-guard] ── 法令・リスクチェック（サポート）
```
- **起動順**: copywriter + compliance-guard（並列）
- **最終出力**: copywriter がレビューレポートを作成、compliance-guard の指摘を統合

### n8n-workflow-validator（n8nワークフロー検証）
```
[n8n-engineer] ── 検証・修正提案（単独）
```
- **起動順**: n8n-engineer 単独起動
- **最終出力**: n8n-engineer が検証レポートを作成

### storytelling-writer（ストーリーテリング）
```
[storyteller] ── 物語構造設計・執筆（リード）
[koma-writer] ── 文体チェック・仕上げ（サポート）
```
- **起動順**: storyteller → koma-writer（逐次）
- **最終出力**: koma-writer が最終仕上げ

### writing-style-clone（文体クローン）
```
[koma-writer] ── 文体再現・執筆（リード）
[editor] ────── 品質チェック（サポート）
```
- **起動順**: koma-writer → editor（逐次）
- **最終出力**: koma-writer が最終版を確定

---

## ワークフロー別チーム編成

### LP作成
```
[researcher] → [strategist] → [copywriter] → [koma-writer] → [editor] + [compliance-guard]
  市場調査      コンセプト設計    LP文章作成      文体仕上げ      品質＋法令チェック
```
**フルチーム**: researcher → strategist → copywriter → koma-writer → editor + compliance-guard

### Note有料教材作成
```
[strategist] → [storyteller] + [koma-writer] → [editor]
 コンセプト確認     ストーリー構築＋執筆          品質チェック
```

### Note有料ローンチ
```
[launch-director] が統括
  ├── [strategist] → ローンチコンセプト
  ├── [copywriter] → セールスコピー
  ├── [x-creator] → X投稿5日分
  ├── [koma-writer] → 文体仕上げ
  └── [compliance-guard] → 法令チェック
```

### Note無料ローンチ
```
[launch-director] が統括
  ├── [strategist] → ローンチコンセプト
  ├── [storyteller] → 記事のストーリー構築
  ├── [x-creator] → X投稿5日分
  ├── [koma-writer] → 文体仕上げ
  └── [editor] → 品質チェック
```

### X投稿作成
```
[x-creator] → [koma-writer] → [editor]
  投稿作成       文体仕上げ      品質チェック
```

### Xプレゼント企画
```
[researcher] → [x-creator] → [koma-writer]
 トレンド調査    企画立案・投稿作成   文体仕上げ
```

### SNSアカウント設計
```
[researcher] → [strategist] → [koma-writer]
  市場調査      アカウント設計     プロフィール文作成
```

### ウェビナー台本作成
```
[strategist] → [storyteller] + [copywriter] → [koma-writer] → [editor]
 コンセプト設計   ストーリー＋セールス         文体仕上げ      品質チェック
```

### セールストーク作成
```
[strategist] → [copywriter] → [koma-writer] → [compliance-guard]
 コンセプト設計   トーク作成       文体仕上げ       法令チェック
```

### バックエンド商品設計
```
[researcher] → [strategist]
  市場調査      商品設計・価格戦略
```

### 個別ロードマップ生成
```
[strategist] → [koma-writer]
  現在地分析・ロードマップ設計   こまの言葉でアウトプット
```

### 自己紹介記事作成
```
[storyteller] → [koma-writer] → [editor]
 V字回復ストーリー構築   こまの声で執筆    品質チェック
```

### n8nワークフロー生成
```
[n8n-engineer]（単独）
```

### Clipping整理
```
一般処理（エージェント不要）
```

---

## チーム起動の原則

1. **並列起動できるものは並列で**: 独立した工程のエージェントは同時に起動
2. **前工程の出力が必要なものは逐次**: 調査→設計→執筆の流れは逐次
3. **品質チェックは最後**: editor と compliance-guard は最終工程
4. **koma-writer は常に最終仕上げ**: 他のエージェントの出力を「こまの声」に変換
5. **launch-director はオーケストレーター**: ローンチ時は全体を統括

## 使い方の例

### コンセプト設計を依頼された場合
```
1. researcher を起動 → 市場・競合調査
2. researcher の結果を strategist に渡す
3. strategist がコンセプトシートを作成
```

### Note有料ローンチを依頼された場合
```
1. launch-director の戦略フレームワークに従って全体設計
2. strategist でコンセプト確認
3. copywriter + x-creator を並列起動
4. koma-writer で文体を統一
5. compliance-guard で最終チェック
```
