# Original Textures

Aurora v1x用に制作するオリジナル衣装テクスチャを保存します。

推奨構成：

```text
textures/
  tops/
  bottoms/
  legwear/
  shoes/
  source/
```

- PNGは透明度を維持して保存する
- 編集元データを管理する場合は `source/` に置く
- ファイル名には対象テンプレートと部位を含める
- 第三者衣装のテクスチャを複製、トレース、切り取り、合成しない
- UVガイドはVRoid Studioから対象テンプレートごとに書き出す

例：

```text
tops/outer-shirt-jacket.png
tops/inner-black-top.png
tops/mock-neck-skin-overlay.png
bottoms/wrap-panel-base.png
legwear/black-leggings-base.png
shoes/lace-up-shoes-base.png
```
