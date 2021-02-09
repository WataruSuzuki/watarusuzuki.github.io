---
layout: post
title:  "R8やProguardでビルド時にmodule-info.classでエラーが出てビルドできない場合に回避する方法"
tags:
- Engineer-Life
- Study
- Android

---

`Warning: class [META-INF/versions/9/module-info.class] unexpectedly contains class [module-info]`

とエラーが出てR8やProguard利用時にビルドが出来ない問題に遭遇した。

エラー内容でググると、よくある回避方法としては`packagingOptions`に`exclude`を指定することで回避できる場合が多いようである。
```groovy
packagingOptions {
  exclude 'META-INF/DEPENDENCIES'
  exclude 'META-INF/DEPENDENCIES.txt'
  exclude 'META-INF/LICENSE'
  exclude 'META-INF/LICENSE.txt'
  exclude 'META-INF/license.txt'
  exclude 'META-INF/NOTICE'
  exclude 'META-INF/NOTICE.txt'
  exclude 'META-INF/notice.txt'
  exclude 'META-INF/INDEX.LIST'
  exclude 'META-INF/versions'
  exclude 'META-INF/versions/9/module-info.class'
}
```

が、今回の場合は上手く行かない。
解決策としては幾つか調べると、`-dontwarn module-info`をProguardのルールに追記することで解決した。

（記述した内容から推察すると、依存ライブラリ間で異なるJDKでビルドしたやつがいるとダメな場合があるのかな？？）
Dynamic moduleを使うケースでも同じような場合があるらしい。

----------
#### 参考
- [Cancellation and Timeouts](https://kotlinlang.org/docs/reference/coroutines/cancellation-and-timeouts.html)
