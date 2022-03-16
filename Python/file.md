# File

> 파일 열기/닫기, 읽기, 쓰기, 모드



#### 파일 열기/닫기

```python
file = open('data.txt')
content = file.read()
file.close()
```

#### 파일 자동으로 닫기

```python
with open('data.txt') as file:
    	content = file.read()
```

#### 줄 단위로 읽기

```python
content = []
with open('data.txt') as file:
	for line in file:
        contents.append(line)
```

#### 파일 모드

```python
# 쓰기모드
with open('data.txt', 'w') as file:
    file.write('Hello')
```

