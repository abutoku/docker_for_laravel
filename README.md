# LaravelのDocker環境構築
- Laravel 8~10
- nginx
- PHP8.1
- mysql8.0

## Laravelのルートディレクトリに配置する場合

```
composer create-project laravel/laravel example-app
```

※バージョン指定
```
composer create-project laravel/laravel:^9.0 example-app
```

上記コマンドでLaravelプロジェクトを作成

ルートディレクトリに本リポジトリの各ファイルを配置してコンテナを立ち上げる

```
docker compose up --build
```

## 本環境内にLaravelをインストールする場合

.dockerignoreファイルを削除
```
rm .dockerignore
```
srcディレクトリを作成しLaravelをインストール
```
mkdir src
cd src
composer create-project laravel/laravel example-app
```
ファイルをsrcディレクトリ直下に配置する
```
mv example-app/* ./
mv example-app/.* ./
rmdir example-app
```
docker-compose.ymlのパスを変更しコンテナを立ち上げる

※コメントアウトしている方のパスに変える
```
docker compose up --build
```

## DB接続
必要に応じ.envを変更する

デフォルトで使用する場合は下記の通りとなる
```
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=mysqluser
DB_PASSWORD=mysqluserpass
```
