---
layout: post
title:  "iOS9からABAddressBookがdeprecated, Contactsが用意されています"
date:   2016-12-31 03:22:04 +0900
categories: iOS-Dev
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


最後に、こちらに勉強時のコードをアップしました。  
[https://github.com/WataruSuzuki/iOS9_Contacts](https://github.com/WataruSuzuki/iOS9_Contacts)  
