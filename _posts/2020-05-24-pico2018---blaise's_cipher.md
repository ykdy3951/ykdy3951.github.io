---
date: 2020-05-24 14:31:23
layout: post
title: "pico2018 - blaise\'s_cipher"
subtitle: 'Solving Cryptography problem!'
description: 'Cryptography problem in https://2018game.picoctf.com/ '
image: https://raw.githubusercontent.com/ykdy3951/ykdy3951.github.io/master/_src/picoCTF/image.png
optimized_image: https://raw.githubusercontent.com/ykdy3951/ykdy3951.github.io/master/_src/picoCTF/image.png
category: Cryptography
tags:
  - picoCTF
  - '2018'
  - Cryptography
author: ykdy3951
paginate: false
---

# 2018 picoCTF - Cryptography

> 문제 : [blaise's cipher](https://2018game.picoctf.com/problems).

문제

![placeholder](https://github.com/ykdy3951/ykdy3951.github.io/blob/master/_src/picoCTF/2018/Cryptography/6/1.png?raw=true 'problem')

solution

`nc 2018shell.picoctf.com 26039`에 접속하면 Encrypt된 message가 나온다.

문제를 보고 blaise cipher를 검색 했더니 vigenere cipher가 맨 먼져 보였고 이걸 이용해서 풀면 되겠다는 생각을 했다.

`nc 2018shell.picoctf.com 26039`에 접속해서 나온 Encrypted message를 이 사이트([vigenere solver](https://www.guballa.de/vigenere-solver))에 입력을 했더니 암호화 하는데 썼던 key는 `flag`이라는 것과 decrypt된 message를 얻을 수 있다.

![placeholder](https://github.com/ykdy3951/ykdy3951.github.io/blob/master/_src/picoCTF/2018/Cryptography/6/2.png?raw=true 'solve!')

flag = `picoCTF{v1gn3r3_c1ph3rs_ar3n7_bad_901e13a1}`
