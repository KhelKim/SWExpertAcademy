# 비트연산

## 비트 연산자

### 프로그래밍 언어에서 지원하는 비트 연산자들

| 연산자 | 연산자의 기능                                     | ex           |
| ------ | ------------------------------------------------- | ------------ |
| &      | 비트단위로 AND 연산을 한다.                       | num1 & num2  |
| \|     | 비트단위로 OR 연산을 한다.                        | num1 \| num2 |
| ^      | 비트단위로 XOR 연산을 한다(같으면 0 다르면 1)     | num1 ^ num2  |
| ~      | 단항 연산자로서 피연산자의 모든 비트를 반전시킨다 | ~num         |
| <<     | 피연산자의 비트 열을 왼쪽으로 이동시킨다.         | num << 2     |
| \>\>     | 피연산자의 비트 열을 오른쪽으로 이동시킨다.       | num >> 2     |

- 비트 연산자는 다른 연산자들에 비해 실행 시간 적게 소요
- 프로그램에서 비트 연산 적용 시 연산 속도를 향상시키거나 메모리 절약 가능
  - 변수에 저장된 양의 정수 값의 홀수와 짝수 판별 - 모듈러 연산자 이용(N % 2)
  - 비트단위 AND(&) 연산 이용 - 마지막 비트값이 일(1)인지 영(0)인지를 보고 판단(N & 1)
  - `1 << n`
    - 2^n의 값을 가짐
    - 원소가 n개일 경우의 모든 부분집합의 수를 의미
    - Power set(모든 부분 집합)
      - 공집합과 자기 자신을 포함한 모든 부분집합
      - 각 원소가 포함되거나 포함되지 않는 2가지 경우의 수를 계싼하면 모든 부분집합의 수가 계산됨
  - i & (1 << j)
    - 계산 결과는 i의 j번째 비트가 1인지 아닌지를 의미

## 비트 연산 예제

### 비트 연산1

특정 위치의 비트값을 확인하는 수식에 대한 예제

~~~python
def BitPrint(i):
    for j in range(7, -1, -1):
        print('1' if (i & (1 << j)) else '0' , end="") 
        # print("%d" % ((i >> j) & 1), end="")
    
for i in range(-5, 6):
    print("%2d = " %i, end="") # %2d, str 시작에서 공백 (2-1)칸
    BitPrint(i)
    print()
~~~

### 비트 연산2

4바이트 크기의 인트형 변수에 저장된 값들을 한 바이트씩 읽어서 비트형태로 출력하는 예제

~~~python
a = 0x10
x = 0x01020304
print("%d = " % a, end="")
BitPrint(a)
print()
print("%08x = " % x, end="")
for i in range(0, 25, 8):
    BitPrint(x >> i)
    print(end="")
~~~

## 엔디안

### 엔디안(Endianness)

- 컴퓨터의 메모리와 같은 1차원의 공간에 여러 개의 연속된 대상을 배열하는 방법을 의미하며 HW 아키텍처마다 다름

- 주의 사항

  - 속도 향상을 위해 바이트 단위와 워드 단위를 변환하여 연산할 때 올바로 이해하지 않으면 오류를 발생시킬 수 있음

- 빅 엔디안(Big-endian)

  - 보통 큰 단위가 앞에 나옴
  - 네트워크

- 리틀 엔디안(Little-endian)

  - 작은 단위가 앞에 나옴

  - 대다수 데스크탑 컴퓨터

    | 종류        | 0x1234의 표현 | 0x12345678의 표현 |
    | ----------- | ------------- | ----------------- |
    | 빅 엔디안   | 12 34         | 12 34 56 78       |
    | 리틀 엔디안 | 34 12         | 78 56 34 12       |

### 비트 연산3

자신의 컴퓨터가 어떤 엔디안 방식인지 확인하는 코드

- 엔디안 확인 코드

~~~python
n = 0x00111111
if n & 0x11:
    print("little endian")
else:
    print("big endian")
~~~

## XOR

### 비트 연산4

비트 연산자 ^를 두 번 연산하면 처음 값을 반환

~~~python
a = 0x86
key = 0x66
print("a ==> ", end="")
BitPrint(a)
print()
print("a ^= key ==> ", end="")
a ^= key
BitPrint(a)
print()
print("a ^= key ==> ", end="")
a ^= key
BitPrint(a)
print()
~~~

