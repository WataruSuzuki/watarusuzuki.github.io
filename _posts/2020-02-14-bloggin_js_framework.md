---
layout: post
title:  "GitHub Pagesに構築したブログをJekyllからReactなヤツに乗り換えるには？"
tags:
- Engineer-Life
- Study

---

なんとなく`markdown`でブログを書きたいと思って、今あるGitHub Pagesの設定はいつぞかに調べた設定を使っています。

が、畑違いで専門外でも`React`や`Vue`、`Nuxt`といった単語に目を触れる機会は頻繁に訪れるので、ちょっといい機会に調べてみる事にしました。

### そもそもどんなライブラリまたはフレームワークを選定するべきか？

- [JSフレームワーク事情2020年始め](https://note.com/erukiti/n/na654ad7bd9bb)
  - とても直近の現状がわかりやすい。以前なんとなく`Cordova`に関してお勉強した時は`Angular`をチョイスしたけど、最近は人気が下降気味とのこと・・・
  - 仕事で`React Native`を触る機会はそこそこあるので、ひょっとしたら`React`を触っておくのが正解かもしれない
  - ただ記事中にはもちろん、職場でも（その畑に行くと）感じるのは`Nuxt.js`を立ち上げ時に手っ取り早く使えるので使っているというのは感じている
    - [Nuxt.js - ユニバーサル Vue.js アプリケーション](https://ja.nuxtjs.org)

### ReactとVueのどちらを選ぶか？

- これはドンピシャな記事で、今回の検討レベルでは↓をそのまま検討の材料とする事に(^-^)
  - [ReactとVueのどちらを選ぶか - Qiita](https://qiita.com/yoichiwo7/items/236b6535695ea67b4fbe)
    - 勉強メモな側面があるので、`React`で問題なし

### Reactで静的サイト作れるの？

- [Gatsby](https://www.gatsbyjs.org)ってヤツがとても良さそう
  - [Reactベース静的サイトジェネレータGatsbyの真の力をお見せします - Qiita](https://qiita.com/uehaj/items/1b7f0a86596353587466)
  - [Reactの最強フレームワークGatsby.jsの良さを伝えたい！！ - Qiita](https://qiita.com/hppRC/items/00739eaf9ae7fc95c1ca)
- GitHub Pagesで使ってみた系記事もゴロゴロ出てくる
  - [Gatsby + GitHub Pages でブログを構築](https://suzukalight.com/2019-06-29-hello-world/)
  - [Gatsby + Markdownでブログを作り直しました](https://diff001a.netlify.com/gatsby-blog-with-markdown/)
  - [Gatsby のサイトを GitHub Actions で GitHub Pages にデプロイ - Qiita](https://qiita.com/peaceiris/items/2f6d83802f2aefa66f9d)

### Reactで広告貼れるの？
- いくつか記事出てくるし、大丈夫じゃね？と思われる
  - [Google AdsenseをReactで使う方法(パッケージ未使用) - Qiita](https://qiita.com/qrusadorz/items/14972b6e069feaf777a9)
  - [React Adsenseライブラリの概要 - GatsbyJsにadsenseの広告付ける方法](https://codechacha.com/ja/react-adsense-library/)

### Reactってなんか良いIDEあるの？
- [Reactide](http://reactide.io)ってヤツがとても良さそう
  - [世界初！React Webアプリ開発専用のIDE「Reactide」](https://itnews.org/news_contents/product-reactide)

