---
layout: post
title:  "アプリProjのステップ数算出"
tags:
- Study
- iOS

---
単なるメモです。  

特に受託開発のお仕事などでは仕事量を測る対象として、対象プログラムにおけるソースコードの行数を見積もりや実績の基準として利用することは珍しいことではないと思います。  
~~この値で進捗を測ったりするのはビルゲイツ曰く「飛行機の完成具合を総重量の割合で見るくらい間抜けな行為」というモノに強く賛同しますが~~
大人の事情なんかも色々ありますので、手取り早く算出する方法を残しておきます。

#### 【ファイルのstep数】※iOSプロジェクトの場合

```bash:
$ find . -name "*.m" -o -name "*.h" -o -name "*.swift" -o -name "*.storyboard" -o -name "*.xib" -o -name "*.strings" -o -name "*.plist" -o -name "*.pbxproj"  -o -name "*.xcscheme"| xargs wc -l
```

#### 【Gitの変更step数】
```bash:
$ git ls-files | xargs cat | wc -l
$ git diff --stat 前コミット HEAD パス
```

まあ、こういう事情の無い職場の方がエンジニアはだいたい幸せだと思います。

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
