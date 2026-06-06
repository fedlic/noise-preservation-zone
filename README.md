# 保存区域 チェンマイ（noise-preservation-zone）

> 作者：PON
> 掲載：[syosetu.com](https://syosetu.com/)「ノイズ（仮）」
> 管理：noise-preservation-zone

チェンマイ滞在を起点とした連作の長期管理リポジトリ。
本編・設定資料・分岐ルート・将来の翻訳/映像化資料を、ブランチとディレクトリで整理して保管する。

---

## まず読む

### 現行本編

- [第001話 湿度と漂流](main/001_湿度と漂流.md)
- [第002話 同期と余白](main/002_同期と余白.md)
- [第003話 情報のない午後](main/003_情報のない午後.md)
- [第004話 BPMと身体](main/004_BPMと身体.md)
- [第005話 時間を持たない人](main/005_時間を持たない人.md)
- [第006話 読経とフィードバック](main/006_読経とフィードバック.md)
- [第007話 安定した人々](main/007_安定した人々.md)
- [第008話 夢の速度](main/008_夢の速度.md)
- [第009話 パーイへの道](main/009_パーイへの道.md)
- [第010話 触れる速度](main/010_触れる速度.md)
- [第011話 呼吸する部屋](main/011_呼吸する部屋.md)
- [第012話 なんでもない一日](main/012_なんでもない一日.md)

### 旧稿・分岐稿

- [archive/](archive/) — 旧 ep011 分岐稿、旧 ep012〜017 を保管
- [archive/_index.md](archive/_index.md) — 旧稿一覧

---

## 経緯

もともとは「小説家になろう」で連載していたが、AIを使った創作があまり歓迎されない雰囲気を感じたこと、そして途中で巻き戻したり別ラインに分岐させたくなる場面が増えてきたため、GitHub で版管理する方針に切り替えた。

## Background

Originally serialized on [syosetu.com](https://syosetu.com/) (Shōsetsuka ni Narō), but moved to GitHub-based version control — partly because AI-assisted writing didn't feel particularly welcomed there, and partly because I wanted the freedom to rewind the story or branch it into alternate routes mid-way through.

---

## ディレクトリ構成

```
noise-preservation-zone/
├── README.md              # このファイル
├── CONVENTIONS.md         # 命名・運用規約
│
├── docs/                  # AI執筆・Canon/Lore 運用ルール
├── main/                  # 本編（確定稿）
│   └── NNN_<title>.md     # 3桁ゼロ埋め番号
│
├── characters/            # 登場人物
├── relationships/         # 人物間の関係性
├── world/                 # 世界観・舞台・テクノロジー
├── timeline/              # 時系列・年表
├── branches/              # 分岐ルートの説明（メタ情報）
├── notes/                 # 構想メモ・雑記
├── archive/               # ボツ案・破棄稿
│
└── media/                 # 映像化・メディア展開資料
    ├── anime/
    ├── movie/
    ├── visual/
    └── soundtrack/
```

各ディレクトリの詳細運用は、各 `_index.md` および [CONVENTIONS.md](CONVENTIONS.md) を参照。

---

## ルート分岐モデル

| 範囲 | 性質 |
|---|---|
| 第001〜011話 | **共通ルート（オリジナル）**。全ブランチで共有される |
| 第012話以降 | **分岐可能区間**。`main` と `route/<name>` で異なる物語を並行展開できる |

第012話は現時点で **2つの候補が並走**している：

- `main` の `main/012_なんでもない一日.md` — **本線候補**
- `route/shenzhen` の `main/012_なんでもない一日.md` — **深圳ルート候補**

どちらも採択前の候補。最終的にどれを「本線」とするかは確定していない（タグ `published/ep-012` を切った時点で凍結される）。

> Note: 共通ルート（第001〜011話）は全ブランチで同じ内容を保持する。修正したいときは `main` を編集し、`route/*` 側へマージで取り込む。

---

## ブランチ戦略

| ブランチ | 用途 | 命名例 |
|---|---|---|
| `main` | 本線・なろう公開準拠の確定稿 | — |
| `route/<name>` | パラレルルート（本線の分岐） | `route/shenzhen` |
| `wip/ep-NNN` | 単話作業（任意・短命） | `wip/ep-013` |
| `i18n/<lang>` | 翻訳版（本線ミラー） | `i18n/en` |

映像化資料はブランチではなく [`media/`](media/) ディレクトリで管理する。

### 現存ブランチ

- [`main`](../../tree/main) — 本線
- [`route/shenzhen`](../../tree/route/shenzhen) — 深圳ルート（第011話直後から分岐）

---

## タグ戦略

| タグ | 用途 | 例 |
|---|---|---|
| `published/ep-NNN` | なろう公開済み区切り | `published/ep-012` |
| `arc-NN/complete` | 章完結スナップショット | `arc-01/complete` |
| `pitch/<name>` | 提案版スナップショット | `pitch/anime-v1` |

---

## なろう公開版と Git 版の役割分離

| 項目 | なろう | Git (main) | Git (その他ブランチ・ディレクトリ) |
|---|:---:|:---:|:---:|
| 確定稿 | ○ | ○ | ○（route別） |
| 履歴・差分 | × | ○ | ○ |
| 分岐ルート | × | × | ○（route/*） |
| 設定資料 | × | ○ | ○ |
| WIP | × | △ | ○（wip/*） |
| 翻訳 | × | × | ○（i18n/*） |
| 映像化資料 | × | ○（media/） | — |

**公開フロー**: `main` で完成 → `published/ep-NNN` タグ付け → なろう投稿。

---

## 全話一覧（main）

| # | タイトル | 区分 |
|---|---|---|
| 001 | [湿度と漂流](main/001_湿度と漂流.md) | 共通 |
| 002 | [同期と余白](main/002_同期と余白.md) | 共通 |
| 003 | [情報のない午後](main/003_情報のない午後.md) | 共通 |
| 004 | [BPMと身体](main/004_BPMと身体.md) | 共通 |
| 005 | [時間を持たない人](main/005_時間を持たない人.md) | 共通 |
| 006 | [読経とフィードバック](main/006_読経とフィードバック.md) | 共通 |
| 007 | [安定した人々](main/007_安定した人々.md) | 共通 |
| 008 | [夢の速度](main/008_夢の速度.md) | 共通 |
| 009 | [パーイへの道](main/009_パーイへの道.md) | 共通 |
| 010 | [触れる速度](main/010_触れる速度.md) | 共通 |
| 011 | [呼吸する部屋](main/011_呼吸する部屋.md) | 共通 |
| 012 | [なんでもない一日](main/012_なんでもない一日.md) | **本線候補** |

## 深圳ルート（route/shenzhen）

| # | タイトル | 区分 |
|---|---|---|
| 001〜011 | （共通ルート） | main と同一 |
| 012 | なんでもない一日（v1） | **深圳ルート候補** |
| 013 | 揺らぎながら接続する（v1） | 深圳ルートのみ |
| 014 | 痕跡（v1） | 深圳ルートのみ |
| 015 | 空白の重さ（v1） | 深圳ルートのみ |
| 016 | 分子として漂う（v1） | 深圳ルートのみ |
| 017 | 再同期（v1） | 深圳ルートのみ |
| 018 | 未来の匂い（v1） | 深圳ルートのみ |

詳細: [branches/shenzhen-route.md](branches/shenzhen-route.md)

---

## クイックリンク

- 運用規約: [CONVENTIONS.md](CONVENTIONS.md)
- AI執筆・Canon/Lore運用: [docs/_index.md](docs/_index.md)
- Canon / Lore ポリシー: [docs/canon_policy.md](docs/canon_policy.md)
- AI執筆ルール: [docs/ai_writing_rules.md](docs/ai_writing_rules.md)
- 分岐ルート一覧: [branches/_index.md](branches/_index.md)
- 登場人物: [characters/_index.md](characters/_index.md)
- 関係性: [relationships/_index.md](relationships/_index.md)
- 世界観: [world/_index.md](world/_index.md)
- 時系列: [timeline/_index.md](timeline/_index.md)
- 映像化資料: [media/_index.md](media/_index.md)
