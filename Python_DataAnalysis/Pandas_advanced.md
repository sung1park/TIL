# Pandas Advanced

> 조건으로 검색하기, 함수로 데이터 처리하기, 그룹으로 묶기, MultiIndex & pivot_table



### 조건으로 검색하기 Boolean Indexing

- numpy array와 마찬가지로 masking 연산이 가능하다

```python
df = pd.DataFrame(np.random.rand(5, 2), columns=['A', 'B'])

df['A'] < 0.5
# 여러 조건을 동시에 만족
df[(df['A'] < 0.5) & (df['B'] > 0.3)]
# 쿼리문 이용 가능
df.query('A < 0.5 and B > 0.3')
```

- 문자열이라면 다른 방식으로도 조건 검색이 가능

```python
df['Animal'].str.contains('Cat')
df.Animal.str.match('Cat')
```



### 함수로 데이터 처리하기

##### apply

- 함수로 데이터를 다룰 수 있다.

```python
df = pd.DataFrame(np.arange(5), columns=['Num'])
def square(x):
    return x**2
df['Square'] = df['Num'].apply(square)
df['Square'] = df.Num.apply(lambda x: x**2)
```

##### replace

- apply 기능에서 데이터 값만 대체하고 싶을 때

```python
# 복사본 출력
df.Sex.replace({'Male': 0, 'Female': 1})
# 원본 수정
df.Sex.replace({'Male': 0, 'Female': 1}, inplace=True)
```



### 그룹으로 묶기

##### groupby 

- 간단한 집계를 넘어 조건부로 집계하고 싶은 경우

```python
df = pd.DataFrame({'key': ['A', 'B', 'C', 'A', 'B', 'C'],
                  'data1': [1, 2, 3, 1, 2, 3],
                  'data2': np.random.randint(0, 6, 6)})
df.groupby('key')
df.groupby('key').sum()
df.groupby(['key', 'data1']).sum()
```

![image-20220304101239428](C:\Users\sungi\TIL\Python_DataAnalysis\assets\image-20220304101239428.png)

##### aggregate

- `groupby`를 통해서 집계를 한 번에 계산하는 방법

```python
df.groupby('key').aggregate(['min', np.median, max])
df.groupby('key').aggregate({'data1': 'min', 'data2': np.sum})
```

![image-20220304101444044](C:\Users\sungi\TIL\Python_DataAnalysis\assets\image-20220304101444044.png)

##### filter

- `groupby`를 통해서 그룹 속성을 기준으로 데이터 필터링

```python
def filter_by_mean(x):
    return x['data2'].mean() > 3
df.groupby('key').mean()
df.groupby('key').filter(filter_by_mean)
```

![image-20220304101804857](C:\Users\sungi\TIL\Python_DataAnalysis\assets\image-20220304101804857.png)

##### apply

- `groupby`를 통해서 묶인 데이터에 함수 적용

```python
df.groupby('key').apply(lambda x: x.max() - x.min())
```

![image-20220304101851213](C:\Users\sungi\TIL\Python_DataAnalysis\assets\image-20220304101851213.png)

##### get_group

- `groupby`로 묶인 데이터에서 key값으로 데이터를 가져올 수 있음

```python
df = pd.read_csv('./univ.csv')
df.head()
df.groupby('시도').get_group('충남')
```

![image-20220304102042844](C:\Users\sungi\TIL\Python_DataAnalysis\assets\image-20220304102042844.png)



### MultiIndex

- 인덱스를 계층적으로 만들 수 있다

```python
df = pd.DataFrame(
	np.random.randn(4, 2),
    index = [['A', 'A', 'B', 'B'], [1, 2, 1, 2]],
    columns = ['data1', 'data2']
)
```

![image-20220304105946755](C:\Users\sungi\TIL\Python_DataAnalysis\assets\image-20220304105946755.png)

- 열 인덱스도 계층적으로 만들 수 있다

```python
df = pd.DataFrame(
	np.random.randn(4, 4),
    columns = [['A', 'A', 'B', 'B'], ['1', '2', '1', '2']]
)
```

![image-20220304110002320](C:\Users\sungi\TIL\Python_DataAnalysis\assets\image-20220304110002320.png)

- 다중 인덱스 컬럼의 경우 인덱싱은 계층적으로 한다.
- 인덱스 탐색의 경우`loc`, `iloc` 사용 가능

```python
df['A']
df['A']['1']
```



### pivot_table

- 데이터에서 필요한 자료만 뽑아서 새롭게 요약
- 분석할 수 있는 기능 엑셀에서의 피봇 테이블과 같다
- Index : 행 인덱스로 들어갈 key
- Column :  열 인덱스로 라벨링 될 값
- Value : 분석할 데이터

```python
# 타이타닉 데이터에서 성별과 좌석별 생존률 구하기
df.pivot_table(
	index='sex', columns='class', values='survived',
    aggfunc=np.mean
)
```

![image-20220304110549108](C:\Users\sungi\TIL\Python_DataAnalysis\assets\image-20220304110549108.png)
