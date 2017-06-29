# SchemaSpy for mysql

[http://schemaspy.org/](SchemaSpy)

I output the table definition of the MySQL database using SchemaSpy and provide the environment identifying the table definition that SchemaSpy output from a browser.

SchemaSpyを使ってMySQLデータベースのテーブル定義を出力し、SchemaSpyが出力したテーブル定義をブラウザから確認する環境を提供します。

## Description

It was SchemaSpy where update had settled on, but update was reopened in a nice thing by a volunteer.

Because it was a good opportunity, I performed the table definition output of MySQL in SchemaSpy and decided to provide the environment that could easily confirm the definition book that I output from a browser.

Preparations for structure reading trouble to prepare for Graphviz environment in preparations and Alpine linux of the JDBC driver and the table definition that I output can omit troublesome work.

更新が止まってしまったSchemaSpyですが、嬉しい事に有志によって更新が再開されました。

いい機会なので、MySQLのテーブル定義出力をSchemaSpyで行い、出力した定義書をブラウザから簡単に確認できる環境を提供する事にしました。

JDBCドライバの準備や、Alpine linuxにGraphviz環境を準備する手間や、出力したテーブル定義を閲覧する仕組みの準備等、面倒な作業を省く事ができます。

## Features

- SchemaSpy v6.0
- MySQL-server(any version)
- Dcoker v17
- docker-compose v1.14
- alpine:3.6 v3.6
- nginx:1.13.1-alpine

## Requirement

- Docker(version 1.13.0 or higher)
- docker-compose

## Screenshot

### Table list

<img width="427" alt="screenshot01" src="https://user-images.githubusercontent.com/12574048/27702410-f0fcff92-5d3e-11e7-9fa6-418f5bd5d559.png">

### Relationship

<img width="427" alt="screenshot02" src="https://user-images.githubusercontent.com/12574048/27702411-f0fef4dc-5d3e-11e7-9b15-a4903d973d9c.png">

### Table detail

<img width="427" alt="screenshot03" src="https://user-images.githubusercontent.com/12574048/27702632-a2ead8c8-5d3f-11e7-9153-1bb94e693cdf.png">

## Usage

```bash
# git clone
git clone https://github.com/treetips/simple-static-file-viewer.git
# Run containers and execute SchemaSpy
docker-compose up -d
# Browse table definition
http://localhost:8081/
# Update table definition
docker-compose run --rm schemaspy
```

## Change database settings

`schemaspy.properties` is the database connection configuration file.

Restart docker-compose after edit settings.

`schemaspy.properties` がデータベース接続設定ファイルです。

データベースに設定情報に修正し、修正した後はdocker-composeを再起動して下さい。

## Change Lang

Edit docker-compose.yml.

    environment:
      - LANG=ja_JP.UTF-8

## Change timezone

Edit docker-compose.yml.

    environment:
      - TZ=Asia/Tokyo

# Customie nginx

Customize default.conf freely.

default.conf is read as follows by nginx.conf.

default.confを自由にカスタマイズして下さい。

default.confは以下のようにnginx.confによって読み込まれます。

    include /etc/nginx/conf.d/*.conf;

## Known issue

It is fixed, and it seems to be to 3306 without becoming the designation ても existence effect in port in schemaspy.properties when SchemaSpy has a bug and chooses MySQL for a database.

SchemaSpyにはバグが有り、データベースにMySQLを選択した場合、schemaspy.propertiesでportを指定ても有効にならず、固定で3306になってしまうようです。

## License

[MIT](http://b4b4r07.mit-license.org)