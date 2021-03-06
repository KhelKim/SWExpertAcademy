# 최장 증가 수열

어떤 수열이 왼쪽에서 오른쪽으로 순서대로 나열되어있을 때, 나열된 순서를 유지하면서 크기가 점진적으로 커지는 가장 긴 부분수열의 길이는 얼마일까?

### 최장 증가 수열

- 어떤 수열이 왼쪽에서 오른쪽으로 나열되어 있으면, 그 나열 순서를 유지하면서 크기가 점진적으로 커지는 가장 긴 부분수열을 추출하는 문제

- 부분 수열의 요소들이 연속적일 필요는 없음

### 최장 증가 수열 문제에 완전 검색 적용

1. 수열의 모든 부분 집합 구함
2. 해당 부분 집합이 증가 수열 여부 판별
3. 증가 수열 중 가장 길이가 긴 값을 구함

부분 수열 길이가 긴 것부터 조사하는 것이 유리

### 완전 검색으로 최장 증가 수열을 찾기 위한 알고리즘

- $$O(2^n)$$, 지수시간 복잡도

```python
# S: 수열
for i in range(N, 0, -1):
    for ALL subsequence of S with length of i:
        if there is noe increasing subsequence:
            break
```

### 최장 증가 수열을 찾는 다른 방법

LIS(i)를 LIS(1), LIS(2), . . ., LIS(i-1)과의 관계로 표현할 수 있을까?

- Case1: LIS(i)가 $$a_i$$를 포함하지 않는다면, LIS(i) = LIS(i-1)

- Case2: LIS(i)가 $$a_i$$를 포함한다면, LIS(i) = ?

길이 i인 수열에서 $$a_i$$로 끝나는 최장 증가 수열

각 요소로 끝나는 최장 증가 수열들 중 가장 긴 수열이 최장 증가 수열

- Case2: LIS(i)가 $$a_i$$를 포함하는 경우
  - LIS(i)는 $$a_i$$를 포함하는 최장 증가 수열의 길이
  - 증가 수열의 관계인 $$a_j$$ < $$a_i$$인 $$a_j $$찾음($$j$$ < $$i$$)
  - $$j$$값을 알 수 없으므로 모두 검색해야 함
  - 최대값을 찾아 1 증가시켜 LIS(i)에 저장
  - $$LIS(i) = 1 + max_{j < i \text{ and } a_j < a_i}(LIS(j))$$
  - LIS() 중에서 최대값을 찾음

### DP접근 알고리즘

- $$O(n^2)$$

```python
# LIS(i): a[i]로 끝나는 최장 증가 수열의 길이 저장
def LIS_DP():
    for i in range(1, len(a)):
        LIS[i] = 1
        for j in range(1, i):
            if a[j] < a[i] and 1 + LIS[j] > LIS[i]:
                LIS[i] = 1 + LIS[j]
    return max(LIS)
```

## 이진탐색 적용

### 이진 탐색을 이용한 보다 효율적인 방법

- C[k]: 길이 k의 증가 수열에 대하여 가장 작은 값을 C[k]에 저장
- 각 위치에서 C[]를 갱신하기 위해 이진 탐색 수행
- O(nlogn)
- 수열의 길이 n만큼 반복하고 최대 길이 n에 대한 이진 탐색 수행 -> 알고리즘의 시간 복잡도는 O(nlogn)이 됨

