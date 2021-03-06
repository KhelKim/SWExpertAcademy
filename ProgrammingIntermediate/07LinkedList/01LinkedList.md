# Linked List

## List

- 리스트(List)

  1. 순서를 가진 데이터의 묶음 - 같은 데이터의 중복 저장 가능

  2. 시퀀스 자료형 - 인덱싱, 슬라이싱, 연산자, 메서드 사용 가능

  3. 크기제한 없음, 타입제한 없음

     |        | 크기      | 데이터의 타입                  |
     | ------ | --------- | ------------------------------ |
     | 배열   | 변경 불가 | 선언된 한가지 타입만 저장 가능 |
     | 리스트 | 변경 가능 | 다양한 데이터 타입 저장 가능   |

  - 순차 리스트: 배열을 기반으로 구현된 리스트
  - 연결 리스트: 메모리의 동적할당을 기반으로 구현된 리스트

## 순차 List

- 초기화 및 생성
  - 변수에 값을 초기화하는 것으로 리스트 생성
- 데이터 접근
  - 리스트의 인덱스를 이용해 원하는 위치에 데이터를 변경하고 참조할 수 있음
- 리스트
  - 동적 배열로 작성된 순차 리스트
- 자료의 삽입, 삭제 연산
  - 원소의 이동 작업이 필요
- 원소의 개수가 많고 삽입, 삭제 연산이 빈번한 작업
  - 소요되는 시간이 크게 증가

### 리스트 복사

- 여러 가지 방법으로 리스트 복사
- 수행시간의 차이가 있고, 의미가 다른 항목 존재

|      | 코드                                                    | 설명                                                         |
| ---- | ------------------------------------------------------- | ------------------------------------------------------------ |
| 1    | `new_list = old_list`                                   | 주소의 복사, 얕은 복사                                       |
| 2    | `new_list = old_lsit[:]`                                | 슬라이싱, 깊은 복사                                          |
| 3    | `new_list = [] <br /> new_list.extend(old_list)`        | extend(): 리스트를 추가하는 함수, 깊은 복사                  |
| 4    | `new_list = list(old_list)`                             | list(), 깊은 복사                                            |
| 5    | `import copy <br /> new_list = copy.copy(old_list)`     | copy 활용, 깊은 복사                                         |
| 6    | `new_list = [i for i in old_list]`                      | 리스트 함축, 깊은 복사                                       |
| 7    | `import copy <br /> new_list = copy.deepcopy(old_list)` | 리스트 원소까지도 깊은 복사, 가장 느림, 깊은 복사, 메모리가 가장 많이 쓰임 |

2 -> 3 -> 4 -> 5 -> 6 -> 7 순으로 시간이 더 걸림

## 연결 List

- 연결 리스트

  - 리스트의 단점을 보완한 자료 구조
    1. 자료의 논리적인 순서와 메모리 상의 물리적인 순서가 일치하지 않고, 개별적으로 위치하고 있는 원소의 주소를 연결하여 하나의 전체적인 자료구조를 이룸
    2. 링크를 통해 원소에 접근하므로, 순차 리스트에서 물리적인 순서를 맞추기 위한 작업이 필요하지 않음
    3. 자료구조의 크기를 동적으로 조정할 수 있어, 메모리의 효율적인 사용이 가능
    4. 탐색 - 순차탐색

- 연결 리스트 사용을 위한 주요 함수

  | 함수명       | 기능                                                |
  | ------------ | --------------------------------------------------- |
  | addtoFirst() | 연결 리스트의 앞쪽에 원소를 추가하는 연산           |
  | addtoLast()  | 연결 리스트의 뒤쪽에 원소를 추가하는 연산           |
  | add()        | 연결 리스트의 특정 위치에 원소를 추가하는 연산      |
  | delete()     | 연결 리스트의 특정 위치에 있는 원소를 삭제하는 연산 |
  | get()        | 연결 리스트의 특정 위치에 있는 원소를 리턴하는 연산 |

- 노드

  - 연결 리스트에서 하나의 원소에 필요한 데이터를 갖고 있는 자료단위
    - 데이터 필드: 원소의 값을 저장하는 자료구조
    - 링크 필드: 다음 노드의 주소를 저장하는 자료구조

- 헤드

  - 리스트의 처음 노드를 가리키는 레퍼런스

### 단순 연결 리스트

- 노드가 하나의 링크 필드에 의해 다음 노드와 연결되는 구조를 가짐
- 헤드가 가장 앞의 노드르르 가리키고, 각 노드의 링크 필드가 연속적으로 다음 노드를 가리킴
- 최종적으로 None을 가리키는 노드가 리스트의 가장 마지막 노드임

### 단순 연결 리스트의 삽입 연산

- 'A', 'C', 'D'를 원소로 갖고 있는 리스트의 두 번째에 'B' 노드를 삽입할 때,

  1. 메모리를 할당하여 새로운 노드 new 생성
  2. 새로운 노드 new의 데이터 필드에 'B'를 저장
  3. 삽입될 위치의 바로 앞에 위치한 노드의 링크 필드를 new에 복사
  4. new의 주소를 앞 노드의 링크 필드에 저장

- ~~~python
  def addtoFirst(data):
      global Head
      Head = Node(data, None)
  def add(pre, data):
      if pre == None:
          print("error")
      else:
          pre.link = Node(data, pre.link)
  def addtoLast(data):
      global Head
      if Head == None:
          Head = Node(data, None)
      else:
          p = Head
          while p.link != None:
              p = p.link
          p.link = Node(data, None)
  ~~~

### 단순 연결 리스트의 삭제 연산

- 'A', 'B', 'C', 'D' 리스트의 'B' 노드를 삭제할 때

  1. 삭제할 노드의 앞 노드(선행노드) 탐색
  2. 삭제할 노드의 링크 필드를 선행노드의 링크 필드에 복사

- ~~~python
  def deletetoFirst():
      global Head
      if Head == None:
          print("error")
      else:
          Head = Head.link
  def delete(pre):
      if pre == None or pre.link == None:
          print("error")
      else:
          pre.link = pre.link.link
  ~~~

### 이중 연결 리스트

- 양쪽 방향으로 순회할 수 있도록 노드를 연결한 리스트
- 두 개의 링크 필드와 한 개의 데이터 필드로 구성
- cur이 가리키는 노드 다음에 D값을 가진 노드를 삽입하는 과정
  1. 메모리를 할당하여 새로운 노드 new를 생성하고 데이터 필드에 'D'를 저장
  2. cur의 next를 new의 next에 저장하여 cur의 다음 노드를 삽입할 노드의 다음 노드로 연결
  3. new의 값을 cur의 next에 저장하여, 삽입할 노드를 cur의 다음 노드로 연결
  4. cur의 값을 new의 prev 필드에 저장하여 cur를 new의 이전 노드로 연결
  5. new의 값을 new가 가리키는 노드의 다음 노드의 prev 필드에 저장하여 삽입하려는 노드의 다음 노드와 삽입하려는 노드를 연결

### 이중 연결 리스트의 삭제 연산

- cur이 가리키는 노드를 삭제하는 과정
  1. 삭제할 노드의 다음 노드의 주소를 삭제할 노드의 이전 노드의 next 필드에 저장하여 링크를 연결
  2. 삭제할 노드의 다음 노드의 prev 필드에 삭제할 노드의 이전 노드의 주소를 저장하여 링크를 연결
  3. cur이 가리키는 노드에 할당된 메모리를 반환

