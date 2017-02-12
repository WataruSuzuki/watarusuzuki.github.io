---
layout: post
title:  "iOS9以降のシミュレータマクロ"
tags:
- Study
- iOS

---
※こちらも以前書いたものを移植しています。  

通勤中に[iOS9対応でやろうと思っていることまとめ](http://nsblogger.hatenablog.com/entry/2015/09/01/ios9_optimization)を読んでいたら知りましたが、iOS9から「TARGET_IPHONE_SIMULATOR」がdeprecatedになっているそうです。  
※自分の環境だとiOS7以降に対応しているせいなのか、warningなどは出てません。  

ただ動作確認するにしても、Xcode7でiOS8のシミュレータとかちゃんと動かないんですよね。（動く人いたら教えてください）  
加えて2009年のiMacだとCPUが遅くて、Xcode7でビルドするとすごく時間がかかるんですが、新しいMacを買うにはお金を貯める必要があり、現時点ではこいつで我慢しながら作るしか無い訳です。  

少し様子見な感じですが、確認が取れた段階で利用するアプリには順次適用していきたいところです。  


<div style="float:left;">
<a href="https://px.a8.net/svt/ejp?a8mat=2TIH2O+BUVTIQ+3GOM+60WN5" target="_blank" rel="nofollow">
<img border="0" width="300" height="250" alt="" src="https://www22.a8.net/svt/bgt?aid=170503152717&wid=001&eno=01&mid=s00000016159001012000&mc=1"></a>
<img border="0" width="1" height="1" src="https://www11.a8.net/0.gif?a8mat=2TIH2O+BUVTIQ+3GOM+60WN5" alt="">
</div>
<div style="float:left;">
<a href="https://px.a8.net/svt/ejp?a8mat=2TGWP4+E51N02+50+4YNR7L" target="_blank" rel="nofollow">
<img border="0" width="300" height="250" alt="" src="https://www25.a8.net/svt/bgt?aid=170430088855&wid=001&eno=01&mid=s00000000018030008000&mc=1"></a>
<img border="0" width="1" height="1" src="https://www10.a8.net/0.gif?a8mat=2TGWP4+E51N02+50+4YNR7L" alt="">
</div>
