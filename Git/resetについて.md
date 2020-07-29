# resetコマンドのあれこれ

## git resetコマンドとは

gitで管理しているレポジトリの状態を、以前のコミットに戻すコマンド。



## 通常の書き方

```
git reset [--soft or --hard or no-option] [commitID]
```

コミット履歴はgit logコマンドで確認することができる。

git logを抜け出すにはターミナル上でqを押すだけ。



## resetの種類

### --soft

実行したコミットだけをなかったことにする。

addでステージングしたものは忘れられない。

### -hard

ファイルの変更自体をなかったことにする。

### no option

コミットとaddをなかったことにする。



## 参照

https://qiita.com/fnobi/items/ec036c1b5d7ee5a8517c

https://murank.hatenadiary.org/entry/20110327/1301224770





