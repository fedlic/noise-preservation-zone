# CONVENTIONS

`noise-preservation-zone` の運用規約。
迷ったときの判断基準。

---

## 1. ファイル命名

### 本編（main/）

- 形式: `NNN_<title>.md`
- `NNN` は 3桁ゼロ埋め（`001`〜`999`、999話まで対応）
- `<title>` は本文先頭の見出しと一致させる
- 例: `main/013_揺らぎながら接続する.md`

### 設定資料（characters/, world/, timeline/）

- 形式: `<id>.md`（半角英数・小文字・ハイフン）
- 例: `characters/pon.md`, `world/chiangmai.md`, `timeline/main-timeline.md`

### 分岐ルート説明（branches/）

- 形式: `<route-name>.md`
- ブランチ名 `route/<route-name>` と一致させる
- 例: `branches/shenzhen-route.md` ↔ `route/shenzhen`

### ボツ案（archive/）

- 形式: `NNN_<title>_<reason>.md`
- 例: `archive/012_なんでもない一日_v1-discarded.md`

### メモ（notes/）

- 自由形式（`<topic>.md` または `YYYYMMDD_<topic>.md`）

---

## 2. ディレクトリ運用

- 各ディレクトリ直下に `_index.md` を置き、用途・命名規則・索引を記す
- 新規ディレクトリを作るときは必ず `_index.md` も作成
- ファイルが増えたら `_index.md` の索引セクションを更新する

---

## 3. コミットメッセージ

### 形式

```
<type>: <subject>
```

### type 一覧

| type | 用途 |
|---|---|
| `feat` | 新エピソード追加・新ルート開始など機能追加相当 |
| `docs` | README/CONVENTIONS/_index.md などドキュメント更新 |
| `edit` | 既存話の本文編集（推敲・修正） |
| `fix` | 誤字・整合性修正 |
| `chore` | ディレクトリ整理・ファイル移動など雑務 |
| `archive` | ボツ案を archive/ へ移動 |
| `setup` | 設定資料（characters/world/timeline）の追加・更新 |
| `media` | 映像化資料の追加・更新 |

### 例

- `feat: ep-013 揺らぎながら接続する 追加`
- `edit: ep-007 安定した人々 推敲（湿度描写を強化）`
- `setup: characters/pon を追加`
- `archive: ep-012 v1 をボツ採用版とは別保管`
- `media: anime/episode-001 映像構成メモを追加`

---

## 4. ブランチ運用

### 命名規則

| プレフィックス | 用途 | 例 |
|---|---|---|
| `main` | 本線 | — |
| `route/<name>` | パラレルルート | `route/shenzhen` |
| `wip/ep-NNN` | 単話作業（短命） | `wip/ep-013` |
| `i18n/<lang>` | 翻訳版 | `i18n/en` |

### 運用方針

- `main` は確定稿のみ。直push可（一人運用前提）
- `route/*` は本線へマージしない（独立ライン）
- `wip/*` は完成後 main にマージして削除
- `i18n/*` は本線の変更を都度マージ取り込み（本線ミラー）

### ルート起こし手順

1. `git checkout main`（分岐したい時点で）
2. `git checkout -b route/<name>`
3. `branches/<name>-route.md` をそのブランチで作成 or main に追記
4. push

### ルート分岐モデル（重要）

本作は以下のルート分岐モデルを採用する：

- **第001〜011話**: 共通ルート（オリジナル）。全ブランチで共有される
- **第012話以降**: 分岐可能区間。`main` と `route/<name>` で異なる展開を持てる

#### 候補と確定

- `main` の第012話以降は **本線候補**
- `route/<name>` の第012話以降は **分岐ルート候補**
- いずれも採択前の候補として並走させてよい
- 「本線」確定はリリース時点で行う（`published/ep-NNN` タグで凍結）

#### 共通ルート編集ルール

- 第001〜011話は **共通ルート** のため、編集は必ず `main` で行う
- 編集後、`route/*` ブランチへは `git merge main` で取り込む
- 共通ルートを `route/*` 側だけで編集してはならない（ルート間の整合性が崩れる）
- 共通ルート最終話である ep011 を大幅改稿する場合は、[notes/ep-011-rewrite-operations.md](notes/ep-011-rewrite-operations.md) の連動更新チェックリストに従う

---

## 5. タグ運用

### published/

- `published/ep-NNN` — なろうに公開した時点でタグを切る
- 公開後の修正は `edit:` コミットを重ねるが、タグは動かさない（公開時点の凍結）

### arc-NN/

- `arc-NN/complete` — 章完結時にタグを切る
- 例: `arc-01/complete` = 第1章（ep-001〜ep-012）完結

### pitch/

- 提案版のスナップショット
- 例: `pitch/anime-v1` = アニメ化提案 v1 提出時点

---

## 6. PR / マージ方針

- 一人運用のため通常は直 push でよい
- 大きな構造変更や route → main へのマージは PR を作って差分を見返す
- マージは可能なら fast-forward、無理なら merge commit（rebase はしない）

---

## 7. 公開フロー（なろう）

1. `main` でエピソード完成
2. `published/ep-NNN` タグを切る
3. なろうに投稿
4. なろう投稿URLを `notes/published-log.md` に記録（任意）

### 公開後の修正

- 誤字・軽微な修正: `fix:` コミット → なろうも修正
- 大幅改稿: `edit:` コミット → 必要なら `published/ep-NNN-rev2` タグ追加

---

## 8. 翻訳（i18n/）

- ブランチ `i18n/<lang>` を切る
- そのブランチで `main/NNN_xxx.md` を翻訳上書き
- 本線の改稿は適宜 `git merge main` で取り込む
- 翻訳のメタ情報（用語集など）は `i18n/<lang>` ブランチ上の `notes/translation-glossary.md` に

---

## 9. 映像化資料（media/）

- ブランチではなく `media/` ディレクトリで管理
- サブディレクトリ: `anime/`, `movie/`, `visual/`, `soundtrack/`
- バイナリ（画像・音源）は含めず、外部ストレージのリンクで管理（リポジトリ肥大化防止）
- 提案版ごとに `pitch/<name>` タグを切る

---

## 10. 100話超への対応

- 当面は `main/` フラット運用（3桁ゼロ埋めで識別性は保てる）
- 章が増えたら（目安: 50話超 or 第3章開始時）`main/arc-NN/` でサブディレクトリ化を検討
- 移行時は git mv で履歴を保つ
