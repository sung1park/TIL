# graph traversal

> 그래프로 표현된 모든 자료를 빠짐없이 탐색하는 것

### 

### BFS

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



### DFS

```
DFS(v)
	visited[v] <- true
	
	for each all w in adjacency(G, v)
		if visited[w] != true
			DFS(w)
```

