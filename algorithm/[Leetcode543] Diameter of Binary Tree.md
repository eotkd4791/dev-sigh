### [Leetcode543] Diameter of Binary Tree

![](./images/leetcode.png)

### 문제 링크

[Leetcode Diameter of Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree/)

### 문제 설명

트리를 이루는 임의의 두 노드 간 거리의 최대값을 구하는 문제였다.
임의의 두 노드 간 거리가 최대가 되는 경우, `루트를 지나지 않는 경로`가 존재할 수 있다.
노드의 갯수는 최소 1개 부터 최대 10000(만)개까지 입력으로 주어진다.

### 풀이 설명

먼저 루트 노드를 기준으로 생각해보면,
`루트 노드를 지나는 경로의 최대 거리` = `루트에서 가장 먼 왼쪽 서브 트리 내의 노드에서 루트까지의 경로` + `루트에서 가장 먼 오른쪽 서브 트리 내의 노드에서 루트까지의 경로` 이다.

`루트에서 가장 먼 왼쪽 서브 트리 내의 노드에서 루트까지의 경로`는 다시 왼쪽 자식 노드를 루트로 보고, 해당 루트부터 왼쪽 서브 트리 노드와 오른쪽 서브 트리 노드의 최대 거리 합과 같다. 따라서 재귀 함수를 이용하여 더 작은 문제로 쪼개어 생각했다.

아래 코드를 보면 `recur 함수`의 인자로 전달된 노드를 루트로 하는 왼쪽 서브 트리, 오른쪽 서브 트리가 있다면, 왼쪽 서브 트리에 존재하는 노드 중 인자로 전달된 노드와의 최대 거리값이 `left` 변수에 할당되고, 오른쪽 서브트리 까지의 거리는 `right`에 할당된다.

따라서 인자로 전달된 노드를 지나는 최대 거리값은 `left + right`로 나타낼 수 있다. 재귀 함수 `recur`가 반환하는 값은 `left + right`가 아니라 `left`와 `right`중 더 큰 값에 `부모 노드까지의 거리(1)을 더한 값`을 반환해야한다. 부모 노드까지 연결되는 경로는 인자로 전달된 노드의 자손 노드가 아닌, 다른 곳에 위치한 노드를 의미하기 때문이다.

### 풀이

<script src="https://gist.github.com/eotkd4791/5125356ecd3e7988168da06fc5d6365f.js"></script>