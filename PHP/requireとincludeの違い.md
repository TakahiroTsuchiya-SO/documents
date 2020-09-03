# requireとinclude構文の種類と違いについて

## require

指定されたファイルが読み込めない場合、Fatal Error(致命的なエラー)となり処理が停止する。

https://www.php.net/manual/ja/function.require.php



## require_once

ファイルがすでに読み込まれているかどうかをPHPがチェックする。一つのファイル内で2度同じファイルを呼ぶ場合、2回目の読み込みではファイルを読み込まない。

https://www.php.net/manual/ja/function.require-once.php



##  include

指定されたファイルが読み込めない場合、Warning(警告)となるがその先の処理はそのまま行われる。

https://www.php.net/manual/ja/function.include.php



## incude_once

ファイルがすでに読み込まれているかどうかをPHPがチェックする。一つのファイル内で2度同じファイルを呼ぶ場合、2回目の読み込みではファイルを読み込まない。



https://www.php.net/manual/ja/function.include-once.php