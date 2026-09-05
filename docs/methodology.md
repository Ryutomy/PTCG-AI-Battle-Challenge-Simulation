# Methodology

## 1. Rule-based Agent

各ターンに与えられるObservationから、盤面、手札、Energy、残りPrize、合法手を読み取り、合法手ごとに優先度を付けて行動を選択します。

ルールは大きく次の層に分かれます。

1. 実行不可能・不正なActionの除外
2. 即時勝利やPrize取得の判定
3. 攻撃可能なPokémonと退避経路の判定
4. 進化・展開・Energy付与の優先順位
5. 対面固有の例外ルール
6. 通常時のfallback

## 2. Replay-driven Development

勝率の低い対面やKaggle上の敗戦を確認し、単に「負けたときに存在した状態」を原因とはみなしません。修正前のエージェントで対象promptとActionを再現し、判断が一致することを確認してから候補ルールを作ります。

```text
敗戦を選ぶ
  → prompt・盤面・合法手・選択Actionを再構成
  → 修正前の判断を再現
  → 最小条件の候補を実装
  → 対象局面でAction差を確認
  → 対戦パネルで副作用を評価
```

## 3. Isolated A/B Evaluation

候補評価では、デッキ変更と方針変更を混在させず、一つの変更を分離します。

- feature OFF/ONを同じwrapperで比較
- 両armで同じseed streamを使用
- seat 0/1を同数に固定
- matchup別・seat別・aggregateを確認
- error件数を記録
- 必要に応じてpaired 95% CI、符号検定、McNemar検定を使用
- loaderやRNG driftを検出するためpolicy-identical nullを配置

別セッションの絶対勝率は、seed、対戦相手、loader、cacheの差を含む可能性があります。そのため採否では、同じ実験内の対照差を優先します。

## 4. Admission Decision

- **Adopt:** 対象局面を正しく変え、広いパネルで重大な回帰が見られない
- **HOLD:** 方向性はあるが、信頼区間、試合数、対面範囲が不十分
- **Reject:** 広いパネルで悪化、または副作用が利益を上回る
- **Correctness-only:** 勝率差はなくても、明らかに不正確な判断を限定条件で修正

## 5. Submission Audit

提出前には方針の性能だけでなく、実行可能性とパッケージ同一性を確認します。

- ordered deckが60枚である
- source、build package、archive展開後のコードが一致する
- `cg/api.py`、共有ライブラリなど必要ファイルが存在する
- Python cacheや危険なarchive memberがない
- 代表対面のsmoke testでerrorがない
- replay上のActionが意図どおりである
- 通常importだけでなくKaggle形式のraw `exec`でも起動する

## 6. Evidence Boundary

現在確認済みの事実と、開発終了時の記録値を分けます。

| Evidence level | 内容 |
|---|---|
| Current artifact | 回収アーカイブ、SHA-256、member一覧、60行のdeck.csv |
| Historical record | 当時の勝率、paired差、信頼区間、採否判断 |
| Not recovered | 全ベンチマーク生ログ、全候補ソース、元実験環境 |
