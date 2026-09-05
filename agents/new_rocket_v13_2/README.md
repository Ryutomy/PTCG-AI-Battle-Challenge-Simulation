# New_Rocket v13.2

New_Rocket v13.2は、Team Rocket's Spidopsを中心に盤面を広げ、Team Rocket's Mewtwo exを終盤の攻撃役として利用する最終提出エージェントです。

## Strategic Goal

Rocket Rushは自分の場にいるTeam RocketのPokémon数に応じて打点が上がるため、単純な攻撃優先ではなく、盤面の幅と攻撃継続性を維持する必要があります。

エージェントは主に次を制御します。

- Protonによる序盤のBasic Pokémon展開
- SpidopsとRocket Rushの攻撃準備
- Team Rocket's Mewtwo exを早期に2 Prize献上しないための保護
- Team Rocket EnergyとBasic Grass Energyの付与先
- Mimikyuの壁・コピー用途
- Neutralization Zoneを置く対面とタイミング
- Giovanniによる攻撃役交代と相手Benchの呼び出し

## v13.2 Policy

v13.2はv13のordered 60-card deckを変更せず、3つの限定方針を有効化したpolicy-only releaseです。

- **D:** Ogerpon系に対するMimikyuとEnergyのルーティング
- **P:** 山札安全策を解除するのは、そのターンに実行可能な勝利手順がある場合に限定
- **R:** Crustle/Dwebbleが見えた場合でも、rule-boxを含むhybrid boardではNeutralization Zoneを許可

候補として検証したMareepやUltra Ballへのデッキ交換は最終版へ含めず、v13の60枚を維持しています。

## Historical Evaluation

| 対象 | 記録値 | 判断 |
|---|---:|---|
| Ogerpon、1,000 games | +11.8pt | D方針を採用 |
| Crustle/Kangaskhan、2,000 games | +2.975pt | D+P+Rを採用 |
| Mareep候補、broad18 | -0.797pt | 棄却 |
| Ultra Ball候補、broad18 | -0.964pt | 棄却 |

これらは開発終了時の履歴値です。元の生ログが現存しないため、現在再実行済みの結果ではありません。

## Recovered Submission

Kaggleから回収したアーカイブについて、次を確認しました。

- ファイル名: `New_Rocket_v13_2_submission.tar.gz`
- SHA-256: `21306279B855EB721758DC1CDC724060ADCCF751889BD2936357875D73719283`
- `deck.csv`: 60行
- entry point: `main.py`
- archive内でD/P/Rのみが有効化されている

ローカルファイルの扱いは[submission/README.md](submission/README.md)を参照してください。

## Provenance

アーカイブ内のコメントでは、Team Rocket系の初期ゲームプランをKaggle上の「Oshbocker」の20 ladder episodesから分析したことが記録されています。その観察を出発点に、New_Rocketではリプレイ再現、対面別ルーティング、候補のpaired比較を繰り返しました。公開時もこの初期分析元を明記します。
