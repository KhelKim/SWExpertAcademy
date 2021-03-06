# 탐욕 알고리즘

## 소개

### 탐욕(그리디) 알고리즘

- 최적화 문제를 해결하는 알고리즘
  - 탐욕 알고리즘은 최적해를 구하는 데 사용되는 근시안적인 방법
- 최적화 문제: 최적(최대값 이나 최소값 같은) 값을 구하는 문제
  - 해당 문제에 여러 해가 있을 수 있음
  - The 최적해를 구하는 것이 아니라 an 최적해를 구하는 것
- 머리 속에 떠오르는 생각을 검증 없이 바로 구현할 경우 Greedy 접근이 됨

1. 여러 경우 중 하나 선택
2. 선택 시 마다 최적이라고 생각되는 것을 선택
3. 최종적인 해답에 도달

- 한번 선택된 것은 번복하지 않음
  - 대부분의 탐욕 알고리즘들은 단순하며, 제한적인 문제들에 적용
- 각 선택의 시점에서 이루어지는 결정은 지역적으로 최적
  - 선택들을 계속 수집하여 최종적 해답을 만들었다고 하여, 최적이라는 보장은 없음

## 동작 과정

### 탐욕 알고리즘의 수행 과정

1. 해 선택
   1. 현재 상태에서 부분 문제의 최적해를 구한 뒤, 부분 해 집합(Solution Set)에 추가
   2. 하나의 선택이 이루어지면 새로운 부분 문제 발생
2. 실행 가능성 검사 실시
   1. 새로운 부분 해 집합의 실행가능 여부 확인
   2. 문제의 제약 조건 위반을 검사
3. 해 검사
   1. 새로운 부분 해 집합이 문제의 해가 되는지 확인
   2. 전체 문제의 해가 완성되지 않았다면 1의 해 선택부터 다시 시작