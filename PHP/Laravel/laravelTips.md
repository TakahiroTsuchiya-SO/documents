# Laravel Tips



## SSL化に対応したCSSの読み込み方法

```PHP
@if(app('env') == 'production')
    <link href="{{ secure_asset('css/app.css') }}" rel="stylesheet">
@else
    <link href="{{ asset('css/app.css') }}" rel="stylesheet">
@endif
```

Layout.blade.phpなどでproductionモードとの場合分けを行い、CSSを読み込むようにする。

ローカル環境ではSSL化(https)されていないので、production環境と分けて読み込む。