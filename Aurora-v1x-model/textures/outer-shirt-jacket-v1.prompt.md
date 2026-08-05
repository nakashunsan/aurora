# Aurora v1x Outer Shirt Jacket v1 Prompt

Built-in ImageGenの画像編集モードを使用しました。

## 入力画像

1. `hoodie-default-texture.png`：編集対象とアルファ・UV配置の基準
2. `hoodie-uv-guide.png`：UV境界の制約
3. `../../Aurora v1x/Aurora-v1x-casual-C-layered.png`：デザインと配色の参照

## Prompt

```text
Use case: precise-object-edit
Asset type: production-ready VRoid Studio clothing texture PNG for the standard hoodie/jacket UV template
Input images: Image 1 is the exact edit target and alpha/UV layout; Image 2 is the exact UV guide and hard panel-boundary constraint; Image 3 is the outfit design and palette reference only.
Primary request: Repaint Image 1 into Aurora v1x casual layered outfit C while preserving the exact canvas, UV islands, transparency, alignment, seams, silhouette, and panel boundaries of Image 1. The result must remain a flat 2D UV texture, not a garment mockup or character illustration.
Design: off-white modern casual overshirt/jacket fabric; pale ice-blue cuffs and two pale ice-blue front patch-pocket accents; restrained cool-gray seams and subtle fabric folds; small matte silver button-like details along the front edges where technically appropriate; hood panel in very pale ice blue to harmonize with the cuffs. Keep the interior/front opening transparent exactly where Image 1 is transparent.
Color palette: warm off-white #F4F2EC, pale ice blue #B9D9E8, muted teal #339CA4 used only as tiny accent stitching, cool charcoal #292B2E only for sparse seam detail.
Constraints: preserve exact square UV topology and every UV island position from Image 1; paint only inside existing opaque garment islands; preserve alpha outside the islands; no changes to island geometry; seamless across mirrored panels; no labels, text, logos, watermark, character, body, background, presentation board, or 3D render. Do not copy or imitate any third-party clothing texture. Create fully original surface decoration based only on the high-level design reference.
```

## 後処理

1. 黒背景をImageGenスキルの `remove_chroma_key.py` で透明化
2. 1280×1280から2048×2048へ拡大
3. VRoid Studioの新規レイヤーへ読み込み
4. 3D表示で袖口、ポケット、ボタン、前合わせを確認

## レイヤー整理

作業モデルのトップスを再確認し、標準「パーカー」のデフォルト画像が非表示であることを
確認しました。あわせて、自作ジャケットの下に残っていた空の`レイヤー1`を削除し、
パーカー側は採用テクスチャの`Layer`と非表示の`デフォルト画像`だけに整理しています。
統合トップスのカスタムアイテムを上書きし、作業モデルへ保存済みです。
