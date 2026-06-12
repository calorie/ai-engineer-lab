# Week 01 - 再起動と環境構築

## 目的

AI学習を継続可能な形で再開するために、リポジトリ、学習ログ、実験環境を整備する。

## 今週の成果物

- [x] リポジトリを作成した
- [x] Python環境を作成した
- [x] 基本的な機械学習ライブラリをインストールした
- [ ] 最初のデータセットを選定した
- [ ] 最初のベースラインNotebookを作成した

## ログ

### Day 1

やったこと:

- GitHub に ai-engineer-lab リポジトリを作成した
- README.md を作成した
- notes/week01.md を作成した
- experiments, notes, reports, src ディレクトリを作成した
- AGENTS.md を作成し、リポジトリ運用ルールを定義した

うまくいったこと:

- 学習ログと成果物を残すための最小構成を作成できた
- リポジトリ内では日本語を利用する方針を明文化できた

詰まったこと:

- 特になし

次にやること:

- Python 実行環境を作成する
- 基本的な機械学習ライブラリをインストールする
- 最初のデータセット候補を選ぶ

### Day 2

やったこと:

- uv を使って Python 実行環境を作成した
- Python 3.14.5 を利用するように固定した
- numpy, pandas, scikit-learn, matplotlib, jupyter, torch を追加した
- src/check_environment.py を作成した
- import の動作確認を行った
- Jupyter Notebook の起動確認を行った

うまくいったこと:

- `uv run python src/check_environment.py` で主要ライブラリの import とバージョン確認が成功した
- `uv run jupyter notebook` で Jupyter Server が起動した

詰まったこと:

- 特になし

次にやること:

- 最初のデータセット候補を選ぶ
