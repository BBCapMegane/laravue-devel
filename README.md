## 準備

```
cp .env.example .env
```

## コンテナ起動
```
docker-compose up -d laravue
```
これでRFP管理画面及び個人学習支援パックの２つが起動します

## workspace

```
docker-compose run --rm workspace
```

## マイグレーション
コンソールにログイン後に以下のコマンドで設定する
```
/var/www # cp .env.example .env
/var/www # composer install
/var/www # php artisan migrate
/var/www # php artisan db:seed
```

## vue

コンパイル
```
npm run dev
```

ホットデプロイ
```
npm run watch
```


