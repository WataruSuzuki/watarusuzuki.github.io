---
layout: post
title:  "bitrise試してみた"
tags:
- Engineer-Life
- Study

---
モバイルアプリ開発のCIサービスとして、キラキラしたエンジニア達から今一番選ばれているのは~~綾鷹~~[bitrise](https://app.bitrise.io/)かと思います。

以前から名前は聞いていたし、何より[CI/CD Test Night](https://testnight.connpass.com/event/103064/)で色んな会社さんが効果的に使っているのを目の当たりに、普段はJenkinsおじさんな都合があっても個人開発では使ってみたい、ということで試してみました。

----------

### GitHubリポジトリ側の設定

いきなり出来上がったものから書いていきますが、こちらのプロジェクトで試しました。

[Study-Using-CI-service-iOS](https://github.com/WataruSuzuki/Study-Using-CI-service-iOS/)
* publicリポジトリ
  * この設定だと外部からは丸見えだけど、ビルド時間が10分から45分に延びる
  * [Free Developer Plan features for Open Source Projects on Bitrise](https://blog.bitrise.io/free-developer-plan-features-for-open-source-projects-on-bitrise)
* アプリのサンプルは[Unit Testing Apps and Frameworks](https://developer.apple.com/library/archive/samplecode/UnitTests/Introduction/Intro.html#//apple_ref/doc/uid/DTS40011742-Intro)から拝借・・


### bitrise側の設定

こちらも別にサンプルなので、`public`で作成しました。

[Dashboard / WataruSuzuki / Study-Using-CI-service-iOS](https://app.bitrise.io/app/085c861a1917b9c6#/builds)

基本はGitHubアカウントと連携済みなので、Automaticallyに設定されます。  
![img](https://watarusuzuki.github.io/assets/images/bitrise_github_pullreq001.png)

ただ別件で、仕事のリポジトリで試しにManualでWebHookとか設定したら、とりあえずはビルド出来るものの、GitHubのPullRequestとかに結果を反映することはできないみたいでした。  
（あくまでアカウント連携が必須。多分面倒なAPI連携を丸ごとやってくれるから、かと）  
[Reporting the build status to your git hosting provider](https://devcenter.bitrise.io/builds/triggering-builds/status-reporting/)

またマニュアルで設定するときは↓な感じ  
![img](https://watarusuzuki.github.io/assets/images/bitrise_github_webhook001.png)  
![img](https://watarusuzuki.github.io/assets/images/bitrise_github_webhook002.png)

### おまけ

purrかわいい  
![img](https://watarusuzuki.github.io/assets/images/bitrise_setting_env_var.png)
