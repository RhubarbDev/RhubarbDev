---
title: "Sieve of Eratosthenes"
date: 2024-08-16T14:30:53+01:00
slug: 2024-08-16-sieve-of-eratosthenes
type: posts
draft: false
categories:
  - default
tags:
  - default
---
Another short post while I finish a project I'm working on.

I thought I'd continue on from the last post by discussing another algorithm to find prime numbers.

The sieve of Eratosthenes is an algorithm attributed to the Greek polymath Eratosthenes, it iterates through a list upto **n** and marks multiples of each prime as composite.

To implement this I've created an object to represent each number and store whether it's prime.

```java
public class PrimeNumber {
  public int number;
  public boolean isPrime;
  public boolean visited;

  public PrimeNumber(int number) {
    assert number > 1;
    this.number = number;
  }
}
```

This object can then be used to determine prime numbers upto a value **n**

```java
public static void sieveOfEratosthenes(int n) {
  assert n > 0;
  PrimeNumber[] range = new PrimeNUmber[n - 1];
  IntStream.range(2, n + 1).forEach(i -> range[i - 2] = new PrimeNumber(i));

  for (int i = 0; i < range.length; i++) {
    if (range[i].visited) {
      continue;
    }

    for (int j = i; j < range.length;) {
      range[j].isPrime = false;
      range[j].visited = true;
      j += range[i].number;
    }

    range[i].isPrime = true;
    System.out.print(range[i].number + ", ");
  }
}
```
