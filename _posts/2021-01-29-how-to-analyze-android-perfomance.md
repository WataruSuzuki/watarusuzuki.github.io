---
layout: post
title:  "Android開発でパフォーマンス解析するとき"
tags:
- Engineer-Life
- Study
- Android

---

メモ。色々あるけど、少しずつやるしか無いよ。

- 処理時間を調べてボトルネックを特定する
  -  ~TimingLoggerとか使いましょう~ これAPI Level 30では非推奨になっていくみたいです。
      ```
      Use Trace, or Android Studio.
      In general, milliseconds is the wrong granularity for method-level tracing.
      Rounding errors can overemphasize cheap operations, or underemphasize repeated operations.
      This timing system also does not take CPU scheduling or frequency into account.
      ```
  - [`trace`](https://developer.android.com/reference/android/os/Trace)を使う
  - `Android Studioのプロファイラ`を使う

----------
#### 参考
- [Android:TimingLoggerで処理間隔をログで出力する](http://yuki312.blogspot.com/2012/09/androidtiminglogger.html)
