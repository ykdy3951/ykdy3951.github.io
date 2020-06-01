---
date: 2020-05-20 11:01:30
layout: post
title: 'Lord of SQLinjection - 1 (gremlin)'
subtitle: 'Learning SQLinjection'
description: "'https://los.eagle-jump.org/'에서 SQLinjection을 연습해보자!!"
image: https://raw.githubusercontent.com/ykdy3951/ykdy3951.github.io/master/_src/SQLinjection/1/image.png
optimized_image: https://raw.githubusercontent.com/ykdy3951/ykdy3951.github.io/master/_src/SQLinjection/1/image.png
category: Webhacking
tags:
  - Webhacking
  - SQL
  - SQLInjection
author: ykdy3951
paginate: false
comments: true
---

# Webhacking - SQLinjection

> 필요한 지식 : sql <br>
> 문제 : [SQLinjection level1 - gremlin](https://los.eagle-jump.org/gremlin_bbc5af7bed14aa50b84986f2de742f31.php).

### 문제

![placeholder](https://github.com/ykdy3951/ykdy3951.github.io/blob/master/_src/SQLinjection/1/1.png?raw=true 'target')

문제를 보면 get 방식으로 id와 pw를 입력을 받음을 알 수 있고
preg_match를 보면 `OR`이나 `'`는 filtering 하지 않음을 알 수가 있다. 또한 `#`을 url encoding한 `%23`을 이용하여 `pw`입력 부분을 주석으로 만들면 문제는 쉽게 풀린다.

`https://los.eagle-jump.org/gremlin_bbc5af7bed14aa50b84986f2de742f31.php?id=' or 1=1 %23`

![placeholder](https://github.com/ykdy3951/ykdy3951.github.io/blob/master/_src/SQLinjection/1/2.png?raw=true 'solve!')
