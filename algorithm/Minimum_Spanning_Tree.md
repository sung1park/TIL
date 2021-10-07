# Minimum Spanning Tree

> 최소 신장 트리
>
> 무향 가중치 그래프에서 신장 트리를 구성하는 간선들의 가중치의 합이 최소인 신장 트리

- 신장 트리 
  - n 개의 정점으로 이루어진 무향 그래프에서 n개의 정점과 n-1개의 간선으로 이루어진 트리

- 그래프 최소 비용 문제
  1. 모든 정점을 연결하는 간선들의 가중치의 합이 최소가 되는 트리
  2. 두 정점 사이의 최소 비용의 경로 찾기 (최단 경로)



## Kruskal 알고리즘

> 간선을 하나씩 선택해서 MST를 찾는 알고리즘

1. 최초, 모든 간선을 가중치에 따라 오름차순으로 정렬
2. 가중치가 가장 낮은 간선부터 선택하면서 트리를 증가시킴
3. n-1개의 간선이 선택될 때까지 2를 반복

```
MST_Kruskal(G, w)
	For vertex v in G.V
		Make_Set(v)
	
	G.E에 포함된 간선들을 가중치 w를 기준으로 정렬
	
	FOR 가중치가 가장 낮은 간선 (u, v) 중 G.E에 포함된 것 선택(n-1개)
		IF Find_Set(u) != Find_Set(v)
			union(u, v)
```



## Prim 알고리즘

> 하나의 정점에서 연결된 간선들 중에 하나씩 선택하면서 MST를 만들어 가는 방식

1. 임의 정점을 하나 선택해서 시작
2. 선택한 정점과 인접하는 정점들 중의 최소 비용의 간선이 존재하는 정점을 선택
3. 모든 정점이 선택될 때 까지 1,2 과정을 반복



- 간선이 상대적으로 많을 경우 Kruskal보다 시간적으로 유리함
  - Kruskal은 정렬하는데 nlogn의 시간 소요
- Dijkstra와 유사하지만 Prim은 MST(최소신장트리), Dijkstra는 출발점에서 각 정점까지의 최소거리를 찾아냄

```
MST_PRIM(G, r)
	result <- 0, cnt <- 0			// result: 신장트리 최소비용, cnt : 처리한 정점 수
	For u in G.V
		minEdge[u] = <- infinite	// minEdge[] : 각 정점에서 다른 정점과의 간선 최소
	minEdge[r] <- 0					// 시작 정점 r의 최소비용 0 처리
	While true					// 빈 Q가 아닐동안
		u <- Extract_Min()		// 방문하지 않은 최소비용 정점 찾기
		visited[u] <- true		// 방문 처리
		result <- result + minEdge[u] // 비용 누적
		if (++cnt == N) break;  // 모든 정점이 다 연결되었으면 최소신장트리 완성
		For v in G.Adj[u]		// u의 인접 정점들
			If visited[v] == false AND w(u, v) < minEdge[v]
				minEdge[v] <- w(u, v);
	return result	
```
