# ICR

## 2023/05/27
- TabPFNというテーブルデータのためのTransformerモデル
- 論文では「小さな表形式データに対して1秒以内に教師あり分類タスクを実行でき，ハイパーパラメータのチューニングがいらない高精度のモデル」
- 精度としてはOpenML-CC18というデータセットの中の30個のデータセットでGBDTの性能を上回ったほか，AutoMLに対して同等の精度を70倍の速度で達成した
- PFN(Prior-Data Fitted Networks)をもとに構築されており，ベイジアンニューラルネットワークと構造的因果モデルに基づき表形式データの根底にある複雑な特徴量の依存性と潜在的な因果構造をモデル化する事前分布を作り出す
- 1回のフォワードパスで新しい事前分布を確率的に推定するように事前に訓練されたTransformerで，小規模の分類タスク(サンプル数<1000,特徴量数100，10クラス)を1秒未満で解き，高い精度を達成しました
- ニューラルネットワークやGBDTの帰納バイアスはL2正則化や木の深さの調整などのパラメータに依存しますが，TabPFNではそのような設定は不要
- XGBoost,LightGBM，CatBoostなどの分類アルゴリズムより精度が高く，AutoMLが5〜60分で達成できる性能と同等の性能を示した
![image](https://github.com/plandic/ICR/assets/34090657/fda1920a-d90a-4a9e-86a8-73c325082474)

## 2023/05/28
- drop_cols = ['AY','BC', 'BZ','CL']
- ![image](https://github.com/plandic/ICR/assets/34090657/5bbb3775-6586-40b7-8589-75aa59913faf)

## 2023/05/29
- TabPFN は、小さな表形式のデータセットの教師あり分類を 1 秒未満で実行でき、ハイパーパラメーターの調整が不要で、最先端の分類手法と競合できる、トレーニング済みの Transformer です。 TabPFN はネットワークの重みに完全に組み込まれており、トレーニング サンプルとテスト サンプルを設定値の入力として受け入れ、単一の前方パスでテスト セット全体の予測を生成します。 TabPFN は事前データ適合ネットワーク (PFN) であり、事前データから抽出された合成データセットに対するベイズ推論を近似するために、オフラインで 1 回トレーニングされます。 この事前予測には、因果推論のアイデアが組み込まれています。これには、単純な構造を優先した、構造的因果モデルの大きなスペースが必要です。 最大 1,000 個のトレーニング データ ポイント、最大 100 個の欠損値のない純粋な数値特徴、および最大 10 個のクラスを含む OpenML-CC18 スイートの 18 個のデータセットでは、私たちのメソッドが明らかにブーストされたツリーを上回り、同等のパフォーマンスを発揮することを示します。 最大 70 倍のスピードアップを実現する複雑な最先端の AutoML システム。 GPU が利用可能な場合、これは 3200 倍のスピードアップに増加します。 また、これらの結果を、OpenML からの追加の 67 個の小さな数値データセットでも検証します。 すべてのコード、トレーニング済みの TabPFN、インタラクティブなブラウザ デモ、および Colab ノートブックをこの https URL で提供します。

## 2023/05/30
- outlier処理
- ![image](https://github.com/plandic/ICR/assets/34090657/d8757413-db06-435a-b2c0-399d1e262ce0)
- LBは0.2下がった

## 2023/05/3
![image](https://github.com/plandic/ICR/assets/34090657/26a08fb2-1fb2-487d-8983-87852c59c174)

