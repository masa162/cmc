# CMC プロジェクト移行完了

このリポジトリは、各タイトルごとの独立したリポジトリに分割されました。

## 新しいリポジトリ構成

### 共通テーマ
- **cmc-hugo-theme**: https://github.com/masa162/cmc-hugo-theme
  - マンガプロジェクト用の共通Hugoテーマ
  - hugo-bookベースのカスタマイズ版
  - 新規タイトル作成用のテンプレートファイル含む

### タイトル別リポジトリ

#### 1. Blue Moon Madness
- **リポジトリ**: https://github.com/masa162/blue-moon-madness
- **概要**: ゆる日常＋ギャグ＋都会の寂寥感を照らす間接照明ヒューマンドラマ
- **コンテンツ**:
  - エピソード: episode-01, episode-02
  - キャラクター: トーコ, Johny, Watson, 深夜コンビニ店員ズ, 父
  - 設定資料: 構成、方針

#### 2. Junk Punk City
- **リポジトリ**: https://github.com/masa162/junk-punk-city
- **概要**: サイバーパンク×ヒューマンドラマ - ジャンク都市で生きる人々の物語
- **コンテンツ**:
  - エピソード: episode-01, episode-02
  - キャラクター: 壬生アキラ, リン, ゼロ, データイーター, 朝霧市
  - 設定資料: サイバーパンク設定、都市設定、モチーフ案、キャラクター素案など

#### 3. Peach Float
- **リポジトリ**: https://github.com/masa162/peach-float
- **概要**: 新しいマンガプロジェクト（開発初期段階）
- **コンテンツ**:
  - 世界観設定

## 移行の利点

### ✅ 実現されたこと

1. **タイトル追加時の水平展開が容易**
   - 各タイトルが独立したリポジトリ
   - 新規タイトルは `cmc-hugo-theme` のテンプレートから簡単に作成可能

2. **ナビゲーション・見渡しの改善**
   - 各タイトルのサイトには該当タイトルのコンテンツのみ表示
   - 他タイトルの情報が混在しない

3. **SSG部分とコンテンツの分離**
   - 共通テーマ: `cmc-hugo-theme` （SSG設定・レイアウト）
   - コンテンツ: 各タイトルリポジトリ（mdファイル）
   - テーマは submodule として管理

4. **ローカルMarkdown + AIエディタ連携を維持**
   - すべてのコンテンツはMarkdownファイルとして管理
   - Cursor等のAIエディタとの協業は従来通り可能
   - Git管理でバージョン管理も容易

## 新規タイトルの作成方法

詳細は [cmc-hugo-theme/docs/README.md](https://github.com/masa162/cmc-hugo-theme/blob/main/docs/README.md) を参照してください。

### クイックスタート

```bash
# 新規Hugoサイトを作成
hugo new site new-manga-title
cd new-manga-title

# Git初期化
git init

# テーマをsubmoduleとして追加
git submodule add https://github.com/masa162/cmc-hugo-theme.git themes/cmc-hugo-theme

# テンプレートファイルをコピー
cp themes/cmc-hugo-theme/docs/template.gitignore .gitignore
cp themes/cmc-hugo-theme/docs/template.Makefile Makefile
cp themes/cmc-hugo-theme/docs/template.hugo.toml hugo.toml
cp themes/cmc-hugo-theme/docs/template.archetypes.episode.md archetypes/episode.md
cp themes/cmc-hugo-theme/docs/template.archetypes.character.md archetypes/character.md
cp themes/cmc-hugo-theme/docs/template.README.md README.md

# hugo.tomlとREADME.mdを編集してタイトル名を設定

# 開発サーバーを起動
make serve
```

## 各リポジトリの使い方

### ローカルでの作業

```bash
# リポジトリをクローン
git clone https://github.com/masa162/blue-moon-madness.git
cd blue-moon-madness

# テーマ（submodule）を取得
git submodule update --init --recursive

# 開発サーバーを起動
make serve
```

### コンテンツの編集

```bash
# 新しいエピソードを作成
hugo new episodes/episode-03.md

# 新しいキャラクターを作成
hugo new characters/new-character.md

# 編集後、コミット
git add content/
git commit -m "Add new episode"
git push origin main
```

### ビルド

```bash
# サイトをビルド（public/に出力）
make build

# ビルド成果物を削除
make clean
```

## テーマの更新

各タイトルリポジトリで共通テーマを最新版に更新する場合：

```bash
cd your-title-repo
git submodule update --remote themes/cmc-hugo-theme
git add themes/cmc-hugo-theme
git commit -m "Update cmc-hugo-theme to latest version"
git push origin main
```

## リポジトリ一覧

| リポジトリ | URL | 用途 |
|----------|-----|------|
| cmc-hugo-theme | https://github.com/masa162/cmc-hugo-theme | 共通Hugoテーマ |
| blue-moon-madness | https://github.com/masa162/blue-moon-madness | Blue Moon Madness プロジェクト |
| junk-punk-city | https://github.com/masa162/junk-punk-city | Junk Punk City プロジェクト |
| peach-float | https://github.com/masa162/peach-float | Peach Float プロジェクト |
| cmc (このリポジトリ) | https://github.com/masa162/cmc | 旧統合リポジトリ（アーカイブ） |

## 今後の運用

### このリポジトリ（cmc）について

このリポジトリは、各タイトルが独立したリポジトリに移行されたため、アーカイブとして保持することを推奨します。

- 新しいコンテンツの追加は各タイトルリポジトリで行ってください
- このリポジトリは参照用・バックアップ用として保持

### 推奨ワークフロー

1. **日常の編集**: 各タイトルリポジトリで作業
2. **新規タイトル追加**: `cmc-hugo-theme` のテンプレートから新規リポジトリを作成
3. **テーマのカスタマイズ**: `cmc-hugo-theme` を編集し、各タイトルで submodule 更新

## 移行日

2025年11月8日

## 参考リンク

- [CMC Hugo Theme README](https://github.com/masa162/cmc-hugo-theme/blob/main/README.md)
- [新規タイトル作成ガイド](https://github.com/masa162/cmc-hugo-theme/blob/main/docs/README.md)
- [Hugo Documentation](https://gohugo.io/documentation/)
