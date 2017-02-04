J-Bobのインストールとlittle-proverを動かす方法(Windows編)
======================================================

2017/2/4 @iitaka1142

# 環境

## OS

Windows 10(64bit)

## Scheme

Racketをインストール。動作確認には同時にインストールされるDrRacketを使用。
ダウンロードはこちら。
https://download.racket-lang.org

# J-BoBの入手

``` shell
> cd <path>/<to>/<work>/<directory>
> git clone https://github.com/the-little-prover/j-bob
```

# 実行

Windows -> Racket -> DrRacket を選択。DrRacketが起動する。

# (オプション: DrRacketの日本語化)

メニュー -> ヘルプ -> DrRacketを日本語で使う を選択

# Schemeの設定

README.md に従い、以下の通り設定

# ソースファイルの変更

DrRacket内でフォルダを移動する方法が不明なため、
スクリプトファイルをロードすることで対応する。

# 実行例
1. j-bob-lang.scmを読み込み、ほかのファイルはREPLからloadする
``` scheme
Welcome to DrRacket, version 6.7 [3m].
Language: R5RS [custom]; memory limit: 128 MB.
```
2. little-prover.scmにloadを追加し、little-prover.scmを読み込む
