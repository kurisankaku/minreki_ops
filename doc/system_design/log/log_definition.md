# Log 定義

## Log Format
### 1st version
* ::Logger::Formatterを使用する

### 2nd version
* [Lograge](https://github.com/roidrage/lograge)を使用する
* fluentdにそのまま送るためにJsonに変換する

## Log保存先
### 1st version
* S3にそのまま保存（日別）

### 2nd version
* fluentd を通して、Mongo DBに保存
* Mongo DB → Elasticsearch へインデックス作成
* Kibanaでグラフ化

## Log 集める元
* Nginx
* Unicorn
* Rails
* MySQL
