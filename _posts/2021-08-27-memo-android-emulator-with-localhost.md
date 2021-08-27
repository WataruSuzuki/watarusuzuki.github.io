---
layout: post
title:  "（メモ）Androidエミュレータをlocalhostに接続する方法"
tags:
- Engineer-Life
- Study
- Android

---

iOSシミュレータの場合は気にする必要は無いが、Androidエミュレータの場合、エミュレータ自身がLocalhostを持っている？ので、開発マシン上のLocalhostで走らせているサーバーなどに接続するには、http://localhostでは繋がらない。
またHTTPで接続する場合、Clear Text Trafficの設定も忘れずに設定する必要あり。

### network_security_config.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<network-security-config>
    <domain-config cleartextTrafficPermitted="true">
        <domain includeSubdomains="true">10.0.2.2</domain>
    </domain-config>
</network-security-config>
```

### AndroidManifest

```xml
    <application
        android:name=".MyApplication"
        android:label="@string/app_name"
        android:networkSecurityConfig="@xml/network_security_config"
```

----------

#### 参考
- [Network address space](https://developer.android.com/studio/run/emulator-networking.html#networkaddresses)
