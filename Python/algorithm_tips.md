# Python Algorithm Tips

> 파이썬 알고리즘 문제 풀이시 팁



### 입출력

`input()` 대신 `sys.stdin.readline()`을 사용

```python
# 임의의 개수의 정수를 한 줄에 입력받아 리스트에 저장할 때
import sys
input_nums = list(map(int, sys.stdio.readline().split()))

# 문자열 n줄을 입력받아 리스트에 저장할 때
import sys
n = int(sys.stdio.readline())
data = [sys.stdin.readline().strip() for i in range(n)]
```

- 한 두줄 입력받는 문제라면 상관 없지만, 반복문으로 여러 줄을 입력 받아야 하는 경우 `input()`으로 입력 받는다면 시간초과가 발생할 수 있다
- `readline()` 또는 `readlines()`의 경우 입력받은 라인 끝에 `\n`이 붙는다.



### 문자열을 문자 단위로 리스트로 입력받기

```python
list(input())
```



### 2차원 배열 선언하기

```python
board = [[0 for i in range(COL)] for j in range(ROW)]
```



### Python에서 정수 최대값

Python 3에서는 정수의 한계가 없어졌지만, `sys.maxsize`를 사용할 수 있다. [공식문서](https://docs.python.org/3/whatsnew/3.0.html#integers)



### Set을 List로

```python
mylist = list(myset)
```



### 날짜, 시간

```python
import datetime from datetime
print(datetime.today().strftime('%Y-%m-%d'))
```

- `datetime` 라이브러리의 `datetime` 클래스를 가져와 사용
- `strftime`으로 날짜 및 시간을 형식에 맞추어 출력할 수 있다

```
%d : 0을 채운 10진수 표기로 날짜를 표시
%m : 0을 채운 10진수 표기로 월을 표시
%y : 0을 채운 10진수 표기로 2자리 년도
%Y : 0을 채운 10진수 표기로 4자리 년도
%H : 0을 채운 10진수 표기로 시간 (24시간 표기)
%I : 0을 채운 10진수 표기로 시간 (12시간 표기)
%M : 0을 채운 10진수 표기로 분
%S : 0을 채운 10진수 표기로 초
%f : 0을 채운 10진수 표기로 마이크로 초 (6자리)
%A : locale 요일
%a : locale 요일 (단축 표기)
%B : locale 월
%b : locale 월 (단축 표기)
%j : 0을 채운 10진수 표기로 년중 몇 번째 일인지 표시 
%U : 0을 채운 10진수 표기로 년중 몇 번째 주인지 표시 (일요일 시작 기준)
%W : 0을 채운 10진수 표기로 년중 몇 번째 주인지 표시 (월요일 시작 기준)
```



### 리스트 정렬

**sort** : 정렬. 기본값은 오름차순 정렬

```python
# 오름차순 정렬
a.sort()
# 내림차순 정렬
a.sort(reverse=True)
# key 옵션에 지정된 함수의 결과에 따라 정렬
a.sort(key=len)
```

**reverse** : 리스트를 거꾸로 뒤집음

```python
a.reverse()
```

**sorted** : 정렬된 결과를 반환

```
b = sorted(a)
```

**reversed** : 거꾸로 뒤집은 결과를 iterable한 객체로 반환. list로 변환해야 확인 가능

```python
b = reversed(a)
list(a)
```

##### 여러 기준으로 정렬하기

```python
list.sort(key=lambda x: (기준1, 기준2, ...))
```



### 최대공약수 구하기 - 유클리드 호제법

a, b가 정수이고, a를 b로 나눈 나머지가 r이라고 할 때, a와 b의 최대 공약수를 (a, b)라고 하면 다음이 성립한다.

`(a, b) = (b, r)`

```
78696과 19332의 최대공약수를 구하는 경우
    78696 ＝ 19332×4 ＋ 1368
    19332 ＝ 1368×14 ＋ 180
     1368 ＝ 180×7 ＋ 108
      180 ＝ 108×1 ＋ 72
      108 ＝ 72×1 ＋ 36
       72 ＝ 36×2 ＋ 0
이 때, 최대공약수는 36이다.
```



### Binary counting for Python

```python
for i in range(1<<n):
    for j in range(n):
        if i & (1<<j):
            pass
```
