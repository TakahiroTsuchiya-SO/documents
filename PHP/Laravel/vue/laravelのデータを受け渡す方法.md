# laravelのデータを受け渡す方法

laravelのデータをvueに受け渡すには、json化する必要がある。



## vueコンポーネントでpropsとして受け取る方法

controllerでjson化したあと、vueコンポーネントでpropsとして受け取る。

laravelにvueをシングルファイルコンポーネントとして使用する場合におすすめ



https://qiita.com/maejima_f/items/96ee60bc9e71ed19c7cb



## インスタンス生成時に受け渡す方法

controllerでjson化したあと、vueインスタンス生成時にjson.parse()を使う。

laravelのblade内で、jquery的なノリでvueを使いたい場合にオススメ。



```controller
$categoryJson = json_encode($categories);

return view('tasks/index', [
						...
            'categoryJson'  => $categoryJson,
        ]);
```

```blade
new Vue({
      el: "#app",
      data: {
        categoryJson: JSON.parse(`{!! $categoryJson !!}`),
      }
  })
```

