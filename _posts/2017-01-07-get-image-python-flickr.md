---
layout: post
title:  "Flickr APIで画像データを収集する"
tags:
- Study
- DeepLearning

---
今年勉強するテーマのひとつは**機械学習について理解を深める**、です。  
とは言っても具体的なアルゴリズムなどは説明を読んでも数学的な知識も必要で、ちっとも理解できません。。。  
※かたや一緒に働くとあるエンジニアはDeepLearningについて執筆中なので、まさに天と地の差が・・

とはいえ、自分の勉強スタイルは手で動かしてみて理解すること。よってまずは[TensorFlowについて][TensorFlow]勉強することに決めました。

すでに用意されたデータでは、自分の力量では理解まで進まない可能性があるので、学習用データの作成から取り組んでみることにしました。  
画像を識別するアプリなどを最終的に作ってみたいので、まずは画像データの収集するノウハウを手に入れる必要があります。

[今回はFlickr APIを][FlickrDevelop]を利用して画像データを収集してみたいと思います。  
すこしググると、[ichiroexさんが書いたものが便利そうです](http://qiita.com/ichiroex/items/605fec47b3188b31bd53)ので
これを[Forkして](https://github.com/WataruSuzuki/getImageFromFlickr)利用することにしました。

ここだけ、少しいじって使いやすくします。

```diff:getImageFromFlickr.py
     query = sys.argv[1]
+    numbers = sys.argv[2]
#API KEY, クエリ, 取得したい画像の数を渡す
-    url_list = getImageUrlFromFlickr(API_KEY, query, 10)
+    url_list = getImageUrlFromFlickr(API_KEY, query, numbers)
```

加えてURLを取得したら、テキストファイルに出力して、それを読み込んでwgetするプログラムもささっと作りました。

```python
#!/usr/bin/python
# coding: UTF-8
import os

f = open('urls.txt')
lines = f.readlines() # 1行毎にファイル終端まで全て読む(改行文字も含まれる)
f.close()
# lines: リスト。要素は1行の文字列データ

for line in lines:
    os.system("wget "+ line),
print
```

これで、こんな感じで利用します。

```bash
$ python getImageFromFlickr.py [検索ワード] [画像の枚数] > urls.txt
# たとえば寿司の画像が１０枚ほしいなら
# $ python getImageFromFlickr.py 寿司 10 > urls.txt
$ python download.py
```

これで画像データは収集可能です。

<!--
<a href="https://px.a8.net/svt/ejp?a8mat=2TIH2O+BZ1UR6+50+35UAKX" target="_blank" rel="nofollow">
<img border="0" width="300" height="250" alt="" src="https://www29.a8.net/svt/bgt?aid=170503152724&wid=001&eno=01&mid=s00000000018019121000&mc=1"></a>
<img border="0" width="1" height="1" src="https://www15.a8.net/0.gif?a8mat=2TIH2O+BZ1UR6+50+35UAKX" alt="">
-->


[TensorFlow]: https://www.tensorflow.org/
[FlickrDevelop]: https://www.flickr.com/services/api/
