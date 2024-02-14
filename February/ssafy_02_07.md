# Stack

<br>

## 스택의 특성

* 마지막에 삽입된 자료를 가장 먼저 꺼낸다. 후입선출(LIFO, Last-In-First-Out)

## 스택을 프로그램에서 구현하기 위해서 필요한 자료구조와 연산

* 자료구조: 자료를 선형으로 저장할 저장소
    * 배열 사용 가능
    * 저장소 자체를 스택이라고 부름
    * 스택의 마지막 삽입 원소를 Top이라 부름
 
<br>

## 스택의 삽입/삭제 과정

* 빈 스택에 원소 A, B, C를 차례대로 삽입 후 한 번 삭제하는 연산과정

```
push A
[A] <- Top = A
push B
[A, B] <- Top = B
push C
[A, B, C] <- Top = C
pop
[A, B] C(out)
```
* append로 순차적으로 삽입 후, pop()으로 마지막에 들어간 원소를 뺀다

<br>

## 재귀 호출

* 필요한 함수가 자신과 같은 경우 자신을 다시 호출하는 구조

* 함수에서 실행해야 하는 작업의 특성에 따라 일반적인 호출방식보다 재귀호출방식으로 함수를 만들면 프로그램의 크기를 줄이고 간단하게 작성

```python
def fibo(n):
    if n == 1:
        return 1
    if n == 0:
        return 0
    else:
        return fibo(n-1) + fibo(n-2)
```

# Memoization

```python
def fibo1(n):
    global memo
    if n >= 2 and memo[n] == 0
        memo[n] = fibo1(n-1) + fibo1(n-2)
    return memo[n]

memo = [0] * (n+1)
memo[0] = 0
memo[1] = 1
```

```python

```