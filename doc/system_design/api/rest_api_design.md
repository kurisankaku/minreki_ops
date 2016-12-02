# REST API設計

## 参考文献
* [REST APIとは？ – API設計のポイント！](http://wp.tech-style.info/archives/683)
* [翻訳: WebAPI 設計のベストプラクティス](http://qiita.com/mserizawa/items/b833e407d89abd21ee72)
* [GoogleのWebAPI設計とWebAPI設計のベストプラクティスを比較してみる](http://qiita.com/howdy39/items/3b2b14ce73ec44c54f7b)
* [Github API v3](https://developer.github.com/v3/) を参考にする。

## 1. Current version
* Headerに指定

`Accept: application/vnd.github.v3+json`

## 2. Schema
```
curl -i https://api.github.com/users/octocat/orgs

HTTP/1.1 200 OK
Server: nginx
Date: Fri, 12 Oct 2012 23:33:14 GMT
Content-Type: application/json; charset=utf-8
Connection: keep-alive
Status: 200 OK
ETag: "a00049ba79152d03380c34652f2cb612"
X-GitHub-Media-Type: github.v3

X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4987
X-RateLimit-Reset: 1350085394

Content-Length: 5
Cache-Control: max-age=0, private, must-revalidate
X-Content-Type-Options: nosniff
```
Blank fields are included as null instead of being omitted.

All timestamps are returned in ISO 8601 format:

`YYYY-MM-DDTHH:MM:SSZ`

## 3. Error Response Format
```error.json
HTTP/1.1 422 Unprocessable Entity
Content-Length: 149

{
  "message": "Validation Failed",
  "errors": [
    {
      "resource": "Issue",
      "field": "title",
      "code": "missing_field"
    }
  ]
}
```
* `message`パラメータは必須。
* `code`はValidation error時に使用。単語を決めておく。

## 4. Status Code
|Number|Code|Description|
|:------|:------|:------|
|200|OK|GET, PUT, PATCH, DELETE リクエストが成功した場合に応答。もしくは、POST リクエストが結果的に何もリソースを作らなかった場合に応答。|
|201|Created|POST リクエストがリソース作成に成功した場合に応答。なお、そのリソースへのリンクを`Location`ヘッダに含める必要がある。|
|204|No Content|成功したDELETE リクエストで、ボディを返したくない場合に応答|
|304|Not Modified|HTTP キャッシュが有効な場合に応答|
|400|Bad Request|パース不可能なリクエストボディが来た場合に応答|
|401|Unauthorized|認証がされていない、もしくは不正なトークンの場合に応答|
|403|Forbidden|認証はされているが、認可されていないリソースへのリクエストに応答|
|404|Not Found|存在しないリソースへのリクエストに応答|
|405|Method Not Allowed|認可されていないメソッドでのリクエストに応答|
|410|Gone|今は存在しないリソース（廃止されたAPIなど）で空要素を返す場合などに応答|
|415|Unsupported Media Type|対応していない MediaType が指定された場合に応答|
|422|Unprocessable Entity|バリデーションエラーに対して応答|
|429|Too Many Requests|回数制限をオーバーしたリクエストに対して応答|
|500|Server Error|サーバー内のエラーに対して応答|

## 5. HTTP Verbs
|Verb|Description|
|:------|:------|
|GET|リソースの取得|
|POST|リソースの作成|
|PUT|リソースの更新|
|DELETE|リソースの削除|

## 6. Pagination
Requests that return multiple items will be paginated to 30 items by default. You can specify further pages with the `?page` parameter. For some resources, you can also set a custom page size up to 100 with the `?per_page` parameter. Note that for technical reasons not all endpoints respect the `?per_page` parameter, see events for example.

`curl 'https://api.github.com/user/repos?page=2&per_page=100'`

## 7. Rate Limiting
For requests using Basic Authentication or OAuth, you can make up to 5,000 requests per hour. For unauthenticated requests, the rate limit allows you to make up to 60 requests per hour. Unauthenticated requests are associated with your IP address, and not the user making requests. Note that the Search API has custom rate limit rules.

You can check the returned HTTP headers of any API request to see your current rate limit status:

|Header Name|Description|
|:------|:------|
|X-RateLimit-Limit|The maximum number of requests that the consumer is permitted to make per hour.|
|X-RateLimit-Remaining|The number of requests remaining in the current rate limit window.|
|X-RateLimit-Reset| The time at which the current rate limit window resets in UTC epoch seconds.|

## 8. Conditional requests
Most responses return an ETag header. Many responses also return a Last-Modified header. You can use the values of these headers to make subsequent requests to those resources using the If-None-Match and If-Modified-Since headers, respectively. If the resource has not changed, the server will return a 304 Not Modified.

Note: Making a conditional request and receiving a 304 response does not count against your Rate Limit, so we encourage you to use it whenever possible.

```
curl -i https://api.github.com/user
HTTP/1.1 200 OK
Cache-Control: private, max-age=60
ETag: "644b5b0155e6404a9cc4bd9d8b1ae730"
Last-Modified: Thu, 05 Jul 2012 15:31:30 GMT
Status: 200 OK
Vary: Accept, Authorization, Cookie

X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4996
X-RateLimit-Reset: 1372700873


curl -i https://api.github.com/user -H 'If-None-Match: "644b5b0155e6404a9cc4bd9d8b1ae730"'
HTTP/1.1 304 Not Modified
Cache-Control: private, max-age=60
ETag: "644b5b0155e6404a9cc4bd9d8b1ae730"
Last-Modified: Thu, 05 Jul 2012 15:31:30 GMT
Status: 304 Not Modified
Vary: Accept, Authorization, Cookie

X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4996
X-RateLimit-Reset: 1372700873


curl -i https://api.github.com/user -H "If-Modified-Since: Thu, 05 Jul 2012 15:31:30 GMT"
HTTP/1.1 304 Not Modified
Cache-Control: private, max-age=60
Last-Modified: Thu, 05 Jul 2012 15:31:30 GMT
Status: 304 Not Modified
Vary: Accept, Authorization, Cookie

X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4996
X-RateLimit-Reset: 1372700873
```
