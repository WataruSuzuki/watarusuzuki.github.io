---
layout: post
title:  "格安SIMのプロファイル一覧サイト"
tags:
- MyApp
- WebApp

---
以前に[格安SIMの設定を助けるアプリ][post20170101]である[APNアシスタント][APNAssistant]を紹介しました。  

紹介したGitHub Pagesには記載していますが、実はこのアプリをApp Storeに申請した際にはレビューガイドラインとは別の理由で何度もAppleともめた経緯があります。  
「それって恣意的で、いくらでもAppleの都合に合わせて解釈可能じゃないですか？明文化しないのですか？」と聞きましたが、それについては一切回答がありませんでした。。。

まあApple Review Team~~の質は一貫していないので~~にも色々な方がいらっしゃるので、現状は一応App Storeからダウンロードできるわけですが、せっかく集めたデータなどが埋もれてしまうのも勿体無いので、[OSSとして公開したり][OSS_APNAssistant]する他に、これらのプロファイルをWEBサイトからダウンロードできるように、簡単な[Webアプリ][APNBookmarkPage]を作って見ました。

[![img](https://watarusuzuki.github.io/assets/images/APNBookmarkPage.png)][deploy_APNBookmarkPage]  


公開されている各国のMVNO向けAPN情報を元に、自前で構成プロファイルを作成、または公式の構成プロファイルURLリンクへアクセスできるようにしています。使いたいMVNOのAPNを選んでタップすれば、あとはSafariがインストール許可を求めてくるので、従って操作すればOKです。

利用は[こちらから][deploy_APNBookmarkPage]可能ですので、是非iPhone/iPadユーザはブックマークしておいてください(^ ^)


<!--
<a href="https://px.a8.net/svt/ejp?a8mat=2TIH2O+BUVTIQ+3GOM+60OXD" target="_blank" rel="nofollow">
<img border="0" width="300" height="250" alt="" src="https://www22.a8.net/svt/bgt?aid=170503152717&wid=001&eno=01&mid=s00000016159001011000&mc=1"></a>
<img border="0" width="1" height="1" src="https://www10.a8.net/0.gif?a8mat=2TIH2O+BUVTIQ+3GOM+60OXD" alt="">
-->


[APNAssistant]: https://watarusuzuki.github.io/APNAssistant/
[APNBookmarkPage]: https://watarusuzuki.github.io/APNBookmarkPage/
[post20170101]: https://watarusuzuki.github.io/2017/01/01/apn-assistant/
[OSS_APNAssistant]: https://github.com/WataruSuzuki/APNAssistant/
[deploy_APNBookmarkPage]: https://watarusuzuki.github.io/APNBookmarkPage/deployment/
