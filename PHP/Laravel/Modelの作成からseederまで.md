# Model作成からseederでテストデータを挿入するまでの流れ

プロジェクトにおいて要件定義、テーブル定義を行った後はmodel, controllerの実装を行うと思う。

一連の流れについて簡単にまとめていく。



## modelの作成

以下のコマンドでmodelの雛形を作成できる。

```
php artisan make:model [Model name]
```



modelの作成と同時に付随するcontrollerも作成する場合、以下のコマンドで一発でどちらも作成できる.

```
php artisan make:model ModelName -mr
```



## Modelディレクトリの作成

生成したmodelはappディレクトリ直下に設置される。

これだと少しわかりにくいので、app/Models/を作成し、その直下にmodelを移動する。

その際、namespaceやregistarcontrollerなどを変更する必要がある。

Laravel6.xの場合、以下のような修正が必要である。



### 各modelの冒頭の名前空間を変更

```各modelの冒頭
<?php
namespace App\Models;
```



### composer.jsonを変更

```
"autoload": {
        "psr-4": {
            "App\\": "app/",
            "Models\\": "app/Models/"
        },
    },
```



### UserFactory.phpの名前空間を変更

```/database/factories/UserFactory.php
<?php

/** @var \Illuminate\Database\Eloquent\Factory $factory */

use App\Models\User;
```



### auth.phpのディレクトリ指定を修正

```/config/auth.php
 'providers' => [
        'users' => [
            'driver' => 'eloquent',
            'model' => App\Models\User::class,
        ],
```



### RegisterController.phpを変更

```
<?php

namespace App\Http\Controllers\Auth;

use App\Http\Controllers\Controller;
use App\Providers\RouteServiceProvider;
use App\Models\User;
```



なお、バージョンにより修正箇所が異なる場合があるので要検索。



## seederの作成・実行

テストデータを簡単に挿入できるseederは以下のコマンドで生成する。

```
php artisan make:seeder [TableName]TableSeeder
```



[TableName]の部分はmodel名を複数形で書くことが多い。

seederデータの挿入は下記のようにfor文を使うと書きやすい。

```
for ($i = 1; $i <= 3; $i++) {
            User::create([
                'name'           => 'test' .$i,
                'email'          => 'test' .$i .'@test.com',
            ]);
        }
```



seederを実行するには、特定のテーブルを指定して実行する方法と一度にたくさんのseederを実行する方法の2通りがある。



#### ①特定のテーブルを指定して実行する

下記のコマンドをターミナル上で実行する。

```
php artisan db:seed --class=[TableName]TableSeeder
```



#### ②一度にたくさんのseederを実行する

App/database/seeds/Databaseseeder.phpを開き、実行したいseederを以下のように登録する。

```
public function run()
    {
        $this->call([
        [TableName]TableSeeder::class,
        ...
        ]);
    }
```



全てのファイルの登録が済んだら、ターミナルで下記のコマンドを入力し、実行する。

```
php artisan db:seed
```



次のような出力がターミナルから帰ってきたら成功。

```
Seeding: [TableName]TableSeeder
Seeded:  [TableName]TableSeeder (0.53 seconds)
Database seeding completed successfully.
```

