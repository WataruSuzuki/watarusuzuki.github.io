---
layout: post
title:  "GitHubの便利なIssue検索"
tags:
- Engineer-Life
- Study

---
メモ。

仕事で「今年一年の作業内容とか集計してね」的なのがあったときに、もしGitHubのIssueドリブンな働き方なら↓な感じで調べれば簡単。

----------

### やり方

1. [https://github.com/issues](https://github.com/issues) にアクセス
2. 検索フィルターに `is:issue assignee:<アカウント名> archived:false updated:>=2018-01-01 ` みたいな感じでセット
3. ![img](https://watarusuzuki.github.io/assets/images/12_neko_sugoi.png)

参考: [https://engineer.blog.lancers.jp/2016/12/github_search_query_hack/](https://engineer.blog.lancers.jp/2016/12/github_search_query_hack/)

### え、普段Redmine使ってる？

~~転職したらいいと思いまs~~  
自身でテキトーにクエリー作りましょう(^-^)
