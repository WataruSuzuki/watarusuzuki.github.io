---
layout: post
title:  "Androidでmulti moduleなプロジェクトでjacocoレポートをマージする際の罠"
tags:
- Engineer-Life
- Study
- Android

---

ハマったので・・・

下記のようなプロジェクトがあったとします。

```
└── project's root
    ├── target module
    ├── related module 001
    ・・・
    └── related module 002
```

ここで`jacoco`でカバレッジを取得しようと試みました。  

欲しいのはあくまで`target module`のカバレッジです。  
`related module XXX`は`target module`の公開APIをテストするモジュールです。  
例えばAndroidでライブラリ開発をするケースで、`target module`は本体、`related module`はサンプルアプリです。
- `target module`は`JUnit`
- `related module`は`Espresso`

で、カバレッジを`jacoco`で取得し、結果を集計しようとしますが、マージされない物が出てきます・・・

深く調べていないので結論だけ書きますが、

**ターゲットモジュールの名前が昇降順で先頭にならないとレポートのマージに失敗します**  
----------

- [試したリポジトリ](https://github.com/WataruSuzuki/Example-CodeCoverage-AndroidLibrary)

#### 期待通りにマージできる例

```
└── project's root
    ├── target module name is "aaa"
    ├── related module name is "bbb"
    └── related module name is "ccc"
```

#### 期待通りにマージできない例

```
└── project's root
    ├── target module name is "zzz"
    ├── related module name is "bbb"
    └── related module name is "ccc"
```

暇で暇で仕方ない日が訪れたら、深く潜ってみても良いかもしれません。。
