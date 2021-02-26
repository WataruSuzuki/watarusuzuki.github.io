---
layout: post
title:  "Gradle: 依存ライブラリ入りのjarを作る"
tags:
- Engineer-Life
- Study
- Gradle

---

業務でFaaSな社内ツールを作る必要があり、今回は既存コードの流用がしたいケースなのでJavaを使うことにした。

今まで`.jar`や`.aar`はMaven経由で取得するバイナリしか作ったことがなかったので、単一バイナリに依存ライブラリも含める必要があったので調べてみたら、意外と簡単だった。

----------

#### 参考
- [Gradle: 依存ライブラリ入りのjarを作る](https://qiita.com/suin/items/641c1c1ec9ab5447221e)
