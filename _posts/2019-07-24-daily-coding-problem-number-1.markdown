---
title: 'Daily Coding Problem #1'
date: 2019-07-24 13:52:00 Z
tags:
- Google
Author: Austin and JiaJun
solved: true
layout: post
---

Good morning! Here's your coding interview problem for today.

This problem was recently asked by Google.

Given a list of numbers and a number k, return whether any two numbers from the list add up to k.

For example, given `[10, 15, 3, 7]` and k of 17, return true since `10 + 7` is `17`.

Bonus: Can you do this in one pass?

**<u>SOLUTION</u>**

*This solution is written by Austin and Jiajun, running in $$O(n^2)$$ complexity*

```java
public int findSum(arr, k) {
  for(int i = 0; i < arr.length; i++) {
    for(int j = i+1; j < arr.length; j++) {
      if (!arr[j]) {
        return false;
      }
      if (arr[j] + arr[i] === k) { 
      	return true;
      }
    }
  }
  return false;
}
```
**<u>SOLUTION $$O(n)$$</u>**
> This solution also uses $$O(n)$$ space.

```java
public int findSum(arr, k) {
  Map<int, int> storage = new HashMap<int,int>();
  for(int i = 0; i < arr.length; i++) {
    int remainder = Math.abs(arr[i] - k);
    if (!storage.containsKey(remainder) {
      /*  If there isn't a key in the storage yet.
       *	add: (<currentNumber>, <remainder>);
       */
      storage.put(arr[i], remainder);
    } else {
      if(storage.get(remainder) == arr[i]) {
        return true;
      }
    }
  }
  return false;
}
```

Example:

`[10, 15, 3, 7]`, k = 17

- i = 0;

  - arr[0] = 10

  - remainder = 7

  - storage = 

    | key  | value |
    | ---- | ----- |
    | 10   | 7     |

- i = 1;

  - arr[1] = 15

  - remainder = 2;

  - storage =

    | key  | value |
    | ---- | ----- |
    | 10   | 7     |
    | 15   | 2     |

- i = 2

  - arr[2] = 3

  - remainder = 14

  - storage = 

    | key  | value |
    | ---- | ----- |
    | 10   | 7     |
    | 15   | 2     |
    | 3    | 14    |

- i = 3
  - arr[3] = 7
  - remainder = 10 **condition runs `line 10`**
  - `line11`: **true**
  - `return true`










