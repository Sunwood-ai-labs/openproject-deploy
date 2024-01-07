# OpenProject Deploy

Recipes and examples for deploying OpenProject.

* [Docker Compose](./compose/)
* [Kubernetes](./kubernetes/)



## 前提条件
- DockerとDocker Composeがインストールされていること。
- 基本的なコマンドライン操作に慣れていること。

## リポジトリのクローン

まず、OpenProjectのDockerデプロイリポジトリをクローンします。

```bash

git clone https://github.com/Sunwood-ai-labs/openproject-deploy
```


## ディレクトリの移動

次に、クローンしたリポジトリの中の`compose`フォルダに移動します。

```bash

cd openproject-deploy/compose
```

![file](https://hamaruki.com/wp-content/uploads/2024/01/image-1704625937249.png)


## 環境設定ファイルの準備

サンプルの`.env`ファイルをコピーして、必要に応じて編集します。

```bash

cp .env.example .env
```

`OPENPROJECT_HOST__NAME`をサーバーの名前に変更してください。

```bash

##
# All environment variables defined here will only apply if you pass them
# to the OpenProject container in docker-compose.yml under x-op-app -> environment.
# For the examples here this is already the case.
#
# Please refer to our documentation to see all possible variables:
#   https://www.openproject.org/docs/installation-and-operations/configuration/environment/
#
TAG=13
OPENPROJECT_HTTPS=false
OPENPROJECT_HOST__NAME=maki-green
PORT=0.0.0.0:8080
# PORT=127.0.0.1:8080
OPENPROJECT_RAILS__RELATIVE__URL__ROOT=
IMAP_ENABLED=false
DATABASE_URL=postgres://postgres:p4ssw0rd@db/openproject?pool=20&encoding=unicode&reconnect=true
RAILS_MIN_THREADS=4
RAILS_MAX_THREADS=16
PGDATA="/var/lib/postgresql/data"
OPDATA="/var/openproject/assets"

```




## コンテナの起動

以下のコマンドでコンテナを起動します。

```bash

docker-compose up -d
```


## OpenProjectの確認

しばらく待つと、OpenProjectが`http://localhost:8080`で稼働します。ブラウザでアクセスして確認しましょう。

![file](https://hamaruki.com/wp-content/uploads/2024/01/image-1704626073776.png)

---