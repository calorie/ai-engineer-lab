# AIエンジニア転身 学習計画

このドキュメントは、シニアソフトウェアエンジニアから、AIモデルそのものを実装・訓練・評価・チューニングできるエンジニアへ転身するための学習計画である。

ここで目指す「AIエンジニア」は、AI APIやRAGアプリケーションを利用してプロダクトを作るエンジニアではない。主に次のロールに近い能力を目指す。

- ML Engineer
- Research Engineer
- Deep Learning Engineer
- Model Training Engineer
- ML Systems Engineer

## ゴールの再定義

最終目標は、AIをブラックボックスとして利用することではない。

> 損失関数、最適化、勾配計算、訓練ループ、モデルアーキテクチャ、評価手法を自分で実装・検証・チューニングできる状態になる。

より具体的には、代表的な機械学習・深層学習モデルを自分で実装し、学習が進む理由、進まない理由、性能が変化する理由を、実験ログ・数式・コードで説明できる状態を目指す。

## 到達イメージ

この計画の完了条件は、教材の完了ではない。

完了条件は、ML Engineer / Research Engineer 候補としてレビュー可能な実装・実験・論文再現成果物を GitHub 上に残すことである。

到達後に説明できるべきことは次のとおり。

- 教師あり学習における `X`, `y`, `fit`, `predict`, `y_pred`, `y_test` の関係
- train / validation / test split の意味
- accuracy, precision, recall, F1, ROC-AUC, confusion matrix の使い分け
- 損失関数と最適化の関係
- 勾配降下法、mini-batch SGD、Momentum、Adam の違い
- 数値微分、解析的勾配、gradient check の意味
- backpropagation が何を計算しているか
- PyTorch の `loss.backward()` と optimizer update の関係
- CNN / RNN / Attention / Transformer の主要部品
- Transformer の causal mask, multi-head attention, layer normalization の役割
- 学習が不安定なときの診断と改善仮説
- 論文の中心アイデアを読み取り、簡略版を実装する方法
- 小規模モデルを訓練し、評価結果・制限事項・再現手順付きで Hugging Face Hub に公開する方法

## 学習姿勢の原則

### 1. 読書量を進捗とみなさない

読書は進捗ではない。進捗として扱うのは次の成果物だけである。

- 動くコード
- 実験ログ
- 評価指標
- 失敗原因の仮説
- 改善前後の比較
- 数式とコードの対応説明
- 自分の言葉による説明

### 2. 理解してから作るのではなく、作って失敗してから理論に戻る

AI学習では、数式、実装、実験、評価が循環して初めて理解が進む。

したがって、基本姿勢を次のように定義する。

> 読むために読むのではなく、実験で壊すために読む。  
> 理解してから作るのではなく、作って失敗してから理論で修正する。

### 3. 理解度60%で実装に進む

完全理解を待たない。実装で破綻した箇所だけ理論に戻る。

完全理解を前提にすると、抽象理論の前で停止しやすい。必要なのは、理論を使って実験結果を説明し、改善する能力である。

### 4. 学習単位は「章」ではなく「実験」にする

悪い学習単位:

- 第2章を読む
- Transformerについて調べる
- 最適化を勉強する

良い学習単位:

- 学習率を `0.001`, `0.01`, `0.1`, `1.0` に変えて loss curve を比較する
- 正則化あり・なしで validation score を比較する
- threshold を変えて precision / recall のトレードオフを見る
- attention mask を外したときに生成結果がどう壊れるか確認する

### 5. AI活用アプリを主目的にしない

RAG、Agent、LLM API アプリケーションは主目標ではない。

優先順位は次のとおり。

1. モデル・損失・最適化・訓練
2. 評価・誤差分析・チューニング
3. アーキテクチャ実装
4. 論文実装
5. モデル公開・再現可能なリリース
6. 必要最低限の推論API化
7. RAG / Agent / LLMアプリ

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
2. notebook または script を1回だけ実行する
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

## 48週間計画

24週間では基礎実装の入口までである。AI自体を実装・チューニングできる水準を目指すため、計画は48週間を標準とする。

### Phase 0: 再起動と実験基盤（1週目）

目的は、学習内容そのものではなく、継続可能で再現可能な実験環境を作ることである。

やること:

- GitHubリポジトリを作成する
- `README.md`, `AGENTS.md`, `notes/`, `experiments/`, `reports/`, `src/` を整備する
- Python実行環境を固定する
- 学習ログテンプレートを作る
- 最初のデータセット候補を選ぶ

成果物:

- `README.md`
- `AGENTS.md`
- `notes/week01.md`
- `docs/learning-plan.md`
- `pyproject.toml`
- `uv.lock`
- `experiments/001_baseline.ipynb`

### Phase 1: 教師あり学習と評価設計（2〜5週目）

目的は、モデルの良し悪しを測る能力を作ることである。

扱う内容:

- train / validation / test split
- cross validation
- data leakage
- baseline
- precision / recall / F1
- ROC-AUC
- confusion matrix
- class imbalance
- threshold tuning
- calibration
- overfitting / underfitting

成果物:

- `experiments/001_baseline.ipynb`
- `experiments/002_threshold_tuning.ipynb`
- `experiments/003_cross_validation.ipynb`
- `reports/01-supervised-learning-evaluation.md`

完了条件:

- accuracy だけでは不十分な理由を説明できる
- threshold を変えると precision / recall がどう動くか説明できる
- validation を使わずに test を何度も見ると何が壊れるか説明できる
- cross-validation の平均と分散を見る理由を説明できる

### Phase 2: NumPyでMLアルゴリズムを自作する（6〜11週目）

目的は、`fit` の中で何が起きているかを自分で実装して理解することである。

実装するもの:

- 線形回帰
- ロジスティック回帰
- softmax回帰
- 勾配降下法
- mini-batch SGD
- Momentum
- Adam
- L1 / L2 正則化
- 数値微分
- 解析的勾配
- gradient check

成果物:

```text
src/ml_from_scratch/
  linear_regression.py
  logistic_regression.py
  softmax_regression.py
  losses.py
  optimizers.py
  regularization.py
  gradient_check.py
```

完了条件:

- loss, gradient, optimizer update の関係を説明できる
- scikit-learn の結果と自作実装の結果を比較できる
- 学習率が大きすぎる場合・小さすぎる場合の挙動を実験で示せる
- 正則化が最適化問題として何を変えるか説明できる

### Phase 3: NumPyでニューラルネットワークを自作する（12〜17週目）

目的は、自動微分なしで backpropagation の意味を理解することである。

実装するもの:

- affine layer
- ReLU
- sigmoid
- softmax
- cross entropy
- MLP
- forward / backward
- mini-batch training
- dropout
- batch normalization または layer normalization の簡易版

成果物:

```text
src/nn_from_scratch/
  layers.py
  activations.py
  losses.py
  mlp.py
  trainer.py
```

完了条件:

- forward pass と backward pass を説明できる
- chain rule が backpropagation でどう使われるか説明できる
- train loss / validation loss を可視化できる
- 過学習と正則化の関係を実験で示せる

### Phase 4: PyTorchで訓練システムを作る（18〜23週目）

目的は、研究実験を再現可能に回す訓練基盤を作ることである。

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
- gradient clipping
- mixed precision の基礎

成果物:

```text
src/training/
  trainer.py
  callbacks.py
  metrics.py
  config.py
  checkpoint.py
```

完了条件:

- PyTorch の `loss.backward()` が何を計算するか説明できる
- optimizer がどのパラメータを更新するか説明できる
- seed固定、checkpoint、metric logging を含む訓練ループを再利用できる形で実装できる

### Phase 5: CNN / RNN / Attention を実装する（24〜31週目）

目的は、代表的アーキテクチャの帰納バイアスを理解することである。

実装するもの:

- CNN
- RNN
- LSTM または GRU
- attention
- seq2seq
- transformer encoder

完了条件:

- なぜCNNは画像に強いのか説明できる
- なぜRNNは系列を扱えるのか説明できる
- なぜAttentionは系列内の依存を直接扱えるのか説明できる
- 各アーキテクチャの学習曲線と失敗例を比較できる

### Phase 6: Transformerをスクラッチ寄りに実装する（32〜37週目）

目的は、Transformerをブラックボックスではなく、テンソル演算の組み合わせとして理解することである。

実装するもの:

- token embedding
- positional encoding
- scaled dot-product attention
- multi-head attention
- residual connection
- layer normalization
- feed-forward network
- causal mask
- decoder-only Transformer
- tiny language model

やるべき実験:

- head数を変える
- embedding dimensionを変える
- layer数を変える
- learning rateを変える
- context lengthを変える
- dropoutを変える
- weight decayを変える

成果物:

```text
projects/04-tiny-transformer/
  README.md
  model.py
  train.py
  generate.py
  experiments.md
```

完了条件:

- causal mask の意味を説明できる
- attention weight を可視化できる
- 小規模言語モデルを訓練し、loss が下がることを確認できる
- generation の temperature 変更による出力差を説明できる

### Phase 7: 論文実装（38〜43週目）

目的は、論文を読み、中心アイデアを実装に落とす能力を作ることである。

候補:

- Attention Is All You Need
- Adam
- Dropout
- Batch Normalization
- ResNet
- LoRA

最低2本、可能なら3本を paper to code する。

各論文について残すもの:

- 何を解決した論文か
- 既存手法と何が違うか
- 中心数式は何か
- 自分の実装ではどこを簡略化したか
- 再現できた結果
- 再現できなかった点
- ablation 結果

成果物:

```text
papers/
  attention_is_all_you_need.md
  lora.md

projects/05-paper-reproduction/
```

### Phase 8: モデルチューニングと訓練安定化（44〜46週目）

目的は、訓練がうまくいかないときに原因仮説を立て、改善実験を設計できるようになることである。

扱う内容:

- learning rate tuning
- batch size tuning
- weight decay
- dropout
- scheduler
- warmup
- gradient clipping
- initialization
- normalization
- overfitting diagnosis
- underfitting diagnosis
- data augmentation

成果物:

- `reports/training-diagnostics.md`
- `reports/hyperparameter-tuning.md`

完了条件:

- loss が下がらない原因候補を複数挙げられる
- train loss だけ良い場合の原因候補を説明できる
- validation が不安定な場合の原因候補を説明できる
- 勾配爆発・勾配消失への対策を説明できる

### Phase 9: Hugging Faceモデル公開（47〜48週目）

目的は、自作または自分で訓練した小規模モデルを、再現手順・評価結果・制限事項付きで公開できるようになることである。

公開候補:

- `tiny-transformer-from-scratch`
- `tiny-transformer-ja-charlm`
- `mnist-mlp-from-scratch`

やること:

- model weights を保存する
- tokenizer または前処理手順を保存する
- config を定義する
- 推論スクリプトを用意する
- 評価スクリプトを用意する
- model card を作成する
- license を明記する
- limitations を明記する
- GitHub repo と Hugging Face model repo を相互リンクする

成果物:

```text
projects/06-hf-model-release/
  README.md
  train.py
  model.py
  tokenizer.py
  generate.py
  eval.py
  config.json
  model_card.md
  release_checklist.md
```

完了条件:

- Hugging Face Hub にモデルを公開できる
- model card に訓練条件、評価結果、制限事項、再現手順が書かれている
- GitHub 上の training code から再訓練または推論を再現できる

## 「機械学習のための連続最適化」の扱い

この本は捨てない。ただし、最初に精読する本ではなく、実験で詰まったときに読む本として扱う。

| 実験で起きた問題 | 読むべき理論 |
|---|---|
| lossが発散する | 勾配法、学習率、収束 |
| lossが下がらない | 条件数、スケーリング、非凸性 |
| trainは良いがvalidが悪い | 正則化、汎化 |
| optimizerで結果が違う | SGD, Momentum, Adam |
| 制約条件がある | ラグランジュ、制約付き最適化 |
| モデルが不安定 | 凸性、滑らかさ、初期値依存 |

完了条件は「読んだ」ではない。

各トピックについて、以下を満たしたら完了とする。

- 数式を1つ自分の言葉で説明する
- その数式に対応するPythonコードを書く
- 実験で挙動を確認する
- この知識がチューニングでどう使えるかを3行で書く

## リポジトリ構成

採用や公開を意識した最終成果物は、単なるNotebook集ではなく、実装・実験・説明が分離された構成にする。

```text
src/
  ml_from_scratch/
  nn_from_scratch/
  training/

experiments/
  001_baseline.ipynb
  002_threshold_tuning.ipynb
  003_cross_validation.ipynb

projects/
  01-ml-from-scratch/
  02-nn-from-scratch/
  03-training-loop-pytorch/
  04-tiny-transformer/
  05-paper-reproduction/
  06-hf-model-release/

papers/
  attention_is_all_you_need.md
  lora.md

reports/
  01-supervised-learning-evaluation.md
  training-diagnostics.md
  hyperparameter-tuning.md
```

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

### Week 2: ベースライン改善とスケーリング

- StandardScaler を追加する
- Logistic Regression の標準化前後を比較する
- confusion matrix を比較する
- 悪性 recall がどう変化するか確認する

成果物:

- `experiments/001_baseline.ipynb` の拡張
- `reports/baseline_report.md`

### Week 3: 閾値調整と交差検証

- `predict_proba()` を使う
- threshold を変える
- precision / recall trade-off を見る
- cross-validation を入れる
- 平均と標準偏差を記録する

成果物:

- `experiments/002_threshold_tuning.ipynb`
- `experiments/003_cross_validation.ipynb`
- `reports/cv_results.csv`

### Week 4: ロジスティック回帰の中身へ進む準備

- sigmoid を理解する
- binary cross entropy を理解する
- 勾配の意味を理解する
- NumPy実装の準備をする

成果物:

- `reports/01-supervised-learning-evaluation.md`
- `notes/week04.md`

## この計画の定義

この学習計画を次の一文で定義する。

> AIを使うエンジニアではなく、AIモデルを作るエンジニアになる。  
> そのために、アプリケーション開発ではなく、教師あり学習、損失関数、最適化、勾配、backpropagation、PyTorch訓練ループ、Transformer、論文実装、チューニング診断、モデル公開を主軸にする。
