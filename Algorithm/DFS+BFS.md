# 깊이우선탐색(DFS)와 넓이우선탐색(BFS)

# 깊이 우선 탐색 (Depth First Search)
- "더 나아갈 길이 보이지 않을 때까지 깊이 들어간다"
- 동작방식
	1. 시작 정점을 밟은 후 이 정점을 방문했음으로 표시
    2. 이 정점과 이웃하는 정점 중에 아직 방문하지 않은 곳을 선택하여 이를 시작 정점으로 삼아 다시 깊이 우선 탐색을 시작 (1번을 다시 수행)
    3. 정점에 더 이상 방문하지 않은 인접 정점이 없ㅇ므ㅕㄴ 이전 정점으로 돌아가서 2단계 수행
    4. 이전 정점으로 돌아가도 더 이상 방문할 이웃이 없다면 그래프의 모든 정점을 방문했다는 의미. -> 탐색 종료
 
```JAVA
    public static void dfs(int i){
        visited[i] = true;
        
        for(int j=1; j<=N; j++){
            if(graph[i][j]==1&& visited[j]==false){ //정점이 이어져 있고, 방문하지 않았다면
                dfs(j);
            }
        }
    }
      

```

# 너비 우선 탐색 (Breath First Search)
- "꼼꼼히 좌우를 살피며 다니자"
- 동작방식
	1. 시작 정점을 방문했음으로 표시하고 큐에 삽입
    2. 큐로부터 정점을 제거함. 제거한 정점이 이웃하고 있는 인접 정점 중 아직 방문하지 않은 곳들을 '방문했음'으로 표시하고 큐에 삽입
    3. 큐가 비게 되면 탐색이 끝난 것임. 큐가 빌 때까지 2의 과정 반복

```JAVA  
    public static void bfs(int i){
        Queue<Integer> q = new LinkedList<Integer>();
        q.offer(i);
        visited[i] = true;
        
        int temp;
        while(!q.isEmpty()){
            temp = q.poll();
            for(int j=1; j<=N; j++){
                if(graph[temp][j]==1&&visited[j]==false){
                    q.offer(j);
                    visited[j]=true;
                }
            }                       
        }
    }

```