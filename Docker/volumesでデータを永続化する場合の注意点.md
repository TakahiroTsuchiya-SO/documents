# volumesでデータを永続化する際の注意点

Docker-compose.ymlファイルでdbを作成し、データを永続化する場合、下記のように記述する。

```
version: '3'
services: 
	db:
		image: mysql:8.0
		container_name:...
		
		//中略

volumes:
      - mysql-data:/var/lib/mysql
volumes:
  mysql-data:
```

このようにして永続化した場合、コンテナを消してもイメージを削除しても永続化したファイルは残ってしまう。そのため、sqlの設定やデータベース名などを変えたい場合、エラーが発生してしまう。



## 対応方法

ターミナルで以下のコマンドを入力する。

```
docker volume ls
```



使用されていないvolumeを全て削除する。

```
docker volume prune
```



## エラーを起こさないための対策

開発上の事情がない限り永続化しない。

```
        volumes:
        - ./docker/db/data:/var/lib/mysql
        - ./docker/db/sql:/docker-entrypoint-initdb.d
```

