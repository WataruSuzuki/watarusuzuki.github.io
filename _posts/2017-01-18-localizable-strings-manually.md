---
layout: post
title:  "UITestingなどでNSLocalizedStringを使う"
tags:
- Study
- iOS

---
UnitTestターゲットやEmbedded Frameworkとかで活用できそうなTipsです。  

XcodeのUITestingなどではレコーディング機能を利用して比較的簡単にテストケースを生成できますが、レコーディング中のLocalizationで飲み動作する内容しか記録できません。そこからコードをいじって汎用的にするわけですが、NSLocalizedStringで定義しているキーにアクセスする際はTestターゲットの場合には一工夫が必要です。

具体的には以下のような感じですが、TestターゲットなどからBundleが見えない場合、そのパスからbundleを取り直してやればバイナリ内の然るべきstringsファイルからキー参照ができるようになります。

```swift:
if let languageBundlePath = Bundle(for: HogeHoge.self).path(forResource: NSLocale.current.languageCode!, ofType: "lproj") {
  if let localizationBundle = Bundle(path: languageBundlePath) {
    let str = NSLocalizedString(key, bundle:localizationBundle, comment: "")
  }
}
```

今や需要は少ないかもしれないですが、Objective-Cならこんな感じ？  
※動作は未確認ですけど。

```objdump:
NSBundle *bundle = [NSBundle bundleForClass:[HogeHoge self]];
NSString *languageBundlePath = [bundle pathForResource:NSLocaleLanguageCode ofType:@"lproj"];
NSBundle *localizationBundle = [NSBundle bundleWithPath:languageBundlePath];
NSString *str = NSLocalizedStringFromTableInBundle(key, nil, localizationBundle, @"");
```

Frameworkでは勝手が違うかもしれませんので、検証する機会があれば追記します。


<a href="https://px.a8.net/svt/ejp?a8mat=2TIH2O+BUVTIQ+3GOM+60WN5" target="_blank" rel="nofollow">
<img border="0" width="300" height="250" alt="" src="https://www22.a8.net/svt/bgt?aid=170503152717&wid=001&eno=01&mid=s00000016159001012000&mc=1"></a>
<img border="0" width="1" height="1" src="https://www11.a8.net/0.gif?a8mat=2TIH2O+BUVTIQ+3GOM+60WN5" alt="">
