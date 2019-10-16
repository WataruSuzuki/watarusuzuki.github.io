---
layout: post
title:  "(メモ) Skip phrase on GitHub Actions"
tags:
- Engineer-Life
- Study

---

仕事でも趣味アプリでも、CIがあるといちいち手動でテストしないで楽なのでサボらず積極的に書くようにしている。  
が、仕事のビルド対象は毎回全てテストしていると結構な時間がかかってしまうので`Jenkins`で使っていた[GitHub PullRequest Builder Plugin](https://plugins.jenkins.io/ghprb/)のようにPR説明欄のコメントをトリガにビルドする方法があるのか調べたら意外と簡単に出来たのでメモ。

### 参考

[GitHub Actions で \[ci skip\] できるようにしました](https://srz-zumix.blogspot.com/2019/10/github-actions-ci-skip.html)


----------


### YAMLサンプル

```yaml
name: CI

on: [pull_request]

jobs:
  validation:
    runs-on: macOS-latest
    steps:
      - run: echo "[please test action] == ${{ contains(github.event.pull_request.body, '[please test action]') }}"

  test:
    runs-on: macOS-latest
    needs: validation
    if: "contains(github.event.pull_request.body, '[please test action]')"
    steps:
    - uses: actions/checkout@v1

    - name: Run ALL TESTS
      run: ./test_all.sh
```

- [Skip-Phrase-On-GitHub-Actions](https://github.com/WataruSuzuki/Skip-Phrase-On-GitHub-Actions)
