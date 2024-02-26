## AR 関連技術のリポジトリ

このリポジトリには、AR.js と model-viewer(Quicklook) を使用した AR プロジェクトが入っています。

### ファイル構成

```
.
├── ar_js/
│   ├── assets/
│   │ 　└── ...（AR.js 用の 3d モデルと QR コードの patt）
│   ├── marker/
│   │ 　└── ...（AR.js 用の QR コードを入れる想定）
│   └── index.html（AR.js 用のコード）
│
└── model_viewer/
    ├── mock/
    │   ├── model/
    │   ├── index.html（コーヒー QuickLook 用のコード）
    │   └── k_index.html（からあげ君 QuickLook 用のコード）
    └── prod_mock/
        ├── fried_rice/
        │   ├── 3d.usdz
        │   ├── 3d.glb
        │   └── index.html
        └── ...（QuickLook などで使う 3D モデルとHTML）

```

### 3D モデルの準備状況

- フリー素材のドリンク （初回モック）
- 通常サイズのからあげ君レギュラー （iPhone スキャンのモック）
- ペペロンチーノ
- ペペロンチーノ 3 倍
- 焼きそば 3 倍
- からあげ君 box
  ※フリー素材のドリンク以外は model-viewer のみの実装となっています。

### model-viewer 使い方

mock フォルダに過去の打ち合わせでお見せした物が入っており prod_mock フォルダにラボでスキャンした製品のソースが入っています。  
prod_mock フォルダにラボでスキャンした製品は製品ごとにフォルダ分けをしてその中にその製品の 3D モデルと HTML が入っています。

1. S3 など静的ホスティングサービスにファイルをアップロードします。
2. ドメイン/model_viewer/prod_mock/fried_rice/index.html とすると唐揚げチャーハンのモックにアクセスができます。

### AR.js 使い方

1. ドメインを確定して'ドメイン/index.html'で QR コードを作成します。
2. 1 で作った画像を元に AR マーカーの画像ファイルと patt ファイルを作成します。([ここなどを利用](https://jeromeetienne.github.io/AR.js/three.js/examples/marker-training/examples/generator.html))
3. 2 で作った patt ファイルをこのリポジトリ内の'assets/marker.patt'と置き換えます
4. S3 など静的ホスティングサービスにファイルをアップロードします。
5. ドメイン/ar_js/index.html にアクセスすると表示されるカメラで AR マーカーを読み取ると３ D モデルが表示されます。
