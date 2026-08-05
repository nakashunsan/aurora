# Original Textures

Aurora v1x用に制作するオリジナル衣装テクスチャを保存します。

## 衣装C・外シャツ初稿

VRoid Studio 2.14.0の標準「パーカー」メッシュを、前開きのカジュアルジャケットとして
使用しています。第三者衣装のテクスチャは使用していません。

- `hoodie-uv-guide.png`：VRoid Studioから書き出した2048×2048のUVガイド
- `hoodie-default-texture.png`：VRoid Studio標準テクスチャの作業用書き出し
- `outer-shirt-jacket-imagegen-source.png`：ImageGenが生成した1280×1280の元画像
- `outer-shirt-jacket-alpha-1280.png`：黒背景を透明化した中間画像
- `outer-shirt-jacket-v1.png`：VRoidへ読み込む2048×2048の採用テクスチャ
- `outer-shirt-jacket-v1.prompt.md`：生成プロンプトと後処理手順

`outer-shirt-jacket-v1.png`は作業モデルへ読み込み、袖口、ポケット、前合わせ、ボタンの
UV位置を確認済みです。

## 衣装C・黒インナー初稿

VRoid Studio 2.14.0の標準「Tシャツ」メッシュ用に、チャコールブラックのインナーを
制作しました。パーカーのカスタムトップスへTシャツテンプレートを追加し、1つの
トップスアイテムとして同時着用できる状態まで確認済みです。

- `inner-tshirt-uv-guide.png`：VRoid Studioから書き出した1024×2048のUVガイド
- `inner-tshirt-default-texture.png`：標準Tシャツの作業用書き出し
- `inner-black-top-imagegen-reference.png`：ImageGenが生成した参照画像
- `inner-black-top-v1.png`：VRoidへ読み込む1024×2048の採用テクスチャ
- `inner-black-top-v2.png`：背景を正しく透過し、ジャケットから出る袖領域を除いた統合用テクスチャ
- `inner-black-top-v1.prompt.md`：生成プロンプト、後処理、読み込み手順

統合トップスでは`inner-black-top-v2.png`を使用します。Tシャツの袖長を0に設定し、
袖UVを透明化することで、肩付近でジャケットより外へ出ていた黒い部分を解消しました。

## 衣装C・非対称腰レイヤー初稿

VRoid Studio 2.14.0の標準「ペンシルスカート（五分丈）」を型紙にして、男性向けの
ストリートウェアとして見えるラップパネルを制作しました。黒い斜めの外布、水色の
内布、右腰の小さなDリングで衣装Cの腰まわりを再現しています。

- `layered-pencil-skirt-default-texture.png`：標準型紙の作業用書き出し
- `layered-pencil-skirt-uv-guide.png`：標準型紙のUVガイド
- `layered-wrap-imagegen-source.png`：ImageGenが生成した1254×1254の元画像
- `layered-wrap-v1.png`：VRoidへ読み込む1024×1024の採用テクスチャ
- `layered-wrap-v1.prompt.md`：生成プロンプト、後処理、読み込み手順

`layered-wrap-v1.png`はボトム単体のカスタムアイテムとして作業モデルへ保存済みです。

## 衣装C・細身パンツ初稿

VRoid Studio 2.14.0の標準「ズボン（折り目なし）」を型紙にして、チャコールブラックの
細身テクニカルパンツを制作しました。腰ラップを主役にするため装飾は抑え、布の皺、
縫い目、ガンメタルのバックル、足首の細い青緑ラインだけを加えています。

- `slim-pants-default-texture.png`：標準型紙の作業用書き出し
- `slim-pants-uv-guide.png`：標準型紙のUVガイド
- `slim-pants-imagegen-source.png`：ImageGenが生成した1254×1254の元画像
- `slim-pants-v1.png`：VRoidへ読み込む1024×1024の採用テクスチャ
- `slim-pants-v1.prompt.md`：生成プロンプト、後処理、読み込み手順

`slim-pants-v1.png`は腰ラップのカスタムボトムへ追加し、1つのボトムアイテムとして
同時着用できる状態にしています。

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
