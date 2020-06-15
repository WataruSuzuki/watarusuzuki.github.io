---
layout: post
title:  "Kotlin Coroutinesメモ"
tags:
- Engineer-Life
- Study
- Android

---

SDK開発では、なるべく依存関係を減らしておく方がユーザーには有益です。  
しかし、（特に昨今の非同期処理をシンプルに記述するにあたっては）外部ライブラリの導入を考えたくなる誘惑を断ち切るのは容易ではありません。

たいてい、その際に正気を取り戻すのはTestの記述のしやすさ。。。  
（どうもRx系のライブラリは、この辺がお手軽とは思えず、導入をためらいます）

よってプラットフォーマーのおすすめライブラリや公式ライブラリには、その辺の解消が期待されるわけですが[Kotlin coroutine](https://kotlinlang.org/docs/reference/coroutines/coroutines-guide.html)はその辺がシンプルに記述できる感じだったので調べたリンクを残しておきます。

いちおう[ゴミみたいなサンプル](https://github.com/WataruSuzuki/Kotlin-Coroutines-Example-Android)も残しておいた(^^;;

-----

### リンク

- [Android での Kotlin コルーチン](https://developer.android.com/kotlin/coroutines?hl=ja)
- [Kotlin コルーチンでアプリのパフォーマンスを改善する](https://developer.android.com/kotlin/coroutines-adv?hl=ja)
- [Asynchronous Programming Techniques](https://kotlinlang.org/docs/tutorials/coroutines/async-programming.html)
- [Asynchronous Flow - Kotlin Programming Language](https://kotlinlang.org/docs/reference/coroutines/flow.html)
- [Android で簡単コルーチン: viewModelScope](https://developers-jp.googleblog.com/2019/04/android-viewmodelscope.html)
