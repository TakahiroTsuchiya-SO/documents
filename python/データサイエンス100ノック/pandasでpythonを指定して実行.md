# pandasでファイルや文字指定の際のエラー対処法

pandasを使ってファイルを読み込んだり、特定の文字列を含むデータを読み込もうとするとエラーが発生する場合がある。



エラーの原因は、デフォルトの読み込み言語がC言語となっているからである。この状態だと、日本語や全角が入ったものを読み込むことができない。



そのため、以下のようにpythonで実行することを明記する必要がある。



## 対策方法

- 対策前

```
df = pd.read_csv("○○.csv"）
```



-  対策後

```
df=pd.read_csv("○○.csv", engine="python"）
```



https://punhundon-lifeshift.com/engine_python