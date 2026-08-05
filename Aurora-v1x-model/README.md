# Aurora v1x Model Workspace

`Aurora-v1x-casual-C-layered.png`を基に、Aurora v1xのオリジナル衣装とVRMモデルを
制作するための作業ディレクトリです。

## 目標

- 第三者衣装 `Parker Set EC-Sky` を使用しない
- VRoid Studioの標準メッシュと、ここで制作するオリジナルテクスチャを使用する
- 再利用可能な衣装を `.vroidcustomitem` またはXWearとしてローカル出力する
- Aurora v1xをVRM 1.0形式でローカル出力する

## ディレクトリ

- [`source`](./source)：編集元となる非公開の `.vroid` ファイル
- [`references`](./references)：デザイン資料と実装メモ
- [`textures`](./textures)：Gitで管理するオリジナル衣装テクスチャ
- [`exports`](./exports)：非公開のCustom Item、XWear、VRM出力

## 最初に必要なもの

1. Auroraの編集可能な元モデル `.vroid`
2. 使用しているVRoid Studioのバージョン
3. 衣装をどの程度コンセプト画像へ忠実に再現するか

元モデルは `source/Aurora v1.3 - AnimeStyle.vroid`、制作中の作業コピーは
`source/Aurora-v1x-layered-working.vroid` としてローカルに配置しています。どちらも
`.gitignore` の対象であり、GitHubには公開されません。VRMしか残っていない場合、VRMを
VRoid Studioへ戻して編集することはできないため、元の `.vroid` を探すか、モデルを作り
直す必要があります。

## 現在の実装方針

VRoid Studio 2.14.0で作業コピーを開き、第三者衣装のトップスを保存・複製せずに外しました。
衣装Cのトップスは、VRoid Studio標準メッシュだけで次のように構成します。

- 外側：前開きのロングコート系トップスを、オフホワイトのシャツジャケットとして使用
- 内側：同じカスタムアイテム内に標準トップスを重ね、黒いインナーとして使用
- 首元：内側トップスと必要に応じた肌テクスチャで、黒いモックネックを表現
- 装飾：アイスブルーの袖口とポケット、ボタン、縫い目をオリジナルテクスチャで表現

このモデルの「上半身インナー」プリセットは下着形状のため、モックネック用のメッシュには
使用しません。

## 推奨する制作方法

### 方法A：VRoid Studio内で完結する

今回の衣装では、まずこの方法を推奨します。

1. 元の `.vroid` を複製し、`Aurora-v1x-working.vroid` として開く
2. 既存の第三者衣装をすべて外す
3. トップスを複数テンプレートのレイヤーで構成する
   - 内側：黒いモックネックトップス
   - 外側：オフホワイトのゆったりしたシャツジャケット
   - ポケットとカフス：アイスブルーのテクスチャ
4. ボトムスを黒いパンツまたはショートパンツとラップ風パネルの組み合わせで作る
5. レギンスを無地の黒で作る
6. 靴を黒いレースアップシューズとして塗り直す
7. 各部位をCustom Itemとして保存・ローカル出力する
8. 完成モデルをVRM 1.0で `exports/` に出力する

標準メッシュだけでは、前を完全に開いたシャツ、独立したラップパネル、厚みのあるポケット
などを厳密に再現できない場合があります。その場合は、形状を簡略化してテクスチャと透明化
で表現します。

### 方法B：Blenderなどで専用衣装をモデリングする

コンセプト画像のシルエットを厳密に再現する場合の方法です。衣装をモデリングし、ウェイト、
マテリアル、揺れ物を設定してから、UnityとUniVRMまたはVRoid Studioのドレスアップ機能へ
持ち込みます。品質の自由度は上がりますが、メッシュ制作、リギング、ウェイト調整が必要に
なるため、まず方法Aで試作して不足部分を確認する方が効率的です。

## 出力物

- `textures/`：衣装テクスチャPNG
- `exports/Aurora-v1x-outfit.vroidcustomitem`：VRoidエディター用衣装
- `exports/Aurora-v1x-outfit.xwear`：ドレスアップ機能用衣装
- `exports/Aurora-v1x.vrm`：完成モデル

モデルデータと出力ファイルは公開リポジトリへコミットしないでください。

## 作業チェックリスト

- [x] 元の `.vroid` ファイルを `source/` に配置する
- [x] VRoid Studioのバージョンを記録する（2.14.0）
- [x] トップスに使用する標準衣装テンプレートを決定する
- [ ] シャツジャケットのテクスチャを制作する
- [ ] モックネックトップスのテクスチャを制作する
- [ ] ボトムスとラップパネルのテクスチャを制作する
- [ ] レギンスと靴のテクスチャを制作する
- [ ] VRoid Studio上で継ぎ目、透過、肌マスクを確認する
- [ ] Custom ItemまたはXWearをローカル出力する
- [ ] VRM 1.0をローカル出力し、使用先で表示を確認する

## 公式資料

- [Custom Itemのインポート・エクスポート](https://vroid.pixiv.help/hc/en-us/articles/7467455312409-How-to-import-and-export-custom-items)
- [VRoid Studio衣装をXWearへ変換する方法](https://vroid.pixiv.help/hc/en-us/articles/38729525846809-How-to-convert-costumes-and-accessories-made-in-VRoid-Studio-to-XWear)
- [VRMとして出力する方法](https://vroid.pixiv.help/hc/en-us/articles/38726063278233-How-do-I-export-a-model-as-VRM)
- [VRoid Studioのファイル形式](https://vroid.pixiv.help/hc/en-us/articles/23731198070809-About-file-formats-used-by-VRoid-Studio)
