# 保存区域 チェンマイ（noise-preservation-zone）

> 作者：PON
> 掲載：syosetu.com「ノイズ（仮）」
> 管理：noise-preservation-zone

チェンマイ滞在中の生活と思考を、十二の断章として保存するための区域。
本文・推敲中の原稿・周辺メモを、ブランチとディレクトリで分離して管理する。

## 経緯

もともとは「小説家になろう」で連載していたが、AIを使った創作があまり歓迎されない雰囲気を感じたこと、そして途中で巻き戻したり別ラインに分岐させたくなる場面が増えてきたため、GitHub で版管理する方針に切り替えた。

## Background

Originally serialized on [syosetu.com](https://syosetu.com/) (Shōsetsuka ni Narō), but moved to GitHub-based version control — partly because AI-assisted writing didn't feel particularly welcomed there, and partly because I wanted the freedom to rewind the story or branch it into alternate routes mid-way through.

## ブランチ構成

| ブランチ | 内容 |
|---|---|
| `main` | 確定稿ライン（第1〜12話） |
| `drafts/shenzhen-route` | 第12話以降の「深圳ルート」分岐版（v1） |

`drafts/shenzhen-route` は第11話「呼吸する部屋」の直後から分岐した別ラインで、現行 main とは別の展開。

## ディレクトリ構成

```
noise-preservation-zone/
├── main/      # 確定稿（公開・連載用）
├── drafts/    # 推敲中の原稿（_v1, _v2 ...）※ drafts ブランチのみ
└── notes/     # 構想・断片・周辺メモ
```

## 全十二話（main）

| # | タイトル |
|---|---|
| 01 | 湿度と漂流 |
| 02 | 同期と余白 |
| 03 | 情報のない午後 |
| 04 | BPMと身体 |
| 05 | 時間を持たない人 |
| 06 | 読経とフィードバック |
| 07 | 安定した人々 |
| 08 | 夢の速度 |
| 09 | パーイへの道 |
| 10 | 触れる速度 |
| 11 | 呼吸する部屋 |
| 12 | なんでもない一日 |

## 深圳ルート（drafts/shenzhen-route）

| # | タイトル |
|---|---|
| 12 | なんでもない一日（v1） |
| 13 | 揺らぎながら接続する（v1） |
| 14 | 痕跡（v1） |
| 15 | 空白の重さ（v1） |
| 16 | 分子として漂う（v1） |
| 17 | 再同期（v1） |
| 18 | 未来の匂い（v1） |

## 運用ルール

- `main/` は確定稿。直接編集せず、`drafts/` で推敲してから差し替える。
- `drafts/` は `NN_タイトル_vN.md` 形式で版を重ねる。
- `notes/` は自由形式。構想・引用・断片を残す。
- 分岐ラインは `drafts/<route-name>` ブランチで管理する。
