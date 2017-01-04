---
layout: post
title:  "iOS9ではUIPopoverControllerがdeprecatedに・・・"
date:   2016-12-31 02:22:04 +0900
categories: iOS-Dev
---
以前書いたものを移植したものです。

iOS9からUIPopoverControllerが軒並みdeprecatedになっています。  
SplitViewと相性が良くないんでしょうか？謎です。  
そのせいなのか、UIPopoverPresentationControllerの矢印がズレる不具合が出ています。  
iPadだと吹き出しみたいで、カワイイから維持したいのに・・  

![img](https://3.bp.blogspot.com/-2rsnpXnXv5k/Vd6hqnBixlI/AAAAAAAAAFg/jKV0gj4Wzqc/s320/UIPopover_datausagecat.png)

AppleにはBug report出しましたけど、deprecatedだとメンテしなさそうなので期待薄です。

とりあえず他の対応を進めようかと思います。

対策知っている人居たら良いのにな〜。
