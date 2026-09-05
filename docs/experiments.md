# Experiment Highlights

全候補を列挙するのではなく、最終提出2エージェントの設計判断が分かる代表例をまとめます。数値は開発終了時の全期間まとめに基づく履歴値であり、現在の再実行結果ではありません。

## Adopted

| Agent | Candidate | Historical evidence | Decision |
|---|---|---:|---|
| Yuki | v14.1からv16までの統合方針 | 6対面、12,000 games/版で+2.3333pt、paired 95% CI [+1.5036, +3.1631] | v16を最終提出 |
| Yuki | Poffin-before-Pad | 対象リプレイの初手順序を限定修正 | correctness-scopedとして採用 |
| New_Rocket | Ogerpon policy D | 1,000 gamesで+11.8pt、CIは正側 | 採用 |
| New_Rocket | D+P+R | Crustle/Kangaskhan 2,000 gamesで+2.975pt、CIは正側 | v13.2へ採用 |

## Held or Rejected

| Agent | Candidate | Historical evidence | Decision |
|---|---|---:|---|
| Yuki | Impidimpの手張りをMunkidoriへ移す | 12,000 paired gamesで-0.3917pt | HOLD |
| Yuki | Xerosic discard保持順位 | 2,000 games、26行動変化、勝敗変化0 | HOLD |
| Yuki | Froslass-after-Munkidori Poke Pad拡張 | 10対面で-1.2875pt、CIも負側 | 棄却 |
| New_Rocket | Battle Colosseum | 4,000 gamesで-1.8125pt、CIは負側 | 棄却 |
| New_Rocket | Neutralization ZoneからUnfair Stampへの交換 | 5対面で-14.3～-15.2pt | 棄却 |
| New_Rocket | Grass EnergyをMareepへ交換 | broad18で-0.797pt | 棄却 |
| New_Rocket | Grass EnergyをUltra Ballへ交換 | broad18で-0.964pt | 棄却 |

## What These Experiments Show

## Submission Score Timeline

`assets/ScoreFluctuation.jpg`には、2026-08-14から08-31にかけての最終提出後のLeaderboard score推移を記録しています。画像上の最終表示は、New_Rocket v13.2が871、Yuki v16が823です。Bronze Medal lineは853.5、Silver Medal lineは924.0として描画されています。

このグラフは提出後の順位・スコアの時系列であり、他参加者の提出やLeaderboard更新の影響を含みます。そのため、候補方針の採否を判断するpaired A/B評価とは分け、提出後の運用結果を示す補助的な証拠として扱います。

### A correct-looking move is not always a performance improvement

局面上は自然に見える修正でも、勝敗が変化しないことがあります。その場合は、バグ修正としての価値と、性能改善の証拠を分けました。

### A narrow gain can create a broad regression

特定の敗戦だけに合わせたルールは、別の対面や席で悪化する可能性があります。対象リプレイでActionが改善しても、それだけでは最終版へ採用しませんでした。

### Rejected candidates are part of the result

New_Rocketの最終版でデッキ交換を行わなかったのは、候補を試さなかったからではありません。Mareep、Ultra Ball、Battle Colosseum、Unfair Stampなどを比較し、同じ条件で悪化を確認したうえでv13のordered deckを維持しました。
