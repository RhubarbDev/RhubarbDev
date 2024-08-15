---
title: "Prime Detection"
date: 2024-08-15T13:29:15+01:00
slug: 2024-08-15-prime-detection
type: posts
draft: false
categories:
  - default
tags:
  - default
---
Short Post - Intresting stuff coming soon (tm) *also the first post on the new site*

One way to determine if something is prime is by using the Miller-Rabin primality test. While you cannot be 100% certain if the value is prime, it's very unlikely to be wrong.

The algorithm is quite simple, it picks **m** random numbers within the range 2 and n-1 inclusive - **where n is the number being tested**

It then tests each of these numbers, *x*, against two conditions.

1. xⁿ⁻¹ = 1 % n
2. 1 < gcd(((xⁿ) - 1), n) < n

The program stores a counter, that increments when either condition is met, if the value after checking **m** is less than half of **n**, then the value is likely to be prime.

Here's some code,

```java
private static int gcd(int a, int b) { return b == 0 ? a : gcd(b, a % b); }

private static boolean isPrime(int n) {
  int m = (int)(n - 1 / Math.pow(2, 10));

  Random random = new Random();

  int witnessCount = 0;

  for (int i = 0; i < m; i++) {
    int w = random.nextInt(2, n);

    // condition 1
    if (Math.pow(w, n - 1) == 1 % n) {
      witnessCount++;
    }

    // condition 2
    int greatest = gcd(((int)Math.pow(w, n) - 1), n);

    if (1 < greatest && greatest < n) {
      witnessCount++;
    }
  }

  return 0.5 * m > witnessCount;
}
```

I'll be posting more soon!

Sneak preview: https://github.com/RhubarbDev/undetected-chromedriver




