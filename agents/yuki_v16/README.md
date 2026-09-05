# Yuki v16

Yuki v16は、Marnie's Grimmsnarlを中心とした進化デッキ向けの最終提出エージェントです。

## Strategic Goal

序盤にImpidimpを安定して展開し、Rare CandyやMorgremを経由してGrimmsnarl exを攻撃可能な状態へ進めます。盤面完成後は、Munkidoriによるダメージ移動、Bench枠、Energy、退避経路、残りPrizeを同時に評価します。

## v16 Policy

v16の追加点は、Buddy-Buddy PoffinとPoke Padの順序を限定条件で修正したことです。

次の条件を満たす最初の自分のターンだけ、PoffinをPoke Padより先に評価します。

- PoffinとPoke Padがどちらも合法手である
- Benchに3枠以上の空きがある
- 使用可能なGrimmsnarl進化ラインをまだ確保していない
- Munkidoriをまだ確保していない
- Impidimpを山札から探索できる

Poffinで探索対象の限られたImpidimpを先に置き、Poke Padの柔軟な探索を後段へ残す狙いです。一般的な「常にPoffin優先」ではなく、初手の狭い局面だけに作用します。

## Historical Evaluation

開発終了時の記録では、v16はv14.1との6対面パネルで評価されました。

| 項目 | 記録値 |
|---|---:|
| 対面数 | 6 |
| 1対面あたり | 2,000 games |
| 1バージョン合計 | 12,000 games |
| v14.1 | 62.0292% |
| v16 | 64.3625% |
| paired差 | +2.3333pt |
| paired 95% CI | [+1.5036, +3.1631] |

この集計は当時の履歴値です。元の全ベンチマーク生ログは現存しないため、現在再実行済みの結果ではありません。また、v16固有のPoffin-before-Padだけに+2.3333ptを帰属させることはできません。

## Recovered Submission

Kaggleから回収したアーカイブについて、次を確認しました。

- ファイル名: `marnie_grimmsnarl_deck_yuki_v16_submission.tar.gz`
- SHA-256: `87CD0DF2560E0775257958553700E7E446015D82A354C2B559C461C0D582CB96`
- `deck.csv`: 60行
- entry point: `main.py`
- Kaggle raw-source executionで`__file__`がない場合のpackage探索を実装

ローカルファイルの扱いは[submission/README.md](submission/README.md)を参照してください。

## Provenance

提出アーカイブには、初期の参考Notebookから続く共通エージェント実装と、その上に追加したYuki固有の方針が含まれます。公開時は共通部分と独自の局面ルールを区別し、元Notebookへの帰属を保持します。
