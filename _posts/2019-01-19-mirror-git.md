---
layout: post
title:  "(メモ)Gitリポジトリのミラーリング"
tags:
- Engineer-Life
- Study

---
メモ。

----------

### こんな感じ.sh

```shell
#bin/sh

git clone --mirror ＜ミラー元のリポジトリ＞
cd mealdock-ios.git
git remote set-branches origin 'heads/*'
git remote set-url --push origin ＜ミラー先のリポジトリ＞
git fetch -p origin

git for-each-ref --format="ref=%(refname)" --shell refs/pull | \
while read entry
do
  eval $entry
  git update-ref -d $ref
done

git push --mirror
```
