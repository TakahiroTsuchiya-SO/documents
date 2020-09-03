```
Docker-compose down --rmi all
```

でコンテナ、イメージ、ネットワークを削除しようとした時、以下のようなエラーが発生する場合がある。

```
Error response from daemon: conflict: unable to remove repository reference "nginx" (must force) - container ○○○ is using its referenced image △△△
```

訳：○○○というコンテナは△△△というイメージを参照している。

つまり、イメージを削除するにはそのイメージに依存しているコンテナを先に消す必要がある。

以下のコマンドを実行し、コンテナを削除。

```
docker rm ○○○
```

再び、以下のコマンドでコンテナ、イメージ、ネットワークの削除を試みる。

```
Docker-compose down --rmi all
```

ここでまたエラーが発生した場合、同様に依存しているコンテナを削除する。



