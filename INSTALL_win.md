J-Bobのインストールとlittle-proverを動かす方法(Windows上のscheme編)
======================================================

2017/2/5 @iitaka1142  新規作成
2017/5/27 @iitaka1142 Chicken Schemeを追加

# 環境

## OS

Windows 10(64bit)

## Scheme

WindowsでR5RSに対応したSchemeの処理系として、RacketとCheckenがあります。
Racketはj-bobの動作が確認されています。しかし、IDEで操作するため最初に覚えることが多く、操作性もよくありません。特に、↑↓キーで履歴を追えないため、j-bobの実行は大変です。
Chicken Schemeはコマンドラインベースなため、コマンドラインに慣れた人にとっては扱いやすいです。欠点としてシンボルの表現が'symbolではなく(quote symbol)になってしまうことです。どちらをインストールしてもj-bobの操作は同じです。

### Racket
Racketをインストール。動作確認には同時にインストールされるDrRacketを使用。

ダウンロードはこちら。

https://download.racket-lang.org

### CHICKEN Scheme
Chocolateyからのインストールを勧めます。

``` shell
choco install chicken
```

## J-Bob

githubからcloneする。gitのインストールは割愛。

``` shell
> cd <path>/<to>/<work>/<directory>
> git clone https://github.com/the-little-prover/j-bob
```

# 実行

## Racketの場合
### IDEの起動

Windows -> Racket -> DrRacket を選択。

DrRacketが起動する。

### (オプション: DrRacketの日本語化)

メニュー -> ヘルプ -> 「DrRacketを日本語で使う」
を選択。※再起動を要求される。

以降の手順は英語のままで説明する。

### 言語設定

README.md に従い、以下の通り設定。

* メニュー -> Language -> Choose Language... を選択。(ショートカット Ctrl+L)
* Other Languages -> R5RS を選択。
* 下にあるボタン"Show Details"を選択。
* "Initial Bindings"と書かれた枠内にある"Disallow redifinition of initial bindings"のチェックを外す。
* "OK"を押す。

### ソースファイルの変更

DrRacket内でフォルダを移動する方法が不明なため、スクリプトファイルをロードすることで対応する。

実行する際にlittle-prover.scmを確認できると都合が良いので、以下のように編集する。

```little-prover.scm
(load "j-bob-lang.scm") ;; 先頭に追加
(load "j-bob.scm")      ;; 次の行に追加
```

### 実行例

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

## CHICKEN Schemeの場合

### Chicken Schemeの起動
J-Bobをダウンロードしたフォルダに移動して、コマンドラインからCHICKEN Schemeを立ち上げます。CHICKEN Schemeのコマンドは`csi`です。

``` shell
> cd <path>\<to>\<j-bob>
> csi
CHICKEN
(c) 2008-2016, The CHICKEN Team
(c) 2000-2007, Felix L. Winkelmann
Version 4.11.0 (rev ce980c4)
windows-mingw32-x86-64 [ 64bit manyargs dload ptables ]
compiled 2016-05-28 on yves.more-magic.net (Linux)

#;1>
```
### 実行例

``` shell
#;1> (load "j-bob-lang.scm")
; loading j-bob-lang.scm ...
#;2> (load "j-bob.scm")
; loading j-bob.scm ...
#;3> (load "little-prover.scm")
; loading little-prover.scm ...
#;4> (chapter1.example1)
(quote ham)
#;5> (print (chapter1.example1))
(quote ham)
#;6> (J-Bob/step (prelude)
        '(car (cons 'ham '(eggs)))
        '(((1) (cons 'ham '(eggs)))))
(car (quote (ham eggs)))
```


# 参考
* [Getting started with 'The Little Prover' - LambdaCat](http://www.lambdacat.com/getting-started-with-the-little-prover/)
* [CHICKEN Scheme](https://www.call-cc.org/)
