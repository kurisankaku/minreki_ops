# ファイルパス仕様

## 本番と開発による変更
1. 本番環境：S3 ローカル：プロジェクトpublic/upload/images以下

## ファイルパス
* AWS S3 の最適化に従ってパス名を決定。
[リクエスト率およびリクエストパフォーマンスに関する留意事項](http://docs.aws.amazon.com/ja_jp/AmazonS3/latest/dev/request-rate-perf-considerations.html)

## ファイル名
* ランダムな16進数の32文字の文字列

## ファイルパスのプレフィックス決定方法
* ランダムな16進数の4文字をプレフィックスとして毎回生成。

## 複数サイズ
1. 複数サイズを作っておき、画像名_60x60.pngのようにする

## プロフィール
* サイズ
  * 複数
* パス
  * /prefix-profile/avator/

## プロフィール背景
* サイズ
  * 複数
* パス
  * /prefix-profile/background

## 歴史画像
* サイズ
  * 複数
* パス
  * /prefix-history/歴史名/

## 史実画像
* サイズ
  * 複数
* パス
  * /prefix-history/歴史名/史実名
