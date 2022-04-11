# Shortest Path

> 간선의 <u>가중치가 있는 그래프</u>에서 두 정점 사이 경로들 중 간선의 가중치의 합이 최소인 경로

:heavy_check_mark: 가중치가 없는 경우 탐색 중간에 탐색을 끝낼 수 있는 BFS가 절대적으로 유리



#### 알고리즘

- 하나의 시작 정점에서 끝 정점까지의 최단 경로
  - **다익스트라(dijkstra)** 알고리즘
    - 음의 가중치를 허용하지 않음
  - **벨만-포드(Bellman-Ford)** 알고리즘
    - 음의 가중치 허용

- 모든 정점들에 대한 최단 경로
  - 플로이드-워샬(Floyd-Warshall) 알고리즘



## Dijkstra 

> 시작 정점에서의 거리가 최소인 정점을 선택해 나가면서 최단 경로를 구하는 방식

- 탐욕 기법을 사용한 알고리즘으로 MST의 Prim 알고리즘과 유사
- <u>음의 가중치를 가진 경우에는 유효하지 않음</u>

```
s: 시작 정점, A: 인접 행렬, D: 시작정점에서의 거리
V: 정점 집합, U: 선택된 정점 집합

Dijkstra(s, A, D)
	U = {s};
	
	For  모든 정점 v
		D[v] <- A[s][v]
		
	While U != V
		D[w]가 최소인 정점 w in V-U 를 선택
		U <- U + {w}
		For w에 인접한 모든 미방문 정점 v
			D[v] <- min(D[v], D[w] + A[w][v])
```

### Priority Queue를 이용하기

```python
def dijkstra(start, V, graph):
    dist = [float('inf')] * V
    dist[start] = 0
    pq = [(0, start)]
    
    while pq:
        cur_dist, cur_vertex = heapq.heappop(pq)
        if cur_dist > dist[cur_vertex]: continue
        
        for neighbor, weight in graph[cur_vertex].items():
            distance = cur_dist + weight
            if distance < dist[neighbor]:
                dist[neighbor] = distance
                heapq.heappush(pq, (distance, neightbor))
                
	return dist
```



## Bellman-Ford

> 시작 정점에서 다른 모든 정점까지의 최단경로를 구하는 알고리즘

- 다익스트라와 다르게 <u>음의 가중치에도 유효</u>함

1. 모든 간선에 대해서 가중치의 합을 갱신
2. 위의 과정을 정점의 수 만큼 반복

```python
def bellman(start, V, E, edges):
    dist = [float('inf')] * V
    dist[start] = 0
    
    for i in range(V):
        for j in range(E):
            st = edges[j][0]
            ed = edges[j][1]
            weight = edges[j][2]
            
            if dist[st] + weight < dist[ed]:
                dist[ed] = dist[st] + weight
    
	for i in range(E):
        st = edges[i][0]
        ed = edges[i][1]
        weight = edges[i][2]
        
        if dist[st] + weight < dist[ed]:
            return -1

    return dist
```

