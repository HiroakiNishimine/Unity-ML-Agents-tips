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
  * 学習を実行(`ml-agents-master\python`配下にMLAgentsExamples.exeという実行ファイルがある場合)
    * `python learn.py MLAgentsExamples.exe --train`
  * 保存されたモデルをロードして、続きから学習を実行
    * `python learn.py MLAgentsExamples.exe --train --load`
  * Unity上でデバッグ状態で学習を実行
    * `python learn.py --train`
  * Tensorboard起動
    * `tensorboard --logdir=summaries`
## 詰まったポイント
* プロジェクトの保存先（ディレクトリ）に日本語が入っていると、以下のようなエラーとなります。（環境(env)からの応答がなくなって、タイムアウトエラー）
  * エラー文 : `The Unity environment took too long to respond.`
  * 対応：日本語のパスは使わないで、すべて英語のパスとする
* Sceneの保存(3章 P68)
  * https://dotinstall.com/lessons/basic_unity/24604
* Hierarchyへの画像の追加(3章 P69~70)
  * エクスプローラーからAssetsへ画像をドラッグアンドドロップ。AssetsからHierarchyへドラッグアンドドロップ。（その他のやり方があるかもしれません）
* Inspecter(Component)を変更した場合、OKボタン（Applyボタン）などはなく、設定は即時反映されるようであるが、保存はCtrl＋Sで行います。
* オブジェクトにコンポーネントを追加することを「アタッチ」というようです。
  * 例：「Academyオブジェクトにスクリプトをアタッチ」
* Academyオブジェクトを追加し、そこへスクリプトを追加(3章 P71~73)
  * https://dotinstall.com/lessons/basic_unity/24612
  * スクリプトの名前を付けるときに拡張子は自動でつくので、MazeAcademy.csと入力するとMazeAcademy.cs.csという名前になり以下のようなエラーが出ます。
    * エラー文 : `Can't add script behavior UnityRIOutput. The script needs to derive from MonoBehavior!`
      * このエラーはスクリプトに何らかのエラーがある場合に発生するもののようです。
      * 正確にはファイル名とスクリプトのクラス名が一致していいない場合に発生するエラーのようです。
        https://www.ipentec.com/document/unity-error-cant-add-script-when-attach-script-to-object
    * 対応：スクリプトにおける何らかのエラーを修正する（僕の場合は、MazeAcademy.cs.csとなった名前をMazeAcademy.csに修正しました）
      * また、オブジェクトのコンポーネントにあるAdd Componentからスクリプトを追加するとうまくいくことがありました。
