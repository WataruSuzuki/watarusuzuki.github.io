---
layout: post
title:  "(メモ) fastlaneをCIサービスで使った時のTIPS"
tags:
- Engineer-Life
- Study

---

仕事柄、テストの自動化とかは色々書いていたけどアプリのアップロードをTravisCIとかGitHub Actionsで書いたことがありませんでした。  
※bitriseの無料お試しビルドとかでかまけてた

まあ、そこそこ色々調べたので今後のためにメモ。

### 参考になったページ

- [GitHub Actionsを使ってFirebase App Distributionへ配布する](https://kouki.hatenadiary.com/entry/2019/10/02/094358)
- [fastlane deliver使用時に、App Storeでの説明のローカライズを追加する](https://qiita.com/yutailang0119/items/69b7d0b3807d7212b401)
- [Apple IDの2FA必須化に伴うCI環境でのfastlane実行の問題と対応](http://tofucodes.hatenablog.jp/entry/2019/03/31/212850)
- []()
- []()


----------


### Fastfileはこんな感じ

```ruby
default_platform(:ios)

platform :ios do

    desc "Import Certificates for CI service"
    private_lane :import_certificates_for_actions do
        setup_ci(
            force: true,
            provider: "travis",
        )
        import_certificate(
            certificate_path: "certificates/development.p12",
            certificate_password: '',
            keychain_name: ENV["MATCH_KEYCHAIN_NAME"] || "" # MATCH_KEYCHAIN_NAME created by setup_ci action
        )
        install_provisioning_profile(path: "certificates/MyApp_Development.mobileprovision")
        install_provisioning_profile(path: "certificates/MyAppTodayWidget_Development.mobileprovision")
        import_certificate(
            certificate_path: "certificates/distribution.p12",
            certificate_password: ENV["CERTIFICATE_PASSWORD"],
            keychain_name: ENV["MATCH_KEYCHAIN_NAME"] || "" # MATCH_KEYCHAIN_NAME created by setup_ci action
        )
        install_provisioning_profile(path: "certificates/MyApp_Production.mobileprovision")
        install_provisioning_profile(path: "certificates/MyAppTodayWidget_Production.mobileprovision")
    end

    desc "Push a new release build to the App Store"
    lane :release do
        import_certificates_for_actions
        build_app(workspace: "APNAssistant.xcworkspace", scheme: "APNAssistant")
        upload_to_app_store
    end

end
```

### その他

- 当然ながらProvisioning ProfileのAuto ManagingはCIサービス環境下でXcodeがサインインしてないので無効化
  - それも面白いかも知れないけど
- ほげ
