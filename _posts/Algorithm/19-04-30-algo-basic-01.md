---
layout: post
title: "0. 알고리즘 기초 - 간단한 문제풀이"
date:   2019-03-30 20:53 +0900
categories: ComputerScience
---
>[모두의 알고리즘 with 파이썬](http://www.kyobobook.co.kr/product/detailViewKor.laf?ejkGb=KOR&mallGb=KOR&barcode=9791160501728&orderClick=LAG&Kc=)을 읽고 간단히 정리한 내용입니다.

## 알고리즘
- 어떤 문제를 풀기 위한 절차나 방법
- 주어진 입력을 출력으로 만드는 과정을 구체적이고 명료하게 표현한 것

- 알고리즘 분석 : 알고리즘의 성능이나 특징을 분석하는 것

## 간단한 예제로 알고리즘 입문

#### 1부터 n까지의 합 구하기


- 방법 1
```
def sum(n):
    sum = 0
    for i in range(1, n+1):
        sum = sum + i
    return sum;
```

- 방법 2
```
def sum1(n):
    return n * (n+1) // 2

# 1부터 n까지의 합 공식
```

- 계산복잡도(complecity) : 알고리즘 문제를 풀기 위해 해야하는 계산의 복잡한 정도
  - 시간복잡도 : 특정 알고리즘 수행에 얼마나 시간이 오래 걸리는지 분석
  - 공간복잡도 : 특정 알고리즘을 수행하는 데 얼마나 많은 공간(메모리/기억장소)가 필요한지 분석


- 대문자 O표기법 (빅 오 표기법)을 많이 사용한다.
  - O(n) : 필요한 계산횟수가 입력크기 n과 정비례 할 경우
  - O(1) : 필요한 계산횟수가 입력크기 n과 무관할 경우

<br>

방법 1은 O(n)이고, 방법 2는 O(1)이다.

- 방법 1은 n의 크기 만큼 계산횟수가 정비례 한다.
- 반면, 방법 2는 n의 크기가 매우 커져도 덧셈 1, 곱셈1, 나눗셈 1, 총 3번의 연산만 수행하므로 입력크기와 상관없는 O(1)이다.


 #### 최댓값 찾기

 - 리스트(List) 활용

#####많이 사용되는 list 메소드
- len(a) : 리스트a의 길이(자료개수)를 구한다.
- append(x) : 자료 x를 리스트 맨 뒤에 추가
- insert(i, x) : 리스트의 i번 위치에 x를 추가
- pop(i) : i번 위치의 자료를 리스트에서 빼내고 빼낸 값을 결과값으로 리턴
i를 지정하지 않을 시 맨 마지막 값을 빼내고 리턴
- clear() : 리스트의 모든 자료를 삭제
- x in a : x가 리스트a 안에 있는지 확인하고 bool로 리턴 (x not in a는 반대결과)


#### 방법 1

```
def find_max(num_list):
    n = len(num_list)
    max = num_list[0]
    for i in range(1,n):
        if num_list[i] > max:
            max = num_list[i]

    return max

=======결과값
v = [7, 5, 16, 25]
find_max(v)
25
```

- n의 크기만큼 비교 계산 수가 커지므로 계산복잡도는 O(n)이다.


#### 방법2
- 리스트에 숫자 n개가 있을 때 가장 큰 값이 있는 위치 번호를 돌려주는 알고리즘

```
def find_max_inx(num_list):
    n = len(num_list)
    max_idx = 0
    for i in range(1, n):
        if num_list[i] > num_list[max_idx]:
            max_idx = i
    return max_idx
```

## 집합

- 집합에는 같은 자료가 중복되어 들어가지 않고, 자료 순서도 의미가 없다.
- set()으로 집합을 생성할 수 있다.


#### 자주 쓰는 집합 기능
- len(s) : 집합의 길이(자료 개수) 구함
- add(x) : 집합에 자료 x를 추가
- discard(x) : 집합에 자료 x가 있다면 삭제하고 없다면 변화없음
- clear() : 집합의 모든 자료 삭제
- x in s : 어떤 자료 x가 집합s에 들어 있는지 확인 (있다면 True, 없다면 False 반환)


#### 동명이인 구하는 알고리즘

```
def find_same_name(name_list):
    n = len(name_list)
    result = set()
    for i in range(0, n-1) :
        for j in range(i+1, n):
            if name_list[i] == name_list[j]:
                result.add(name_list[i])

    return result
```

## 재귀함수

#### 팩토리얼 알고리즘

```
def fact(n):
    f = 1
    for i in range(1, n+1):
        f = f * i
    return f
---
print(fact(5))
```

#### 재귀호출로 팩토리얼 알고리즘 만들기

- 재귀 호출 프로그램이 정상적으로 작동하려면 '종료조건'이 필요하다.
- 특정 조건이 되면 자신을 호출하지 않고 멈추도록 설계해야 한다.

팩토리얼을 구하려면
`n! = n x (n-1)!`
팩토리얼을 구하기 위해 팩토리얼을 다시 호출한다.

```
def fact(n):
    if n <=1:
        return 1
    return n * fact(n-1)
```
n<=1을 만날 때 까지 n*fact(n-1)이 재귀호출되며 팩토리얼 알고리즘이 된다.


#### 최대공약수 구하기

```
def gcd(a, b):
    i = min(a, b) #두 수중 최소값을 구하는 파이썬 함수
    while True:
        if a % i == 0 and b % i ==0:
            return i
        i = i - 1
```

#### 유클리드 알고리즘으로 최대공약수 구하기

- a와 b의 최대공약수는 'b'와 'a를 b로 나눈 나머지'의 최대공약수와 같다.
- 즉, gcd(a,b) = gcd(b, a % b)
- 어떤 수와 0의 최대공약수는 어떤 수 자기자신이다. gcd(n, 0) = n

예시

gcd(60, 24) = gcd(24, 60 % 24) = gcd(12, 24 % 12) = gcd(12, 0) = 12

```
def gcd(a, b):
    if b == 0:
        return a
    return (b, a % b)
```
