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

> 준비물 : 잠겨진 zip 파일, 010 editor

zip파일을 열어보면 <strong>flag.txt</strong>만 잠겨 있다는 것을 알 수 있다.
![placeholder](https://github.com/ykdy3951/ykdy3951.github.io/blob/master/_src/post_200517/image1.png?raw=true "포렌식 과제.zip")


잠겨있는 <strong>flag.txt</strong>t을 열어보기 위해서 `010 editor` 가지고 zip 파일을 열어 보았다.
![placeholder](https://github.com/ykdy3951/ykdy3951.github.io/blob/master/_src/post_200517/image2.png?raw=true "before overwrite with 010 editor")

<strong>flag.txt</strong>의 dirEntry에 ushort deFlags 부분의 <ins>value</ins>가 1이므로 잠겨있다는 것을 확인했고 이를 0으로 overwrite 하면 
![placeholder](https://github.com/ykdy3951/ykdy3951.github.io/blob/master/_src/post_200517/image3.png?raw=true "after overwrite with 010 editor")

<strong>flag.txt</strong>파일을 열어서 `flag`를 확인할 수 있다!
![placeholder](https://github.com/ykdy3951/ykdy3951.github.io/blob/master/_src/post_200517/image4.png?raw=true "flag.txt")

`flag{당신은 이제 어엿한 포렌서입니다!!!}`