---
layout: post
title:  "(メモ) Android Emulator Runner on GitHub Actions"
tags:
- Engineer-Life
- Study

---

通常、業務上のAndroid開発におけるCIは転職してからエイヤでセットアップした`Jenkins`を普段は使っています。  
（Japanse Locaseで実行する必要があるのですが、今作っているSDK開発用のビルドプロジェクトだと、その辺上手くマッチングするCI as a Serviceが無い事情があり・・）

とはいえ、昨今の新型コロナウイルスによるリモートワーク増加により、クラウド上でのCIももう少し充実させた方が都合がよくなってきたので、手っ取り早い`GitHub Actions`でAndroid Emulatorを動作させようとやってみた次第です。

### 自前で記述する場合

```yaml
name: Android Emulator DIY

on: [push, pull_request]

jobs:
  hello-world:
    runs-on: macOS-latest
    steps:
    - uses: actions/checkout@v1

    - name: Run Android Emulator
      run: |
        echo "y" | $ANDROID_HOME/tools/bin/sdkmanager --install 'system-images;android-27;google_apis;x86'
        echo "no" | $ANDROID_HOME/tools/bin/avdmanager create avd -n xamarin_android_emulator -k 'system-images;android-27;google_apis;x86' --force
        echo $ANDROID_HOME/emulator/emulator -list-avds
        echo "Starting emulator"
        nohup $ANDROID_HOME/emulator/emulator -avd xamarin_android_emulator -no-snapshot > /dev/null 2>&1 &
        $ANDROID_HOME/platform-tools/adb wait-for-device shell 'while [[ -z $(getprop sys.boot_completed | tr -d '\r') ]]; do sleep 1; done; input keyevent 82'
        $ANDROID_HOME/platform-tools/adb devices
        echo "Emulator started"
    - name: Run ALL TESTS
      run: ./test_all.sh
```

`Run Android Emulator`の箇所が結構長ったらしい（スクリプトとかでまとめたら多少楽だろうけど）
で、手軽にできるもの無いかググると[Android Emulator Runner](https://github.com/marketplace/actions/android-emulator-runner?version=v2.4.0)が出てきました。

### Android Emulator Runnerで記述する場合

```yaml
name: Android Emulator Runner

on: [push, pull_request]

jobs:

  android-emulator-runner-with-strategy:
    runs-on: macOS-latest
    strategy:
      matrix:
        api-level: [23, 29]
        target: [default]

    steps:
    - uses: actions/checkout@v1

    - name: Android Emulator Runner with strategy matrix
      uses: ReactiveCircus/android-emulator-runner@v2.4.0
      with:
        api-level: ${{ matrix.api-level }}
        target: ${{ matrix.target }}
        arch: x86_64
        profile: Nexus 6
        script: ./test_all.sh
```

文句無しで、こちらの方が良いですね。

----------

### その他

- [Study-Using-CI-service-Android](https://github.com/WataruSuzuki/Study-Using-CI-service-Android)
