---
layout: post
title:  "格安SIMの設定を助けるWebサイト"
tags:
- MyApp
- WebApp

---
以前に[格安SIMの設定を助けるアプリ][post20170101]である[APNアシスタント][APNAssistant]及び
[格安SIMのプロファイル一覧サイト][post20170311]を紹介しました。  

[APNアシスタントが嫌われている件はこちらで紹介した通りですが][post20170311]、中でも特に**構成プロファイルがアプリ内で生成されること**にネチネチと小言を言われるわけです。

ただ実際のところ、構成プロファイルは[仕様にある通り][ConfigProfileReference]ただのxmlファイルなので、Nativeアプリはもちろん、Webアプリで生成することも容易です。すでに私がデプロイせずとも[iOS用APN構成プロファイルジェネレータ][AzureGenerator]がオープンしていたりする訳で、あくまでこちらとしては、この機能をオフライン中にも利用したいだけなので。

ウェブサイトで利用するだけなら、アプリに対するお試しサービスとしてもちょうどいいので、これも[OSSとして公開しました][APNProfileGenerator]。

[![img](https://watarusuzuki.github.io/images/APNProfileGenerator.png)][deploy_APNProfileGenerator]  


利用するSIMのAPN情報がわかるなら、あとは適切な情報を入力して「Download」をタップすれば、Safariがよろしくプロファイルの設定まで誘導してくれます。※多分iOSではSafariでしか動作しません。

あと作成時に若干悩みの種だったのが、Safari(iOS, macOSどちらも)が[Download属性][DownloadAttribute]に対応していないということでした。。  
ChromeやFireFoxでは利用できるんですが、何より構成プロファイルを認識して制御してくれなきゃ困るブラウザで未対応、ってのは困るので、別のアプリをHerokuでかませてファイル生成→ダウンロードする仕組みとして、とりあえず動作させています。

利用は[こちらから][deploy_APNProfileGenerator]可能ですので、是非iPhone/iPadユーザはブックマークしておいてください(^ ^)


<div style="float:left;">
<a href="https://px.a8.net/svt/ejp?a8mat=2TIH2O+BUVTIQ+3GOM+60OXD" target="_blank" rel="nofollow">
<img border="0" width="300" height="250" alt="" src="https://www22.a8.net/svt/bgt?aid=170503152717&wid=001&eno=01&mid=s00000016159001011000&mc=1"></a>
<img border="0" width="1" height="1" src="https://www10.a8.net/0.gif?a8mat=2TIH2O+BUVTIQ+3GOM+60OXD" alt="">
</div>
<div style="float:left;">
<a href="https://px.a8.net/svt/ejp?a8mat=2TIH2O+BZ1UR6+50+35UAKX" target="_blank" rel="nofollow">
<img border="0" width="300" height="250" alt="" src="https://www29.a8.net/svt/bgt?aid=170503152724&wid=001&eno=01&mid=s00000000018019121000&mc=1"></a>
<img border="0" width="1" height="1" src="https://www15.a8.net/0.gif?a8mat=2TIH2O+BZ1UR6+50+35UAKX" alt="">
</div>

(^ ^)


[APNAssistant]: https://watarusuzuki.github.io/APNAssistant/
[APNBookmarkPage]: https://watarusuzuki.github.io/APNBookmarkPage/
[APNProfileGenerator]: https://watarusuzuki.github.io/APNProfileGenerator/
[post20170101]: https://watarusuzuki.github.io/2017/01/01/apn-assistant/
[post20170311]: https://watarusuzuki.github.io/2017/03/11/apn-bookmark-page/
[OSS_APNAssistant]: https://github.com/WataruSuzuki/APNAssistant/
[deploy_APNBookmarkPage]: https://watarusuzuki.github.io/APNBookmarkPage/deployment/
[deploy_APNProfileGenerator]: https://watarusuzuki.github.io/APNProfileGenerator/deployment/
[ConfigProfileReference]: https://developer.apple.com/library/content/featuredarticles/iPhoneConfigurationProfileRef/Introduction/Introduction.html
[AzureGenerator]: https://mobileconfig.azurewebsites.net
[DownloadAttribute]: https://developer.mozilla.org/ja/docs/Web/HTML/Element/a
