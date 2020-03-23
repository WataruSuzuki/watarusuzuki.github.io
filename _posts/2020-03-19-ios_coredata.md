---
layout: post
title:  "(メモ) 久々にiOSのCoreDataを触ったら・・・"
tags:
- Engineer-Life
- Study
- iOS

---

ちょいちょいっと何かを作るときはもっぱら`Firebase`というのが昨今のスタンダードな感じだったので、個人開発アプリのアイデアを考えていたときに久しぶりにCloudKit（と、そこにて使うことになるCoreData）を触ることになったが、当初使ったときは・・・
- `Objective-C`全盛
- まだまだ知識や経験が無い状況（`FatViewController`上等）

な感じで、無理矢理データが保存できれば良い、程度で使っていた。

そこからは`Realm`使ってみたりもしたが、`Firebase Realtime Database`とか`Firestore`の方が便利すぎてたまらん、みたいな感じだったので、久しぶりに使うと完全に面食らった・・・・

また色々と調べるのも面倒なので、調べたこととか見た事だけメモしておく

##### 一対多のリレーションって、どう組むんだっけ・・
- [Mastering In CoreData (Part 5 Relationship Between Entities in Core Data)](https://medium.com/@aliakhtar_16369/mastering-in-coredata-part-5-relationship-between-entities-in-core-data-b8fea1b50efb)

##### なんかNSManagedObjectのsub class生成してビルドするとエラーなんだけど・・・
- [CoreDataのSubclass/Propertiesクラスを生成したらMultiple commands produce...によりビルトが通らなくなった](https://chu-bura.hateblo.jp/entry/20190517/swift/coredata)

##### スレッドセーフなんだっけ？
- [CoreDataによる並列処理](https://qiita.com/hongmhoon/items/606a352b1e96dfb0bec5)

----------

### そのほか参考

- [iOSアプリでデータベース（CoreData）を使う時に必要な知識をまとめてみた](https://qiita.com/merrill/items/2a3588aa98cc64b5dea0)
