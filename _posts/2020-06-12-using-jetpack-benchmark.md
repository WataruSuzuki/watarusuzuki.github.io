---
layout: post
title:  "JetPackのbenchmark機能を使ってみた（CIにはまだ早い・・）"
tags:
- Engineer-Life
- Study
- Android

---

SDK開発が普段のお仕事なので、あまりエンドユーザの操作性（快適さとか）に悩む機会は無い。

でも今後に向けて新しい開発機能も勉強しておこう、ということで[Benchmark](https://developer.android.com/studio/profile/benchmark?hl=en)を触ってみた。

### セットアップの仕方
- [Quick Start](https://developer.android.com/studio/profile/benchmark?hl=en#quickstart)もあるけど、これだと既存のtestモジュールが使い物にならなくなってしまう。
  - あくまでお試し用な感じ
- [Full project setup](https://developer.android.com/studio/profile/benchmark?hl=en#full-setup)にある通り、[専用のモジュールを用意する](https://developer.android.com/studio/profile/benchmark?hl=en#create-module)のが良い感じ

### 使ってみた感じ

#### 計測する内容の記述
- [Write the benchmark](https://developer.android.com/studio/profile/benchmark?hl=en#write-benchmark)に倣って記述する
- [サンプル](https://developer.android.com/studio/profile/benchmark?hl=en#samples)も充実しているので、書くのは難しくないと思う

#### 計測の実行

Android Studioから特定のベンチマーク用テストクラスを選んで実行する分には問題はない。  
（ちゃんとスコアとかが表示される）

問題はgradleコマンドから実行した場合・・  
（まだリファレンス通りには動いてないっぽい。。[既知の問題](https://developer.android.com/jetpack/androidx/releases/benchmark?hl=ja#1.1.0-alpha01)にも書いてあったorz）

```bash
既知の問題

・コマンドラインによるベンチマークの gradle 呼び出しで、結果が直接出力されません。
　この問題を回避するには、Studio を介して実行するか、JSON 出力ファイルを解析して結果を取得します。
・ベンチマーク レポートで、applicationId が「android」または「download」（大文字と小文字を区別しない）で
　終わるアプリがインストールされているデバイスからレポートを取得できません。
　この問題が発生した場合は、Android Gradle プラグインを 4.2-alpha01 以降にアップグレードする必要があります。
```

[実行の仕方](https://developer.android.com/studio/profile/benchmark?hl=en#run-benchmark)に

```bash
./gradlew benchmark:connectedCheck
```

とあるが、普通にエラーになる・・・

```bash
java.io.IOException: Failed to create file for benchmark report.
        Make sure the instrumentation argument additionalOutputDir is set to a writable
```

もちろん、[enableAdditionalTestOutput](https://developer.android.com/studio/profile/benchmark?hl=en#android_gradle_plugin_36_and_higher)の設定も追加するが変化なし・・・

`GrantPermissionRule`の追加も試してみたけど、`InitializationError`になるので違う気がする・・

ちなみにadbコマンドだと動作するので、CIなどでデータ収集する場合はこちらを使うしか無いかも・・

```bash
adb shell am instrument -w -e "androidx.benchmark.output.enable" "true" com.android.foo/androidx.benchmark.junit4.AndroidBenchmarkRunner
```

ただし、以下の記述にある挙動は既知の問題にある通りなので、マニュアルで収集する必要がありそうです。
>JSON reports are copied from device to host. These are written on the host machine at:
> `project_root/module/build/outputs/connected_android_test_additional_output/debugAndroidTest/connected/device_id/app_id-benchmarkData.json`

↓が直れば、改善されるかも知れません。
https://issuetracker.google.com/issues/156065464
