---
date: 2020-05-17 06:54:03
layout: post
title: "Forensics basic"
subtitle: 
description: "Icewall 포렌식 기초"
image: https://raw.githubusercontent.com/ykdy3951/ykdy3951.github.io/master/_src/forensics.jpg
optimized_image: https://raw.githubusercontent.com/ykdy3951/ykdy3951.github.io/master/_src/forensics.jpg
category: forensics
tags:
  - forensics
  - icewall
  - CTF study
author: ykdy3951
paginate: false
---

ICEWALL CTF - forensics homework

> forensics homework
> 준비물 : 잠겨진 zip 파일, 010 editor

zip파일을 열어보면 flag.txt만 잠겨 있다는 것을 알 수 있다.

잠겨있는 flag.txt을 열어보기 위해서 010 editor 가지고 zip 파일을 열어 보았다.


flag.txt의 dirEntry에 ushort deFlags 부분의 value가 1이므로 잠겨있다는 것을 확인했고 이를 0으로 overwrite 하면 

flag.txt파일을 열어서 flag를 확인할 수 있다!
![placeholder](https://placehold.it/200x200 "flag.txt")

flag{당신은 이제 어엿한 포렌서입니다!!!}