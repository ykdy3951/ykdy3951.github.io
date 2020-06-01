---
date: 2020-05-28 09:46:11
layout: post
title: 'pico2018 - caesar cipher 1'
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
comments: true
---

# 2018 picoCTF - Cryptography

> 문제 : [caesar cipher 1](https://2018game.picoctf.com/problems).

### 문제

![placeholder](https://github.com/ykdy3951/ykdy3951.github.io/blob/master/_src/picoCTF/2018/Cryptography/4/1.png?raw=true 'problem')

### solution

[caesar cipher 1](https://2018shell.picoctf.com/static/8b8d9e1fd4c9cd66facc3794d9c69175/ciphertext)을 다운 받으면 Encrypt된 message가 나온다.

`picoCTF{payzgmuujurjigkygxiovnkxlcgihubb}`

`payzgmuujurjigkygxiovnkxlcgihubb` decrypt해야하는 message가 이거 인것을 알았고 caesar cipher을 decrypt을 하면 된다.

우선 caesar cipher에 대해서 알아보자. [About caesar cipher](https://learncryptography.com/classical-encryption/caesar-cipher)

위의 message의 암호화한 key를 모르므로 brute-force attack을 이용해서 해야한다.

아래는 brute-force 코드이다.

### Solution code

```python
import string

Letter = string.ascii_lowercase

encryptMessage = "payzgmuujurjigkygxiovnkxlcgihubb"

for key in range(len(Letter)):
    translated = ''
    for symbol in encryptMessage:
        if symbol in Letter:
            num = Letter.find(symbol)
            num = num - key
            if num < 0:
                num = num + len(Letter)
            translated = translated + Letter[num]
        else:
            translated = translated + symbol
    print(f'Key #{key}: {translated}')
```

#### 실행결과

```s
 caesar_cipher_1/solution.py
Key #0: payzgmuujurjigkygxiovnkxlcgihubb
Key #1: ozxyflttitqihfjxfwhnumjwkbfhgtaa
Key #2: nywxeksshsphgeiwevgmtlivjaegfszz
Key #3: mxvwdjrrgrogfdhvduflskhuizdferyy
Key #4: lwuvciqqfqnfecguctekrjgthycedqxx
Key #5: kvtubhppepmedbftbsdjqifsgxbdcpww
Key #6: justagoodoldcaesarcipherfwacbovv
Key #7: itrszfnncnkcbzdrzqbhogdqevzbanuu
Key #8: hsqryemmbmjbaycqypagnfcpduyazmtt
Key #9: grpqxdllaliazxbpxozfmeboctxzylss
Key #10: fqopwckkzkhzywaownyeldanbswyxkrr
Key #11: epnovbjjyjgyxvznvmxdkczmarvxwjqq
Key #12: domnuaiixifxwuymulwcjbylzquwvipp
Key #13: cnlmtzhhwhewvtxltkvbiaxkyptvuhoo
Key #14: bmklsyggvgdvuswksjuahzwjxosutgnn
Key #15: aljkrxffufcutrvjritzgyviwnrtsfmm
Key #16: zkijqweetebtsquiqhsyfxuhvmqsrell
Key #17: yjhipvddsdasrpthpgrxewtgulprqdkk
Key #18: xighouccrczrqosgofqwdvsftkoqpcjj
Key #19: whfgntbbqbyqpnrfnepvcuresjnpobii
Key #20: vgefmsaapaxpomqemdoubtqdrimonahh
Key #21: ufdelrzzozwonlpdlcntaspcqhlnmzgg
Key #22: tecdkqyynyvnmkockbmszrobpgkmlyff
Key #23: sdbcjpxxmxumljnbjalryqnaofjlkxee
Key #24: rcabiowwlwtlkimaizkqxpmzneikjwdd
```

brute-force의 결과 key와 decrypt된 message를 확인할 수 있었다.

### Answer

`Key #6: justagoodoldcaesarcipherfwacbovv`

### flag

`picoCTF{justagoodoldcaesarcipherfwacbovv}`
