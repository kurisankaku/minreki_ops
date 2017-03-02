# フロントエンドURL Endpoint Design
* ドメイン
  `https://minreki.com/`

## トップ
`/`

## ログイン
`/login`

## 新規登録
### ユーザー登録
`/signup`
### メール認証
`/signup/confirm_email`

## 設定
### プロフィール
`/settings/profile`
### アカウント
`/settings/account`
### Email
`/settings/email`

## ユーザー
### ユーザー一覧紹介トップ
`/users`
### おすすめユーザー一覧
`/users/recommended`
### 人気ユーザー一覧
`/users/popularity`
### 人気ユーザー日本一覧
`/users/popularity/country/jp`

### ユーザートップ
`/:owner_name`
### 歴史一覧
`/:owner_name/histories`
### フォロワー
`/:owner_name/followers`
### フォローイング
`/:owner_name/followings`

## 歴史
### 歴史一覧トップ
`/histories`
### おすすめ歴史一覧
`/histories/recommended`
### 人気歴史一覧
`/histories/popularity`
### 人気スポーツ歴史一覧
`/histories/popularity/sports`
### イベント一覧トップ
`/histories/events/`
### おすすめイベント一覧
`/histories/events/recommended`
### 人気イベント一覧
`/histories/events/popularity`
### 人気スポーツイベント一覧
`/histories/events/popularity/sports`

### 歴史新規作成
`/:owner_name/histories/new`
### 歴史詳細
`/:owner_name/:history_code`
### 歴史編集
`/:owner_name/:history_code/edit`
### 歴史設定
`/:owner_name/:history_code/settings`
### イベント新規作成
`/:owner_name/:history_code/events/new`
### イベント
`/:owner_name/:history_code/events/:event_code`
### イベント編集
`/:owner_name/:history_code/events/:event_code/edit`
### イベント設定
`/:owner_name/:history_code/events/:event_code/settings`
### メンバー一覧
`/:owner_name/:history_code/members`

## 検索
`/search`
  * `q`に全文検索
  * `type`にタイプ指定検索

Githubを参考にする。
