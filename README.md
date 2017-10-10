# fasttextを使用した、口コミサイトなどのレビューのネガポジ判定する分類器。
[GitHub-nekosfc negapozi](https://github.com/nekosfc/text_writer "GitHub text-writer") のおまけ

また、今回は実際の口コミサイトでクローラを走らせて口コミを回収し、それらを元にモデルを作成しました。
ただ、生の口コミデータは少し問題があるかもしれないので生データは削除し、学習済みモデルとモデル作成・モデルを使用した分類器のスクリプトのみの公開という形にしました。
詳しい説明はおまけなので割愛します。

とりあえずpredict.pyだけでも動かす手順は以下の通りです。

- `git clone git@github.com:nekosfc/negapozi.git`
- `cd negapozi/src`
- `python predict.py`

デフォルトで適当な文章が入っているので何か別の文章を判定してみたい時はpredict.pyの28行目の文章の部分を編集し、任意のものに変えてみてください。

実際に学習させたい時は、ポジティブな文章をml_data/posi.txtの中に、ネガティブな文章をml_data/nega.txtの中にたくさん書き込んでください。
その後、src/data_refactor.pyを実行すると、ml_dataの中にlabel_negaposi.lstというファイルが生成されます。
これがラベル付けされた文章データになります。

その後、src/makemodel.pyを実行すると新しいmodel.binがsrcの中に作成されるのでsrc/predict.pyを実行するとそのモデルを使用した判定結果を返してくれます。

学習させるデータによって判定結果にも色が出てくると思うので是非いろんなデータで試してみてください。
