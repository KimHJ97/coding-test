# DFS

DFS(Depth First Search, 깊이 우선 탐색)는 그래프나 트리에서 깊이(depth)를 우선적으로 탐색하는 알고리즘입니다. 시작 정점에서 출발하여 한 방향으로 가능한 깊이까지 탐색한 후, 더 이상 갈 곳이 없으면 이전 정점으로 되돌아가 다른 경로를 탐색하는 방식으로 진행됩니다.

 - __스택 기반__: DFS는 스택(Stack) 자료구조를 사용하여 구현됩니다. 스택을 명시적으로 사용할 수도 있고, 재귀 호출을 통해 암묵적으로 스택을 활용할 수도 있습니다.
 - __완전 탐색__: 모든 노드와 간선을 탐색할 수 있습니다.
 - __깊이 우선__: 같은 경로를 따라 최대한 깊숙이 탐색한 후, 다른 경로로 이동합니다.
 - __백트래킹__: 더 이상 탐색할 노드가 없으면 이전 단계로 돌아가 다른 선택지를 탐색합니다.

```
# DFS 동작 과정
1. 시작 노드에서 출발하여 현재 노드를 방문 처리합니다.
2. 인접한 노드들 중 방문하지 않은 노드를 찾아 스택에 추가합니다.
3. 스택의 최상단 노드를 꺼내어 탐색합니다.
4. 더 이상 방문할 노드가 없으면 스택을 비우고 종료합니다.
```
