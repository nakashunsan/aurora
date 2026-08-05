# Lace-up Boots v1 — ImageGen Prompt

## 入力画像

- `lace-up-boots-default-texture.png`：VRoid Studio 2.14.0の標準「スニーカー」テクスチャ
- `lace-up-boots-uv-guide.png`：同テンプレートのUVガイド
- `../../Aurora v1x/Aurora-v1x-casual-C-layered.png`：衣装Cのデザイン参照

## 生成プロンプト

```text
Use case: precise-object-edit
Asset type: production-ready VRoid Studio shoe UV texture PNG.

The first image is the exact editable VRoid sneaker texture and defines the canvas, UV islands, positions, and alignment. The second image is its UV guide and is a hard geometric constraint. The third image is the Aurora v1x casual-C outfit reference and defines the intended fashion direction.

Repaint the first texture into modern masculine black lace-up ankle sneakers/boots for the boy Aurora. Keep the exact same 1024x1024 UV layout, silhouette coverage, island positions, scale, and transparent background as the first image so it can be imported directly into VRoid Studio.

Design: understated casual urban footwear, matte black leather and technical-fabric panels, subtle charcoal shading, black laces, small gunmetal eyelet details, low-profile slightly chunky black sole, and only a very thin muted teal outsole accent matching the outfit. Make it coordinated with the off-white overshirt, black layers, slim trousers, and asymmetric teal waist panel. Avoid fantasy, sci-fi glow, neon, bright cyan laces, broad white borders, labels, logos, text, symbols, mockups, feet, body, or scenery.

Palette: near-black #15171A, charcoal #25282D, soft graphite #555B61, muted teal #339CA4.

Preserve clean UV-ready edges and readable material separation at texture resolution. Output only the finished flat UV texture PNG.
```

## 後処理

ImageGen出力の1254×1254画像を1024×1024へ縮小しました。出力に透明チェッカーが
焼き込まれていたため、背景の高輝度領域をアルファ化し、PNGの透明度を復元しています。

- `lace-up-boots-imagegen-source.png`：ImageGenの元出力
- `lace-up-boots-v1.png`：1024×1024、RGBAのVRoid読み込み用画像

## VRoid Studioへの組み込み

標準「スニーカー」のテクスチャへ`lace-up-boots-v1.png`を新規レイヤーとして読み込み、
旧レイヤーとデフォルト画像を非表示にしました。靴カテゴリの新規カスタムアイテムとして
保存し、`Aurora-v1x-layered-working.vroid`へ適用済みです。
