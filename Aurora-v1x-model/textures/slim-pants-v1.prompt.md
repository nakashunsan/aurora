# Slim Pants v1 — ImageGen Prompt

Aurora v1xの衣装Cで、腰ラップの内側に着る細身パンツを制作した際の記録です。

## Input

- `slim-pants-default-texture.png`：VRoid Studio標準「ズボン（折り目なし）」のテクスチャ
- `slim-pants-uv-guide.png`：同テンプレートのUVガイド
- `Aurora v1x/Aurora-v1x-casual-C-layered.png`：衣装デザイン参照

## Prompt

```text
Use case: precise-object-edit
Asset type: production-ready VRoid Studio slim men's trousers UV texture PNG
Input images: Image 1 is the exact texture edit target and UV layout; Image 2 is the exact UV guide and hard boundary constraint; Image 3 is the outfit design reference only.
Primary request: Repaint Image 1 as Aurora v1x outfit C's modern slim charcoal-black technical trousers for a boy. Preserve the exact square canvas, front/back leg islands, waistband, belt, buckle, alignment, UV seams, silhouette, and all panel boundaries.
Design: matte near-black stretch twill, clean tapered silhouette, subtle natural folds at hips, knees and ankles, understated reinforced side seams, low-contrast belt and gunmetal buckle, tiny cool-teal piping only along the outer ankle hems. The waist wrap remains the visual focus, so keep the pants restrained and minimal.
Color palette: near-black #15171A, charcoal #22252A, seam gray #34383E, gunmetal #555B61, muted teal #339CA4 only as a very thin ankle accent.
Constraints: paint only inside the existing opaque trousers and belt UV islands; preserve exact geometry and front/back placement; seamless across mirrored panels; no cargo pockets, logos, text, watermark, character, body, mockup, background scene, labels, or third-party texture influence. Output only the flat 2D UV texture.
```

## Post-processing

ImageGenの1254×1254出力を`slim-pants-imagegen-source.png`として保存しました。
1024×1024へリサイズし、黒い背景だけを輝度に基づいて透明化した採用版が
`slim-pants-v1.png`です。

## VRoid Studio

腰ラップのカスタムボトムへ標準「ズボン（折り目なし）」テンプレートを追加し、
`slim-pants-v1.png`を新規レイヤーとして読み込みました。標準画像レイヤーは非表示にし、
腰ラップとパンツを同じボトムアイテムへ統合しています。
