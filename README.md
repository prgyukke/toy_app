# [Docker_for_Ruby_on_Rails](https://github.com/prgyukke/Docker_for_Ruby_on_Rails)
## はじめに
プロジェクトディレクトリを`app`コンテナ内の`/var/www/app`にマウントしています。  
OSXにて、[Docker For Mac](https://www.docker.com/docker-mac)のインストール前提です。  
[Docker Community Edition for Mac - Docker Store](https://store.docker.com/editions/community/docker-ce-desktop-mac)の[Get Docker]をクリックしてダウンロード後、インストールしてください。 
  
ビルトインサーバは自動起動です。  
`http://localhost:3000/`にて確認可能です。  

### 各バージョン
- Ruby 2.5
- Rails 5.1.4
- postgres 10

## 環境構築
### 初回のみ
```
$ git clone git@github.com:prgyukke/toy_app.git
$ cd toy_app/
$ rm -rf .git
$ git init
$ git update-index --skip-worktree Gemfile.lock
$ docker-compose up -d --build
```

appコンテナに入る
```
$ docker exec -it toy_app_app_1 /bin/bash
# (必要であれば)migrate
# rails db:migrate
```

### 2回目以降
```
$ cd toy_app/
$ docker-compose up -d
```

### コンテナに入る際
```
$ docker exec -it toy_app_1 /bin/bash
```

### コンテナを抜ける際
```
# コンテナ上にて
# exit
```

### 開発終了時
```
$ docker-compose down
$ docker rmi toy_app_app
```
