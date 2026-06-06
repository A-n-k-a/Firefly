---
title: "Foundations of Security Revision Notes - Bilingual"
published: 2026-06-06
description: "English-Chinese revision notes for Foundations of Security, focusing on calculation steps for cryptographic algorithms."
image: ./124984225.jpg
tags: []
category: Foundations of Security
draft: false
pinned: false
lang: en
author: "ChatGPT"
comment: true
---

> 此文章由 GPT-5.5 生成。ChatGPT 也可能会犯错。请核查重要信息。

# Foundations of Security Revision Notes / 信息安全基础复习笔记

## 1. Security Basics / 安全基础

**Week 1:** The three main security goals are confidentiality, integrity, and availability. Confidentiality means only authorised users can read the data. Integrity means data is not modified, inserted, deleted, or replayed without authorisation. Availability means authorised users can access systems and data when needed.

**第 1 周：** 三个核心安全目标是机密性、完整性和可用性。机密性表示只有授权用户能读取数据；完整性表示数据不会被未授权修改、插入、删除或重放；可用性表示授权用户在需要时可以访问系统和数据。

**Week 1:** Passive attacks only observe information, such as snooping and traffic analysis. Active attacks modify or disrupt the system, such as modification, masquerading, replaying, repudiation, and denial of service.

**第 1 周：** 被动攻击只观察信息，例如窃听和流量分析。主动攻击会修改或破坏系统，例如篡改、冒充、重放、抵赖和拒绝服务攻击。

**Week 1:** Security services include confidentiality, data integrity, authentication, non-repudiation, and access control. Security mechanisms are the technical methods used to provide these services, such as encryption, signatures, hashing, and access checks.

**第 1 周：** 安全服务包括机密性、数据完整性、认证、不可抵赖性和访问控制。安全机制是实现这些服务的技术方法，例如加密、数字签名、哈希和访问检查。

## 2. Number Theory for Cryptography / 密码学数论基础

**Week 2:** The greatest common divisor, $gcd(a, b)$, is the largest positive integer that divides both $a$ and $b$ with no remainder. Two numbers are co-prime if their GCD is 1. This matters because modular inverses and RSA public exponents require co-prime values.

**第 2 周：** 最大公因数 $gcd(a, b)$ 是能同时整除 $a$ 和 $b$ 的最大正整数。若两个数的 GCD 为 1，则它们互素。这很重要，因为模逆元和 RSA 公钥指数都要求相关数字互素。

**Week 2:** Euclid's algorithm repeatedly divides and keeps the remainder until the remainder becomes 0. Example: $56 = 32(1) + 24$, $32 = 24(1) + 8$, $24 = 8(3) + 0$, so $gcd(56, 32) = 8$.

**第 2 周：** 欧几里得算法不断做带余除法，直到余数为 0。例：$56 = 32(1) + 24$，$32 = 24(1) + 8$，$24 = 8(3) + 0$，所以 $gcd(56, 32) = 8$。

**Week 2:** The Extended Euclidean Algorithm expresses the GCD as a linear combination: $ax + by = gcd(a, b)$. Example: $34 = 12(2) + 10$, $12 = 10(1) + 2$, so $2 = 12 - 10 = 12 - (34 - 2\cdot 12) = 3\cdot 12 - 34$. Therefore $x = 3$, $y = -1$.

**第 2 周：** 扩展欧几里得算法把 GCD 表示成线性组合：$ax + by = gcd(a, b)$。例：$34 = 12(2) + 10$，$12 = 10(1) + 2$，所以 $2 = 12 - 10 = 12 - (34 - 2\cdot 12) = 3\cdot 12 - 34$。因此 $x = 3$，$y = -1$。

**Week 2:** Modular arithmetic uses remainders. $a \bmod n$ is the remainder after dividing $a$ by $n$. Example: $16 \bmod 12 = 4$, so $16 ≡ 4 (\bmod 12)$.

**第 2 周：** 模运算使用余数。$a \bmod n$ 表示 $a$ 除以 $n$ 后的余数。例：$16 \bmod 12 = 4$，所以 $16 ≡ 4 (\bmod 12)$。

**Week 2:** Useful modular rules are $(a + b) \bmod n = [(a \bmod n) + (b \bmod n)] \bmod n$, $(a - b) \bmod n = [(a \bmod n) - (b \bmod n)] \bmod n$, and $(ab) \bmod n = [(a \bmod n)(b \bmod n)] \bmod n$.

**第 2 周：** 常用模运算规则有：$(a + b) \bmod n = [(a \bmod n) + (b \bmod n)] \bmod n$，$(a - b) \bmod n = [(a \bmod n) - (b \bmod n)] \bmod n$，$(ab) \bmod n = [(a \bmod n)(b \bmod n)] \bmod n$。

**Week 2:** Fast modular exponentiation squares and reduces repeatedly. Example: $3^10 \bmod 5$: $3^2 \bmod 5 = 9 \bmod 5 = 4$; $3^4 \bmod 5 = 4^2 \bmod 5 = 16 \bmod 5 = 1$; $3^8 \bmod 5 = 1$; $3^10 = 3^8 \cdot 3^2$, so result is $1 \cdot 4 \bmod 5 = 4$.

**第 2 周：** 快速模幂通过反复平方并取模来简化计算。例：$3^10 \bmod 5$：$3^2 \bmod 5 = 9 \bmod 5 = 4$；$3^4 \bmod 5 = 4^2 \bmod 5 = 16 \bmod 5 = 1$；$3^8 \bmod 5 = 1$；$3^10 = 3^8 \cdot 3^2$，所以结果为 $1 \cdot 4 \bmod 5 = 4$。

**Week 3:** Fermat's Little Theorem says if $p$ is prime and $p$ does not divide $a$, then $a^{p-1} ≡ 1 (\bmod p)$. Example: since 523 is prime, $213^522 \bmod 523 = 1$.

**第 3 周：** 费马小定理：如果 $p$ 是质数且 $p$ 不整除 $a$，则 $a^{p-1} ≡ 1 (\bmod p)$。例：523 是质数，所以 $213^522 \bmod 523 = 1$。

**Week 3:** Euler's totient function $\phi(n)$ counts the integers from 1 to $n$ that are co-prime to $n$. If $p$ is prime, $\phi(p) = p - 1$. If $p$ is prime, $\phi(p^k) = p^k - p^{k-1}$. If $a$ and $b$ are co-prime, $\phi(ab) = \phi(a)\phi(b)$.

**第 3 周：** 欧拉函数 $\phi(n)$ 统计 1 到 $n$ 中与 $n$ 互素的整数个数。若 $p$ 为质数，则 $\phi(p) = p - 1$。若 $p$ 为质数，则 $\phi(p^k) = p^k - p^{k-1}$。若 $a$ 与 $b$ 互素，则 $\phi(ab) = \phi(a)\phi(b)$。

**Week 3:** Euler's theorem says if $gcd(a, m) = 1$, then $a^\phi(m) ≡ 1 (\bmod m)$. Example: $\phi(10) = \phi(2)\phi(5) = 1 \cdot 4 = 4$, so $3^4 \bmod 10 = 81 \bmod 10 = 1$.

**第 3 周：** 欧拉定理：若 $gcd(a, m) = 1$，则 $a^\phi(m) ≡ 1 (\bmod m)$。例：$\phi(10) = \phi(2)\phi(5) = 1 \cdot 4 = 4$，所以 $3^4 \bmod 10 = 81 \bmod 10 = 1$。

**Week 4:** A modular multiplicative inverse of $a \bmod m$ is a number $x$ such that $ax ≡ 1 (\bmod m)$. It exists only when $gcd(a, m) = 1$. Example: $3x ≡ 1 (\bmod 17)$. Extended Euclid gives $1 = 3(6) + 17(-1)$, so $x = 6$.

**第 4 周：** $a \bmod m$ 的模乘逆元是一个数 $x$，满足 $ax ≡ 1 (\bmod m)$。只有当 $gcd(a, m) = 1$ 时逆元存在。例：$3x ≡ 1 (\bmod 17)$。扩展欧几里得得 $1 = 3(6) + 17(-1)$，所以 $x = 6$。

**Week 4:** The Chinese Remainder Theorem solves simultaneous congruences when moduli are pairwise co-prime. For $x ≡ a_i (\bmod m_i)$, compute $M = m1\cdot m2\cdot \ldots$, $M_i = M/m_i$, find $y_i$ where $M_i\cdot y_i ≡ 1 (\bmod m_i)$, then $x = sum(a_i\cdot M_i\cdot y_i) \bmod M$.

**第 4 周：** 中国剩余定理用于求解模数两两互素的同余方程组。对于 $x ≡ a_i (\bmod m_i)$，先算 $M = m1\cdot m2\cdot \ldots$，再算 $M_i = M/m_i$，找 $y_i$ 使 $M_i\cdot y_i ≡ 1 (\bmod m_i)$，最后 $x = sum(a_i\cdot M_i\cdot y_i) \bmod M$。

**Week 4:** Example CRT: $x ≡ 2 (\bmod 3)$, $x ≡ 3 (\bmod 5)$, $x ≡ 2 (\bmod 7)$. $M = 105$; $M1 = 35$, $M2 = 21$, $M3 = 15$; inverses are $y1 = 2$, $y2 = 1$, $y3 = 1$. Therefore $x = (2\cdot 35\cdot 2 + 3\cdot 21\cdot 1 + 2\cdot 15\cdot 1) \bmod 105 = 233 \bmod 105 = 23$.

**第 4 周：** CRT 例题：$x ≡ 2 (\bmod 3)$，$x ≡ 3 (\bmod 5)$，$x ≡ 2 (\bmod 7)$。$M = 105$；$M1 = 35$，$M2 = 21$，$M3 = 15$；逆元为 $y1 = 2$，$y2 = 1$，$y3 = 1$。所以 $x = (2\cdot 35\cdot 2 + 3\cdot 21\cdot 1 + 2\cdot 15\cdot 1) \bmod 105 = 233 \bmod 105 = 23$。

## 3. RSA / RSA 算法

**Weeks 4-5:** RSA key generation: choose two primes $p$ and $q$; compute $n = pq$; compute $\phi(n) = (p - 1)(q - 1)$; choose public exponent $e$ such that $1 < e < \phi(n)$ and $gcd(e, \phi(n)) = 1$; compute private exponent $d$ such that $ed ≡ 1 (\bmod \phi(n))$. Public key is $(n, e)$, private key is $(n, d)$.

**第 4-5 周：** RSA 密钥生成：选择两个质数 $p$ 和 $q$；计算 $n = pq$；计算 $\phi(n) = (p - 1)(q - 1)$；选择公钥指数 $e$，满足 $1 < e < \phi(n)$ 且 $gcd(e, \phi(n)) = 1$；计算私钥指数 $d$，满足 $ed ≡ 1 (\bmod \phi(n))$。公钥是 $(n, e)$，私钥是 $(n, d)$。

**Weeks 4-5:** RSA encryption uses the recipient's public key: $C = M^e \bmod n$. RSA decryption uses the recipient's private key: $M = C^d \bmod n$.

**第 4-5 周：** RSA 加密使用接收者的公钥：$C = M^e \bmod n$。RSA 解密使用接收者的私钥：$M = C^d \bmod n$。

**Weeks 4-5:** Small RSA example: choose $p = 11$, $q = 3$. Then $n = 33$, $\phi(n) = 20$. Choose $e = 7$, and find $d = 3$ because $7\cdot 3 = 21 ≡ 1 (\bmod 20)$. If $M = 4$, then $C = 4^7 \bmod 33 = 16384 \bmod 33 = 16$. Decrypt: $M = 16^3 \bmod 33 = 4096 \bmod 33 = 4$.

**第 4-5 周：** 小型 RSA 例题：选择 $p = 11$，$q = 3$。则 $n = 33$，$\phi(n) = 20$。选择 $e = 7$，因为 $7\cdot 3 = 21 ≡ 1 (\bmod 20)$，所以 $d = 3$。若 $M = 4$，则 $C = 4^7 \bmod 33 = 16384 \bmod 33 = 16$。解密：$M = 16^3 \bmod 33 = 4096 \bmod 33 = 4$。

**Weeks 4-5:** Alice's lecture example uses $pA = 61$, $qA = 53$, so $nA = 3233$ and $\phi(nA) = 3120$. With $eA = 17$, solve $17dA ≡ 1 (\bmod 3120)$. Extended Euclid gives $dA = 2753$, verified by $17\cdot 2753 = 46801 = 3120\cdot 15 + 1$.

**第 4-5 周：** 讲义中的 Alice 例子使用 $pA = 61$，$qA = 53$，所以 $nA = 3233$，$\phi(nA) = 3120$。取 $eA = 17$，求 $17dA ≡ 1 (\bmod 3120)$。扩展欧几里得得到 $dA = 2753$，验证：$17\cdot 2753 = 46801 = 3120\cdot 15 + 1$。

**Weeks 4-5:** Bob's lecture example uses $pB = 3$, $qB = 11$, so $nB = 33$ and $\phi(nB) = 20$. With $eB = 7$, solve $7dB ≡ 1 (\bmod 20)$. Since $7\cdot 3 = 21 ≡ 1 (\bmod 20)$, $dB = 3$.

**第 4-5 周：** 讲义中的 Bob 例子使用 $pB = 3$，$qB = 11$，所以 $nB = 33$，$\phi(nB) = 20$。取 $eB = 7$，求 $7dB ≡ 1 (\bmod 20)$。因为 $7\cdot 3 = 21 ≡ 1 (\bmod 20)$，所以 $dB = 3$。

**Weeks 4-5:** If Alice sends $M = 2$ to Bob, she uses Bob's public key $(nB = 33, eB = 7)$: $C = 2^7 \bmod 33 = 128 \bmod 33 = 29$. Bob decrypts with $dB = 3$: $M = 29^3 \bmod 33 = 24389 \bmod 33 = 2$.

**第 4-5 周：** 如果 Alice 给 Bob 发送 $M = 2$，她使用 Bob 的公钥 $(nB = 33, eB = 7)$：$C = 2^7 \bmod 33 = 128 \bmod 33 = 29$。Bob 用 $dB = 3$ 解密：$M = 29^3 \bmod 33 = 24389 \bmod 33 = 2$。

**Week 5:** Chosen Ciphertext Attack on plain RSA exploits multiplicative structure. If original ciphertext is $C$, attacker chooses random $r$ co-prime to $n$ and computes $C' = C\cdot r^e \bmod n$. The decrypted response is $Res = (C')^d \bmod n = M\cdot r \bmod n$. The attacker computes $M = Res\cdot r^{-1} \bmod n$.

**第 5 周：** 对原始 RSA 的选择密文攻击利用了 RSA 的乘法结构。若原密文为 $C$，攻击者选择与 $n$ 互素的随机数 $r$，计算 $C' = C\cdot r^e \bmod n$。解密响应为 $Res = (C')^d \bmod n = M\cdot r \bmod n$。攻击者再计算 $M = Res\cdot r^{-1} \bmod n$。

**Week 5:** Lecture CCA example: $M = 2$, $C = 29$, Bob's public key $(e = 7, n = 33)$, choose $r = 2$. Compute $C' = 29\cdot 2^7 \bmod 33 = 29\cdot 128 \bmod 33 = 16$. Bob decrypts $Res = 16^3 \bmod 33 = 4$. Since $2^{-1} \bmod 33 = 17$, recover $M = 4\cdot 17 \bmod 33 = 68 \bmod 33 = 2$.

**第 5 周：** 讲义 CCA 例题：$M = 2$，$C = 29$，Bob 公钥 $(e = 7, n = 33)$，选择 $r = 2$。计算 $C' = 29\cdot 2^7 \bmod 33 = 29\cdot 128 \bmod 33 = 16$。Bob 解密得 $Res = 16^3 \bmod 33 = 4$。因为 $2^{-1} \bmod 33 = 17$，恢复 $M = 4\cdot 17 \bmod 33 = 68 \bmod 33 = 2$。

## 4. Classical Ciphers / 古典密码

**Week 6:** Caesar Cipher shifts every plaintext letter by a fixed key $k$. Use $A = 0, B = 1, \ldots, Z = 25$. Encryption is $C = (p + k) \bmod 26$; decryption is $p = (C - k) \bmod 26$.

**第 6 周：** Caesar 密码把每个明文字母按固定密钥 $k$ 平移。采用 $A = 0, B = 1, \ldots, Z = 25$。加密公式为 $C = (p + k) \bmod 26$；解密公式为 $p = (C - k) \bmod 26$。

**Week 6:** Example: with shift $k = 3$, $A \to D$, $B \to E$, and $P \to S$. To brute-force Caesar, try all 25 possible shifts and look for readable English. The lecture ciphertext `PHHW PH DIWHU WKH WRJD SDUWB` decrypts with key 3 to `MEET ME AFTER THE TOGA PARTY`.

**第 6 周：** 例：平移 $k = 3$ 时，$A \to D$，$B \to E$，$P \to S$。暴力破解 Caesar 时，尝试全部 25 个可能平移量并寻找可读英文。讲义密文 `PHHW PH DIWHU WKH WRJD SDUWB` 用密钥 3 解密为 `MEET ME AFTER THE TOGA PARTY`。

**Week 6:** Monoalphabetic substitution uses one fixed one-to-one mapping from plaintext alphabet to ciphertext alphabet. Example key begins $A \to Q$, $B \to W$, $C \to E$, $D \to R$, $E \to T$. Using that mapping, `HELLO` becomes `ITSSG`. Decryption reverses the mapping.

**第 6 周：** 单表替换密码使用一个固定的一一映射，把明文字母映射到密文字母。例子密钥开头为 $A \to Q$，$B \to W$，$C \to E$，$D \to R$，$E \to T$。按该映射，`HELLO` 变为 `ITSSG`。解密时反向查表。

**Week 6:** Monoalphabetic substitution is vulnerable to frequency analysis because the same plaintext letter always becomes the same ciphertext letter. Common letters such as `E` in English often reveal the mapping.

**第 6 周：** 单表替换容易受到频率分析攻击，因为同一个明文字母总是变成同一个密文字母。英语中 `E` 等高频字母常常会暴露映射关系。

**Week 6:** Vigenere Cipher is polyalphabetic. Repeat the keyword until it matches the plaintext length, convert letters to numbers, then compute $C_i = (p_i + k_i) \bmod 26$. Decryption is $p_i = (C_i - k_i) \bmod 26$.

**第 6 周：** Vigenere 密码是多表替换密码。先把关键词重复到与明文长度相同，把字母转成数字，再计算 $C_i = (p_i + k_i) \bmod 26$。解密为 $p_i = (C_i - k_i) \bmod 26$。

**Week 6:** Example: encrypt `HELLO` with key `KEY`. Repeat key as `KEYKE`. Values: $H(7)+K(10)=17 \to R$; $E(4)+E(4)=8 \to I$; $L(11)+Y(24)=35 \bmod 26 = 9 \to J$; $L(11)+K(10)=21 \to V$; $O(14)+E(4)=18 \to S$. Ciphertext is `RIJVS`.

**第 6 周：** 例：用密钥 `KEY` 加密 `HELLO`。重复密钥为 `KEYKE`。计算：$H(7)+K(10)=17 \to R$；$E(4)+E(4)=8 \to I$；$L(11)+Y(24)=35 \bmod 26 = 9 \to J$；$L(11)+K(10)=21 \to V$；$O(14)+E(4)=18 \to S$。密文为 `RIJVS`。

**Week 6:** Another Vigenere example from the lecture: key `deceptivedeceptivedeceptive`, plaintext `wearediscoveredsaveyourself`, ciphertext `zicvtwqngrzgvtwavzhcqyglmgj`. The calculation is still letter-by-letter addition modulo 26.

**第 6 周：** 讲义另一个 Vigenere 例子：密钥 `deceptivedeceptivedeceptive`，明文 `wearediscoveredsaveyourself`，密文 `zicvtwqngrzgvtwavzhcqyglmgj`。计算本质仍是逐字母相加并对 26 取模。

## 5. Symmetric Key, Diffie-Hellman, ElGamal, and Signatures / 对称密钥、DH、ElGamal 与签名

**Week 6:** Symmetric key encryption uses the same secret key for encryption and decryption. It is fast, but the key distribution problem is serious: if the shared key is sent over a public channel and intercepted, all communication protected by that key is compromised.

**第 6 周：** 对称密钥加密使用同一个秘密密钥进行加密和解密。它速度快，但密钥分发问题严重：如果共享密钥通过公共信道发送并被截获，那么该密钥保护的所有通信都可能被破解。

**Week 7:** Diffie-Hellman lets two users create a shared secret over a public channel. Public values are prime $p$ and generator $g$. Alice chooses secret $a$ and sends $A = g^a \bmod p$; Bob chooses secret $b$ and sends $B = g^b \bmod p$. Alice computes $K = B^a \bmod p$; Bob computes $K = A^b \bmod p$. Both equal $g^{ab} \bmod p$.

**第 7 周：** Diffie-Hellman 允许两个用户在公共信道上建立共享秘密。公开值为质数 $p$ 和生成元 $g$。Alice 选择秘密 $a$ 并发送 $A = g^a \bmod p$；Bob 选择秘密 $b$ 并发送 $B = g^b \bmod p$。Alice 计算 $K = B^a \bmod p$；Bob 计算 $K = A^b \bmod p$。两者都等于 $g^{ab} \bmod p$。

**Week 7:** Lecture DH quiz: $p = 11$, $g = 2$, Alice secret $S_A = 3$, Bob secret $S_B = 4$. Alice public value is $C_A = 2^3 \bmod 11 = 8$; Bob public value is $C_B = 2^4 \bmod 11 = 16 \bmod 11 = 5$. Shared key is $C_B^{S_A} \bmod 11 = 5^3 \bmod 11 = 125 \bmod 11 = 4$, also $C_A^{S_B} \bmod 11 = 8^4 \bmod 11 = 4$.

**第 7 周：** 讲义 DH 小测：$p = 11$，$g = 2$，Alice 秘密 $S_A = 3$，Bob 秘密 $S_B = 4$。Alice 公共值 $C_A = 2^3 \bmod 11 = 8$；Bob 公共值 $C_B = 2^4 \bmod 11 = 16 \bmod 11 = 5$。共享密钥为 $C_B^{S_A} \bmod 11 = 5^3 \bmod 11 = 125 \bmod 11 = 4$，也等于 $C_A^{S_B} \bmod 11 = 8^4 \bmod 11 = 4$。

**Week 7:** ElGamal key generation: choose prime $p$, generator $g$, private key $x$, and compute public key $y = g^x \bmod p$. Public key is $(p, g, y)$, private key is $x$.

**第 7 周：** ElGamal 密钥生成：选择质数 $p$、生成元 $g$、私钥 $x$，计算公钥 $y = g^x \bmod p$。公钥为 $(p, g, y)$，私钥为 $x$。

**Week 7:** ElGamal encryption of message $m$: choose random session key $k$; compute $c_1 = g^k \bmod p$; compute $c_2 = m\cdot y^k \bmod p$; ciphertext is $(c_1, c_2)$. Decryption: compute $s = c_1^x \bmod p$, find $s^{-1} \bmod p$, then recover $m = c_2\cdot s^{-1} \bmod p$.

**第 7 周：** ElGamal 加密消息 $m$：选择随机会话密钥 $k$；计算 $c_1 = g^k \bmod p$；计算 $c_2 = m\cdot y^k \bmod p$；密文为 $(c_1, c_2)$。解密：计算 $s = c_1^x \bmod p$，求 $s^{-1} \bmod p$，再恢复 $m = c_2\cdot s^{-1} \bmod p$。

**Week 7:** ElGamal lecture quiz calculation: $p = 23$, $g = 5$, public key $Y = 4$, random $k = 3$, message $M = 15$. $c_1 = 5^3 \bmod 23 = 125 \bmod 23 = 10$. $Y^k = 4^3 \bmod 23 = 64 \bmod 23 = 18$. $c_2 = 15\cdot 18 \bmod 23 = 270 \bmod 23 = 17$. Ciphertext is $(10, 17)$.

**第 7 周：** ElGamal 讲义小测计算：$p = 23$，$g = 5$，公钥 $Y = 4$，随机数 $k = 3$，消息 $M = 15$。$c_1 = 5^3 \bmod 23 = 125 \bmod 23 = 10$。$Y^k = 4^3 \bmod 23 = 64 \bmod 23 = 18$。$c_2 = 15\cdot 18 \bmod 23 = 270 \bmod 23 = 17$。密文为 $(10, 17)$。

**Week 7:** A digital signature proves authenticity, integrity, and non-repudiation. The sender signs using the sender's private key, and the receiver verifies using the sender's public key.

**第 7 周：** 数字签名用于证明真实性、完整性和不可抵赖性。发送者用自己的私钥签名，接收者用发送者的公钥验证。

**Week 7:** RSA signature example: choose $p = 3$, $q = 17$, so $n = 51$, $\phi(n) = 32$; choose $e = 5$; find $d = 13$ because $5\cdot 13 = 65 ≡ 1 (\bmod 32)$. For hash $h = 2$, signature is $s = h^d \bmod n = 2^13 \bmod 51 = 8192 \bmod 51 = 32$. Verify by $h' = s^e \bmod n = 32^5 \bmod 51 = 2$; since $h' = h$, signature is valid.

**第 7 周：** RSA 签名例题：选择 $p = 3$，$q = 17$，所以 $n = 51$，$\phi(n) = 32$；选择 $e = 5$；因为 $5\cdot 13 = 65 ≡ 1 (\bmod 32)$，所以 $d = 13$。对于哈希值 $h = 2$，签名为 $s = h^d \bmod n = 2^13 \bmod 51 = 8192 \bmod 51 = 32$。验证时计算 $h' = s^e \bmod n = 32^5 \bmod 51 = 2$；因为 $h' = h$，签名有效。

## 6. Feistel Cipher and DES / Feistel 结构与 DES

**Week 7:** A Feistel cipher splits a block into left and right halves. Each round computes $L_i = R_{i-1}$ and $R_i = L_{i-1} \oplus F(R_{i-1}, K_i)$. Decryption uses the same structure but applies subkeys in reverse order.

**第 7 周：** Feistel 密码把一个分组拆成左右两半。每轮计算 $L_i = R_{i-1}$，$R_i = L_{i-1} \oplus F(R_{i-1}, K_i)$。解密使用相同结构，但子密钥顺序反过来。

**Week 7:** Feistel example: plaintext is $\texttt{1010 1100 0110 0011}$, so $L_0 = \texttt{1010 1100}$ and $R_0 = \texttt{0110 0011}$. $K_1 = \texttt{1100 1010}$, $K_2 = \texttt{0011 0101}$. Round function is $R \oplus K$, then left circular shift by 2 bits.

**第 7 周：** Feistel 例题：明文为 $\texttt{1010 1100 0110 0011}$，所以 $L_0 = \texttt{1010 1100}$，$R_0 = \texttt{0110 0011}$。$K_1 = \texttt{1100 1010}$，$K_2 = \texttt{0011 0101}$。轮函数为 $R \oplus K$ 后循环左移 2 位。

**Week 7:** Feistel round 1: $R_0 \oplus K_1 = \texttt{0110 0011} \oplus \texttt{1100 1010} = \texttt{1010 1001}$; left shift 2 gives $\texttt{1010 0110}$; then $R_1 = L_0 \oplus F = \texttt{1010 1100} \oplus \texttt{1010 0110} = \texttt{0000 1010}$; $L_1 = R_0 = \texttt{0110 0011}$.

**第 7 周：** Feistel 第 1 轮：$R_0 \oplus K_1 = \texttt{0110 0011} \oplus \texttt{1100 1010} = \texttt{1010 1001}$；循环左移 2 位得 $\texttt{1010 0110}$；然后 $R_1 = L_0 \oplus F = \texttt{1010 1100} \oplus \texttt{1010 0110} = \texttt{0000 1010}$；$L_1 = R_0 = \texttt{0110 0011}$。

**Week 7:** Feistel round 2: $R_1 \oplus K_2 = \texttt{0000 1010} \oplus \texttt{0011 0101} = \texttt{0011 1111}$; left shift 2 gives $\texttt{1111 1100}$; $R_2 = L_1 \oplus F = \texttt{0110 0011} \oplus \texttt{1111 1100} = \texttt{1001 1111}$; $L_2 = R_1 = \texttt{0000 1010}$. Ciphertext is $L_2 \parallel R_2 = \texttt{0000 1010 1001 1111}$.

**第 7 周：** Feistel 第 2 轮：$R_1 \oplus K_2 = \texttt{0000 1010} \oplus \texttt{0011 0101} = \texttt{0011 1111}$；循环左移 2 位得 $\texttt{1111 1100}$；$R_2 = L_1 \oplus F = \texttt{0110 0011} \oplus \texttt{1111 1100} = \texttt{1001 1111}$；$L_2 = R_1 = \texttt{0000 1010}$。密文为 $L_2 \parallel R_2 = \texttt{0000 1010 1001 1111}$。

**Weeks 8-9:** DES is a symmetric-key block cipher. It encrypts 64-bit blocks using a 56-bit effective key, has 16 Feistel rounds, and uses permutations, expansion, XOR with subkeys, S-box substitution, and P-box permutation.

**第 8-9 周：** DES 是对称密钥分组密码。它用 56 位有效密钥加密 64 位分组，包含 16 轮 Feistel 结构，并使用置换、扩展、与子密钥异或、S-box 替换和 P-box 置换。

**Weeks 8-9:** DES high-level process: start with 64-bit plaintext; apply Initial Permutation (IP); split into $L_0$ and $R_0$; generate 16 subkeys; run 16 Feistel rounds; swap halves; apply Final Permutation (FP/IP inverse); convert final bits to hexadecimal ciphertext.

**第 8-9 周：** DES 总流程：从 64 位明文开始；进行初始置换 IP；拆分为 $L_0$ 和 $R_0$；生成 16 个子密钥；执行 16 轮 Feistel；交换左右半区；执行最终置换 FP/IP 逆；把最终比特转为十六进制密文。

**Weeks 8-9:** DES key schedule: a 64-bit key is permuted by PC-1 and 8 parity bits are removed, leaving 56 bits. Split into $C_0$ and $D_0$, each 28 bits. In each round, rotate $C$ and $D$ left by 1 or 2 bits, then apply PC-2 to select a 48-bit subkey $K_i$.

**第 8-9 周：** DES 密钥调度：64 位密钥经过 PC-1 置换并去掉 8 个奇偶校验位，剩下 56 位。拆成 $C_0$ 和 $D_0$，各 28 位。每轮把 $C$ 和 $D$ 循环左移 1 或 2 位，再用 PC-2 选择 48 位子密钥 $K_i$。

**Weeks 8-9:** DES round formula is the Feistel formula: $L_i = R_{i-1}$ and $R_i = L_{i-1} \oplus F(R_{i-1}, K_i)$. The lecture's first-round inputs include $L_0 = \texttt{1100 1100 0000 0000 1100 1100 1111 1111}$ and $R_0 = \texttt{1111 0000 1010 1010 1111 0000 1010 1010}$.

**第 8-9 周：** DES 轮公式就是 Feistel 公式：$L_i = R_{i-1}$，$R_i = L_{i-1} \oplus F(R_{i-1}, K_i)$。讲义第 1 轮输入包括 $L_0 = \texttt{1100 1100 0000 0000 1100 1100 1111 1111}$，$R_0 = \texttt{1111 0000 1010 1010 1111 0000 1010 1010}$。

**Weeks 8-9:** DES $F$ function calculation: expand the 32-bit $R$ to 48 bits with the E-box; XOR it with the 48-bit subkey; split the result into eight 6-bit chunks; map each chunk through its S-box from 6 bits to 4 bits; concatenate the eight 4-bit outputs into 32 bits; apply the P-box permutation.

**第 8-9 周：** DES 的 $F$ 函数计算：先用 E-box 把 32 位 $R$ 扩展到 48 位；与 48 位子密钥异或；把结果切成 8 个 6 位块；每个块进入对应 S-box，从 6 位映射为 4 位；拼接 8 个 4 位输出成 32 位；最后进行 P-box 置换。

**Weeks 8-9:** DES S-box lookup rule: for a 6-bit input $b_1b_2b_3b_4b_5b_6$, use the outer bits $b_1b_6$ as the row number, and the middle four bits $b_2b_3b_4b_5$ as the column number. Look up the decimal value in the S-box, then convert that value to 4-bit binary.

**第 8-9 周：** DES S-box 查表规则：对于 6 位输入 $b_1b_2b_3b_4b_5b_6$，用外侧两位 $b_1b_6$ 作为行号，用中间四位 $b_2b_3b_4b_5$ 作为列号。查表得到十进制数，再转成 4 位二进制。

**Weeks 8-9:** DES S-box example: $B_1 = \texttt{011000}$. Outer bits are $\texttt{00}$, so row is 0. Middle bits are $\texttt{1100}$, so column is 12. In $S_1$, row 0 column 12 is 5, so output is $\texttt{0101}$.

**第 8-9 周：** DES S-box 例题：$B_1 = \texttt{011000}$。外侧位是 $\texttt{00}$，所以行号为 0。中间位是 $\texttt{1100}$，所以列号为 12。在 $S_1$ 中，第 0 行第 12 列是 5，所以输出为 $\texttt{0101}$。

**Weeks 8-9:** DES first-round lecture example: after E-box and XOR with $K_1$, the 48-bit result is $\texttt{011000 010001 011110 111010 100001 100110 010100 100111}$. After S-boxes and P-box, the lecture gives $F(R_0, K_1) = \texttt{0010 0011 0100 1010 1010 1001 1011 1011}$. Then $R_1 = L_0 \oplus F(R_0, K_1) = \texttt{1110 1111 0100 1010 0110 0101 0100 0100}$, and $L_1 = R_0$.

**第 8-9 周：** DES 第 1 轮讲义例题：经过 E-box 并与 $K_1$ 异或后，48 位结果是 $\texttt{011000 010001 011110 111010 100001 100110 010100 100111}$。经过 S-box 和 P-box 后，讲义给出 $F(R_0, K_1) = \texttt{0010 0011 0100 1010 1010 1001 1011 1011}$。然后 $R_1 = L_0 \oplus F(R_0, K_1) = \texttt{1110 1111 0100 1010 0110 0101 0100 0100}$，且 $L_1 = R_0$。

## 7. AES / AES 高级加密标准

**Weeks 9-11:** AES is a symmetric block cipher. It uses a 128-bit block size and key lengths of 128, 192, or 256 bits. AES-128 has 10 rounds, AES-192 has 12 rounds, and AES-256 has 14 rounds.

**第 9-11 周：** AES 是对称分组密码。它使用 128 位分组，密钥长度可以是 128、192 或 256 位。AES-128 有 10 轮，AES-192 有 12 轮，AES-256 有 14 轮。

**Weeks 9-11:** AES stores a 16-byte block as a 4 by 4 state matrix. The main transformations are SubBytes, ShiftRows, MixColumns, and AddRoundKey. The final round skips MixColumns.

**第 9-11 周：** AES 把 16 字节分组表示为 4x4 状态矩阵。主要变换是 SubBytes、ShiftRows、MixColumns 和 AddRoundKey。最后一轮不执行 MixColumns。

**Weeks 9-11:** AES encryption structure: Key Expansion generates round keys; the initial round XORs the plaintext state with the first round key; each main round performs SubBytes, ShiftRows, MixColumns, and AddRoundKey; the final round performs SubBytes, ShiftRows, and AddRoundKey only.

**第 9-11 周：** AES 加密结构：Key Expansion 生成轮密钥；初始轮把明文状态与第一个轮密钥异或；每个主轮执行 SubBytes、ShiftRows、MixColumns 和 AddRoundKey；最后一轮只执行 SubBytes、ShiftRows 和 AddRoundKey。

**Weeks 9-11:** AES key expansion for AES-128 starts with 16 bytes as four words $W_0$ to $W_3$. It expands to 44 words $W_0$ to $W_{43}$, giving 11 round keys. For the lecture key `cdutobufoscourse`, hexadecimal bytes are $\texttt{63 64 75 74 6F 62 75 66 6F 73 63 6F 75 72 73 65}$.

**第 9-11 周：** AES-128 的密钥扩展从 16 字节开始，即四个字 $W_0$ 到 $W_3$。它扩展为 44 个字 $W_0$ 到 $W_{43}$，形成 11 个轮密钥。讲义密钥 `cdutobufoscourse` 的十六进制字节为 $\texttt{63 64 75 74 6F 62 75 66 6F 73 63 6F 75 72 73 65}$。

**Weeks 9-11:** AES key expansion formula for round 1 is $W_4 = W_0 \oplus g(W_3)$, $W_5 = W_4 \oplus W_1$, $W_6 = W_5 \oplus W_2$, and $W_7 = W_6 \oplus W_3$. The same pattern continues for later words, with $g$ applied at the start of each new round key.

**第 9-11 周：** AES 第 1 轮密钥扩展公式是 $W_4 = W_0 \oplus g(W_3)$，$W_5 = W_4 \oplus W_1$，$W_6 = W_5 \oplus W_2$，$W_7 = W_6 \oplus W_3$。后续字也按类似模式继续，每生成一个新轮密钥开头时使用 $g$ 函数。

**Weeks 9-11:** AES $g$ function has three steps. First, RotWord rotates a word one byte left, for example $[75, 72, 73, 65] \to [72, 73, 65, 75]$. Second, SubWord substitutes each byte using the AES S-box. Third, XOR the first byte with the round constant Rcon.

**第 9-11 周：** AES 的 $g$ 函数有三步。第一，RotWord 把一个字循环左移一个字节，例如 $[75, 72, 73, 65] \to [72, 73, 65, 75]$。第二，SubWord 用 AES S-box 替换每个字节。第三，把第一个字节与轮常量 Rcon 异或。

**Weeks 9-11:** AES S-box lookup uses hexadecimal nibbles: the first hex digit is the row and the second hex digit is the column. Example: byte $\texttt{53}$ is row 5, column 3, and the AES S-box maps it to $\texttt{ED}$.

**第 9-11 周：** AES S-box 查表使用十六进制半字节：第一个十六进制数字是行号，第二个是列号。例：字节 $\texttt{53}$ 表示第 5 行第 3 列，AES S-box 把它映射为 $\texttt{ED}$。

**Weeks 9-11:** AddRoundKey is byte-wise XOR between the state and the round key. XOR rule: same bits give 0, different bits give 1. For example, $63 \oplus 2F = 4C$ because each pair of hexadecimal bytes is converted to binary and XORed bit by bit.

**第 9-11 周：** AddRoundKey 是状态矩阵与轮密钥逐字节异或。XOR 规则：相同位得 0，不同位得 1。例如 $63 \oplus 2F = 4C$，因为两个十六进制字节先转为二进制，再逐位异或。

**Weeks 9-11:** ShiftRows rotates rows of the AES state to the left. Row 0 is unchanged, row 1 shifts left by 1 byte, row 2 shifts left by 2 bytes, and row 3 shifts left by 3 bytes.

**第 9-11 周：** ShiftRows 把 AES 状态矩阵的各行向左循环移位。第 0 行不变，第 1 行左移 1 字节，第 2 行左移 2 字节，第 3 行左移 3 字节。

**Weeks 9-11:** MixColumns treats each column as four bytes and multiplies it by a fixed AES matrix in $GF(2^8)$. Multiplication is done modulo the irreducible polynomial $x^8 + x^4 + x^3 + x + 1$. For exam-style revision, remember that MixColumns mixes each column independently and is skipped in the final round.

**第 9-11 周：** MixColumns 把每一列看成四个字节，并在 $GF(2^8)$ 中乘以固定 AES 矩阵。乘法要对不可约多项式 $x^8 + x^4 + x^3 + x + 1$ 取模。复习时要记住：MixColumns 独立混合每一列，且最后一轮跳过。

## 8. Hashing and Password Security / 哈希与密码安全

**Week 7 Seminar:** Hashing is one-way: it turns an input into a fixed-length digest and should not be reversible. A small input change should produce a very different hash. Hashing is used for password storage, integrity checking, and digital signatures.

**第 7 周 Seminar：** 哈希是单向的：它把输入转换为固定长度摘要，并且不应能反向还原。输入的微小变化应产生完全不同的哈希。哈希用于密码存储、完整性检查和数字签名。

**Week 7 Seminar:** Hashing is not encryption. Encryption is reversible with a key and is used for confidentiality. Hashing is not meant to be reversed and is used for verification.

**第 7 周 Seminar：** 哈希不是加密。加密可以用密钥还原，主要用于机密性。哈希不应被还原，主要用于验证。

**Week 7 Seminar:** Common hash algorithms in the material include MD5, SHA-1, and SHA-256. MD5 and SHA-1 are considered weak because of collision attacks. SHA-256 is stronger, but passwords should ideally use password-hashing algorithms such as bcrypt, scrypt, or Argon2.

**第 7 周 Seminar：** 材料中常见哈希算法包括 MD5、SHA-1 和 SHA-256。MD5 和 SHA-1 因碰撞攻击而被认为较弱。SHA-256 更强，但密码存储更推荐使用 bcrypt、scrypt 或 Argon2 等专用密码哈希算法。

**Week 7 Seminar:** A dictionary attack tries common passwords from a wordlist, hashes each guess, and compares it with the stolen hash. A rainbow table is a precomputed table of password-hash pairs, allowing faster lookup.

**第 7 周 Seminar：** 字典攻击会从常见密码列表中逐个尝试，把每个猜测哈希后与被盗哈希比较。彩虹表是预先计算好的“密码-哈希”表，可以更快查找。

**Week 7 Seminar:** Salting protects password hashes by adding a unique random string to each password before hashing. Store the salt with the hash; it is not secret. Because each user has a different salt, identical passwords produce different hashes and rainbow tables become ineffective.

**第 7 周 Seminar：** 加盐通过在哈希前给每个密码加入唯一随机字符串来保护密码哈希。盐值可以和哈希一起存储，它不是秘密。由于每个用户的盐不同，相同密码会产生不同哈希，彩虹表也会失效。

## 9. What to Practise by Hand / 手算复习清单

**Weeks 2-11:** Practise Euclid and Extended Euclid until you can compute GCDs and modular inverses without looking at notes. These steps appear inside RSA, CRT, and CCA.

**第 2-11 周：** 反复练习欧几里得和扩展欧几里得，直到能不看笔记计算 GCD 和模逆元。这些步骤会出现在 RSA、CRT 和 CCA 中。

**Weeks 2-11:** Practise modular exponentiation by repeated squaring. Do not expand huge powers directly unless the numbers are tiny.

**第 2-11 周：** 练习用重复平方计算模幂。除非数字很小，不要直接展开巨大指数。

**Weeks 2-11:** Practise RSA key generation from $p$, $q$, and $e$: compute $n$, $\phi(n)$, $d$, then encrypt and decrypt a small message.

**第 2-11 周：** 练习从 $p$、$q$ 和 $e$ 生成 RSA 密钥：计算 $n$、$\phi(n)$、$d$，然后加密并解密一个小消息。

**Weeks 2-11:** Practise CCA on RSA: compute $C' = C\cdot r^e \bmod n$, obtain or calculate $Res$, find $r^{-1}$, and recover $M = Res\cdot r^{-1} \bmod n$.

**第 2-11 周：** 练习 RSA 选择密文攻击：计算 $C' = C\cdot r^e \bmod n$，得到或计算 $Res$，求 $r^{-1}$，再恢复 $M = Res\cdot r^{-1} \bmod n$。

**Weeks 2-11:** Practise Caesar and Vigenere letter arithmetic using $A = 0$. For Vigenere, always write the repeated key above the plaintext.

**第 2-11 周：** 练习 Caesar 和 Vigenere 的字母取模计算，使用 $A = 0$。做 Vigenere 时，一定先把重复密钥写在明文上方。

**Weeks 2-11:** Practise DH and ElGamal with small primes. For ElGamal, remember the ciphertext has two parts: $(c_1, c_2)$.

**第 2-11 周：** 用小质数练习 DH 和 ElGamal。对于 ElGamal，要记住密文有两个部分：$(c_1, c_2)$。

**Weeks 2-11:** Practise DES S-box lookup: outer bits are row, middle bits are column, table value becomes 4-bit binary. Then practise XOR for DES Feistel rounds.

**第 2-11 周：** 练习 DES S-box 查表：外侧两位是行，中间四位是列，表中数值转为 4 位二进制。然后练习 DES Feistel 轮中的 XOR。

**Weeks 2-11:** Practise AES round vocabulary and simple lookups: SubBytes uses S-box, ShiftRows rotates rows, MixColumns mixes columns in $GF(2^8)$, and AddRoundKey is XOR.

**第 2-11 周：** 练习 AES 轮函数术语和简单查表：SubBytes 使用 S-box，ShiftRows 循环移动行，MixColumns 在 $GF(2^8)$ 中混合列，AddRoundKey 是异或。
