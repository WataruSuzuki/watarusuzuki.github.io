---
layout: post
title:  "(メモ) Android Libraryのパブリッシュは\"publishing\"を使う"
tags:
- Engineer-Life
- Study
- Android

---

仕事柄、AndroidでもiOSでもモジュールバイナリを作成して配布する機会がそこそこあります。

Androidの場合、大抵はCIからgradle taskを叩いて行いますので差分に気づく機会が少ないのですが、実は`uploadArchives`と`publishing`では`.pom`に記述される`<scope>`が異なります。

[サンプル差分](https://github.com/WataruSuzuki/Playground-Android-Library/pull/2/files)

### uploadArchivesの場合

一律`compile`が指定されます。これはAndroid Gradle Plugin `2.x`系では問題になりませんが、`3.x`以降では`api`と`implementation`で依存関係の種別を切り替えられるので、場合によっては利用者となるアプリモジュールで不都合があるかもしれません。

### publishingの場合

`scope`自体が指定されません。  
もし指定したい場合は↓のようになります。

| type | scope |
|--|--|
| implementation | runtime |
| api | compile |

[こんな感じ](https://github.com/WataruSuzuki/Playground-Android-Library/pull/2/files#r556401871)で指定すれば書き出されます。

※以前にこの変更をしたときは、`scope`も指定された気がしますが、もう転職して該当の`build.gradle`にアクセスできないので分かりません(^^;;

----------
