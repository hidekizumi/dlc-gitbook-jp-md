# extract_frames()関数の説明

`deeplabcut.extract_frames(config,
    mode="automatic",
    algo="kmeans",
    cluster_step=1,
    cluster_color=False)`
として、この関数について説明します。変更する可能性があるであろう引数として5つを選びましたが、引数は他にもたくさんありますので、詳しくは[こちら](https://github.com/DeepLabCut/DeepLabCut/blob/master/deeplabcut/generate_training_dataset/frame_extraction.py)を参照してください。

* 第1引数 `config` について

    configには、config.yamlの相対パスを入れます。

  
* 第2引数 `mode` について

    `mode` には、`"automatic"`か`"manual"`を入れます。

  * `"automatic"`はその後ろに書いたアルゴリズムでフレームを抽出することにします
  * `"manual"`は手動で抜き出すフレームを指定します。

  
* 第3引数 `algo` について

    `algo` には、`"kmeans"`か`"uniform"`を入れます。`mode` にて`"automatic"`を指定した場合に有効になります。

  * `"kmeans"`　は 各フレーム画像を統計学的にクラスタリングして、各クラスターから均等にフレーム画像を抽出していくものです。
  * `"uniform"`は 一定の間隔ごとにフレームを抽出します。

  
* 第4引数 `cluster_step` について

    > 動画のフレーム数が多すぎる場合に使う、間引きのためのオプションです。１ならば全フレームを抽出対象にします。10ならば1，11，21，31、、、と10フレーム間引いてフレーム数を減らしてから、抽出アルゴリズムを適用します。この間引きは、kmeansの計算量が多いためにマシーンパワーを節約するためのものです。（引用 : https://note.com/sakulab/n/n539e6b934667 ）

  デフォルトでは1です。

  
* 第5引数 `cluster_color` について

    デフォルトでは`False`になっています。`False`の場合、各画像はグレースケールベクトルとして扱われます（色情報は破棄されます）。`True`の場合は、カラーチャンネルが考慮されます。一方で、カラーチャンネルを考慮すると計算の複雑さが増します。

