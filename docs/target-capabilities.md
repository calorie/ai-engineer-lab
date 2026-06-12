# 到達能力チェックリスト

このドキュメントは、AIモデルそのものを実装・訓練・評価・チューニングできるエンジニアになるための到達能力を定義する。

目的は、AI APIやRAGアプリケーションを利用できることではない。モデル、損失関数、最適化、勾配、訓練ループ、アーキテクチャ、論文実装を自分で扱えることを目指す。

## 1. 教師あり学習と評価

到達条件:

- [ ] `X` が入力データ、`y` が正解ラベルであることを説明できる
- [ ] `fit` が訓練、`predict` が予測であることを説明できる
- [ ] `y_pred` と `y_test` を比較して評価する流れを説明できる
- [ ] train / validation / test split の違いを説明できる
- [ ] accuracy だけでは不十分な理由を説明できる
- [ ] precision / recall / F1 の違いを説明できる
- [ ] confusion matrix から誤分類の種類を読める
- [ ] threshold を変えたときの precision / recall の変化を説明できる
- [ ] cross-validation の平均と標準偏差を見る理由を説明できる

## 2. 古典的機械学習の実装

到達条件:

- [ ] 線形回帰を NumPy で実装できる
- [ ] ロジスティック回帰を NumPy で実装できる
- [ ] softmax回帰を NumPy で実装できる
- [ ] 損失関数を自分で実装できる
- [ ] 解析的勾配を実装できる
- [ ] 数値微分で gradient check ができる
- [ ] 学習率変更による loss curve の違いを説明できる
- [ ] L1 / L2 正則化の効果を説明できる

## 3. 最適化

到達条件:

- [ ] 勾配降下法を実装できる
- [ ] mini-batch SGD を実装できる
- [ ] Momentum を実装できる
- [ ] Adam を実装できる
- [ ] optimizer が何を更新しているか説明できる
- [ ] 学習率が大きすぎる場合の発散を実験で示せる
- [ ] 学習率が小さすぎる場合の収束遅延を実験で示せる
- [ ] 正則化が最適化問題として何を変えるか説明できる

## 4. ニューラルネットワークの自作

到達条件:

- [ ] affine layer の forward / backward を実装できる
- [ ] ReLU の forward / backward を実装できる
- [ ] sigmoid の forward / backward を実装できる
- [ ] softmax + cross entropy を実装できる
- [ ] MLP を NumPy で実装できる
- [ ] backpropagation と chain rule の関係を説明できる
- [ ] mini-batch training を実装できる
- [ ] dropout の効果を実験で示せる
- [ ] normalization の目的を説明できる

## 5. PyTorch訓練基盤

到達条件:

- [ ] `Dataset` / `DataLoader` を使える
- [ ] training loop を自分で書ける
- [ ] validation loop を自分で書ける
- [ ] `loss.backward()` が何をするか説明できる
- [ ] optimizer update の意味を説明できる
- [ ] checkpoint を保存・復元できる
- [ ] seed を固定して再現性を高められる
- [ ] metric logging ができる
- [ ] early stopping を実装できる
- [ ] gradient clipping を実装できる
- [ ] mixed precision の基礎を説明できる

## 6. 代表的アーキテクチャ

到達条件:

- [ ] CNN の基本構造を説明・実装できる
- [ ] RNN の基本構造を説明・実装できる
- [ ] LSTM または GRU の役割を説明できる
- [ ] attention の基本を実装できる
- [ ] seq2seq の構造を説明できる
- [ ] transformer encoder の基本構造を説明できる
- [ ] 各アーキテクチャの帰納バイアスを説明できる

## 7. Transformer

到達条件:

- [ ] token embedding を実装できる
- [ ] positional encoding を説明・実装できる
- [ ] scaled dot-product attention を実装できる
- [ ] multi-head attention を実装できる
- [ ] residual connection の役割を説明できる
- [ ] layer normalization の役割を説明できる
- [ ] causal mask を説明・実装できる
- [ ] decoder-only Transformer を実装できる
- [ ] tiny language model を訓練できる
- [ ] temperature 変更による生成結果の違いを説明できる

## 8. 論文実装

到達条件:

- [ ] 論文が何を解決したか説明できる
- [ ] 既存手法との差分を説明できる
- [ ] 中心数式を説明できる
- [ ] 簡略版を実装できる
- [ ] 再現できた結果を記録できる
- [ ] 再現できなかった点を明記できる
- [ ] ablation を設計できる
- [ ] 論文実装を GitHub 上でレビュー可能な形にできる

## 9. チューニング診断

到達条件:

- [ ] loss が下がらない原因候補を挙げられる
- [ ] train loss だけ良い場合の原因候補を挙げられる
- [ ] validation が不安定な場合の原因候補を挙げられる
- [ ] 勾配爆発への対策を説明できる
- [ ] 勾配消失への対策を説明できる
- [ ] learning rate / batch size / weight decay / dropout の調整実験ができる
- [ ] scheduler / warmup / gradient clipping の効果を比較できる

## 10. Hugging Faceモデル公開

到達条件:

- [ ] 自作または自分で訓練した小規模モデルを保存できる
- [ ] tokenizer または前処理手順を保存できる
- [ ] 推論スクリプトを用意できる
- [ ] 評価スクリプトを用意できる
- [ ] model card を書ける
- [ ] license を明記できる
- [ ] limitations を明記できる
- [ ] 訓練条件と評価結果を公開できる
- [ ] GitHub repo と Hugging Face model repo を相互リンクできる

## 最終判定基準

最終的に、次の成果物が揃っていれば、この学習計画は完了とする。

- [ ] `projects/01-ml-from-scratch/`
- [ ] `projects/02-nn-from-scratch/`
- [ ] `projects/03-training-loop-pytorch/`
- [ ] `projects/04-tiny-transformer/`
- [ ] `projects/05-paper-reproduction/`
- [ ] `projects/06-hf-model-release/`
- [ ] `reports/training-diagnostics.md`
- [ ] `reports/hyperparameter-tuning.md`
- [ ] Hugging Face Hub に公開された小規模モデル
