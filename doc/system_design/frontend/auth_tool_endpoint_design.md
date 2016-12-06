# 認証サーバー Endpoint Design
* ドメイン
  `https://accounts.minreki.com/`

## 認証処理
### 認証コードをURLに埋め込みリダイレクト
`GET /oauth/authorize/:code(.:format) doorkeeper/authorizations#show`
### 認証処理 * APIとして公開
`GET /oauth/authorize(.:format) doorkeeper/authorizations#new`

1. ログインされていない場合は、認証サーバーのログイン画面が表示
1. アプリの認証許可が済んでいない場合は、認証サーバーのアプリ認証許可が画面表示
1. 認証、認可がされている場合は下記のどちらかの処理
  * Authorization Code Grant Flowの場合
    * 設定されているリダイレクトURLにcodeを付与してリダイレクト
  * Implicit Grant Flowの場合
    * 設定されているリダイレクトURLにアクセストークンを付与してリダイレクト

### 認証処理
`POST /oauth/authorize(.:format) doorkeeper/authorizations#create`
* アプリ認証許可画面で認証を押したときの処理。
* Authorization Code Grant Flowの場合
  * 設定されているリダイレクトURLにcodeを付与してリダイレクト
* Implicit Grant Flowの場合
  * 設定されているリダイレクトURLにアクセストークンを付与してリダイレクト

### アプリ認証削除
`DELETE /oauth/authorize(.:format) doorkeeper/authorizations#destroy`
### トークン生成 * APIとして公開
`POST /oauth/token(.:format) doorkeeper/tokens#create`
### トークン破棄 * APIとして公開
`POST /oauth/revoke(.:format) doorkeeper/tokens#revoke`

## 認証アプリ一覧、登録、削除
### 認証アプリ一覧
`GET /oauth/applications(.:format) doorkeeper/applications#index`
### 認証アプリ新規作成画面
`GET /oauth/applications/new(.:format) doorkeeper/applications#new`
### 認証アプリ新規作成
`POST /oauth/applications(.:format) doorkeeper/applications#create`
### 認証アプリ詳細
`GET /oauth/applications/:id(.:format) doorkeeper/applications#show`
### 認証アプリ詳細編集画面
`GET /oauth/applications/:id/edit(.:format) doorkeeper/applications#edit`
### 認証アプリ詳細更新
`PATCH /oauth/applications/:id(.:format) doorkeeper/applications#update`
`PUT /oauth/applications/:id(.:format) doorkeeper/applications#update`
### 認証アプリ削除
`DELETE /oauth/applications/:id(.:format) doorkeeper/applications#destroy`
### 認証済みアプリ一覧
`GET /oauth/authorized_applications(.:format) doorkeeper/authorized_applications#index`
### 認証済みアプリ削除
`DELETE /oauth/authorized_applications/:id(.:format) doorkeeper/authorized_applications#destroy`
### トークン情報取得
`GET /oauth/token/info(.:format) doorkeeper/token_info#show`

## ログイン、ログアウト
### ログイン
`POST /login`
### ログアウト(minrekiアプリのみ使用)
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
