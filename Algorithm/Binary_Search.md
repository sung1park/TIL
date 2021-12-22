# Binary Search

> 자료의 가운데에 있는 항목의 키 값과 비교하여 다음 겸색의 위치를 정하고 검색을 계속 진행하는 방법

- 목적 키를 찾을 때까지 이진 검색을 순환적으로 반복 수행함으로써 검색 범위를 반으로 줄여가면서 보다 빠르게 검색을 수행함



#### 검색 과정

- 자료가 검색하려는 Key 값을 기준으로 정렬된 상태여야 한다

1. 자료 중앙에 있는 원소를 고른다
2. 중앙 원소의 값과 찾고자 하는 목표 값을 비교한다
3. 중앙 원소의 값과 찾고자 하는 목표 값이 일치하면 탐색을 끝낸다
4. 목표 값이 중앙 원소보다 작으면 자료의 왼쪽 반에 대해 새로 검색을 수행, 크다면 오른쪽 반에 대해 새로 검색을 수행한다
5. 찾고자 하는 값을 찾을 때까지 위의 과정을 반복한다



#### 반복 구조

```
binarySearch(S[], n, key)
	start <- 0
	end <- n-1
	
	while start <= end
		mid <- (start+end)/2
		if S[mid] == key
			return mid
		elif S[mid] < key
			start <- mid + 1
		elif S[mid] > key
			end <- mid - 1
	end while
	return -1
```



#### 재귀 구조

```
binarySearch(S[], start, end, key)
	if start > end
		return -1
	else
		mid <- (start+end)/2
		if S[mid] == key
			return mid
		elif S[mid] < key
			return binarySearch(S[], mid+1, end, key)
		else
			return binarySearch(S[], start, mid-1, key)
```



#### java.util.Arrays.binarySearch

- Java의 이진 탐색 API