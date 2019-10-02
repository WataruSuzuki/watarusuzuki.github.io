---
layout: post
title:  "(メモ) Kotlin FuelのTIPS"
tags:
- Engineer-Life
- Study

---

AndroidでJavaから引き継いだプロジェクトとかだと`HttpURLConnection`とかをそのまま継続利用とかが多いんですが、ひょんなことから[Fuel](https://github.com/kittinunf/fuel)を試してみたのでメモ残しておく。  

### 何が良いのか？

非同期の通信処理とか、かなり直感的な感じで書ける気がいました。  
[あとはこの辺みてね](https://github.com/kittinunf/fuel#features)

### インストール

[https://github.com/kittinunf/fuel#installation](https://github.com/kittinunf/fuel#installation)

----------


### 実装サンプル

```kotlin
// async example
"https://watarusuzuki.github.io/".httpGet().response { request, response, result ->
    when (result) {
        is Result.Success -> {
            println("async statusCode：" + response.statusCode)
            //println("async data：" + response.data)
        }
        is Result.Failure -> {
            println("Failed to connect")
        }
    }
}
// sync example
val triple = "https://watarusuzuki.github.io/".httpGet().response()
println("sync statusCode：" + triple.second.statusCode)
//println("sync data：" + triple.second.data)
```
