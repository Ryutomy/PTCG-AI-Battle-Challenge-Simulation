# Submission Artifact Manifest

**監査日:** 2026-09-04  
**取得元:** Kaggleの本人提出履歴から回収したアーカイブ

## Summary

| Agent | Archive | Size | Members | Deck rows | SHA-256 |
|---|---|---:|---:|---:|---|
| Yuki v16 | `marnie_grimmsnarl_deck_yuki_v16_submission.tar.gz` | 585,697 bytes | 16 | 60 | `87CD0DF2560E0775257958553700E7E446015D82A354C2B559C461C0D582CB96` |
| New_Rocket v13.2 | `New_Rocket_v13_2_submission.tar.gz` | 643,725 bytes | 9 | 60 | `21306279B855EB721758DC1CDC724060ADCCF751889BD2936357875D73719283` |

## Checks Performed

- gzip/tarとしてmember一覧を読み取れる
- 絶対パスや親ディレクトリ参照を含むmemberは確認されていない
- entry pointとして`main.py`を含む
- `deck.csv`が60行である
- `cg/api.py`と`cg/libcg.so`を含む
- SHA-256が開発終了時に記録した最終アーカイブの値と一致する

## Scope of Verification

この監査はアーカイブの同一性、基本構造、デッキ行数を確認したものです。ゲームエンジンを利用したsmoke battleや過去ベンチマークの再実行は含みません。

## Publication Status

アーカイブには第三者のコンペティションランタイムや、公開Notebookを起点としたコードが含まれます。再配布条件と帰属を確認するまで、アーカイブと展開物はローカルに保持し、Gitでは追跡しません。
