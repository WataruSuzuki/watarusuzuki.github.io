---
layout: post
title:  "(メモ)Gitリポジトリのミラーリング on CircleCI"
tags:
- Engineer-Life
- Study

---
メモ。

----------

### CircleCIで必要な設定

- `Checkout SSH keys`でUser keyの設定

### こんな感じ.yml

```yml
version: 2
jobs:
  build:
    docker:
      - image: debian:stretch

    steps:
      - checkout

      - run:
          name: Install git
          command: apt-get -qq update; apt-get -y install git

      - run:
          name: Avoid hosts unknown for github
          command: mkdir ~/.ssh/ && echo -e "Host github.com\n\tStrictHostKeyChecking no\n" > ~/.ssh/config

      - run:
          name: Clone then push to other repository
          command: |
            git clone --mirror git@github.com:WataruSuzuki/danger-xcode_analyzing-private.git
            cd danger-xcode_analyzing-private.git
            git fetch -p origin

            git for-each-ref --format="ref=%(refname)" --shell refs/pull | \
            while read entry
            do
              eval $entry
              git update-ref -d $ref
            done

            git remote add upstream git@github.com:WataruSuzuki/danger-xcode_analyzing.git
            git push upstream master


            git clone --mirror ＜ミラー元のリポジトリ＞
            cd ＜ミラー元のリポジトリ＞

            git config user.name "＜なまえ＞"
            git config user.email "＜メルアド＞"

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
