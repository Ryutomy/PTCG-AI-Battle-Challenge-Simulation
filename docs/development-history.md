# Development History

## Scope

対象期間は2026-06-20から2026-08-15です。初期基盤から多数のデッキ系統を試しましたが、このポートフォリオではKaggleの最終提出に使ったYuki v16とNew_Rocket v13.2を中心に扱います。

## Timeline

| 期間 | フェーズ | 主な内容 |
|---|---|---|
| 06-20 ～ 06-25 | 基盤構築 | ローカル対戦、RuleBase、提出アーカイブ、smoke testの基礎を整備 |
| 06-26 ～ 07-10 | ベースライン拡張 | 複数デッキを実装し、比較相手とルールベース設計の土台を作成 |
| 07-11 ～ 07-31 | デッキ別改善 | Marnie/Grimmsnarl、Team Rocketほかを反復改善し、失敗候補も記録 |
| 08-01 ～ 08-09 | リプレイ主導へ移行 | Kaggle敗戦から局面単位の判断を再現し、限定ルールを評価 |
| 08-10 ～ 08-14 | 最終候補形成 | fixed seed、先後均等、paired比較でYukiとNew_Rocketを選定 |
| 08-15 | 互換性修正 | Yuki v16で`__file__`なしraw `exec`起動へ対応 |

## Yuki Lineage

初期のMarnie/Grimmsnarlでは、Poffinによる序盤のbody確保、Munkidori用Bench枠、Rare Candyと通常進化の役割分担を整理しました。Yuki系では、それらを対面・局面限定のルーティングへ発展させました。

- v6～v9: source routingを整備し、広すぎる防御案はHOLD
- v10～v12: Petrel、Unfair Stamp、Poke Pad、Night Stretcherを整理
- v13～v14: Team Rocket対面の退避・Energy復旧と即時進化経路を追加
- v14.1系: Munkidori昇格抑制、終盤Prize、Crustle限定Candyを追加
- v15: Battle Cage、Spikemuth、Munkidori/Crustle scopeを統合
- v16: 狭い初手条件でPoffin-before-Padを追加し、raw `exec`へ対応

## New_Rocket Lineage

初期Team Rocketで得た「Mewtwo exを守りながら盤面を広く保つ」という知見を、New_Rocketでより細かい対面別方針へ発展させました。

- v4～v6.1: Proton、Mimikyu、KO選択、Energy付与を短い変更単位で検証
- v7～v10: Giovanniによるリーサル、Mewtwoのjust-in-time運用、攻撃順を整理
- v11～v12: Tera-copy、stranded Activeの退避、Neutralization Zone、Arianaを整備
- v12.1: Articuno退避をcorrectness-onlyとして修正
- v13: 既存戦術を統合し、デッキ候補を広いパネルで再評価
- v13.2: OgerponおよびCrustle/KangaskhanのリプレイからD/P/Rを採用

## Other Development Lines

Ogerpon、Crustle、Lucario、Dragapult、Alakazam、Archaludonなども比較相手や研究用エージェントとして開発しました。ただし最終提出エージェントではないため、READMEの中心からは外しています。

## Current Recovery Status

| Artifact | Status |
|---|---|
| Yuki v16 submission archive | Kaggleから回収、SHA-256一致 |
| New_Rocket v13.2 submission archive | Kaggleから回収、SHA-256一致 |
| ordered 60-card decks | 両方とも現在確認済み |
| 全ベンチマーク生ログ | 未回収 |
| 全候補・旧バージョン | 未回収 |
| ランキング・メダル画像 | `evidence/`へ追加予定 |
