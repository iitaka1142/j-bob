J-Bobのインストールとlittle-proverを動かす方法(Windows上のscheme編)
======================================================

2017/2/5 @iitaka1142

# 環境

## OS

Windows 10(64bit)

## Scheme

Racketをインストール。動作確認には同時にインストールされるDrRacketを使用。

ダウンロードはこちら。

https://download.racket-lang.org

## J-BoB

githubからcloneする。gitのインストールは割愛。

``` shell
> cd <path>/<to>/<work>/<directory>
> git clone https://github.com/the-little-prover/j-bob
```

# 実行

## IDEの起動

Windows -> Racket -> DrRacket を選択。

DrRacketが起動する。

## (オプション: DrRacketの日本語化)

メニュー -> ヘルプ -> 「DrRacketを日本語で使う」
を選択。※再起動を要求される。

以降の手順は英語のままで説明する。

## 言語設定

README.md に従い、以下の通り設定。

* メニュー -> Language -> Choose Language... を選択。(ショートカット Ctrl+L)
* Other Languages -> R5RS を選択。
* 下にあるボタン"Show Details"を選択。
* "Initial Bindings"と書かれた枠内にある"Disallow redifinition of initial bindings"のチェックを外す。
* "OK"を押す。

# 実行

## ソースファイルの変更

DrRacket内でフォルダを移動する方法が不明なため、スクリプトファイルをロードすることで対応する。

実行する際にlittle-prover.scmを確認できると都合が良いので、以下のように編集する。

```little-prover.scm
(load "j-bob-lang.scm") ;; 先頭に追加
(load "j-bob.scm")      ;; 次の行に追加
```

## スクリプトファイルのロード

* メニュー -> File -> Open...を選択。 (ショートカット Ctrl+O)
* little-prover.scmを選択して開く。
* DrRacketの左下にある"Determin language from source"を"RSR5 Custom"へ変更。
* DrRacket右上の"Run"ボタンを押す。
* 以下の画面が出れば成功。

```shell
Welcome to DrRacket, version <ここは実際のバージョン> [3m].
Language: R5RS [custom]; memory limit: 128 MB.
> 
```

## 実行例

``` shell
Welcome to DrRacket, version 6.7 [3m].
Language: R5RS [custom]; memory limit: 128 MB.
> (chapter1.example1)
'ham
> (J-Bob/step (prelude)
    '(car (cons 'ham '(eggs)))
    '(((1) (cons 'ham '(eggs)))))
(car '(ham eggs))
```

# 参考
* [Getting started with 'The Little Prover' - LambdaCat](http://www.lambdacat.com/getting-started-with-the-little-prover/)
