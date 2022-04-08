# BFS DFS

> 너비우선탐색(DFS)과 깊이우선탐색(DFS)

- 비선형구조인 트리/그래프로 표현된 모든 정점을 빠짐없이 탐색



## BFS

> 너비 우선 탐색, Breath-First Search

- 탐색 시작점의 인접 정점들을 모두 차례로 방문하고, 방문한 정점을 시작점으로 해 다시 인접한 정점을 차례로 방문
- 선입선출 형태의 자료구조인 큐를 활용
- 가중치가 없는 그래프의 최단거리를 찾을때 활용하기 좋음

```
BFS(G, v)
	queue 생성
	시작 정점 v를 큐에 삽입
	정점 v를 방문한 것으로 표시
	while (큐가 비어있지 않은 경우) {
		t <- 큐의 첫 번째 원소 반환
		for (t와 연결된 모든 간선에 대해) {
			u <- t의 인접 정점
			u가 방문되지 않은 곳이면,
			u를 큐에 넣고, 방문한 것으로 표시
		}
	}
```

##### Python

```python
def BFS(graph, root):
    visited = set([root])
    search = []
    queue = deque([root])
    
    while queue:
        cur = queue.popleft()
        search.append(cur)
        for node in graph[cur]:
            if node not in visited:
                queue.append(node)
                visited.add(node)
    
    return search
```





## DFS

> 깊이 우선 탐색, Depth-First Search

- 한 방향으로 갈 수 있는 경로만큼 가고, 더 이상 갈 곳이 없게 되면 갈림길로 돌아와 방문하지 않는 정점으로 탐색을 계속함
- 재귀적으로 사용하거나 후입선출 구조의 자료구조인 스택을 활용
- 재귀 구조를 사용하는 경우 메모리를 많이 사용하지만, 코드가 간결함 

```
DFS(v)
	visited[v] <- true
	
	for each all w in adjacency(G, v)
		if visited[w] != true
			DFS(w)
```

##### Python

```python
def DFS(graph, start_node):
    visit = [start_node]
    stack = []
    
    stack.append(start_node)
    cur = start_node
    
    while stack:
        for node in graph[cur]:
            if node not in visited:
                stack.append(node)
                visited.append(node)
                cur = node
                break
        else:
            stack.pop()
            if stack: 
                cur = stack[-1]

	return visited
```

```python
visited = []

def DFS(graph, cur):
    global visited
    if cur not in visited:
        visited.append(cur)
        for node in graph[cur]:
            DFS(graph, node)
```

