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
