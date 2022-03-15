---
layout: single
title: "[Algorithms] 알고리즘 연습문제(Recursion - Sum of Digits, Power, Greatest Common Divisor, Decimal To Binary)"
categories: algorithms
tags: [python, coding, algorithms, dataStructure, recursion, 2022/03/08]
toc: true
toc_sticky: true
author_profile: true
comments: true
share: true
related: true
published: true
sidebar: 
    nav: "docs"
---


## 1. 서론

&nbsp;&nbsp;자료구조와 알고리즘 공부를 위해 [The Complete Data Structures and Algorithms Course in Python](https://www.udemy.com/course/data-structures-and-algorithms-bootcamp-in-python/) 과정을 듣고 있다. 이 포스트에서는 Section 1-47 중 Section 3에서 다뤘던 [Recursion(재귀)](https://dojang.io/mod/page/view.php?id=2352) 기반 알고리즘 문제들을 리뷰해보려고 한다.

## 2. 본론

함수 안에서 함수 자기자신을 호출하는 방식을 재귀 호출(recursive call)이라고 한다. 재귀 호출은 알고리즘을 구현하는 한가지 방법이다.

### 1. Sum of Digits

&nbsp;&nbsp;🤔 문제는 입력받는 숫자의 각 자리를 더한 값을 구하는 알고리즘을 짜는 것이었다.

⬇️ 코드 ⬇️

```
def sumofDigits(n):
    assert n == int(n) and n >= 0, "The number has to be a positive integer only!"
    if n == 0:
        return 0
    else:
        return int(n % 10) + sumofDigits(int(n/10))
    
print(sumofDigits(1513513531512))
```  

&nbsp;&nbsp;✔️ 이번 챌린지를 통하여 배운 부분이나 느낀점은
- <b>파이썬에 관한 강의도 수강중인데, 확실히 단순히 프로그램 구현을 위한 코딩을 배우는 것과는 다른 느낌의 공부인 것 같다. </b>
- <b>Step 1 : Recursive case - the flow, Step 2 :  Base case — the stopping criterion, Step 3 : Unintentional case — the constraint를 기억하자</b>
- <b>assert(가정설정문)는 뒤의 조건이 True가 아니면 Assererror를 발생시키는 함수라는 것을 배웠다.</b>

### 2. Power

&nbsp;&nbsp;🤔 문제는 밑(base)와 지수(power or exponent)를 입력받으면 거듭제곱한 결과를 출력하는 알고리즘을 짜는 것이었다.

⬇️ 코드 ⬇️

```
def power(base, exp):
    assert exp >= 0 and exp == int(exp), "The exponent must be positive integer only!"
    if exp == 0:
        return 1
    elif exp == 1:
        return base
    return base * power(base, exp-1)

print(power(-3,3))
```  

&nbsp;&nbsp;✔️ 이번 챌린지를 통하여 배운 부분이나 느낀점은
- <b>Step 1 : Recursive case - the flow을 혼자서 생각해내는게 쉽지 않다. 이 문제가 이렇게 카테고리가 주어진 상황이 아닐 때 recursive call을 사용하여 풀 수 있다는 것을 어떻게 알아낼 수 있는지는 더 모르겠다.</b>

### 3. Greatest Common Divisor

&nbsp;&nbsp;🤔 문제는 a와 b 두 숫자들 입력받으면, 두 수의 Greatest Common Divisor(최대 공약수)를 구하는 알고리즘을 짜는 것이었다.

⬇️ 코드 ⬇️

```
def gcd(a, b):
    assert int(a) == a and int(b) == b, "The numbers mubst be integer only!"
    if a < 0:
        a *= -1
    elif b < 0:
        b *= -1
        
    if b == 0:
        return a
    else:
        return gcd(b, a%b)

print(gcd(48, -18))
```  

&nbsp;&nbsp;✔️ 이번 챌린지를 통하여 배운 부분이나 느낀점은
- <b>Step 3 : Unintentional case — the constraint를 생각할 때, 머리속으로 대충 생각하고 결론내리면 안되고(내가 그랬음) 테스트 케이스를 적어놓고 케이스에 따른 결과를 구해보는 것이 필요하다.</b>

### 4. Decimal To Binary

&nbsp;&nbsp;🤔 문제는 십진수 n을 입력받으면, 이진수로 변환하는 알고리즘을 짜는 것이었다. 

⬇️ 코드 ⬇️

```
def decimalToBinary(n):
    assert n == int(n), "The parameter must be a positive integer only!"
    if n == 0:
        return 0
    else:
        return n%2 + 10 * decimalToBinary(int(n/2))

print(decimalToBinary(-13))
```  

&nbsp;&nbsp;✔️ 이번 챌린지를 통하여 배운 부분이나 느낀점은
- <b>1-3번 문제를 같이 풀어나가면서 생각보다 어렵지 않네라고 생각했다가 4번 문제를 보고 생각이 바뀌었다.</b>
  
## 3. 결론

&nbsp;&nbsp;이번 포스팅에서는 재귀함수를 이용한 알고리즘 문제들을 살펴보았다. 바로 어제 올린 포스팅에서 각각의 알고리즘에 해당하는 섹션 강의를 듣고 나서 LeetCode에서 해당 알고리즘의 문제들을 풀어보겠다고 했는데, 가서 문제를 보니 단순히 한 섹션만 공부하고 나서 풀 수 있는 문제들이 아니었다. 그래서 빠르게 이 강의를 완강하고 LeetCode나 Programmars에서 문제풀이를 이어나가야 할 것 같다.

## 4. 참고자료

Ⅰ. [The Complete Data Structures and Algorithms Course in Python](https://www.udemy.com/course/data-structures-and-algorithms-bootcamp-in-python/)

---

```bash
이제 막 프로그래밍 공부를 시작한 초보 개발자입니다.
이 블로그 글들의 주 목적은 공부한것을 복습하기 위한것이며, 
만약 틀리거나 수정하면 좋을 부분들은
친절하게 댓글달아주시면 감사하겠습니다. :)
```

---