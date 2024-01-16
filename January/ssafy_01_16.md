# Sequence Type Data(이어서)

<br>

# List type

* 여러 값을 순서대로 저장하는 **변경 가능한** 시퀀스 자료형

<br>

## 리스트 표현

* 0개 이상의 객체를 포함하여 데이터 목록 저장

* 대괄호([])로 표기

* *어떠한 자료형*도 데이터가 될 수 있다
```
my_list_1 = []

my_list_2 = [1, 'a', 3, 'b', 5]

my_list_3 = [1, 2, ['Hello', 'World']]
```

<br>

## 리스트의 시퀀스 특징

* 인덱싱, 슬라이싱, 길이 등의 시퀀스 요소 모두 보유
```
my_list = [1, 2, 'a', 4, 'b']

print(my_list[1]) # 2
print(my_list[2:4]) #['a', 4]
print(len(my_list)) # 5
```
<br>

## 리스트는 *변경 가능*

```
my_list = [1, 2, 'a', 4, 'b']
my_list[0] = 100
print(my_list) # [100, 2, 'a', 4, 'b']
```
<br>

# Tuple type
* 리스트와 유사하지만 변경이 불가능한 시퀀스 자료

## 튜플 표현

* 0개 이상 객체(리스트와 동일)

* 소괄호(())로 표기

* 리스트와 동일하게 자료형은 무관
```
my_tuple_1 = ()

my_tuple_2 = (1,) # 요소가 하나일 경우에는 반드시 ,가 필요
                  # ,가 없을 시 int형 취급
```
<br>

## 튜플의 시퀀스 특징

* 인덱싱, 슬라이싱, 길이 측정 가능

<br>

## 튜플은 *변경 불가능*

```
my_tuple = (1, 2, 3, 'a', 'b')

# TypeError: 'tuple' object does not support item assignment
my_tuple[1] = 'z'
```

<br>

## 튜플은 어디에 쓰일까?

* 튜플의 불변 특성을 사용해 안전하게 여러 개의 값을 전달, 그룹화, 다중 할당
* *개발자가 직접* 사용하기보다는 '파이썬 내부 동작'에서 주로 사용

<br>

# Range type
* 연속된 정수시퀀스를 생성하는 변경 불가능한 자료형

<br>

## range 표현

* range(n)
    * 0부터 n-1까지의 숫자 시퀀스
> 0부터 시작하기 때문에 n이지만 n-1까지 생성 
* range(n, m)
    * n부터 m-1까지의 숫자 시퀀스

<br>

* 주로 반복문과 함께 사용 
```
my_range_1 = range(5)
my_range_2 = range(1, 10)

print(my_range_1) # range(0, 5)
print(my_range_2) # range(1, 10)

# list로 형 변환하여 데이터 확인
print(list(my_range_1)) # [0, 1, 2, 3, 4]
print(list(my_range_2)) # [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

<br>

# Non-seqeunce type

<br>

# Dict type
* **key-value** 쌍으로 이루어진 *순서와 중복*이 없는 *변경 가능*한 자료형

<br>

## 딕셔너리 표현

* key는 *변경 불가*한 자료형만 사용

* value는 모든 자료형 사용 가능

* 중괄호({})로 표기

<br>

## 딕셔너리 사용

* key를 통해 value에 접근
  
* 요소 간의 순서가 없다
  
* value 변경 가능
```
my_dict = {'apple': 12, 'list': [1,2,3]}

print(my_dict['apple']) # 12

my_dict['apple'] = 100

print(my_dict['apple']) # 100
```

<br>

# Set
* 순서와 중복이 없는 변경 가능한 자료형
  
<br>

## 세트 표현

* 수학의 집합과 동일한 연산 처리

* 중괄호({})로 표기

```
my_set_1 = set() # dict와 겹치기에 빈 set은 set()로 생성
my_set_2 = {1, 2, 3}
my_set_3 = {1, 1, 1}

print(my_set_1, my_set_2, my_set_3) # set(), {1, 2, 3}, {1}
```

## 세트의 집합 연산

```
my_set_1 = {1, 2, 3}
my_set_2 = {3, 6, 9}

# 합집합
print(my_set_1 | my_set_2) # {1, 2, 3, 6, 9}

# 차집합
print(my_set_1 - my_set_2) # {1, 2}

# 교집합
print(my_set & my_set_2) # {3}
```

# Boolean
* True of False의 값

<br>

# Type Conversion

## 암시적 형변환

* Boolean과 Numeric Type에서 가능
```
print(3 + 5.0) # 8.0
# True = 1, False = 0 
print(True + 3) # 4

print(True + False) # 1
```

<br>

# 연산자

<br>

## 산술 연산자

|기호|연산자|
|:---|:---:|
| + | 더하기|
| - |빼기/음수값| 
| * |곱하기|
| / |나누기| 
| // |몫| 
| % |나머지|
| **|지수(제곱)| 

<br>

## 복합 연산자

|기호|예시| 의미|
|:---|:---:|:---:|
| += |a += b| a = a + b|
| -= |a -= b| a = a - b|
| *= |a *= b| a = a * b|
| /= |a /= b| a = a / b|
| //= |a //= b| a = a // b|
| %= |a %= b| a = a % b|
| **= |a **= b| a = a ** b|

<br>

## 비교 연산자

|기호|내용|
|:---|:---:|
| < | 미만|
| <= |이하| 
| > |초과|
| >= |이상| 
| == |같음| 
| != |같지 않음|
| is|같음|
| is not|같지 않음|

<br>

## is 비교 연산자

* 메모리 내에서 같은 객체를 참조하는지 확인

* ==는 동등성(equality), is 는 식별성(identity)

* 값을 비교하는 ==와 다름

```
# 예시

# ==이 더 나은 경우
print(2.0 == 2) # True
print(2.0 is 2) # False

# is가 더 나은 경우
print(1 == True) # True
print(1 is True) # False
```
> 일반적인 값을 비교할 때는 == 사용, is 는 True False를 비교할 때

<br>

## 논리 연산자

|기호|연산자|내용|
|:---|:---:|:---:|
| and |논리곱|두 경우가 모두 True일때 True|
| or |논리합| 한 경우만 True여도 True|
| not |논리부정|반대로 처리|

```
# 예시

print(True and False) # False
print(True or False) # True
print(not True) # False
```
```
# 예시 2
# 비교 연산자와 사용

num = 15
result = (num > 10) and (num % 2 == 0)
print(result) # False
# 10 이상인 짝수 여부 판단
```

<br>

# 단축 평가

* 논리 연산에서 두 번째 피연산자를 평가하지 않고 결과를 결정하는 동작

* and에서 앞이 False일 경우, 뒤의 연산은 실행 되지 않는다

* or에서 앞이 True일 경우, 뒤의 연산은 실행 되지 않는다

<br>

## 단축 평가 이유

* 코드 실행 최적화, 불필요한 연산 회피

<br>

# 멤버십 연산자

* 특정 값이 시퀀스나 다른 컬렉션에 속하는지 여부 확인(강력한 연산자)
```
word = 'hello'
numbers = [1, 2, 3, 4, 5]

print('h' in word) # True
print('z' not in word) # True

print(4 not in numbers) # False
print(2 in numbers) # True
```

<br>

# 시퀀스형 연산자

* 문자열1 + 문자열2 = 문자열1문자열2

* 문자열 * int =  문자열을 int만큼 반복

```
# Junyoung Park
print('Junyoung' + ' Park')

# hihihi
print('hi' * 3)

# [1, 2, 'a', 'b']
print([1, 2] + ['a', 'b'])
```

<br>