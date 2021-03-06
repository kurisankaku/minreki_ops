# 仕様書

## 環境構築

1. rails_apiプロジェクトの作成
1. annotate gemの導入
1. rubcopの導入
1. yardの導入

## API Format
1. API設計
1. APIのベースを作成
1. APIのテンプレートエンジンの導入

## 認証（バックエンド）
1. 新規ユーザー作成
1. メールアドレス認証
1. ユーザー認証
1. アクセストークンの付与
1. 認証必須ページへのアクセス制限
1. ユーザーログアウト（アクセストークンの削除、無効化）
1. リフレッシュトークンを使用してアクセストークンの再取得
1. ユーザーのパスワード変更
1. ユーザーの削除
1. Googleアカウント認証
1. Twitterアカウント認証
1. Facebook認証
1. アプリのclient id の作成
1. アプリのredirect url設定
1. アプリの削除

## エラー処理
1. 400番台のエラー処理方法決定
1. 500番台のエラー処理方法決定
1. エラー処理の実装
  * 想定外の500番台のエラーの処理
  * 想定する500番台のエラー処理
  * 想定する400番台のエラー処理

## ログ
1. 想定外エラーのログ
1. アクセスログ
1. アプリケーションログ（Debug, ...., Error)

## フロントプロジェクト作成
1. reactプロジェクトの作成
1. cssテンプレートの導入

## 認証（フロント）
1. ログイン画面表示作成（htmlのみ)
  * ID, PASSの入力ボックス
  * ログインボタン
  * 新規登録リンク
1. 新規登録画面作成
  * 新規ユーザー登録に必要なHTML
  * 登録ボタンを押下後のAPI処理
  * エラー表示処理
1. ログイン画面処理作成
  * ログインボタンを押下後のAPI処理
  * エラー表示処理
1. ログイン画面 OAuth処理
  * Googleログイン
  * Twitterログイン
  * Facebookログイン
1. 新規登録画面 OAuth処理
  * Google
  * Twitter
  * Facebook
1. 認証後のダミーページ作成
  * 有効なアクセストークンを所持していない場合表示不可
  * ログアウトボタンのみ表示
1. ログアウトボタン押下後のAPI処理

## プロフィール
1. プロフィール画像アップロード
  * ローカルのアップロード先フォルダを決定する
  * 画像の命名規則を決定する
  * Rubyでの単純実装をしてみる
  * CarrierWaveの使用に置き換える
  * プロフィール画像のアップロード保存は、単品で行うようにする。他と組み合わせての保存はしない。
  * Google, Facebook, Twitterからの場合は、プロフィール画像を自動保存しておき、新規画像アップロードフローはスキップする。
  * 画像アップのサイズ制限
  * 画像の加工
  * 画像の複数バージョン
1. プロフィール新規作成
  * ユーザー名
  * 生年月日
    * 公開、非公開、相互フォロー時のみ、フォロワー以上(デフォルトは非公開）
  * 紹介文
  * ロケーション
    * ロケーションは予測変換できるようにする
    * 緯度経度の保存もできるようにする
    * GoogleAPIの使用ができるか検証
    * 国（選択式）自由入力不可
    * 州/区/市
    * 番地/建物
  * ウェブサイト
  * Twitter
  * Facebook
  * Google+
1. プロフィール画像更新
1. プロフィール背景画像更新
1. プロフィール内容更新

## フォロー
1. 相手をフォローする
  * 相手のユーザー名(アカウント名)を元にFind、フォローする
1. フォロワー一覧
1. フォロー一覧
1. フォローを解除する
  * 相手のユーザー名（アカウント名）を元にFind、フォローを解除する

## タグ
1. タグ作成
1. タグ更新
1. タグ削除
1. タグ検索

## アイテムテンプレート
1. アイテムテンプレート作成
1. アイテムテンプレート新規追加
1. アイテムテンプレート更新
1. アイテムテンプレート削除

## 歴史作成
1. 歴史作成
  * タイトル
  * タイトルID(英数字(a_z0_9,-_)) ユニーク
    * 自由記述
  * カテゴリー
  * アイテムテンプレート
  * タグ
  * 説明(Markdown)
  * 公開、非公開、フォロワーのみ公開、メンバーのみ公開
1. 歴史の一覧表示
1. 歴史プロフィール画像アップロード
1. 歴史更新
1. 歴史削除
  * 歴史に史実が関連づいている場合は、史実を削除した後に削除可能。
1. 歴史更新権限（オーナーのみ）
1. 歴史削除権限（オーナーのみ）

## 史実作成
1. 史実作成
  * 歴史IDから歴史と関連付け
  * タイトル
  * タイトルID(英数字(a_z0_9,-_)) ユニーク
    * 自由記述
  * 日付(From)
  * 日付(To) 任意
  * カテゴリー
  * アイテムテンプレート
  * タグ
  * 詳細
    * マークダウン形式
    * 画像差し込み可能
1. 史実の一覧表示
1. 史実の歴史移動
1. 史実の更新
1. 史実の削除
1. 史実更新権限（オーナーのみ）
1. 史実削除権限（オーナーのみ）

## 史実からの歴史情報表示
1. 史実数の表示
1. 期間の表示
  * 最古の史実日時〜最新の史実日時

## お気に入り
1. 歴史のお気に入り登録
1. 歴史のお気に入り一覧
1. 歴史のお気に入り削除
1. 史実のお気に入り登録
1. 史実のお気に入り一覧
1. 史実のお気に入り削除

## 被関連歴史の表示
1. 被関連歴史数の表示
1. 被関連歴史のタイトルを2本表示
  * お気に入り数の高いものを表示
  * その他は別ページとしてリンク表示（もっと見る）

## 被関連史実の表示
1. 被関連史実数の表示
1. 被関連史実のタイトルを2本表示
  * お気に入り数の高いものを表示
  * その他は別ページとしてリンク表示（もっと見る）

## マイ歴史
1. 他のユーザーの史実を自分の歴史に追加
1. 追加した歴史の削除
1. 持ち主に削除された場合は、この歴史は削除されましたという表示を出す。

## メンバー
1. メンバー新規追加
  * 追加するさいは、メンバーに認証メールが飛ぶ
1. メンバー一覧
1. メンバー追加、削除権限
1. メンバーへの権限付与
  * 歴史更新権限
  * 史実更新権限
  * 史実削除権限
  * メンバー追加権限
1. メンバーへのオーナー譲渡機能

## Issue投稿
1. 歴史へのIssue投稿ができる
  * タイトル
  * 対象史実(任意)
    * タイトル検索、ID検索で指定
  * Issueジャンル
    * 削除依頼
    * 修正依頼
    * 追加依頼
    * 違反依頼
  * 説明
1. 歴史のIssue一覧を表示できる
1. Issue内容を変更できる(作者、メンバー、オーナー)
1. Issueを破棄できる(作者、メンバー、オーナー）
1. Issueを再オープンできる(メンバー、オーナー)
1. Issueに対してコメントを書き込める
1. Issueに対してコメントを更新できる
1. Issueのコメントを削除できる
1. Issueを未対応、保留、対応中、対応済み、非対応にステータスを変更できる
1. Issueを作成、コメントをするユーザーをブロックできる

## ホーム
1. マイ歴史一覧が3つ表示されている
1. 表示する歴史を選択できる、保存できる
1. 表示する歴史を削除できる
1. 表示する歴史の順番を変更できる

## 歴史,史実検索
1. 歴史,史実を検索できる
  * フリーワード検索
  * カテゴリー検索
1. 表示順を変更できる
  * 人気歴史順
  * A-Z, Z-A順
  * 年月日順

## ユーザー検索
1. ユーザーをプロフィール名、アカウント名で検索できる

## AWS S3との連携
1. ファイルアップロード先をS3に変更
1. プライベート歴史の場合は画像ドメインとパスが変更される
  * S3のバケットで、Railsサーバーからしかアクセス出来ないようにIP制限をかけるものをつくる。
  * パブリック⇔プライベートのバケット移動を行うようにする。
    * この移動を行っているとき、すべての移動が完了した際に、古い方のものを削除する
  * プライベート画像はRailsを通り、認証をし、NginxからS3へと処理が進む。
  * X-Accel-Redirectを使用し、NginxとS3で処理するように変更
  * ファイルダウンロードをする前に認証をはさむように変更
  * 速度を計測(認証まわりの速度とNginxを1回挟むところが気になる)
  * ファイルをダウンロードする際の認証を下記で検討してみる
    * Redisに下記フォーマットで情報を保存
      * Key:ファイル名（ランダムに生成したもの） Value: private or pulic,保存先パス,共有レベル,owner id,team id,追加ユーザーidをスペース区切りで

## UI作成
1. 順次UI作成していく。頑張れ！！！ここが一番たいへん！！！

## 広告表示
1. Google Adの表示

## 課金組み込み
1. プライベートプロジェクトは1つまで。それ以上は課金。
1. 課金のサイト選定
1. 課金のサイトを組み込み（テスト稼働まで）

## セキュリティー向上
1. 現在ログインしている端末の一覧表示
1. ログイン端末のセッションを削除できる
  * ログインしているセッションのIDを保持するように修正。アクセストークンの場合は、アクセストークン。
1. 知らない端末からのログインの場合は、メールによる二段階認証のログインに変更
1. 既知のログイン端末一覧から、指定端末を削除できる。これにより削除した端末でログインする際は二段階認証が発生。
1. メールでの認証も、リンクによるものではなく、認証コードの直接入力とCookieのセッション情報による照合に変更。
1. 認証コードの入力ミスも3回までに設定し、それ以降は再ログインさせる
  * なので、認証コードは打ちやすい8桁の数値に変更
  * 入力ミス3 * 2 = 6 回ミスをしたらアカウントを1時間ロックする
1. 秘密の質問は導入すべきか。。。最初は導入しない方向で行きましょ。
1. 秘密の質問を導入するのなら、初期のメールアドレス情報とユーザー名は保存しておく。

## エラーページ
1. 404のエラーページ最適化
1. 500のエラーページ最適化

## お問い合わせページ
1. お問い合わせメールの設定
  * お問い合わせフォーマットを載せておく（タイトル、説明の書き方）
1. プライバシーポリシーの表示
1. 著作権の表示
1. 運営団体の表示
1. 広告、営業の問い合わせ場所の表示

## データの打ち込み
1. 歴史、史実データの打ち込み
1. csvとして取り込むツールを作成し、打ち込み

## サーバー構築
1. Unicorn + nginx構築
1. nginxのログ管理方針決定
1. unicornのログ管理方針決定
1. logrotateによるログの設定
1. fluentd利用してのログ集約
1. fluentd利用してのS3へのログの定期送信
1. SMTPサーバーの設定
1. AWSの設定
1. workerのモニタリング
1. Newrelicの設定
1. DBバックアップの設定
1. ドメイン設定

## リリース
1. データを本番DBに反映
1. 課金サイトの本番適用
1. デプロイ

## 周知
1. ブログに周知
1. サイトの制作の流れをブログに書き込み
1. 1ヶ月たって、うん大丈夫！行ける！って思ったらFacebookとTwitterに周知
1. プレスリリースも検討

## スマホアプリ

### OAuth
1. Doorkeeperを導入
1. アクセストークンまたはCookieを使用し、API利用。
  * Cookieは、PCアクセスのみ。SecureにしていればWebViewから取得もできない（Googleで調べても見つからなかったから検証は必要）
