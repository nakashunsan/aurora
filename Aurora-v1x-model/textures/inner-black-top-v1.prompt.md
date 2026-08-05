# Inner Black Top v1 — ImageGen Prompt

Aurora v1xの衣装Cで、パーカー型ジャケットの内側に着る黒インナーを制作した際の記録です。

## Input

- `inner-tshirt-default-texture.png`：VRoid Studio標準TシャツのUV・アルファ配置
- `inner-tshirt-uv-guide.png`：VRoid Studioから書き出したUVガイド
- `Aurora v1x/Aurora-v1x-casual-C-layered.png`：衣装デザイン参照

## Prompt

```text
Use case: precise-object-edit
Asset type: production-ready VRoid Studio inner shirt UV texture PNG
Input images: Image 1 is the exact edit target and UV/alpha layout; Image 2 is the exact UV guide and hard boundary constraint; Image 3 is the outfit design reference only.
Primary request: Repaint Image 1 as Aurora v1x outfit C's minimalist black inner top. Preserve the exact square canvas, front and back UV islands, alpha, alignment, silhouette, and every panel boundary. Output only a flat 2D UV texture.
Design: deep charcoal-black lightweight mock-neck-inspired knit appearance, visually clean and modern; subtle soft fabric folds around chest and waist; extremely restrained cool teal micro-stitch accent only near the lower hem; slightly darker neckline shading to visually suggest a higher collar even though the mesh remains a T-shirt.
Color palette: charcoal #202225, near-black #151719, muted teal #339CA4 only as a tiny accent.
Constraints: paint only inside existing opaque shirt islands; preserve transparency outside; preserve exact island geometry and front/back placement; seamless and symmetric; no logo, text, watermark, character, body, mockup, background, labels, or third-party texture influence.
```

## Post-processing

ImageGenの出力を1024×2048へリサイズし、`inner-tshirt-default-texture.png`のアルファチャンネルを移植して`inner-black-top-v1.png`を作成しました。生成直後の参照画像は`inner-black-top-imagegen-reference.png`です。

## VRoid Studio

パーカーのカスタムトップスへ標準「Tシャツ」テンプレートを追加し、`inner-black-top-v1.png`を新規レイヤーとして読み込みました。標準画像レイヤーは非表示にしています。

パーカーとTシャツを同じトップスアイテムに統合すると同時着用できます。

## Integration fix: v2

`inner-black-top-v1.png`には生成画像の市松模様がRGBとして残り、背景アルファも不透明な
状態だったため、輝度から衣服部分を抽出して背景を透明化しました。さらに、ジャケット
から突き抜けるTシャツの袖UVを透明化し、`inner-black-top-v2.png`として保存しました。

VRoid Studioではv2を新規レイヤーとして読み込み、v1レイヤーを非表示にしています。
Tシャツ側の「袖を長くする」は0に設定しています。
