# Makepad 向け Claude Skills

[English](./README.md) | [中文](./README.zh-CN.md) | [日本語](./README.ja.md)

[![Version](https://img.shields.io/badge/version-1.10.0-blue.svg)](./skills/.claude-plugin/plugin.json)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](./LICENSE)

Rust の [Makepad](https://github.com/makepad/makepad) フレームワークを使用してクロスプラットフォーム UI アプリケーションを構築するための Claude Code Skills です。

## Makepad について

[Makepad](https://github.com/makepad/makepad) は、Rust で書かれた次世代 UI フレームワークで、高性能なクロスプラットフォームアプリケーションの構築を可能にします。主な特徴：

- **クロスプラットフォーム**：単一のコードベースでデスクトップ（macOS、Windows、Linux）、モバイル（Android、iOS）、Web（WebAssembly）に対応
- **GPU アクセラレーション**：SDF（Signed Distance Field）描画によるカスタムシェーダーベースのレンダリング
- **ライブデザイン**：ホットリロード可能な `live_design!` DSL による迅速な UI 開発
- **高パフォーマンス**：ネイティブコンパイル、仮想 DOM なし、最小限のランタイムオーバーヘッド

## Robius について

[Project Robius](https://github.com/project-robius) は、Rust でフル機能のアプリケーション開発フレームワークを構築するオープンソースイニシアチブです。Makepad で構築された本番アプリケーション：

- **[Robrix](https://github.com/project-robius/robrix)** - リアルタイムメッセージング、E2E 暗号化、複雑な UI パターンを実装した Matrix チャットクライアント
- **[Moly](https://github.com/moxin-org/moly)** - データ集約型インターフェースと非同期操作を実装した AI モデルマネージャー

これらの Skills は Robrix と Moly で使用されているパターンから抽出されています。

## インストール

`skills` フォルダを Makepad プロジェクトの `.claude/skills` にコピーします：

```bash
# このリポジトリをクローン
git clone https://github.com/project-robius/makepad-skills.git

# プロジェクトにコピー
cp -r makepad-skills/skills your-project/.claude/skills
```

インストール後のプロジェクト構造：

```
your-project/
├── .claude/
│   └── skills/
│       ├── .claude-plugin/
│       │   └── plugin.json
│       ├── makepad-init/
│       ├── makepad-fundamentals/
│       └── ... (その他の skills)
├── src/
└── Cargo.toml
```

詳細は [Claude Code Skills 公式ドキュメント](https://docs.anthropic.com/en/docs/claude-code/skills) を参照してください。

## Skills 一覧

### 入門

| Skill | 説明 | 使用場面 |
|-------|------|----------|
| [makepad-init](./skills/makepad-init/SKILL.md) | プロジェクトスキャフォールディング | 「新しい Makepad アプリを作成」 |
| [makepad-project-structure](./skills/makepad-project-structure/SKILL.md) | ディレクトリ構成のベストプラクティス | 「Makepad プロジェクトをどう整理すべき？」 |

### コア開発

| Skill | 説明 | 使用場面 |
|-------|------|----------|
| [makepad-fundamentals](./skills/makepad-fundamentals/SKILL.md) | `live_design!` マクロ、ウィジェット、イベント、タイマー | 「ボタンの作り方は？」「クリックイベントの処理」 |
| [makepad-rust](./skills/makepad-rust/SKILL.md) | 所有権、derive、async/tokio、状態管理 | 「借用チェッカーエラー」「Makepad での非同期処理は？」 |
| [makepad-shaders](./skills/makepad-shaders/SKILL.md) | SDF 描画、カスタムシェーダー、視覚効果 | 「グラデーション背景を作成」「グローエフェクトをアニメーション」 |
| [makepad-patterns](./skills/makepad-patterns/SKILL.md) | モーダル、リスト、ナビゲーション、テーマ | 「モーダルダイアログを追加」「無限スクロールを実装」 |
| [makepad-adaptive-layout](./skills/makepad-adaptive-layout/SKILL.md) | レスポンシブレイアウト、AdaptiveView、StackNavigation | 「デスクトップとモバイル両方に対応」 |

### デプロイメント

| Skill | 説明 | 使用場面 |
|-------|------|----------|
| [makepad-packaging](./skills/makepad-packaging/SKILL.md) | デスクトップ、Android、iOS、WebAssembly 向けビルド | 「Android APK をビルド」「Web にデプロイ」 |

### 品質とデバッグ

| Skill | 説明 | 使用場面 |
|-------|------|----------|
| [makepad-troubleshooting](./skills/makepad-troubleshooting/SKILL.md) | よくあるエラーと修正方法 | 「Apply error: no matching field」「UI が更新されない」 |
| [makepad-code-quality](./skills/makepad-code-quality/SKILL.md) | Makepad 対応のリファクタリング | 「このコードを簡略化」（簡略化すべきでないものを理解） |

### 自己改善

| Skill | 説明 | 使用場面 |
|-------|------|----------|
| [makepad-evolution](./skills/makepad-evolution/SKILL.md) | 開発中の学習内容をキャプチャ | 新しいパターン発見時に自動トリガー |

## 使用例

### 新規プロジェクト作成
```
ユーザー: カウンターボタン付きの "my-app" という Makepad アプリを作成
Claude: [makepad-init でプロジェクト作成、makepad-fundamentals でボタン/カウンター実装]
```

### 非同期データ取得の追加
```
ユーザー: UI をブロックせずに API からユーザーデータを取得
Claude: [makepad-rust の tokio アーキテクチャ、makepad-patterns のローディング状態を使用]
```

### モバイル向けビルド
```
ユーザー: Android 向けにアプリをビルド
Claude: [makepad-packaging で APK 生成]
```

### コンパイルエラー修正
```
ユーザー: "no matching field: font" エラーが発生
Claude: [makepad-troubleshooting で正しい text_style 構文を特定]
```

## 構築できるもの

これらの Skills を使用すると、Claude は以下をサポートします：

- 適切な構造で新しい Makepad プロジェクトを初期化
- `live_design!` DSL でカスタムウィジェットを作成
- イベントとユーザーインタラクションを処理
- 視覚効果用の GPU シェーダーを作成
- スムーズなアニメーションを実装
- async/tokio でアプリケーション状態を管理
- レスポンシブなデスクトップ/モバイルレイアウトを構築
- すべてのプラットフォーム向けにアプリをパッケージ化

## これらの Skills で構築されたプロジェクト

makepad-skills と Claude Code を使用して作成された実際のプロジェクト：

| プロジェクト | 説明 | 所要時間 |
|-------------|------|----------|
| [makepad-skills-demo](https://github.com/ZhangHanDong/makepad-skills-demo) | 為替レート変換アプリのデモ | 約 20 分 |
| [makepad-component](https://github.com/ZhangHanDong/makepad-component) | 再利用可能な Makepad コンポーネントライブラリ | - |

### makepad-skills-demo スクリーンショット

<p align="center">
  <img src="./assets/skill-app-demo.jpg" width="60%" alt="為替レート変換アプリ" />
</p>

### makepad-component スクリーンショット

<p align="center">
  <img src="./assets/mc1.png" width="45%" alt="コンポーネント 1" />
  <img src="./assets/mc2.png" width="45%" alt="コンポーネント 2" />
</p>
<p align="center">
  <img src="./assets/mc3.png" width="45%" alt="コンポーネント 3" />
  <img src="./assets/mc4.png" width="45%" alt="コンポーネント 4" />
</p>

## リソース

- [Makepad リポジトリ](https://github.com/makepad/makepad)
- [Makepad サンプル](https://github.com/makepad/makepad/tree/main/examples)
- [Project Robius](https://github.com/project-robius)
- [Robrix](https://github.com/project-robius/robrix)
- [Moly](https://github.com/moxin-org/moly)

## ライセンス

MIT
