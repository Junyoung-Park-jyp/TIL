# INDEX

* Data Structure

* 비시퀀스 데이터 구조

<br>

# 비시퀀스 데이터 타입

<br>

# set(고유한 항목들의 정렬되지 않은 컬렉션)

* 중복이 없고, 비시퀀스(정렬X) 타입

## 세트 관련 메서드

* .add(x): 세트에 x를 추가

    * 세트 내부에 있는 원소는 들어가지 않는다

```python
my_set = {'a', 'b', 1, 2, 3}

my_set.add(4)
print(my_set) # {'a', 'b', 1, 2, 3, 4}

my_set.add(4)
print(my_set) # {'a', 'b', 1, 2, 3, 4} 들어가지 않음
```

* .clear(): 세트의 원소를 모두 제거

* .remove(x): x를 세트에서 제거, x가 없을시 KeyError

* .pop(): 세트에서 임의의 값을 반환하고 제거

> 이용하면 포커게임 같은걸 만들 수 있을듯?

* .update(iterable): 세트에 다른 iterable 요소 추가

```python
my_set = {1,2,3}

my_set.update([1,2,3,4,5,6])
print(my_set) # {1,2,3,4,5,6} 중복값은 들어가지 않음
```

* .discard(): 세트 s에서 항목 x를 제거 remove와 달리 에러는 없음

<br>

## 세트의 집합 메서드

```python
set_1 = {0,1,2,3,4}

set_2 = {1,3,5,7,9}

print(set1.difference(set2)) # {0,2,4} 차집합 set1 - set2
print(set1.intersection(set2)) # {1,3} 교집합 set1 & set2
print(set1.issubset(set2)) # False set1 <= set2
print(set1.issuperset(set2)) # False set1 >= set2
print(set1.union(set2)) # {0,1,2,3,4,5,7,9} 합집합 set1 | set2
```

<br>

# 딕셔너리

* 고유한 항목들의 정렬되지 않은 컬렉션

## 딕셔너리 메서드

* D.clear(): 딕셔너리 내부의 모든 키/값을 젝

* D.get(key[,default]): key에 연결된 값을 반환(없으면 None, 혹은 default 반환)

* D.keys(): 딕셔너리의 key를 모은 객체 반환
    * 대괄호로 감싸져 있음(iterable하다)

* D.values(): 딕셔너리의 value를 모은 객체 반환

* D.items(): 딕셔너리 키/값 쌍을 모은 객체 반환

* D.pop(key[,default]): 키를 제거하고 연결됐던 값을 반환(없으면 에러나 default 반환)

```python
person = {'name': 'Alice', 'age': 25}

print(person.pop('age')) # 25
print(person) {'name' : 'Alice'}
print(person.pop('country')) # KeyError
print(person.pop('country', None)) # None
```

* D.setdefault(key[,default]): 키와 연결된 값을 반환, 키가 없다면 default와 연결한 키를 딕셔너리에 추가하고 default 반환

```python
person  {'name': 'Alice', 'age': 25}

print(person.setdefault('country', 'Korea')) # Korea
print(person) # {'name': 'Alice', 'age': 25, 'country': 'Korea'}
```

* D.update([other]): other의 키/값 쌍으로 딕셔너리 갱신(기존 키는 덮어쓴다)

```python
person = {'name': 'Alice', 'age': 25}
other_person = {'name': 'Jane', 'gender': 'female'}

person.update(other_person)
print(person) # {'name': 'Jane', 'age': 25, 'gender': 'female'}

person.update(age=50)
print(person) # {'name': 'Jane', 'age': 50, 'gender': 'female'}

person.update(country='Korea')
print(person) # {'name': 'Jane', 'age': 50, 'gender': 'female', 'country': 'Korea'}

person.update(age=50, country='Korea') # 동시에 여러가지 업데이트 가능
```

<br>

# 참고

# 해시 테이블(Hash Table)

* 해시 함수를 사용해 변환한 값을 index로 삼아 key, value를 저장하는 자료 구조
    * 데이터를 효율적으로 저장, 검색에 사용

<br>

## 해시 테이블 원리

* key를 해시 함수를 통해 해시 값으로 변환, 그 값을 index로 데이털르 저장, 검색
    * 데이터 검색이 매우 빠름

<br>
 
## 해시(Hash)

* 임의의 크기를 가진 데이터를 고정된 크기의 고유한 값으로 변환

* 이렇게 생성된 고유값은 해당 데이터 식별에 주로 사용
    * 일종의 '지문'같은 역할
    * 데이터를 고유하게 식별
 
* 파이썬에서는 해시 함수를 사용해 데이터를 해시 값으로 변환하고 정수로 표현됨

### 해시 함수(Hash Function)

* 임의의 길이의 데이터를 입력 받아 고정된 길이의 데이터(해시 값)을 출력하는 함수

* 주로 해시 테이블 자료구조에 사용하여 매우 빠른 데이터 검색용 소프트웨어에서 유용하게 사용

### set의 요소 & dictionary의 키와 해시테이블 관계

* 파이썬에서 세트의 요소와 딕셔너리의 키는 해시 테이블로 중복되지 않는 고유값 저장

* 세트 내부의 요소들은 해시 함수로 해시 값을 받고, 해시 값을 기반으로 해시 테이블에 저장

* 딕셔너리의 key도 고유하므로 key를 해시 함수로 변환한 해시 값으로 해시 테이블에 저장
    * 딕셔너리의 key들은 매우 빠르게 탐색되고, 중복값 허용 X

```python
# 정수의 경우, 정수 값 자체가 해시 값

my_set = {3,2,1,9,100,4,87,39,10,52}

print(my_set.pop()) # 1
print(my_set.pop()) # 2
print(my_set.pop()) # 3
print(my_set.pop()) # 100
print(my_set.pop()) # 4
print(my_set.pop()) # 39
print(my_set.pop()) # 9
print(my_set.pop()) # 10
print(my_set.pop()) # 52
print(my_set.pop()) # 87
print(my_set) # set()
```
```python
# 문자열의 경우, 반환 값이 매번 다름

my_str_set = {'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j'}

print(my_str_set.pop()) # a 때로는 c
print(my_str_set.pop()) # f 때로는 j
print(my_str_set.pop()) # ...
print(my_str_set.pop())
print(my_str_set.pop())

print(hash(1)) # 1
print(hash(1)) # 1
print(hash('a')) # 실행마다 다름
print(hash('a')) # 실행마다 다름
```
> 해시함수는 객체의 타입에 따라 다르게 동작
> 정수와 문자열은 다른 타입이기에, 해시 값 계산 방식도 다름

### 파이썬의 해시 함수 - 정수

* 같은 정수는 항상 같은 해시 값

* 해시 테이블에 정수 저장시 효율적

* hash(1), hash(2)는 항상 값이 다르지만, hash(1)의 값은 항상 동일

### 파이썬의 해시 함수 - 문자열

* 문자열의 길이는 가변적

* 각 문자의 유니코드 코드 포인트 등을 기반으로 해시 값 계산

* 이로 인해 문자열의 해시 값이 실행마다 다르게 계산

### set.pop()과 해시 테이블의 관계

* pop()은 set에서 임의의 요소를 제거하고 반환

* 실행시마다 다른 요소를 주는 '무작위'가 아닌 '임의'라는 의미에서 '무작위'
    * 'arbitrary' != 'random

* 해시 테이블의 순서대로 반환 해주는 것

<br>

## hashable

* hash() 함수의 인자로 전달해서 결과가 반환되는 객체를 hashable이라 함

* 대부분의 불변형 데이터 타입은 hashable

* tuple은 불변형이지만 해시 불가능한 객체를 참조할 경우 tuple도 해시 불가능해질 경우 발생

```python
print(hash(1))
print(hash(1.0))
print(hash('1'))
print(hash((1,2,3)))
# 모두 가능

print(hash((1,2,[3,4]))) 
# TypeError: unhashable type: 'list'
```

<br>

## hashable가 불변성 간의 관계

* 해시 테이블의 키는 불변
    * 객체가 생성된 후 값이 변경 불가

* 불변 객체는 해시 값이 변하지 않기에 동일한 값은 일관된 해시 갑승ㄹ 유지

* 단, 'hash 가능 != 불변하다' (dict)

<br>

## 가변형 객체가 hashable 하지 않은 이유

* 값이 변경 가능하기에 동일한 객체의 해시 값이 변경될 가능성 있음(테이블의 무결성 유지 불가)

* 가변형 객체가 변경될 시 해시 값도 변경되기에, 같은 객체가 다른 해시 값을 반환하는 경우 발생(일관성 유지 불가)

```python
print(hash([1,2,3]))
# TypeError: unhashable type: 'list'

my_set = {[1,2,3],1,2,3,4,5}
# TypeError: unhashable type: 'list'

my_dict = {{3,2}: 'a'}
# TypeError: unhashable type: 'set'
```

## hashable 객체의 필요성

1. 해시 테이블 기반 자료 구조 사용
    * set, dict의 키
    * 중복값 방지
    * 빠른 검색과 조회
2. 불변성을 통한 일관된 해시 값
3. 안정성과 예측 가능성 유지