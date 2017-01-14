---
layout: post
title:  "AlamofireにPullReqがマージされました"
tags:
- OSS
- Security

---
Swiftを用いるiOSエンジニアなら誰もが聞いたことはあるであろう、[Alamofire][Alamofire]に先日とある[PullReq][PullReq]を送っていましたが、ついに承認＆マージされました。

私は通常業務でセキュアコーディングについて把握しておく必要が一時期あったのですが、その中で[証明書の失効検証][OCSP]について学、AndroidやiOSアプリで実装する手法や、他のアプリやライブラリ、SDKなどの対応状況も合わせて調べていました。

iOSのSDKでは[それらを行うためのAPI][SecurityFramework]があるようでしたが、[こちらのNoteを読む限り][TechnicalNote]、CRLやOCSPのチェックはアプリ自身で行う必要があるようでした。

>SecPolicyCreateRevocation lets you create a security policy that specifically checks for certificate revocation (for example, via OCSP or a CRL).

一通り必要な手法を調べた後、有名どころのOSSコードを見てみるとAFNetworkやAlamofireではPinningは行なっているものの、CRL/OCSPは行なっていないことがわかりました。
これは自分の得た知識を還元するには良い機会だな、と感じましたので思い切ってPull Requestを大物OSSに送って見た次第です。  
**「なんか変なコード送られてきた、キモい・・」**とか言われないかヒヤヒヤしました(^ ^;)

しかし、そこは天下のAlamofire運営者です。  
今回対応してくれたのは[cnoon][cnoon]さんという方でしたが、丁寧にこのパッチに対するヒアリングをして、適切にパッチの意図や目的を理解するように務めてくれたのです。  
※Nikeのエンジニアが対応してくれたところに、Air Jordanが大好きな自分との妙な運命を感じましたw

バージョン4.3.0で、修正が取り込まれました。下記のテストコードが利用方法としてわかりやすいと思うので載せておきます。

```diff:

 +    // MARK: Server Trust Policy - Perform Revoked Tests
 +
 +    func testThatRevokedCertificateRequestFailsWithRevokedServerTrustPolicy() {
 +        // Given
 +        let policy = ServerTrustPolicy.performRevokedEvaluation(
 +            validateHost: true,
 +            revocationFlags: kSecRevocationUseAnyAvailableMethod
 +        )
 +
 +        let policies = [revokedHost: policy]
 +
 +        let manager = SessionManager(
 +            configuration: configuration,
 +            serverTrustPolicyManager: ServerTrustPolicyManager(policies: policies)
 +        )
 +
 +        let expectation = self.expectation(description: "\(revokedURLString)")
 +        var error: Error?
 +
 +        // When
 +        manager.request(revokedURLString)
 +            .response { resp in
 +                error = resp.error
 +                expectation.fulfill()
 +            }
 +
 +        waitForExpectations(timeout: timeout, handler: nil)
 +
 +        // Then
 +        XCTAssertNotNil(error, "error should not be nil")
 +
 +        if let error = error as? URLError {
 +            XCTAssertEqual(error.code, .cancelled, "code should be cancelled")
 +        } else {
 +            XCTFail("error should be an URLError")
 +        }
 +    }

 ```

もちろんPull Requestを送る上では最低限の礼儀もあると思いますが、臆して行動しないことより行動してみる方を選んで良かったと思います。またこんな感じで、みんなの為になるパッチが送れれば良いなと思いました。

Thanks, cnoon!!

[Alamofire]: https://github.com/Alamofire/Alamofire
[PullReq]: https://github.com/Alamofire/Alamofire/pull/1822
[OCSP]: https://ja.wikipedia.org/wiki/Online_Certificate_Status_Protocol
[SecurityFramework]: https://developer.apple.com/reference/security/1400026-secpolicycreaterevocation
[TechnicalNote]: https://developer.apple.com/library/content/technotes/tn2232/_index.html#//apple_ref/doc/uid/DTS40012884-CH1-SECSTRICTER
[cnoon]: https://github.com/cnoon
