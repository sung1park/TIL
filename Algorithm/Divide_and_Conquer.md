# Divide and Conquer

- Divide : 해결할 문제를 여러 개의 작은 부분으로 나눈다
- Conquer : 나눈 작은 문제를 각각 해결한다
- Combine : (필요하다면) 해결된 해답을 모은다



#### Top-down approach

![image-20211005015659069](algorithm.assets/image-20211005015659069.png)



#### 거듭 제곱

```
Power(x, n) {
	result = 1;
	while (x>0) {
		if (n % 2 == 1) 
			result = result * x;
		
		x = x * x;
		n = n >> 1;
	}
	return result;
}
```

```
Recursive_Power (x, n) {
	if (n == 1) return x;
	if (n % 2 == 0) {
		y = Recursive_Power(x, n/2);
		return y * y;
	} else {
		y = Recursive_Power(x, (n-1)/2);
		return y * y * x;
	}
}
```





### binary search

- 자료의 가운데에 있는 항목의 키 값과 비교하여 다음 검색의 위치를 결정하고 검색을 계속 진행하는 방법
- 목적 키를 찾을 때까지 이진 검색을 순환적으로 반복 수행함으로써 검색 범위를 반으로 줄여가면서 보다 빠르게 검색을 수행함
- 이진 검색을 하기 위해서는 자료가 정렬된 상태여야 한다.



##### 검색 과정

1. 자료의 중앙에 있는 원소를 고른다.
2. 중앙 원소의 값과 찾고자 하는 목표 값을 비교한다.
3. 중앙 원소의 값과 찾고자 한느 목표 값이 일치하면 탐색을 끝낸다.
4. 목표 값이 중앙 원소의 값보다 작으면 자료의 왼쪽 반에 대해서 새로 검색을 수행하고, 크다면 자료의 오른쪽 반에 대해서 새로 검색을 수행한다.
5. 찾고자 하는 값을 찾을 때까지 위의 과정을 반복한다.



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

