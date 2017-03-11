# Error 定義

## 参考資料
* [RailsでAPIをつくるときのエラー処理](http://qiita.com/r7kamura/items/2e88adbdd1782277b2e7)
* [Railsの404,500エラーページをカスタマイズ](http://qiita.com/mr-myself/items/c2f4fb2e5dcee6a336f3#comment-23298b703d75b7d27487)
* [Railsの ActionController::RoutingError は ApplicationController での rescue_from で捕まえられない](http://qiita.com/gaaamii/items/183a9a3091a1751d833a#_reference-f265dd7981a1fd64ae90)
* [Rails と Rack](http://railsguides.jp/rails_on_rack.html)
* [Ruby の Require と ActiveSupportの自動requireについて](http://morizyun.github.io/blog/ruby-require-active_support-load/)

## 例外のキャッチをする場所
### RailsのApi内のエラー
* API層でエラーをキャッチする。

### RailsのApi外のエラー
* ErrorControllerを作成し、configで指定。

## ユーザーへのレスポンス
* 指定したFormatでLogを出力する。
* Status Codeは加工せずにユーザーへ返す。

## Error Response Format
```error.json
HTTP/1.1 422 Unprocessable Entity
Content-Length: 149

{
  "message": "Validation Failed",
  "code": "validation_error",
  "errors":
    {
      "field_name": ["not_blank", "not_number"],
    }
}
```
* `message`パラメータは必須。
* `errors: { field_name: }`field_nameは、errorsで一意であり、エラーによって挿入される文字列が異なる。挿入する文字列はエラーの種類によって決めること。
