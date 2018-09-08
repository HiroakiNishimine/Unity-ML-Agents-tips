# Unity-ML-Agents-tips
* 強化学習ライブラリ Unity ML_Agentsを触ってみたときのTipsを記述しています。
* [Unity ML-Agents実践ゲームプログラミング](https://www.borndigital.co.jp/book/6702.html)に出てくるコードを写経しながら、詰まったところについてメモをしていきます。
* 機械学習歴は1年半くらいで、Unityは完全な初心者です。この本はUnity ML-Agentsの解説本であって、Unityの解説本ではないので、まず[ドットインストールのUnity入門](https://dotinstall.com/lessons/basic_unity)でざっと勉強しました。(動画が2013年公開なので古いですが、使い勝手はあまり変わりありません)

## 実行環境
* OS : Windows 10 Home
* Unity : 2018.2.6f1 Personal(64bit)
* [Unity ML-Agents : Beta 0.4.0b](https://github.com/Unity-Technologies/ml-agents/releases)
* [TensorFlowSharp plugin : v1.7.0](https://github.com/migueldeicaza/TensorFlowSharp/releases)
## 検証日時
* 2018/09/08
## 実行コマンド集
* 2章
  * 学習を実行
    * `python learn.py MLAgentsExamples.exe --train`
  * 保存されたモデルをロードして、続きから学習を実行
    * `python learn.py MLAgentsExamples.exe --train --load`
  * Unity上でデバッグ状態で学習を実行
    * `python learn.py --train`
  * Tensorboard起動
    * `tensorboard --logdir=summaries`
## 詰まったポイント
* プロジェクトの保存先（ディレクトリ）に日本語が入っていると、以下のようなエラーとなる。（環境(env)からの応答がなくなって、タイムアウトエラー）
  * エラー文 : `The Unity environment took too long to respond.`
  * 対応：日本語のパスは使わないで、すべて英語のパスとする
* Sceneの保存(P68)
  * https://dotinstall.com/lessons/basic_unity/24604
* Hierarchyへの画像の追加(P69)
