---
layout: post
title:  "iOS9からABAddressBookがdeprecated, Contactsが用意されています"
tags:
- Study
- iOS

---
以前書いたものを移植したものです。

アプリ開発者が比較的関わることが多いと思われるのが、連絡先データを取得するAPI関連です。  

私もこれまで幾つかのアプリ開発（仕事、プライベートどちらも）で連絡先データを取得するAPIについて調べることがありましたが、今回のiOS9ではABAddressBookとABAddressBookUIが共にdeprecatedになってしまいました。  

代わりにContactsとContactsUIが用意されています。  
[About the Contacts Framework](https://developer.apple.com/library/prerelease/ios/documentation/Contacts/Reference/Contacts_Framework/index.html#//apple_ref/doc/uid/TP40015328)  

幾つかサンプルコードが掲載されていますが、今回AppleはサンプルコードのXcodeProjを用意していない様子。  
代わりにGitHubに用意されているもので、少し使い方を見てみました。  

こちらは有名なiOS9-day-by-dayの一つですね。  
[07-Contacts-Framework](https://github.com/shinobicontrols/iOS9-day-by-day/tree/master/07-Contacts-Framework)  

全てのAPIが試されている訳ではないですが、ContactsUIなどはAddressBookUIと同じ使い勝手で利用することができそうです。  

<!--
<a href="https://px.a8.net/svt/ejp?a8mat=2TIH2O+BZ1UR6+50+35UAKX" target="_blank" rel="nofollow">
<img border="0" width="300" height="250" alt="" src="https://www29.a8.net/svt/bgt?aid=170503152724&wid=001&eno=01&mid=s00000000018019121000&mc=1"></a>
<img border="0" width="1" height="1" src="https://www15.a8.net/0.gif?a8mat=2TIH2O+BZ1UR6+50+35UAKX" alt="">
-->


最後に、こちらに勉強時のコードをアップしました。  
[https://github.com/WataruSuzuki/iOS9_Contacts](https://github.com/WataruSuzuki/iOS9_Contacts)  
