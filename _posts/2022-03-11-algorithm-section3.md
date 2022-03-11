---
layout: single
title: "[Algorithm] 알고리즘 Section 3:Big O - O(n), O(1), O(n^2) "
categories: algorithm
tags: [python, coding, algorithm, dataStructure, 2022/03/11]
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

&nbsp;&nbsp;&nbsp;&nbsp;알고리즘 공부를 위해 Udemy에 있는 [Master the Coding Interview: Data Structures + Algorithms
](https://www.udemy.com/course/master-the-coding-interview-data-structures-algorithms/) 과정을 듣고 있다. 이 포스트에서는 Section 3에서 배웠던 Big O와 관련된 내용들을 리뷰해보려고 한다.

## 2. 본론  

<img src="https://miro.medium.com/max/1200/1*5ZLci3SuR0zM_QlZOADv8Q.jpeg" alt="Big O Complexity" width=500>

&nbsp;&nbsp;&nbsp;&nbsp;위의 사진은 알고리즘 공부를 시작하면 누구나 한번쯤 보게되는 Big O 시간복잡도 차트다.

### 1. O(n)  

⬇️ 작성한 코드 ⬇️

```
import time
import numpy as np

# python에서 list와 array의 다른점
# 1. list는 다른 데이터 타입을 포함할 수 있지만, array는 동일한 데이터 타입만 포함할 수 있다.
# 2. list는 별도의 모듈이 필요 없지만, array는 필요하다.
# 3. list는 산술 연산자를 사용할 수 없지만, array는 가능하다.(예를들어 list를 +연산하면 리스트와 리스트를 합치지만, array는 원소별 덧셈을 한다.)
# 4. list는 list안에 list를 가질 수 있지만, array는 동일한 사이즈의 원소만 가질 수 있다.
# 5. list는 주로 길이가 짧은 연속적인 데이터를 다룰 때 사용하고, array는 길이가 긴 연속적인 데이터를 다룰 때 사용한다.
# 6. list는 원소를 더하거나, 빼거나, 또는 업데이트 하는 것을 쉽게 할 수 있지만, array는 그렇지 않다.
# 7. list는 출력이 쉽게 가능하지만, array를 출력하기 위해서는 반복문이 필요하다.
# 8. list는 원소를 쉽게 더하기 위해 큰 메모리 용량이 필요하지만, array는 list와 비교하여 적은 메모리 용량이 필요하다.

# list와 array의 수행 시간이 다른지 궁금하여 같은 길이의 list와 array 선언.
nemo_list = ['nemo']
everyone_list = ['dory', 'bruce', 'marlin', 'nemo', 'gill', 'bloat', 'nigel', 'squirt', 'darla']
large_list = ['nemo' for i in range(100000)]

nemo_array = np.array(['nemo'])
everyone_array = np.array(['dory', 'bruce', 'marlin', 'nemo', 'gill', 'bloat', 'nigel', 'squirt', 'darla'])
large_array = np.array(['nemo' for i in range(10000)])

def find_nemo(array_or_list):
    # time.time()은 초단위를 받아오므로, 밀리세컨드로 받기 위해 1000을 곱해줌.
    t0 = round(time.time() * 1000)
    for i in range(0,len(array_or_list)):
        if array_or_list[i] == 'nemo':
            print("Found Nemo!!")
    t1 = round(time.time() * 1000)
    print(f'The search took {t1-t0} milliseconds.')
    
# find_nemo(nemo_list)
# find_nemo(everyone_list)
find_nemo(large_list)

# find_nemo(nemo_array)
# find_nemo(everyone_array)
find_nemo(large_array)
```  

&nbsp;&nbsp;&nbsp;&nbsp;✔️ 이번에 배운 부분이나 느낀점은 : 
- <b>[개발자라면 이제는 알아야하는 Big O 설명해드림. 10분컷.](https://www.youtube.com/watch?v=BEVnxbxBqi8) 유튜브에 있는 이 영상도 Big O 개념을 이해하는데 도움이 된다.</b>
- <b>파이썬에서 같은 수의 원소를 가지고 있어도 list가 array보다 큰 메모리 용량이 필요하고, 따라서 탐색 시간도 더 오래걸린다.</b>
- <b>알고리즘의 수행능력은 시간으로 표현하지 않는다. 왜냐하면 컴퓨터라는 하드웨어에 따라 같은 알고리즘이라도 수행시간은 달라질 수 있기 때문이다. 따라서 알고리즘의 스피드는 완료까지 걸리는 절차의 수로 결정한다.</b>
- <b>선형검색의 시간 복잡도는 input 사이즈에 정비례 하기 때문에 O(n)이다.</b>

### 2. O(1)  

⬇️ 작성한 코드 ⬇️

```
import time

array_small = ['nemo' for i in range(10)]
array_medium = ['nemo' for i in range(100)]
array_large = ['nemo' for i in range(100000)]

def finding_nemo(array):
    t0 = time.time() * 1000
    print(array[0]) #O(1) operation
    t1 = time.time() * 1000
    print(f'Time taken = {t1-t0}')

finding_nemo(array_small)
finding_nemo(array_medium)
finding_nemo(array_large)
```  

&nbsp;&nbsp;&nbsp;&nbsp;✔️ 이번에 배운 부분이나 느낀점은 : 
- <b>O(1)은 input 사이즈에 상관 없이 시간 복잡도가 일정하다는 뜻이다.</b>
- <b>위의 코드를 보면 array의 input size에 상관없이, 수행 단계가 오직 하나이기 때문이다.</b>

### 3. O(n^2)  

⬇️ 작성한 코드 ⬇️

```
array = ['a','b','c','d','e']

def log_all_pairs(array):

    for i in range(len(array)): 
        for j in range(len(array)): 
            print(array[i], array[j]) 

log_all_pairs(array)

# # Big O(n^2)

new_array = [1,2,3,4,5]

def print_numbers_then_pairs(array):

    print("The numbers are : ") 
    for i in range(len(array)): 
        print(array[i])               

    print("The pairs are :")  
    for i in range(len(array)): 
        for j in range(len(array)):
            print(array[i], array[j]) 

print_numbers_then_pairs(new_array)

# Big O(n^2)
```  

&nbsp;&nbsp;&nbsp;&nbsp;✔️ 이번에 배운 부분이나 느낀점은 : 
- <b>Rule 1: Worse Case</b>
- <b>Rule 2: Remove Constants</b>
- <b>Rule 3: Different terms for inputs</b>
- <b>Rule 4: Drop Non Dominants</b>


## 3. 결론  

&nbsp;&nbsp;&nbsp;&nbsp;이번 포스팅에서는 알고리즘에서 가장 바탕이 되는 개념인 Big O에 관한 내용들을 리뷰해 보았다. 솔직히 알고리즘에 관한 내용들은 쉽거나 바로 습득할 수 있는 부분은 아니고 많은 문제들을 풀어보면서 몸으로 깨우쳐야 할 것 같다. 

## 4. 참고자료  

Ⅰ. [Master the Coding Interview: Data Structures + Algorithms
](https://www.udemy.com/course/master-the-coding-interview-data-structures-algorithms/)

---

```bash
이제 막 프로그래밍 공부를 시작한 초보 개발자입니다.
이 블로그 글들의 주 목적은 공부한것을 복습하기 위한것이며, 
만약 틀리거나 수정하면 좋을 부분들은
친절하게 댓글달아주시면 감사하겠습니다. :)
```

---