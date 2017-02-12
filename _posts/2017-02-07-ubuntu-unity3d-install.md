---
layout: post
title:  "UbuntuでUnity3Dを使う"
tags:
- Study
- Unity3D

---
私の自宅マシンはMacBook Pro RetinaとiMacですが、iMac側は実質UbuntuとWindowsがメインです。  
※しかもWindows側はとても動作が重いので、どうしてもMicrosoft Officeが必要なときに限り起動...  

個人的にこれからに備え、少しばかりUnity3DとCocos-2dについてプラグインの書き方などを勉強したいのですが、
できればMacBook側はストレージ容量も小さいので、出来る限り必要最低限のアプリのみにしておきたい事情が。。  
というわけで、Ubuntu側に無理やり環境構築を行う方針としました。

が、Unity3Dについては[試験版ビルド？][Unity3D_on_Ubuntu]が紹介されていました。  
これを試したところ、意外にもあっさりとインストールすることができました。。
![img](https://watarusuzuki.github.io/images/unity3donubuntu.png)

※追記  
どうやらUbuntu 16.04 LTSだと[こちらにある通り][CannotLoginUbuntu16]ログインができないようです。  
試験ビルド版を[5.4.0](http://download.unity3d.com/download_unity/linux/unity-editor-5.4.0b18+20160524_amd64.deb)に更新すれば解決しました。


<a href="https://px.a8.net/svt/ejp?a8mat=2TGWP4+E51N02+50+4YNR7L" target="_blank" rel="nofollow">
<img border="0" width="300" height="250" alt="" src="https://www25.a8.net/svt/bgt?aid=170430088855&wid=001&eno=01&mid=s00000000018030008000&mc=1"></a>
<img border="0" width="1" height="1" src="https://www10.a8.net/0.gif?a8mat=2TGWP4+E51N02+50+4YNR7L" alt="">


[Unity3D_on_Ubuntu]: https://blogs.unity3d.com/2015/07/01/the-state-of-unity-on-linux/
[CannotLoginUbuntu16]: http://askubuntu.com/questions/776991/cant-login-unity-game-engine-on-ubuntu-16-04-lts
