# PTCG AI Battle Challenge Simulation

The Pokémon Company - PTCG AI Battle Challenge Simulationにおける解法について

基本的なルールベースエージェントを用いて、6807チーム中590位で銅メダルをゲットしました。

## コンペティションについて

> This project aims to enhance the performance of an AI Training Agent with the Pokémon Trading Card Game (TCG). The research focuses on training AI Training Agents for competitive play in a system where probability, unknown elements, and strategic planning are key determinants of success.

このコンペティションでは、不完全情報ゲームであるポケモンカードゲームにおいてより強いAIエージェントを作成・育成することが目的です。

## 手法

今回私たちは、強化学習を用いたエージェントを作るのは不完全情報ゲームであること、そして単に技術力が足りないと判断したためルールベースでのエージェントを作成することにしました。
ルールベースエージェントを作成する上で、
[フーディンデッキエージェントルールベースモデル](https://www.kaggle.com/code/ryotasueyoshi/rule-based-not-psychic-alakazam-best-5th?scriptVersionId=328654333)
をすべてのデッキエージェントのひな形として採用した。
