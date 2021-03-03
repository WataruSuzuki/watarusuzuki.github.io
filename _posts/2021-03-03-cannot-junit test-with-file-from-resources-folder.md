---
layout: post
title:  "Gradle: JUnitでResourcesフォルダのファイルが読めない場合"
tags:
- Engineer-Life
- Study
- Gradle

---

ハマったのでメモ。

リンクの通りだが、自分の場合は↓を行うことで解消。  
※同じコードで動かないから設定周りだとは思ったけど・・

## In IntelliJ:

1. Right-click your `test/resources` (or `test/java/resources`) directory
1. Select the `"Mark Directory as..."` sub-menu
1. Select `"Test Resources Root"`
1. This directory will appear with a decorator graphic symbolizing that it is in the `classpath`

## In Eclipse:

1. Go to `"Run->Run configurations..."` (in case of debug `"Run->Debug configurations..."`)
1. Open Run (Debug) configuration which you use
1. Open `"Classpath"` tab
1. Select `"User Entries"` and click `"Advanced..."` on the right
1. In the opened window select `"Add folder"`, point to your `src/test/resources`
1. This folder will appear under `"User entries"`, then you should move it up to make it the first on your `classpath`

----------

#### 参考
- [Depending on your IDE it is possible that your resource directory is not in the classpath.](https://stackoverflow.com/a/52206580)
