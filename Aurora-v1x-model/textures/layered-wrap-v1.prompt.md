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
