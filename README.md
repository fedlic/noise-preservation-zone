# 保存区域 チェンマイ（noise-preservation-zone）

> 作者：PON
> 掲載：[syosetu.com](https://syosetu.com/)「ノイズ（仮）」
> 管理：noise-preservation-zone

チェンマイ滞在を起点とした連作の長期管理リポジトリ。
本編・設定資料・分岐ルート・将来の翻訳/映像化資料を、ブランチとディレクトリで整理して保管する。

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
├── main/                  # 本編（確定稿）
│   └── NNN_<title>.md     # 3桁ゼロ埋め番号
│
├── characters/            # 登場人物
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

| # | タイトル |
|---|---|
| 001 | 湿度と漂流 |
| 002 | 同期と余白 |
| 003 | 情報のない午後 |
| 004 | BPMと身体 |
| 005 | 時間を持たない人 |
| 006 | 読経とフィードバック |
| 007 | 安定した人々 |
| 008 | 夢の速度 |
| 009 | パーイへの道 |
| 010 | 触れる速度 |
| 011 | 呼吸する部屋 |
| 012 | なんでもない一日 |

## 深圳ルート（route/shenzhen）

| # | タイトル |
|---|---|
| 012 | なんでもない一日 |
| 013 | 揺らぎながら接続する |
| 014 | 痕跡 |
| 015 | 空白の重さ |
| 016 | 分子として漂う |
| 017 | 再同期 |
| 018 | 未来の匂い |

詳細: [branches/shenzhen-route.md](branches/shenzhen-route.md)

---

## クイックリンク

- 運用規約: [CONVENTIONS.md](CONVENTIONS.md)
- 分岐ルート一覧: [branches/_index.md](branches/_index.md)
- 登場人物: [characters/_index.md](characters/_index.md)
- 世界観: [world/_index.md](world/_index.md)
- 時系列: [timeline/_index.md](timeline/_index.md)
- 映像化資料: [media/_index.md](media/_index.md)
