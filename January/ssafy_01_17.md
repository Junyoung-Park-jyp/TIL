# 함수(Functions)

* 특정 작업을 수행하기 위한 재사용 가능한 코드 묶음

<br>

## 함수를 사용하는 이유

* 두 수의 합을 구하는 함수를 정의하고 사용함으로써 코드의 중복을 방지

* *재사용성*이 높아지고 코드의 *가독성과 유지보수성* 향상

```
# 단순한 합산
num1 = 5
num2 = 3
sum_result = num1 + num2
print(sum_result) # 8

# 함수로 시행
def get_sum(num1, num2):
    return num1 + num2

sum_result= get_sum(num1, num2)
print(sum_result) # 8
```
<br>

# 내장 함수(Built-in function)

* 파이썬이 기본적으로 제공하는 함수(import 없이 즉시 사용 가능)

<br>

## 내장 함수 예시

* 절대값 함수 abs
```
result = abs(-1)

print(result) # 1
```

<br>

# 함수 호출(function call)

* 함수를 실행하기 위해 이름을 사용하여 해당 함수의 코드 블록을 실행하는 것

<br>

## 함수 구조

```
def make_sum(param1, param2):
    """ Docstring(함수 설명)
    이것은 두 숫자의 합을 반환하는 함수입니다
    >>> make_sum(1, 2)
    """"
    return param1 + param2
```
> INPUT을 넣으면 function을 거쳐서 OUTPUT이 나오는 구조

<br>

## 함수의 정의와 호출

* 함수 정의(정의)
    * 함수 정의는 def 키워드로 시작
    * def 키워드 이후 함수 이름 작성
    * 괄호 안에 매개변수를 정의할 수 있음
    * 매개변수(parameter)는 함수에 전달되는 값을 나타냄

* 함수 반환 값
    * 함수는 필요한 경우 결과를 반환할 수 있음
    * return 키워드 이후 반환할 값 명시
    * return 문은 함수의 실행 종료 후 결과를 호출 부분으로 반환
 
* 함수 호출
    * 함수를 호출하기 위해서는 함수의 이름과 필요한 인자(argument)를 전달
    * 호출 부분에서 전달된 인자는 함수 정의 시 작성한 매개변수에 대입됨
 
<br>

# 인자의 종류

<br>

## Positional Areguments(위치인자)

* 함수 호출 시 인자의 위치에 다라 전달되는 인자

* **위치인자는 함수 호출 시 반드시 값을 전달해야 함**

<br>

## Default Argument Values(기본인자 값)

* 함수 정의에서 매개변수에 기본 값을 할당하는 것

* 함수 호출 시 인자를 전달하지 않으면 기본값이 매개변수에 할당됨
```
def greet(name, age=30):
    print(f'안녕하세요 {name}님! {age}살이시군요.')

greet('Bob') # 안녕하세요 Bob님! 30살이시군요.
greet('Albert', 40) # 안녕하세요 Albert님! 40살이시군요.
```

## Keyword Arguments(키워드 인자)

* 함수 호출 시 인자의 이름과 함께 값을 전달하는 인자

* 매개변수와 인자를 일치시키지 않고, 특정 매개변수에 값을 할당할 수 있음

* 인자의 순서는 중요하지 않으며 인자의 이름을 명시하여 전달

* **단, 호출 시 키워드 인자는 위치 인자 뒤에 위치해야함**

## Arbitrary Argument Lists(임의의 인자 목록)

* 정해지지 않은 개수의 인자를 처리하는 인자

* 함수 정의시 매개변수 앞에 *를 붙여 사용하며, 여러 개의 인자를 tuple로 처리

```
def calculate_sum(*args):
    print(args)
    total = sum(args)
    print(f'합계: {total}')
#(1,2,3)
# 합계: 6
```

## 임의의 키워드 인자

* 정해지지 않은 개수의 키워드 인자를 처리하는 인자

*  **를 붙여서 사용

## 함수 인자 권장 작성 순서

* 위치 -> 기본 -> 가변 -> 가변 키워드

* 호출 시 인자를 전달하는 과정에서 혼란을 줄임

* **단, 모든 상황에 적용되는 절대적인 규칙은 아니며 상황에 따라 유연하게 조정가능**

<br>

# Python의 범위(Scope)

* 함수는 코드 내부에 local scope를 생성하며, 그 외의 공간인 global scope로 구분

* scope
    * global scope: 코드 어디에서든 참조할 수 있는 공간
    * local scope: 함수가 만든 scope(함수 내부에서만 참조 가능)
* variable
    * global variable: global scope에 정의된 변수
    * local variable: local scope에 정의된 변수

<br>

## 변수 수명주기(lifecycle)

* 변수의 수명주기는 변수가 선언되는 위치와 스코프에 따라 결정됨
    1. built-in scope
        * 파이썬이 실행된 이후부터 영구 유지
    2. global scope
        * 모듈이 호출된 시점 혹은 인터프리터가 끝날 때까지 유지
    3. local scope
        * 함수가 호출될 때 생성, 함수가 종료될 때까지 유지

<br>
      
## LEGB Rule 예시

* sum이라는 이름을 global scope에서 사용하게 되면서, 기존 built-in scope에 있던 내장함수 sum을 사용하지 못하게 됨

* sum을 참조시 LEGB Rule에 따라 global에서 먼저 찾기 때문

<br>

# 'global' 키워드

* 변수의 스코프를 전역 범위로 지정하기 위해 사용

* 일반적으로 함수 내에서 전역 변수를 수정하려는 경우에 사용

* 가급적 사용하지 말 것, 인자로 넘기고 반환 값 사용을 권장

```
num = 0

def increment():
    global num
    num += 1

print(num) # 0
increment()
print(num) # 1

```

## 'global' 키워드 주의사항

* 선언 전에 접근 금지

* 매개변수에 global 사용 불가

<br>

# 재귀 함수

* 함수 내부에서 자기 자신을 호출하는 함수

<br>

## 재귀 함수 특징

* 특정 알고리즘 식을 표현할 때 변수의 사용이 줄어들며, 코드의 가독성이 높아짐

* 1개 이상의 base case(종료되는 상황)가 존재하고, 수렴하도록 작성

> 재귀 함수 예시 - 팩토리얼
> ```
> n!
> n * (n-1)!
> n * (n-1) * (n-2)!
> ...
> ```
* 종료 조건을 설정해서 재귀 호출이 멈추도록 해야한다

* 재귀 호출의 결과로 문제를 분할하고, 분할한 문제들의 결과를 조합하여 최종 결과를 도출

<br>

# 유용한 함수

<br>

## 유용한 내장 함수

* map과 zip 함수 알아보기

<br>

# map(function, iterable)

* 순회 가능한 데이터 구조(iterable)의 모든 요소에 함수를 적용하고, \n 그 결과를 map object로 반환

```
numbers = [1, 2, 3]
result = map(str, numbers)

print(resut) # <map object at id>
print(list(result)) # ['1', '2', '3']
```

<br>

# zip(*iterables)

* 임의의 iterable을 모아 튜플을 원소로 하는 zip object를 반환

* 가변인자(여러 개를 받는다)

* index가 다를 경우, 작은 쪽에 맞춰진다

<br>

# lambda 함수

* 간단한 연산이나 함수를 한 줄로 표현할 때 사용

* 함수를 매개변수로 전달하는 경우에도 유용

* 표현식은 한 줄로 제한되기 때문에 복잡한 로직은 불가능

<br>

# Packing & Unpacking

<br>

## Packing

* 여러 개의 값을 하나의 변수에 묶어서 담는 것

* '*'를 활용한 패킹
```
numbers = [1, 2, 3, 4, 5]
a, *b, c = numbers
print(a) # 1
print(b) # [2, 3, 4]
print(c) # 5
```
```
# print 함수에서 임의의 가변인자가 작성가능한 이유
def my_func(*objects):
    print(objects) # (1, 2, 3, 4, 5)
    print(type(objects)) # tuple

my_func(1, 2, 3, 4, 5)

# (1, 2, 3, 4, 5)
```

<br>

## Unpacking

* 리스트나 튜플의 값을 개별 변수에 할당

```
packed_values = 1, 2, 3, 4, 5
a, b, c, d, e = packed_values
print(a, b, c, d, e) # 1 2 3 4 5
```
* 길이는 서로 동일해야 함

## '**'를 활용한 언패킹

* '**'는 딕셔너리의 키-값 쌍을 함수의 키워드 인자로 언패킹

## '*', '**' 패킹 / 언패킹 연산자 정리

* '*'
    * 패킹 연산자로 사용될 때 여러개의 인자를 하나의 튜플로 묶는 역할
    * 언패킹 연산자로 사용될 때, 시퀀스나 반복 가능한 객체를 각각의 요소로 언패킹하여 함수의 인자로 전달
* '**'
    * 언패킹 연산자로 사용될 때, 딕셔너리의 키-값 쌍을 키워드 인자로 언패킹하여 함수의 인자로 전달하는 역할