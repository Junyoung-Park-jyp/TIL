# 큐(Queue)

## 특성

* 스택과 마찬가지로 삽입과 삭제의 위치가 제한적(선입선출)

* FIFO(First-In-First-Out): Queue에 삽입한 순서대로 저장, 먼저 들어온 데이터가 먼저 삭제

<br>

## enQueue(item)

* 마지막 원소 뒤에 새로운 원소를 삽입하기
    * rear 값을 증가시켜 새 원소 자리 마련
    * 그 인덱스에 해당하는 Q\[rear]에 저장
```python
def enQueue(item):
    global rear
    if isFull(): print('Queue is full')
    else:
        rear += 1
        Q[rear] = item
```

## deQueue(item)

* 가장 앞의 원소를 삭제하기
    * front 값을 하나 증가시켜, 큐에 남아있는 첫 원소 이동
    * 새로운 첫 원소를 리턴