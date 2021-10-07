# Exhaustive Search

> 완전 탐색 방법인 순열, 조합, 부분 집합

- 모든 경우의 수를 나열해보고 확인하는 기법
- Brute-force, Generate-and-test



## Permutation 순열

> 서로 다른 것들 중 몇 개를 뽑아서 한 줄로 나열하는 것

#### 반복문을 통한 구현 (r이 정해져 있을때)

```
// 3P3
for i from 1 to 3
	for j from 1 to 3
		if j != i then
			for k from 1 to 3
				if k != i and k != j then
				print i, j, k
```



#### 재귀 호출을 통한 구현 - boolean[] 사용

```
nPr
input[] : 숫자 배열
numbers[] : 순열 저장 배열
isSelected[] : 인덱스에 해당하는 숫자가 사용 중인지 저장
perm(cnt)  : 현재까지 뽑은 순열 원소의 개수
	if cnt == N
		순열 생성 완료
	else
		for i from 0 to N-1
			if isSelected[i] == true then continue
			numbers[cnt] <- input[i]
			isSelected[i] <- true
			perm(cnt+1)
			isSelected[i] <- false
```



#### 비트마스킹을 통한 순열 생성 

```
nPn -> N개의 원소로 만들 수 있는 모든 순열 생성
perm(cnt, flag) // flag: 선택된 원소에 대한 비트정보를 표현하는 정수
	if cnt == N
		순열생성 완료
	else
		for i from 0 to N-1
			if (flag & 1<<i) != 0 then continue
			numbers[cnt] <- input[i]
			perm(cnt+1, flag | 1<<i)
```



#### :heavy_check_mark: 비트 연산자

- 1 << i 
  - 뒤에서 i번째 자리에 1을 옮겨 놓음
- `&` 연산은 mask off라고 불림
- `value & 1<<i` 처럼 보고 싶은 자리만 highlight 할 수 있음
  - 이 값은 비트값(0, 1)이 아닌 정수값



#### :heavy_check_mark: Next Permutation

- 배열을 오름차순으로 정렬 후 시작한다.
- 아래 과정을 반복하여 사전 순으로 다음으로 큰 순열 생성(가장 큰 내림차순 순열을 만들때까지 반복)
  1. 뒤쪽부터 탐색하며 교환위치(i-1) 찾기 (i: 꼭대기)
  2. 뒤쪽부터 탐색하며 교환위치(i-1)와 교환할 큰 값 위치(j) 찾기
     - 뒤에서부터 처음으로 자신보다 큰 수의 위치가 j
  3. 두 위치 값 (i-1, j) 교환
  4. 꼭대기위치(i) 부터 맨 뒤까지 오름차순 정렬

```java
public static void main(String[] args) {
    int[] input = {1, 2, 3, 4};
    
    Arrays.sort(input); // 가장 작은 순열 만들기
    
    do {
        System.out.println(Arrays.toString(input));
    } while (np(input)); // next permutation
}

// 다음 큰 순열이 있으면 true, 없으면 false
private static boolean np(int[] numbers) {
    int N = numbers.length;
    
    // step1. 꼭대기(i)를 찾는다. 꼭대기를 통해 교환위치 찾기
    int i = N-1;
    while (i>0 && numbers[i-1]>=numbers[i]) --i;
    
    if (i==0) return false;
    
    // step2. i-1 위치값과 교환할 큰 값 찾기
    int j = N-1;
    while (numbers[i-1]>=numbers[j]) --j;
    
    // step3. i-1 위치값과 j 위치값 교환
    swap(numbers, i-1, j);
    
    // step4. 꼭대기(i)부터 맨 뒤까지 내림차순 형태의 순열을 오름차순으로 처리
    int k = N-1;
    while (i<k) {
        swap(numbers, i++, k--);
    }
    
    return true;        
}

```



## Combination  조합

> 서로 다른 n개의 원소 중 r개를 순서 없이 골라낸 것

#### 반복문으로 구현

```
for i from 1 to 4
	for j from i+1 to 4
		for k from j+1 to 4
			print i, j, k
```



#### 재귀 호출로 구현

```
input[] : n개의 원소를 가지고 있는 배열
numbers[] : r개의 크기의 배열, 조합이 저장될 배열

// cnt   : 현재까지 뽑은 조합 원소의 개수
// start : 조합 시도할 원소의 시작 인덱스
comb(cnt, start)
	if cnt == r
		조합 생성 완료
	else
		for i from start to n-1
			numbers[cnt] <- input[i];
			comb(cnt+1, i+1)
		end for
end comb
```



#### :heavy_check_mark: NextPermutation 활용

- 크기 n의 int 배열 P를 생성해 뒤에서 부터 r개 만큼 0이 아닌 값으로 초기화한다
- 순열에서와 같은 방법으로 NP실행하면 



## Subset 부분 집합

> 집합에 포함된 원소들을 선택하는 것

#### 반복문으로 구현

```
for i in 1 -> 0
	selected[1] <- i
	for j in 1 -> 0
		selected[2] <- j
		for k in 1 -> 0
			selected[3] <- k
			for m in 1 -> 3
				if selected[i]==1 then
					print i
```



#### 재귀 호출로 구현

```
input[] : 숫자 배열
isSelected[] : 부분집합에 선택/미선택 여부를 저장한 배열
// cnt : 현재까지 처리한 원소 개수
generateSubSet(cnt)
	if(cnt == N)
		부분집합 완성
	else
		isSelected[cnt] <- true
		generateSubSet(cnt+1)
		isSelected[cnt] <- false
		generateSubSet(cnt+1)
```



#### 바이너리 카운팅을 이용해 사전적 순서(Lexicographical Order)로 생성하는 방법

- 부분집합을 생성하는 가장 자연스러운 방법이자 사전적 순서로 만들기 위한 가장 간단한 방법
- 원소 수에 해당하는 N개의 비트열을 이용한다
- 비트열에 해당하는 10진수를 비트마스킹 된 수로 간주하고 상태를 표현하고 있다고 생각
- n번째 비트값이 1이면 n번째 원소가 포함되었음을 의미한다.

```
int arr[];
int n = arr.length;

for (int i = 0; i < (1 << n); i++) {
	for (int j = 0; j < n; j++) {
		if (i & (1 << j) != 0)
			print(arr[j]+" ");
	}
}
```



