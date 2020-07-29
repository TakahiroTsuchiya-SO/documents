# resetコマンドのあれこれ

## git resetコマンドとは

gitで管理しているレポジトリの状態を、以前のコミットに戻すコマンド。



## 通常の書き方

```
git reset [--soft or --hard or no-option] [commitID]
```

コミット履歴はgit logコマンドで確認することができる。



## resetの種類

### --soft

実行したコミットだけをなかったことにする。

addでステージングしたものは忘れられない。

### -hard

ファイルの変更自体をなかったことにする。

### no option

コミットとaddをなかったことにする。











