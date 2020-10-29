# preventDefault()とは

preventDefault = デフォルトのイベントをさせないようにする設定。

デフォルトのイベントとは、主に以下の2パターンのものがある。



## ユーザーが発生させるイベント

- click、keypress、touchmoveなどといったイベント
- preventDefaultをよく使うのはこちらの方



## ブラウザが勝手に発動させるイベント

- DOMContentLoaded、ended、errorなどといったイベント



## イベントのデフォルト動作の一例早見表

|             イベント             |       ブラウザのデフォルト動作例        |
| :------------------------------: | :-------------------------------------: |
|            touchmove             |     スマホの画面がスクロールされる      |
|          aタグでのclick          |  aタグのherfで指定されたURLへ遷移する   |
| formのチェックボックスでのclick  | チェックボックスのオン/オフが切り替わる |
| テキストタイプのformでのkeypress |            文字が入力される             |
|      inputのsubmitでのclick      | actionで指定されたURLへ遷移＋データ送信 |



## preventDefaultの使用例

```
<p>あなたの名前を小文字のみで入力してください。</p>
<form>
<input type="text" id="my-textbox" />
</form>

<script>
var myTextbox = document.getElementById('my-textbox');
myTextbox.addEventListener( 'keypress', checkName, {passive: false} );

function checkName(e) {
  var charCode = e.charCode;

  if (charCode != 0) {
    if (charCode < 97 || charCode > 122) {
      e.preventDefault();
      alert("小文字のみ入力できます。");
    }
  }
}
</script>
```



フォームで発生する「keypress」イベントに対しイベントリスナを設定している。

このイベントリスナに{ passive: false }を設定しておくことで、preventDefaultを正常に使うことができる。



passiveは「受け身」という意味であり、passiveが「false」ということは
「このイベントリスナは受け身ではない」
＝「このイベントリスナはイベントのデフォルト動作を妨害するかもしれない」
＝「だからブラウザは文字入力の実行を待たなければいけない」という意味になる。

