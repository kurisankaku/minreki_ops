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
### ユーザートップ
`/:owner_name`
### 歴史一覧
`/:owner_name/histories`
### フォロワー
`/:owner_name/followers`
### フォローイング
`/:owner_name/followings`

## 歴史
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
