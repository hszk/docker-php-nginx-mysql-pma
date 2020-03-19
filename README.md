# memo

Laravelを動かそうとしてサンプルを作成

## ミドルウェア構成

- docker-compose
  - 3.7
- php
  - 7.4
- nginx
  - 1.16
- MySQL
  - 8.0
- phpMyAdmin
  - 5.0

## ディレクトリ構造（簡略版）

```
├── docker
│   ├── mysql
│   │   ├── data // データ（ここはディレクトリごとGit管理しない）
│   │   └── my.cnf // 設定ファイル
│   ├── nginx
│   │   └── default.conf // 設定ファイル
│   └── php
│       ├── Dockerfile // dockerイメージ
│       └── php.ini // 設定ファイル
├── server // アプリディレクトリ（ここはディレクトリごとGit管理しない）
└── docker-compose.yml
```

## コマンド

- ビルド
 -- docker-compose build .
- 起動
 -- docker-compose up -d
- 停止
 -- docker-compose down

## URL

- web
  - http://localhost:20080/
- phpMyAdmin
  - http://localhost:2111/

## 注意点

- 現状はserverディレクトリ以下でLaravelフレームワークが動く設定になっています
  - プロジェクト（ディレクトリ）名は「laravel」
  - nginx/default.confのroot（ドキュメントルート）を変更することで他のアプリも動きます
- 初回起動する時はmysql/dataディレクトリはない状態で起動します
  - データを移行したい場合は起動後にdumpファイルなどでデータを取り込んでください
- Dockerfileを変更した時はビルドをしてから起動してください
- 起動ポートなどは自分の好きなように変更してください
- MySQLやphpMyAdminのrootパスワードは必要に応じて変更してください
  - localで使用する分には自己管理で大丈夫なはず
  - AWSなどリモートで動かす時は運用方法考えてください
