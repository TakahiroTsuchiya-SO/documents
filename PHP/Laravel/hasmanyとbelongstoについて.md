# hasManyとBelongstoについて



Modelに対してhasOne、hasMany、belongsTo、belongsToManyを定義することにより、Model間の関連を表すことが出来る。主従（親子）関係より、主（親）となる側にhasOne、hasManyを定義し、従（子）となる側にbelongsToを定義する。



主要な関係性を下記にあげる。

- 一対一

  テーブル構造において、相手のidのカラムを持っているModelにbelongsToを定義し、他方のModelにhasOneを定義する。

- 一対多

  テーブル構造において、相手のidのカラムを持っているModelにbelongsToを定義し、他方のModelにhasManyを定義する。

- 多対多

  両方のModelにbelongsToManyを定義する。



## 書き方・引数の書き方



folderモデルが多数のtaskクラスを持っている場合。

```
class Folder extends Model
{
    public function tasks()
    {
        return $this->hasMany('App\Task');
        // return $this->hasMany(Task::class);
    }
}
```



どちらの書き方でも良い。

引数を省略しない場合は下記のようなコードになる。

```
$this->hasMany('App\Task', 'folder_id', 'id');
```



第一引数が関連するモデル名（名前空間も含む）、第二引数が関連するテーブルが持つ外部キーカラム名、第三引数はモデルに `hasMany` が定義されている側のテーブルが持つ、外部キーに紐づけられたカラムの名前となる。



第二引数が テーブル名単数形_id で第三引数が id である場合、第二引数と第三引数は省略することができる。