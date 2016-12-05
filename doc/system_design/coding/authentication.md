# 認証系設計

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
