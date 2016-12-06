# 認証系設計

## OAuth 認証について
### サーバー構成
* 1st
  * Implicit Grant Flowのみにし、他アプリケーションのことは考えない
  * 認証認可サーバー、リソースサーバーは１つのサーバーで行う
  * api形式のサーバーとし、Cookie、Session、Viewは保持しない
* 2nd
  * Implicit Grant Flow, Authorization Code Grant Flowで運用
  * 認証認可サーバー、リソースサーバーを分けて運用する
  * リソースサーバーをAPIオンリーにする
  * 認証認可サーバーにはCookie, Session, Viewを所持させる。Web上で一度認証処理を行うと、Cookieが切れない限りほかサイトでは認証をしなくて済むようにするため。

### minreki アプリ
* Implicit Grant Flow
  * Webの場合、ClientIdとOriginで判断し、認証を許可する
  * Web以外の場合、ClientIdと独自パラメータの値で判断し、認証を許可する

### その他アプチ
* Authorization Code Grant Flow
  * ClientIdで判断する

## Devise
* 新規ユーザー作成
* ユーザー認証
* パスワード変更
* 認証メール送信
* 認証コード確認
* ログイン失敗回数
* アカウントロック
* OmniAuthからのユーザー認証、作成

### routes.rb設定
今回は独自のエンドポイントを使用するため、routesの自動生成をすべて削除する

```
devise_for :users, skip: :all
```

### ユーザー認証実装

### authenticate_#{mappings}!の判定実装


## OmniAuth
* Google, Twitter, FacebookのOAuth認証

## DoorKeeper
* OAuth 2.0 Authorization Code Flow の実現
* ClientIDの管理
