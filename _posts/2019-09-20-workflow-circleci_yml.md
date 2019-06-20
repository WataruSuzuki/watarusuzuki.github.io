---
layout: post
title:  "(メモ)master push & tag pushをtriggerに on CircleCI"
tags:
- Engineer-Life
- Study

---
かなり[この辺](https://dragon-taro.com/college/post-827/)が参考になりました。

----------


### こんな感じ.yml

```yml
version: 2
jobs:
  build:
    docker:
      - image: debian:stretch

    steps:
      - checkout
      - run: echo build job

  test:
    docker:
      - image: debian:stretch
    steps:
      - run: echo test job

  deploy:
    docker:
      - image: debian:stretch
    steps:
      - run: echo deploy
      - run:
          name: Whether exists tag
          command: |
            if [ -n "${CIRCLE_TAG}" ]; then
                echo "Deploy! ${CIRCLE_TAG}, ${CIRCLE_BRANCH}"
            else
                echo "No deploy tag"
            fi

workflows:
  version: 2
  build-test-and-deploy:
    jobs:
      - build:
          filters:
            tags:
              only: /.*/

      - test:
          requires:
            - build
          filters:
            tags:
              only: /.*/

      - deploy:
          requires:
            - test
          filters:
            tags:
              only: /^v.*/
            branches:
              only: master

```
