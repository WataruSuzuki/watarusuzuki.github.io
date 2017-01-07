---
layout: post
title:  "格安SIMの設定を助けるアプリ"
tags:
- MyApp
- iOS

---
お仕事中に[iOS向け構成プロファイル][ConfigProfileReference]について仕様を把握する機会がありました。  

この中でチャレンジしたのは**アプリ処理から構成プロファイルを生成してインストールできるか？**という点でした。

[リファレンス][ConfigProfileReference]にも記載がありますが、どうやらプロファイルの拡張子「.mobileconfig」を識別しているのはSafariとメールアプリだけ。そこでSafariの履歴を見てみると**「localhost」**とあるでは無いですか！  
*[※ただ後にこれはstackoverflowにも同じこと書いてありましたけど・・](http://stackoverflow.com/questions/2338035/installing-a-configuration-profile-on-iphone-programmatically)*

このお仕事完了後、「これ使えばAPN設定が隠されていてもAPN設定できるアプリ作れるな」と思いついたので、作りました。

[![AppStore](https://watarusuzuki.github.io/MyProfile/banner-images/apnassistant2.png)](https://itunes.apple.com/jp/app/apnashisutanto2/id1160309695?mt=8)  

なぜ**"2"**なのか？という点は[こちらでも見て察してください](https://watarusuzuki.github.io/APNAssistant/)  
とにかくこのアプリは国内で格安SIMを利用しているのみの方にはオーバースペックですが、以下のようなことがアプリだけで行えます。
 - 頻繁にSIMを差し替える場合に、複数のAPN用構成プロファイルを端末内に保持しておける
 - Wi-Fiなしで（機内モード中とかでも）プロファイルの差し替えが行える
 - 海外旅行時に現地のプリペイドSIMを購入時などに、その場でプロファイルが作成できる

実際、自分自身の海外旅行時には間に合わなかったのですが、妻が夏休みに結構した海外旅行時には活躍しました(^ ^)

[こちらにも書きましたが](https://watarusuzuki.github.io/APNAssistant/)、Appleのレビューアはこのアプリを現状あまり好ましく思っていないようなので、もし購入を検討される場合はお早めにｗ  
iOSアプリ開発者であれば[ソースコードは公開しているので](https://github.com/WataruSuzuki/APNAssistant)、ご自身でビルド＆インストールで無料で利用できます。

[ConfigProfileReference]: https://developer.apple.com/library/content/featuredarticles/iPhoneConfigurationProfileRef/Introduction/Introduction.html
