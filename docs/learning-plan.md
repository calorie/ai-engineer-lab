# AIエンジニア転身 学習計画

このドキュメントは、シニアソフトウェアエンジニアからAIエンジニアへ転身するための学習計画である。

目的は、教材を順番に消費することではない。AIシステムを実装し、評価し、チューニングし、説明できる状態になることである。

## 最終目標

24週間で、以下を自分の言葉と成果物で説明できる状態を目指す。

> データセットを選び、ベースラインを作り、評価指標を定義し、モデルを改善し、誤差分析し、PyTorchで再実装し、必要に応じてLLM、RAG、LoRAを使い、実験ログ付きで説明できる。

これは「AIについて勉強した状態」ではなく、AIエンジニアとして最低限必要な実務単位である。

## 学習姿勢の原則

### 1. 読書量を進捗とみなさない

読書は進捗ではない。進捗として扱うのは次の成果物だけである。

- 動くコード
- 実験ログ
- 評価指標
- 失敗原因の仮説
- 改善前後の比較
- 自分の言葉による説明

### 2. 理解してから作るのではなく、作って失敗してから理論に戻る

AI学習では、数式、実装、実験、評価が循環して初めて理解が進む。

したがって、基本姿勢を次のように定義する。

> 読むために読むのではなく、実験で壊すために読む。
> 理解してから作るのではなく、作って失敗してから理論で修正する。

### 3. 理解度60%で実装に進む

完全理解を待たない。実装で破綻した箇所だけ理論に戻る。

完全理解を前提にすると、抽象理論の前で停止しやすい。AIエンジニアに必要なのは、理論を使って実験結果を説明し、改善する能力である。

### 4. 学習単位は「章」ではなく「実験」にする

悪い学習単位:

- 第2章を読む
- Transformerについて調べる
- 最適化を勉強する

良い学習単位:

- 学習率を `0.001`, `0.01`, `0.1`, `1.0` に変えて loss curve を比較する
- 正則化あり・なしで validation score を比較する
- attention mask を外したときに生成結果がどう壊れるか確認する

## 週間運用

標準ラインは週7〜8時間とする。

| 曜日 | 内容 | 成果物 |
|---|---|---|
| 月 | 理論インプット 45〜60分 | メモ10行 |
| 火 | 実装 60分 | Git commit |
| 水 | 実験 60分 | loss / metric / 失敗ログ |
| 木 | 理論補強 45〜60分 | 失敗原因の仮説 |
| 金 | 予備日 | 未完タスク回収 |
| 土 | 2〜3時間の統合実装 | notebook / repo 更新 |
| 日 | 30分レビュー | 翌週の仮説1つ |

## 最低ライン

継続できない週を全損にしないため、最低ラインを定義する。

週に2回、各20分だけでもよい。ただし、やることは固定する。

1. 前回ログを読む
2. notebookを1セルだけ実行する
3. 次にやることを1行書く

これは計画を緩めるためではない。中断を長期離脱に変えないためのフェイルセーフである。

## 中断時の復帰ルール

3日以上空いた場合、記憶から再開しない。

次の手順で復帰する。

1. 最新の学習ログを読む
2. 最新の実験Notebookまたはスクリプトを1回実行する
3. 前回の失敗または次アクションを確認する
4. 20分で終わる最小タスクに分解する

## 週次レビュー

毎週日曜に、以下へ回答する。

```text
1. 今週、動いたものは何か？
2. 今週、壊れたものは何か？
3. loss / metric はどう変化したか？
4. 理論で説明できた現象は何か？
5. まだ説明できない現象は何か？
6. 来週の実験仮説は何か？
```

## 24週間計画

### Phase 0: 再起動準備（1週目）

目的は、学習内容そのものではなく、継続可能な運用環境を作ることである。

やること:

- GitHubリポジトリを作成する
- `README.md`, `AGENTS.md`, `notes/`, `experiments/`, `reports/`, `src/` を整備する
- Python実行環境を固定する
- 学習ログテンプレートを作る
- 最初のデータセット候補を選ぶ

完了条件:

- リポジトリが存在する
- 学習ログが存在する
- Python環境を再現できる
- 最初の実験に着手できる

### Phase 1: 古典的機械学習で評価を叩き込む（2〜5週目）

目的は、AIエンジニアとして最重要の基礎である「モデルの良し悪しを測る能力」を作ることである。

扱う内容:

- train / validation / test split
- cross validation
- data leakage
- baseline
- precision / recall / F1
- ROC-AUC
- confusion matrix
- feature engineering
- overfitting / underfitting

成果物:

- 表形式データの分類または回帰実験
- Logistic Regression, Random Forest などの比較
- 評価指標の比較表
- 誤差分析レポート

この段階では、ニューラルネットワークに急がない。評価設計ができない状態で高度なモデルを使っても、チューニングの意味が崩れる。

### Phase 2: NumPyで学習アルゴリズムを自作する（6〜9週目）

目的は、「学習とは損失関数を最小化することである」ことをコードで理解することである。

実装するもの:

- 線形回帰
- ロジスティック回帰
- 勾配降下法
- 学習率変更による loss curve 比較
- L2正則化
- 数値微分による勾配チェック

この段階で、最適化理論を読み始める。

読む問い:

- なぜ学習率が大きすぎると発散するのか
- なぜ学習率が小さすぎると進まないのか
- 凸性があると何が嬉しいのか
- 勾配法は何を保証し、何を保証しないのか
- 正則化は最適化問題として何を変えているのか

### Phase 3: PyTorchで深層学習の標準訓練ループを身につける（10〜13週目）

目的は、AIモデルを訓練し、デバッグし、改善するための標準作法を身につけることである。

扱う内容:

- `Dataset`
- `DataLoader`
- training loop
- validation loop
- optimizer
- scheduler
- checkpoint
- early stopping
- seed固定
- experiment config管理

成果物:

- 画像分類またはテキスト分類モデル
- loss curve
- accuracy / F1
- 意図的に過学習させた実験
- 正則化で改善した実験

読む理論:

- chain rule
- backpropagation
- activation function
- initialization
- normalization
- dropout
- SGD / momentum / Adam

### Phase 4: Transformerを部品として理解する（14〜17週目）

目的は、巨大LLMをブラックボックスとして使う前に、Transformerの主要部品をテンソル演算として理解することである。

実装するもの:

- token embedding
- positional encoding
- scaled dot-product attention
- multi-head attention
- layer normalization
- feed-forward network
- causal mask
- tiny language model

成果物:

- 小規模テキストによる next-token prediction
- attention mask の可視化
- lossが下がる実験
- temperature変更による生成結果比較

読む理論:

- 線形代数: 内積、射影、行列積
- 確率: softmax、cross entropy
- 情報理論: entropy、KL divergence
- 最適化: Adam、学習率スケジューリング

### Phase 5: LLMアプリケーション実装（18〜21週目）

目的は、モデル単体ではなく、AIシステムとして設計・評価する力を作ることである。

主テーマはRAGとする。

やること:

- 文書分割
- embedding
- vector search
- retrieval
- prompt設計
- answer generation
- hallucination検出
- 評価データセット作成
- 回答品質評価

成果物:

- 小規模RAGアプリ
- 20〜50件の評価質問
- retrieval失敗 / generation失敗 / prompt失敗の分類
- 改善前後の比較

重要なのは「動いた」ではなく、どの失敗が検索由来で、どの失敗が生成由来か説明できることである。

### Phase 6: Fine-tuning / LoRA / MLOps（22〜24週目）

目的は、既存モデルを実務目的に合わせて適応・評価する流れを経験することである。

やること:

- 既存モデルの推論
- dataset整形
- LoRAによる軽量fine-tuning
- before / after比較
- inference cost測定
- model card作成

成果物:

- LoRA fine-tuning notebook
- 評価データ
- before / after の定量比較
- 失敗分析
- 推論速度・メモリ使用量のメモ
- README付き実験レポート

## 「機械学習のための連続最適化」の扱い

この本は捨てない。ただし、最初に精読する本ではなく、実験で詰まったときに読む本として扱う。

| 実験で起きた問題 | 読むべき理論 |
|---|---|
| lossが発散する | 勾配法、学習率、収束 |
| lossが下がらない | 条件数、スケーリング、非凸性 |
| trainは良いがvalidが悪い | 正則化、汎化 |
| optimizerで結果が違う | SGD, momentum, Adam系 |
| 制約条件がある | ラグランジュ、制約付き最適化 |
| モデルが不安定 | 凸性、滑らかさ、初期値依存 |

完了条件は「読んだ」ではない。

各トピックについて、以下を満たしたら完了とする。

- 数式を1つ自分の言葉で説明する
- その数式に対応するPythonコードを書く
- 実験で挙動を確認する
- この知識がチューニングでどう使えるかを3行で書く

## 最初の4週間

### Week 1: 再起動と環境構築

- リポジトリを作成する
- Python環境を作成する
- 基本ライブラリを導入する
- 最初のデータセット候補を選ぶ
- 最初のベースラインNotebookを作成する

成果物:

- `README.md`
- `AGENTS.md`
- `notes/week01.md`
- `docs/learning-plan.md`
- `pyproject.toml`
- `uv.lock`
- `experiments/001_baseline.ipynb`

### Week 2: ベースライン分類器

- データ読み込み
- train / validation split
- Logistic Regression
- Random Forest
- 評価指標比較

成果物:

- `experiments/001_baseline.ipynb`
- `reports/baseline_report.md`
- `reports/confusion_matrix.png`

### Week 3: 誤差分析

- 間違えたサンプルを見る
- featureを追加・削除する
- leakageがないか確認する
- cross-validationを入れる

成果物:

- `reports/error_analysis.md`
- `reports/cv_results.csv`

### Week 4: 第1回レポート

テーマ:

> このデータセットにおいて、何が予測を難しくしているのか？

書く内容:

- 問題設定
- データ概要
- baseline
- 評価指標
- 改善実験
- 失敗分析
- 次の仮説

## 旧計画から残すもの・捨てるもの

### 残すもの

- 数学を重視する姿勢
- Transformerを最終的に理解する方針
- PyTorch中心
- Paper to Code
- MLOps視点
- LoRA / RAG / tuning

### 捨てるもの

- 最初から高難度書籍を精読する
- 数学を体系順に全部やる
- 読書量を進捗とみなす
- 完全理解してから実装する
- 遠すぎる目標だけを置く

## この計画の定義

この学習計画を次の一文で定義する。

> 24週間で、AIの理論を読む人ではなく、実験・評価・改善・説明ができるAIエンジニアになる。理論はすべて、実装上の失敗を説明・修正するために読む。
