# 분할 정복

## 거듭 제곱

* O(n)

```python
def power(base, exponent):
    if base == 0:
        return 1
    result = 1
    for i in range(exponent):
        result *= base
    return result
```

* 부분으로 문제를 나눈다

* 나눈 문제를 해결한다

* 필요하다면 나눈 부분을 합친다

## 퀵 소트

* 주어진 배열을 분할하고, 각각 정렬한다

* 기존 합병정렬과의 차이
    * 그냥 두 부분으로 나누는 것이 아닌, 특정 아이템 중심(pivot item)으로, 이보다 작은 걸 왼쪽, 큰 걸 오른쪽에 위치
    * 각 부분 정렬이 끝난 후, 합병이라는 후처리 작업이 필요없다