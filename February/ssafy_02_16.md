# BFS(너비 우선 탐색)

## 그래프 탐색 방법 두 가지

* dfs: 깊이 우선 탐색

* bfs: 너비 우선 탐색

## BFS의 로직

* 탐색 시작점의 인접 정점을 모두 차례로 방문 후, 방문 정점을 시작점으로 다시 인접 정점을 차례로 방문

* 인접 정점에 대해 탐색 후, 차례로 다시 너비 우선 탐색 진행하기에, 선입선출인 큐를 활용

```python
def bfs(g, v):  # 그래프 g, 탐색시작점 v
    visited = [0] * (n+1)  # n: 정점 수
    queue = deque()  # 큐 생성
    queue.append(v)  # 시작점 삽입
    while queue:  # 큐가 남은 경우
        t = queue.leftpop()  # 첫 원소 반환
        if not visited[t]:  # 방문 처리
            visited[t] = True
            visit(t)  # 정점 t에서 실행할 일
            for i in g[t]:  # 나머지 t와 연결된 정점을
                if not visited[i]:  # 방문 처리하고 큐에 삽입
                    queue.append(i)
```

* 초기 상태
    * Visited 배열 초기화
    * Q 생성
    * 시작점 enqueue(방문 표시)
 
```python
def bfs(g, v, n):
    visited = [0] * (n+1)
    queue = deque()
    queue.append(v)
    visited[v] = 1
    while queue:
        t = queue.popleft()
        visit(t)
        for i in g[t]:
            if not visited[i]:
                queue.append(i)
                visited[i] - visited[t] + 1
```

## bfs는 시작점을 여러 개로 등록 가능

* 시작