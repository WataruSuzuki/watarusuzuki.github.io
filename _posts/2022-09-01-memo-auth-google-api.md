---
layout: post
title:  "（メモ）Google Developer APIをREST APIで使うために認証を行う方法"
tags:
- Engineer-Life
- Study
- Android

---

Google Play Developer APIをREST APIとして扱うためにアクセストークンを取得する方法です。

## JWTを生成する

リファレンスの案内に従って作業していきます

------------------------------------
After you obtain the client ID and private key from the API Console, your application needs to complete the following steps:

1. Create a JSON Web Token (JWT, pronounced, "jot") which includes a header, a claim set, and a signature.
1. Request an access token from the Google OAuth 2.0 Authorization Server.
1. Handle the JSON response that the Authorization Server returns.

![jwt](https://watarusuzuki.github.io/assets/images/jwt.png)  

------------------------------------

Qiitaにあった記事を参考にPythonでJWTを生成する処理を書いてみます。

```python
import jwt
import time

iat = time.time()
exp = iat + 3600

import json
json_open = open('hoge.json', 'r') # サービスアカウントで生成したJSON鍵です
json_load = json.load(json_open)
# print(json_load)

payload = {
    'iss': json_load['client_email'],
    'scope': 'https://www.googleapis.com/auth/playdeveloperreporting',
    'aud': 'https://oauth2.googleapis.com/token',
    'iat': iat,
    'exp': exp
}
additional_headers = {'kid': json_load['private_key_id']}
signed_jwt = jwt.encode(payload, json_load['private_key'], headers=additional_headers,algorithm='RS256')
print(signed_jwt)
```

こんな感じでTerminalで実行します

```shell
pip install pyjwt
pip install cryptography
python3 ＜さっき作ったファイル＞.py
```

上手くいけば、JWTの値が出力されると思います

## アクセストークンを取得する

```shell
export SIGNED_JWT=＜さっき生成したsigned_jwt＞
curl -d grant_type=urn:ietf:params:oauth:grant-type:jwt-bearer -d assertion=$SIGNED_JWT https://oauth2.googleapis.com/token | jq
```

## APIの呼び出し方を調べて実行する

[Reference documentation](https://developers.google.com/play/developer/reporting/reference/rest)を参照します。  
例として[Method: vitals.crashrate.get](https://developers.google.com/play/developer/reporting/reference/rest/v1beta1/vitals.crashrate/get)はこんな感じになるかと思います。

```shell
export ACCESS_TOKEN=＜さっき取得したアクセストークン＞
export YOUR_APP_PACKAGE="com.example.your.awosome.app"
curl -X GET \
  "https://playdeveloperreporting.googleapis.com/v1beta1/apps/$YOUR_APP_PACKAGE/crashRateMetricSet" \
  -H "Authorization: Bearer $ACCESS_TOKEN"
```

----------

#### 参考
- [Preparing to make an authorized API call](https://developers.google.com/identity/protocols/oauth2/service-account#authorizingrequests)
- [GCP のAPIをcurlコマンドで実行するときのメモ](https://qiita.com/testpilot031/items/3f1531bb1b005a1f1f37)
