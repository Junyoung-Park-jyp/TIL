# OOP 2/2

# INDEX

* 상속

* 에러와 예외

* EAFP & LBYL

<br>

# 상속(Inheritance)

* 기존 클래스의 속성과 메서드를 물려받아 새로운 하위 클래스를 생성하는 것

## 상속이 필요한 이유

1. 코드 재사용
    * 상속을 통해 기존 클래스의 속성과 메서드를 재사용 가능
    * 새 클래스를 작성할 때 기존 클래스 기능 그대로 활용, 중복 코드 최소화

2. 계층 구조
    * 상속을 통해 클래스 간의 계층 구조 형성
    * 부모 클래스, 자식 클래스 간 관계 표현, 더 구체적인 클래스 제작 가능

3. 유지 보수 용이
    * 상속을 통해 기존 클래스 수정이 필요할 시, 해당 클래스만 수정하면 해결
    * 코드의 일관성 유지, 수정이 필요한 범위 최소화
  
<br>

# 클래스 상속

## 상속 없이 구현하는 경우

* 학생/교수 정보를 나타내기 어려움
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def talk(self):
        print(f'반갑습니다 {self.name}입니다.')

s1 = Person('김학생', 23)
s1.talk() # 반갑습니다 김학생입니다.

s2 = Person('박교수', 59)
s2.talk() # 반갑습니다 박교수입니다.
```

* 클래스 상속하기
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def talk(self):
        print(f'반갑습니다 {self.name}입니다.')

class Professor(Person): # Person 을 상속
    def __init__(self, name, age, department):
        self.name = name
        self.age = age
        self.department = department

    def talk(self):
        print('잘 부탁드립니다.')
        
class Student(Person): # Person 을 상속
    def __init__(self, name, age, gpa):
        self.name = name
        self.age = age
        self.gpa = gpa

p1 = Professor('박교수', 59, '컴퓨터공학과')
s1 = Student('김학생', 20, 3.5)

print(p1.department) # 컴퓨터공학과
print(s1.gpa) # 3.5

p1.talk() # 잘 부탁드립니다.
s1.talk() # 반갑습니다 김학생입니다.
```
> 같은 이름의 인스턴스 함수는 자신의 클래스에서 먼저 찾는다.
> 없을 시에는 상속된 클래스로 올라가 찾는다.

<br>

# super()

* 부모 클래스 객체를 반환하는 내장 함수
```python
class Person:
    def __init__(self, name, age, number, email):
        self.name = name
        self.age = age
        self.number = number
        self.email = email

class Student(Person): # 위치 인자는 생략할 수 없다
    def __init__(self, name, age, number, email, student_id):
        super().__init__(name, age, number, email) # name~email까지의 4개를 받는다
        self.studet_id = student_id
```

* super()를 쓰는 이유
    * `Person.___init__(name, age, number, email)`도 가능은 하다
    * 하지만 다중 상속, 혹은 상위 클래스 이름 변경시 super()가 용이
 
<br>

# 다중 상속

* 둘 이상의 상위 클래스로부터 여러 행동, 특징 상속 받기

* 상속받은 모든 클래스의 요소 활용 가능

* 중복된 속성, 메서드 존재 시 상속 순서에 의해 결정

```python

class Person:
    def __init__(self, name):
        self.name = name

    def greeting(self):
        return f'안녕, {self.name}'

class Mom(Person):
    gene = 'XX'

    def swim(self):
        return '엄마가 수영'
        
class Dad(Person):
    gene = 'XY'

    def walk(self):
        return '아빠가 걷기'
        
class FirstChild(Dad, Mom):
    def __init__(self, name):
        self.name = name

    def swim(self):
        return '첫째가 수영'

    def cry(self):
        return '첫째가 울음'

baby1 = FirstChild('아기')
print(baby1.cry()) # 첫째가 수영
print(baby1.swim()) # 첫째가 울음
print(baby1.walk()) # 아빠가 걷기
print(baby1.gene) # XY 먼저 상속된 Dad의 gene을 상속
```
> Dad에서 이미 gene이라는 변수를 찾았기 때문에, Mom에서 gene을 찾지 않는다

<br>

# 다이아몬드 문제(The diamond problem)

* 두 클래스 B와 C가 A에서 상속되고, D가 B와 C를 상속받을 때 생기는 모호함

* B, C가 각기 재정의한 메서드가 A에 있고, D가 이를 재정의하지 않음
    * D는 B의 메서드, C의 메서드 중 어느 버전을 상속?

## 파이썬의 해결책

* MRO(Method Resolution Order) 알고리즘을 사용하여 클래스 목록을생성

* 부모 클래스로부터 상속된 속성들의 검색을 깊이 우선으로, 왼쪽에서 오른쪽으로, 계층 구조에서 겹치는 같은 클래스를 두번 검색하지 않음

* 속성이 D에서 발견되지 않을시 B에서, B에도 없을시 C에서 탐색
```python
class D(B, C):
    pass
```

<br>

# MRO(Method Resolution Order)

* 메서드 결정 순서

## super()

* 다중 상속 시 MRO를 기반으로, 현재 클래스가 상속하는 모든 클래스 중 다음 메서드를 자동으로 결정해 호출

```python
class ParentA:
    def __init__(self):
        self.value_a = 'ParentA'

    def show_value(self):
        print(f'Value from ParentA: {self.value_a}')

class ParentB:
    def __init__(self):
        self.value_b = 'ParentB'

    def show_value(self):
        print(f'Value from ParentB: {self.value_b}')

class Child(ParentA, ParentB):
    def __init__(self):
        super().__init__() # MRO에 따라 ParentA클래스의 __init__이 호출
        self.value_c = 'Child'
    
    def show_value(self):
        super().show_value() # 마찬가지로 ParentA의 메서드 호출
        print(f'Value from Child: {self.value_c}')
```

```python

class A:
    def __init__(self):
        print('A')

class B(A):
    def __init__(self):
        super().__init__()
        print('B')

class C(A):
    def __init__(self):
        super().__init__()
        print('C')

class D(B, C):
    def __init__(self):
        super().__init__()
        print('D')
```
> 결과는 A C B D
> 콜스택에 순서대로 D, B, C, A가 쌓이고, A부터 다시 순차적으로 빠짐

## mro()메서드

* 해당 인스턴스의 클래스가 가지는 부모 클래스 확인 메서드

* 기존의 인스턴스 -> 클래스 순으로 탐색하며, 상속 관계에 있는 부모 클래스로 확장

## super의 2가지 사용 사례

1. 단일 상속 구조
    * 명시적으로 이름을 지정하지 않고 부모 클래스를 참조하기에, 코드 유지 보수 용이
    * 클래스 이름 변경, 부모 클래스 교체시에도 super()를 이용하면 코드 수정이 적음
  
2. 다중 상속 구조
    * MRO를 따른 메서드 호출
    * 복잡한 다중 상속 구조에서 발생하는 문제 방지

## MRO의 존재 이유

* 부모 클래스에 여러 번 액세스 하지 않도록, 순서를 보존하고, 부모 클래스를 1회만 호출해 우선순위에 영향 X

* 프로그래밍 언어의 신뢰성, 확장성 있는 클래스 설계에 도움

* 클래스 간의 메서드 호출 순서가 예측 가능하게 유지, 코드 재사용성, 유지보수성 향상

<br>

# 에러 & 예외

<br>

# 버그(bug)

* 소프트웨어에서 발생하는 오류, 결함
* 프로그램의 예상 동작과 실제 동작의 불일치

## 버그의 기원

* Mark II의 회로에 벌레가 들어가 합선을 일으켜 비정상적인 동작을 기록

* 이 사건을 계기로 널리 사용

<br>

# 디버깅(Debugging)

* 소프트웨어의 버그를 찾고 수정하는 과정

## 디버깅 방법

1. print 활용
    * 특정 함수 결과, 반복/조건 결과 등 나눠서 생각, 코드를 bisection으로 나눠서 생각
  
2. 개발 환경(text editor, IDE)등에서 제공하는 기능 활용
    * breakpoint, 변수 조회 등
  
3. Python tutor 활용(단순 파이썬 코드)

4. 뇌 컴파일, 눈 디버깅 등

<br>

# 에러(Error)

* 프로그램 실행 중에 발생하는 예외 상황

## 파이썬의 에러 유형

* 문법 에러(Syntax Error): 프로그램 구문이 올바르지 않음(괄호, 콜론)

* 예외(Exception): 프로그램 실행 중에 감지되는 에러

<br>

# 내장 예외(Built-in Exception)

* 예외 상황을 나타내는 예외 클래스들
    * 파이썬에서 이미 정의되어 있고 특정 예외 상황 처리에 사용

* ZeroDivisionError: 나누기의 두 번째 인자가 0일 시
* NameError: 지역, 전역 변수명 못 찾을 때 발생
* TypeError: 타입 불일치, 인자 누락, 인자 초과, 인자 타입 불일치
* ValueError: 연산, 함수에 부적절한 값의 인자를 받고, IndexError처럼 구체적인 예외로 설명되지 않는 경우
* IndexError: 시퀀스 인덱스가 범위를 벗어날 때 발생
* KeyError: 딕셔너리에 해당 키가 존재하지 않는 경우
* ModuleNotFoundError: 모듈을 찾을 수 없을 때
* ImportError: import할 대상을 찾을 수 없을 때
* KeyboardInterrupt: 사용자가 종료 시킬때(Delete, Ctrl+c)
* IndentationError: 잘못된 들여쓰기에 관련된 문법 오류

<br>

# Try & Except

* 파이썬에서의 예외 처리 구문

## 구조

* try 블록 안에는 예외가 발생하는 코드를 작성

* except 블록 안에는 예외시 처리할 코드 작성

* 예외 발생시, 즉시 except구문으로 이동

```python
try:
    result = 10/0
except ZeroDivisionError:
    print('0으로 나눌 수 없습니다.')
# 0으로 나눌 수 없습니다.

try:
    num = int(input('숫자입력: '))
except ValueError:
    print('숫자가 아닙니다.')
# 숫자입력: a 
# 숫자가 아닙니다.
```

## 복수 예외 처리

1. 발생가능한 에러 모두 명시

2. 에러 별로 별도로 작성

## 예외 처리 주의 사항

* BaseException등의 상위 예외 항목을 먼저 실행할 시, 아래의 예외 처리 코드가 실행 X

* 내장 예외 클래스는 상속 계층 구조기 때문에, 하위 클래스를 우선 작성해야 실행

<br>

# 참고

## as 키워드

* as 키워드를 활용해 에러 메시지를 except 블록에 사용 가능

```python
my_list = []

try:
    number = my_list[1]
except Exception as e:
    print(f'{e}발생')
```

<br>

# EAFP & LBYL

* 예외처리와 검사방식에 대한 두 가지 접근방식

## EAFP

* "Easier to Ask for Forgiveness than Permission"
* "허락보다 용서가 쉽다"
    * 예외처리를 중심으로 코드를 작성하는 방식(try-except)
## LBYL

* "Look Before You Leap"
* "돌다리도 두들겨보고 건너라"
    * 값 검사를 중심으로 코드를 작성하는 방식(if-else)
 
## 두 가지 비교

| EAFP | LBYL |
|:---:  |:---:  |
| "일단 실행 후 예외 처리" | "조건을 검사하고 실행" |
| 코드 실행 후 예외가 발생시 처리 | 코드 실행 전 예외 상황을 검사하고 예외 회피 |
| 미리 대비하는 것이 아닌, 발생 후 처리 | 예측 가능한 동작이지만, 길고 복잡한 코드 |
| 예외 상황을 예측하기 힘들 때 유용 | 예외 상황을 방지할 때 유용 |