# Todo
- このノートブックを使用 https://www.kaggle.com/code/obatayuki/lb-0-69-a-litte-improvement-209808/edit
- Mixed precision でトレーニング(https://www.tensorflow.org/guide/mixed_precision によれば、TPUではbfloat16がよい)
- fp16で保存
- パラメータ数を減らす。


## Aug 20
5:08-5:20
mixed precision training なぜ途中で実行が中断されるのか？

need to switch between TPU and GPU depend on availability, maybe just using the existing method(https://www.kaggle.com/code/obatayuki/1st-place-solution-for-testing/edit) is sufficient.

1エポックに7分かかる→50エポックで350分、mixed_fp16では？
とりあえずfloat16でやってみる。1エポック
https://www.kaggle.com/code/obatayuki/1st-place-solution-for-testing/edit
これでは、with strategy.scopeを用いるために、train_foldという関数を用意し、その中でトレーニングしたモデルを用いていた。

mixed_float16では、間のレイヤーのdtype変換が必要

mixed_float16, GPU P100では、
ざっくり350ms/sample
