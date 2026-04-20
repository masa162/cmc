# CMC（Comic Management Center）ポータル

## このリポジトリの役割
- 全タイトルの進捗・状況を一元管理するポータル
- 作業再開時の「地図」として使う

---

## リポジトリ構成（2026-04現在）

| リポジトリ | 役割 | ローカルに必要？ |
|---|---|---|
| cmc（このリポジトリ） | 管理ポータル | 必要 |
| cmc_pjc | Punk Junk City 本制作 | 必要 |
| cmc-hugo-theme | 共通Hugoテーマ | 不要（submoduleで自動取得） |
| junk-punk-city | PJC旧版（非推奨） | 削除可 |

---

## 各タイトルの状態

### Punk Junk City（cmc_pjc）⭐ アクティブ
- ジャンル: サイバーパンク Webtoon
- 状態: 制作中
- 直近作業: motive108モチーフ整理、マザードライブ設定
- キャラ: 壬生晃・リン・ゼロ・データイーター・朝霧市（舞台）
- 起動: `cd cmc_pjc && make serve`
- 公開URL: https://masa162.github.io/cmc_pjc/

### Blue Moon Madness（cmc/content/blue-moon-madness）
- ジャンル: 日常ギャグ Webtoon
- 主人公: トーコ（26歳SE、コミュ障）
- 状態: 独立リポジトリへの移行未完了（現在はcmc内に在中）
- TODO: blue-moon-madness リポジトリへ移行する

### Peach Float（cmc/content/peach-float）
- 状態: 構想初期のみ（world-setting.mdのみ存在）

---

## 基本ワークフロー（Punk Junk City）

```bash
cd /Users/nakayamamasayuki/Documents/GitHub/cmc_pjc
git submodule update --init --recursive  # 初回のみ
make serve
# → ブラウザで http://localhost:1313 を開く
```

1. VSCode で Markdown を編集
2. `make serve` でローカル確認（http://localhost:1313）
3. `git push` → GitHub Actions → GitHub Pages 自動公開

---

## 更新履歴
- 2026-04-20: 浦島太郎復帰、ポータルとして整備
