# Layered Wrap v1 — ImageGen Prompt

Aurora v1xの衣装Cで、腰に重ねる非対称ラップパネルを制作した際の記録です。

## Input

- `layered-pencil-skirt-default-texture.png`：VRoid Studio標準「ペンシルスカート（五分丈）」のテクスチャ
- `layered-pencil-skirt-uv-guide.png`：同テンプレートのUVガイド
- `Aurora v1x/Aurora-v1x-casual-C-layered.png`：衣装デザイン参照

## Prompt

```text
Use case: precise-object-edit
Asset type: production-ready VRoid Studio pencil skirt (five-part) UV clothing texture PNG
Input images: Image 1 is the exact texture edit target and canvas layout; Image 2 is the exact UV guide and hard boundary reference; Image 3 is the outfit design reference only.
Primary request: Repaint the edit target as Aurora v1x outfit C's masculine modern asymmetric waist-layer garment: a charcoal-black wrap panel with an angled overlapping front hem, plus a cool pale-cyan inner panel visible through the overlap. It must read as a streetwear waist wrap or layered long-shirt panel, not a feminine skirt.
Design details: matte charcoal technical fabric, subtle vertical weave and folds, narrow black waistband, restrained seam lines, one small gunmetal D-ring near the right-front waist, cyan inner panel with a very soft top-to-bottom gradient from muted teal to pale sky blue.
Color palette: near-black #17191C, charcoal #25282D, muted teal #339CA4, pale sky #A9D6E5, gunmetal #555B61.
UV constraints: preserve the exact 1024x1024 square canvas, existing UV placement, panel continuity, alignment, and silhouette. Keep all decoration away from UV seams. The upper usable garment rectangle must remain aligned exactly; create the asymmetry using transparency/negative space in the lower hem and overlap area. Preserve a clean waistband around the top.
Output: only a flat 2D UV texture, front/back/side panels continuous and seamless, no character, no 3D model, no mockup, no labels, no text, no watermark, no background scene, no third-party texture influence.
```

## Post-processing

ImageGenの1254×1254出力を`layered-wrap-imagegen-source.png`として保存しました。
デザイン領域を標準UVの衣服領域へ再配置し、1024×1024へ整形した透過PNGが
`layered-wrap-v1.png`です。上端の折り返し用UVにはチャコール色を設定しています。

## VRoid Studio

標準「ペンシルスカート（五分丈）」へ`layered-wrap-v1.png`を新規レイヤーとして
読み込み、標準画像レイヤーを非表示にしました。ボトム単体のカスタムアイテムとして
保存済みです。

## Shortened lower layer: v2

全身表示では腰ラップが太ももまで長く残り、細身パンツとの境界が重く見えたため、
`layered-wrap-v2.png`を作成しました。y=570までは元のアルファを維持し、y=570〜595を
25pxでフェードアウトして、それより下を透明化しています。

VRoid Studio側ではスカートの長さを26.25へ抑え、旧v1レイヤーを削除しました。黒い
斜めラップと水色の三角アクセントをヒップ下で止め、パンツが独立して見える状態です。

## Cyan diagonal correction: v3 / v4

全身表示で水色パネルの斜め境界がギザギザに見えたため、次のプロンプトで境界を再生成しました。

```text
Use case: precise-object-edit
Asset type: production-ready VRoid Studio asymmetric waist-wrap UV texture PNG.

Image 1 is the exact edit target and must define the canvas, UV alignment, transparency, garment silhouette, waistband, black wrap fabric, shortened lower hem, D-ring, and all unchanged details. Image 2 is the exact UV guide and a hard alignment constraint. Image 3 is the outfit design reference only.

Primary request: change only the visible cyan inset panel and its boundary beneath the black overlapping wrap. Redraw the cyan panel so its exposed upper boundary is one clean, continuous, elegant diagonal curve from lower-left toward upper-right, with strong antialiasing and no stair-stepping, zigzags, notches, sawtooth edge, pixelation, or broken segments. Keep the cyan area a restrained pale-sky-to-muted-teal fabric panel. Preserve the shortened v2 lower edge.

Keep absolutely unchanged: exact 1024x1024 UV layout, black fabric, waistband, D-ring and hanging strap, seams, folds, palette, canvas placement, transparency outside the garment, and every non-cyan region. Do not enlarge or lengthen the garment. Do not add objects, text, logos, patterns, body, model, mockup, background, or watermark. Output only the flat UV texture PNG.
```

- `layered-wrap-v3-imagegen-source.png`：ImageGenの1254×1254出力
- `layered-wrap-v3.png`：生成結果を1024×1024の既存UV位置へ再配置した比較版
- `layered-wrap-v4.png`：透明な水平カットを廃止し、v1の連続したアルファへ戻した採用ベース

v2の水平アルファカットはVRoidの三角ポリゴンを途中で横切り、裾に段差を作るため採用を終了しました。
作業モデルではv4を使用し、丈はテクスチャの透明化ではなく「スカートの長さ」35.00で調整しています。
最後にVRoid Studioの3Dペイントで、水色と黒の境界に残るUV継ぎ目の先端だけを
`#A8D9E9`、ブラシ幅20でなぞって馴染ませました。
