```docker-compose.yml
services:

  [サービス名]:
         image: postgres:10.6
         container_name: [コンテナ名]

         environment:
             TZ: Asia/Tokyo
             POSTGRES_USER: user
             POSTGRES_DB: sample
             POSTGRES_PASSWORD: password
             POSTGRES_ROOT_PASSWORD: password
          volumes:
              \- postgres-data:/var/lib/postgresql
          ports:
              \- 5432:5432
            
volumes:
    postgres-data:
```



上記のように記述する。



Docker環境のlaravelでSQLを切り替える場合は、.envファイル、database.phpを編集する。



```.env
DB_CONNECTION=pgsql
DB_HOST=postgres
DB_PORT=5432
DB_DATABASE=laravel_db
DB_USERNAME=user
DB_PASSWORD=password
```

```database.php
'default' => env('DB_CONNECTION', '[pgsql or mysql]'),
```

