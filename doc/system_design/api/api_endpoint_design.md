# API Endpoint Design
* Domain
  `https://api.minreki.com/`

## ログイン、ログアウト
1st
  * APIとして提供するが、minrekiアプリケーション以外は使用できない。

2nd
  * ログイン、ログアウトの機能は認証認可サーバーにすべて移譲
  * ログイン、ログアウトのAPI自体をすべて削除

### ログイン
`POST /login`
### ログアウト
`GET /logout`
### TwitterOAuth認証ログイン
`GET /login/auth/twitter`
### GoogleOAuth認証ログイン
`GET /login/auth/google`
### FacebookOAuth認証ログイン
`GET /login/auth/facebook`

## 連携認証
### Twitter連携OAuth認証
`GET /auth/twitter`
### Facebook連携OAuth認証
`GET /auth/facebook`

## 認証処理
API を外部に提供する際に作成する。(Doorkeeperのものを流用する)

### 認証処理
`GET /oauth/authorize(.:format) doorkeeper/authorizations#new`

1. ログインされていない場合は、認証サーバーのログイン画面が表示
1. アプリの認証許可が済んでいない場合は、認証サーバーのアプリ認証許可が画面表示
1. 認証、認可がされている場合は下記のどちらかの処理
  * Authorization Code Grant Flowの場合
    * 設定されているリダイレクトURLにcodeを付与してリダイレクト
  * Implicit Grant Flowの場合
    * 設定されているリダイレクトURLにアクセストークンを付与してリダイレクト

### トークン生成(Authorization Code Grant Flow利用時)
`POST /oauth/token(.:format) doorkeeper/tokens#create`
### トークン破棄
`POST /oauth/revoke(.:format) doorkeeper/tokens#revoke`

## アカウント
### アカウント新規登録
`POST /accounts`
### アカウント詳細情報取得
`GET /accounts/:id`
### アカウント削除
`DELETE /accounts/:id`
  * パラメータにforce=trueをつけること。でないと間違って削除しそう。。。

### アカウント名変更
`PUT /accounts/:id/name`
### パスワード変更
`PUT /accounts/:id/password`
### メールアドレス変更
`PUT /accounts/:id/email`

## ユーザー
### ユーザー検索
`GET /users`
### プロフィール表示
`GET /users/:id/profile`
### プロフィール登録
`POST /users/:id/profile`
### プロフィール更新
`PUT /users/:id/profile`
### プロフィール画像作成
`POST /users/:id/profile/images`
### プロフィール画像更新
`PUT /users/:id/profile/images/:image_id`
### フォロワー検索
`GET /users/:id/followers`
### フォローユーザー検索
`GET /users/:id/followings`
### フォロー追加
`POST /users/:id/followers/:follower_id`
### フォロー削除
`DELETE /users/:id/followers/:follwer_id`

## 歴史
### 歴史検索
`GET /histories`
### 歴史詳細表示
`GET /histories/:id`
### 歴史作成
`POST /histories`
### 歴史更新
`PUT /histories/:id`
### 歴史削除
`PUT /histories/:id`
### 歴史画像作成
`POST /histories/:id/images`
### 歴史画像更新
`PUT /histories/:id/images/:image_id`
### 歴史画像削除
`DELETE /histories/:id/images/:image_id`
### お気に入り歴史追加
`POST /histories/:id/favorites`
### お気に入り歴史削除
`DELETE /histories/:id/favorites`
### 歴史メンバー取得
`GET /histories/:id/members`
### 歴史メンバー招待
`POST /histories/:id/members`
### 歴史メンバー権限更新
`PUT /histories/:id/members/:member_id`
### 歴史メンバー削除
`DELETE /histories/:id/members/:member_id`

## イベント
### イベント検索
`GET /events`
### イベント詳細表示
`GET /events/:id`
### イベント作成
`POST /events`
### イベント更新
`PUT /events/:id`
### イベント削除
`DELETE /events/:id`
### イベント画像作成
`POST /events/:id/images`
### イベント画像更新
`POST /events/:id/images/:image_id`
### イベント画像削除
`DELETE /events/:id/images/:image_id`
### お気に入りイベント追加
`POST /events/:id/favorites`
### お気に入りイベント削除
`DELETE /events/:id/favorites`
### イベント閲覧履歴取得
`GET /events/browsings`

## イシュー
### イシュー検索
`GET /issues`
### イシュー作成
`POST /issues`
### イシュー更新
`PUT /issues/:issue_id`
### イシュー削除
`DELETE /issues/:issue_id`
### イシューコメント検索
`GET /issues/:issue_id/comments`
### イシューコメント作成
`POST /issues/:issue_id/comments`
### イシューコメント更新
`PUT /issues/:issue_id/comments/:comment_id`
### イシューコメント削除
`DELETE /issues/:issue_id/comments/:comment_id`

## タグ
### タグ検索
`GET /tags`
### タグ作成
`POST /tags`
### タグ更新
`PUT /tags/:id`

## アイテム
### アイテム検索
`GET /items`
### アイテム作成
`POST /items`
### アイテム編集
`PUT /items/:id`
### アイテム削除
`DELETE /items/:id`
