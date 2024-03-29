# 배열 2(Array 2)

* 배열: 2차원 배열
* 부분집합 생성
* 바이너리 서치(이진 탐색)
* 셀렉션 알고리즘
* 선택 정렬

<br>

## 2차원 배열의 선언

* 1차원 List를 묶어놓은 List
* 2차원 이상의 다차원 List는 차원에 따라 Index를 선언
* 2차원 List의 선언: 세로길이(행의 개수), 가로길이(열의 개수)를 필요로 함
* Python에서는 데이터 초기화를 통해 변수선언과 초기화가 가능함

## 배열 순회

* n X m 배열의 n * m 개의 원소를 모두 조사하는 법

```python
for i in range(n):
    for j in range(m):
        f(array[i][j]) # 필요 메서드 수행

# 열 우선 순회
for j in range(m):
    for i in range(n):
        f(array[i][j]) # 필요 메서드 수행       

# 지그재그 순회
for i in range(n):
    for j in range(m):
        f(array[i][j + (m-1-2*j) * (i%2)]) # 필요 메서드 수행

```

## 델타를 이용한 2파 배열 탐색

* 2차 배열의 한 좌표에서 4방향의 인접 배열 요소를 탐색하는 방법

* 인덱스 (i,j)인 칸의 상하좌우 칸 (ni,nj)
    * di[] <- \[0, 1, 0, -1] 방향별로 더할 값
    * dj[] <- \[1, 0, -1, 0]

```python
for k: 0 -> 3
    ni <- i + di[k]
    nj <- j + dj[k]
```

## 전치 행렬

```python
# 1 2 3 -> 1 4 7
# 4 5 6 -> 2 5 8
# 7 8 9 -> 3 6 9

arr = [[1,2,3],[4,5,6],[7,8,9]]

for i in range(3):
    for j in range(3):
        if i < j:
            arr[i][j], arr[j][i] = arr[j][i], arr[i][j]
```

<br>

# 부분집합의 합(subset sum) 문제

* 유한 개의 정수로 이루어진 집합이 있을 때, 이 집합의 부분집합 중에 원소의 합이 0 이 되는 곳이 있는가

* 완전검색 기법으로 풀 시에는 모든 부분집합을 생성 후 합을 모두 계산

## 부분집합의 수

* 집합의 원소가 n개일 때, 공집합을 포함한 부분집합의 개수는 2^n개이다.
* 이는 각 원소를 부분집합에 포함시키거나 포함시키지 않는 2가지 경우를 모든 원소에 적용한 경우의 수와 같다.

<br>

# 비트 연산자

* &: 비트 단위로 AND 연산을 한다
* |: 비트 단위로 OR 연산을 한다
* <<: 피연산자의 비트 열을 왼쪽으로 이동시킨다
* \>>: 피연산자의 비트 열을 오른쪽으로 이동시킨다

* 1<<n:2**n: 원소가 n개일 경우의 모든 부분집합의 수를 의미

* i*(1<<j): i의 j번째 비트가 1인지 아닌지 검사한다

```python
arr = [3,6,7,1,5,4]

n = len(arr)

for i in range(1<<n):
    for j in range(n):
        if i & (1<<j):
            print(arr[j], end = ',')
    print()
print()
```
