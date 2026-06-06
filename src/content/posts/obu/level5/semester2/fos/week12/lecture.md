---
title: "Foundations of Security Week12 Lecture"
published: 2026-05-26
# updated: 
description: "Revision"
image: ./145464450.png
tags: []
category: Foundations of Security
draft: false
pinned: false
# slug: 
lang: en
author: 🐦‍🔥不死鸟Anka
comment: true
# licenseName: 
# licenseUrl: 
# sourceLink: 
---

## Ethical Hacking ([Week1 Seminar](/posts/obu/level5/semester2/fos/week1/seminar/))

softwares mentioned:
- nmap
- nexpose
- metasploit
- wireshark
- hping

brute force - 暴力破解 不属于Ethical Hacking

## Modular Multiplicative Inverse ([Week4 Lecture](/posts/obu/level5/semester2/fos/week4/lecture/#modular-multiplicative-inverse))

a和m必须互质才能找到x

## Fermat's Theorem ([Week3 Lecture](/posts/obu/level5/semester2/fos/week3/lecture/#fermats-theorem))

## Euler's Totient Function ([Week3 Lecture](/posts/obu/level5/semester2/fos/week3/lecture/#eulers-totient-function))

重要结论：
- $\phi(p^k)=p^k-p^{k-1}$
- $\phi(ab)=\phi(a)\cdot\phi(b)$

## RSA Algorithm ([Week4 Lecture](/posts/obu/level5/semester2/fos/week4/lecture/#rsa-algorithm) and [Week5](/posts/obu/level5/semester2/fos/week5/lecture/))

## Chosen Ciphertext Attacks (CCA) on RSA Algorithm ([Week5](/posts/obu/level5/semester2/fos/week5/lecture/#chosen-ciphertext-attacks-cca-on-rsa-algorithm))

## ElGamal Encryption ([Week7 Lecture](/posts/obu/level5/semester2/fos/week7/lecture/#elgamal-encryption))

3. Compute the ciphertext pair: 
    - $\textcolor{blue}{c_1 = g^k \bmod p}$ (this hides 𝑘 and is sent as part of the ciphertext).
    - $\textcolor{blue}{c_2 = m \cdot y^k \bmod p}$ (this encrypts the message using the recipient’s public key).

## Diffie-Hellman Key Exchange ([Week7 Lecture](/posts/obu/level5/semester2/fos/week7/lecture/#diffie-hellman-key-exchange))

## Data Encryption Standard (DES) ([Week8 Lecture](/posts/obu/level5/semester2/fos/week8/lecture/) and [Week9 Lecture](/posts/obu/level5/semester2/fos/week9/lecture/))

## Advanced Encryption Standard (AES) ([Week9 Lecture](/posts/obu/level5/semester2/fos/week9/lecture/#advanced-encryption-standard-aes), [Week10 Lecture](/posts/obu/level5/semester2/fos/week10/lecture/) and [Week11 Lecture](/posts/obu/level5/semester2/fos/week11/lecture/))
### Rotword and Subword ([Week10 Lecture](/posts/obu/level5/semester2/fos/week10/lecture/#function-gtextcolorbluegg))
### Initial AddRoundKey ([Week10 Lecture](/posts/obu/level5/semester2/fos/week10/lecture/#initial-round-addroundkey))
Subkey 0 is the original key
### Galois Field ([Week10 Lecture](/posts/obu/level5/semester2/fos/week10/lecture/#reading-assignment-and-optional-group-presentation), Optional Presentation and [Week11 Lecture](/posts/obu/level5/semester2/fos/week11/lecture/))
### Mix Columns ([Week11 Lecture](/posts/obu/level5/semester2/fos/week11/lecture/))
irreducible polynomial: $x^8+x^4+x^3+x+1$ -> $x^8=x^4+x^3+x+1$

- 多项式形式
- 二进制（8bit）
- 十六进制

## Chinese Remainder Theorem ([Week4 Lecture](/posts/obu/level5/semester2/fos/week4/lecture/#chinese-remainder-theorem))
