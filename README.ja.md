# Las2Mesh

点群(.las形式)ファイルを3Dモデルに変換するツールです。出力形式は.ply、.stl、.obj、.off、.gltf、.glbに対応しています。

## デモ
![伊豆急下田駅周辺(-d 11オプションを指定)](material/izukyushimoda_d11.png)
[G空間情報センター 静岡県　富士山南東部・伊豆東部　点群データLPデータ](https://www.geospatial.jp/ckan/dataset/shizuoka-2019-pointcloud/resource/d5e98a7b-f15c-45b0-bf40-0287f5b1de68)の.lasファイルを用いて作成（ライセンス: [クリエイティブ・コモンズ 表示](http://opendefinition.org/licenses/cc-by/)）

## 機能
- .lasファイルから頂点カラー付きの3Dモデルを出力
- .ply、.stl、.obj、.off、.gltf、.glbの各形式に対応
- 複数の.lasファイルを一度に変換可能

## 必要環境
- Python 3.7以降
- Open3D、laspy、pygltflibのインストール

## 使い方
las2mesh.exeに点群ファイル(.las)をドラッグ&ドロップしてください。複数ファイルをまとめてドロップすると1つの3Dモデルとして出力されます。デフォルトのファイル名は output.ply です。

詳細なオプション:
```
usage: las2mesh.py [-h] [-d DEPTH] [-o OUTPUT] [-n] [files ...]

.lasファイルからメッシュを生成します

positional arguments:
  files                 対象の .lasファイル。複数指定できます。

optional arguments:
  -h, --help            show this help message and exit
  -d DEPTH, --depth DEPTH
                        メッシュの細かさを整数で指定します。デフォルト値は 10 です。
  -o OUTPUT, --output OUTPUT
                        出力ファイル名を指定します。デフォルト値は output.ply です。
  -n, --nopreview       3Dプレビュー表示を無効にします
```

## ライセンス
Apache License 2.0