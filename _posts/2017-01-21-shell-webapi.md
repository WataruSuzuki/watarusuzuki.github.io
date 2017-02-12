---
layout: post
title:  "シェルスクリプトからWeb APIを叩く"
tags:
- Study
- ShellScript

---
一括でデータを集めたり加工する際にはターミナルなどで実行するコマンドをシェルスクリプトにまとめておくことは、結構誰でもやると思います。  
そこでWeb APIも実行することは可能なのか？と試したところ、結構簡単に実行できました。忘れないようにメモです。

```shell:
#! /bin/sh
# ここではHotPepperのAPIを例にしています
URL_API="https://webservice.recruit.co.jp/hotpepper/gourmet/v1/?key="
KEY_API="YOURKEY"

# 関数の定義
# -------------------------
get_shop_info () {
    curl "${URL_API}${KEY_API}&name=$1" -o "$1.xml"
}

get_shop_info 'SHOPNAME'

```

誤ったスクリプトを書いて、サーバを攻撃しないようにしましょうね!!


<a href="https://px.a8.net/svt/ejp?a8mat=2TIH2O+BZ1UR6+50+35UAKX" target="_blank" rel="nofollow">
<img border="0" width="300" height="250" alt="" src="https://www29.a8.net/svt/bgt?aid=170503152724&wid=001&eno=01&mid=s00000000018019121000&mc=1"></a>
<img border="0" width="1" height="1" src="https://www15.a8.net/0.gif?a8mat=2TIH2O+BZ1UR6+50+35UAKX" alt="">
