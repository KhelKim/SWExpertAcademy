# Binary search Tree

## Binary search Tree의 특징

1. 탐색작업을 효율적으로 하기 위한 자료 구조
2. 모든 원소는 서로 다른 유일한 키를 가짐
3. key(왼쪽 서브트리) < key(루트 노드) < key(오른쪽 서브트리)
4. 왼쪽 서브트리와 오른쪽 서브트리도 이진 탐색 트리임
5. 중위 순회하면 오른차순으로 정렬된 값을 얻을 수 있음

## Binary search Tree의 연산

### 탐색 연산

1. 루트에서 시작
2. 탐색할 키값 x를 루트 노드의 키값과 비교
   1. 키값 x = 루트 노드의 키값
      1. 원하는 원소를 찾았으므로 탐색 연산 성공
   2. 키값 x < 루트 노드의 키값
      1. 루트 노드의 왼쪽 서브트리에 대해서 탐색 연산 수행
   3. 키값 x > 루트 노드의 키값
      1. 루트 노드의 오른쪽 서브트리에 대해서 탐색 연산 수행
3. 서브트리에 대해서 순환적으로 탐색 연산을 반복

### 삽입 연산

1. 먼저 탐색 연산을 수행
   1. 삽입할 원소와 같은 원소가 트리에 있으면 삽입할 수 없으므로, 같은 원소가 트리에 있는지 탐색하여 확인
   2. 탐색에서 탐색 실패가 결정되는 위치가 삽입 위치가 됨
2. 탐색 실패한 위치에 원소를 삽입

## Binary search Tree의 성능

1. 탐색(searching), 삽입(insertion), 삭제(deletion) 시간은 트리의 높이에 좌우 됨
   1. $$O(h)$$, $$h$$: BST의 깊이(height)
2. 평균의 경우
   1. 이진 트리가 균형적으로 생성되어 있는 경우
   2. $$O(logn)$$
3. 최악의 경우
   1. 한쪽으로 치우친 경사 이진 트리의 경우
   2. $$O(n)$$
   3. 순차탐색과 시간복잡도가 같음

### 검색알고리즘의 비교

1. 리스트에서의 순차 검색: $$O(N)$$
2. 정렬된 리스트에서의 순차 검색: $$O(N)$$
3. 정렬된 리스트에서의 이진 검색: $$O(logN)$$
4. 이진 탐색 트리에서의 평균: $$O(logN)$$
   1. 최악의 경우: $$O(N)$$
   2. 완전 이진 트리 또는 균형 트리로 바꿀 수 있다면 최악의 경우를 없앨 수 있음
      1. 새로운 원소를 삽입할 때 삽입 시간을 줄임
      2. 평균과 최악의 시간이 같음, $$O(logN)$$
5. 해쉬 검색: $$O(1)$$

