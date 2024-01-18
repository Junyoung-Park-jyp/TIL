# 개요

* 과학자, 수학자가 모든 이론을 새로 만들거나 증명하지 않듯, 개발자 또한 프로그램 전체를 혼자 작성하진 않음

* 다른 프로그래머가 작성한 수천, 수백만줄의 코드를 사용하는 것이 생산성에서 매우 중요

<br>

# 모듈(Module)

* 한 파일에 모은 함수와 변수의 모음

* 특정한 기능을 하는 코드가 작성된 파이썬 파일(.py)

<br>

## 모듈 예시

* 파이썬의 math 모듈

* 파이썬이 미리 작성해 둔 수학 관련 변수 & 함수가 작성된 모듈

<br>

## 모듈 활용

1. 모듈 import

* 모듈 가져오기
```
import math
# import 이후에 사용 가능

help(math)
# 내장 함수 help를 이용해 모듈에 무엇이 들었는지 확인 가능
```
* 모듈을 import하는 다른 방법
```
# from을 이용하여 특정 모듈의 특정 기능만 가져오기 가능
from math import pi, sqrt

print(pi)
print(sqrt(4))
```
* 명시적인 것은, 모듈 전체를 import하는 방식


2. 모듈 사용하기

* '.(dot)'는 점의 왼쪽 객체에서 점의 오른쪽 이름을 찾으라는 연산자
```
# 모듈명.변수명
print(math.pi)

# 모듈명.함수명
print(math.sqrt(4))
```

3. 모듈 주의 사항

* 만약 다른 모듈이 같은 이름의 함수를 제공할 경우, 마지막 import로 대체 된다
```
from math import pi, sqrt
from my_math import sqrt

# 밑의 sqrt가 사용

# 그렇기에 모듈 내 모든 요소를 가져오는 *은 권장하지 않음
from math import *
```

<br>

# 사용자 정의 모듈

<br>

* 직접 정의한 모듈 사용하기

    1. 모듈 my_math.py 작성
    2. 두 수의 합을 구하는 add 함수 작성
    3. my_math 모듈 import 후 add 함수 호출
 
<br>

# 파이썬 표준 라이브러리

* 비슷한 범주의 모듈을 모은 패키지

* 그러한 패키지와 모듈을 아우르는 라이브러리

* PSL(Python Standard Library) 파이썬 언어와 함께 제공되는 다양한 모듈과 패키지

<br>

# 패키지(Package)

* 관련된 모듈들을 하나의 디렉토리에 모아 놓은 것
    * PSL 내부 패키지: 설치 없이 바로 import 후 사용
    * 외부 패키지: pip를 사용하여 설치 후 import

<br>

## pip

* 외부 패키지 설치를 돕는 파이썬의 패키지 관리 시스템

* PyPI(Python Package Index)에 저장된 외부 패키지들을 설치

<br>

## 패키지 설치

* 최신버전, 특정버전, 최소 버전을 명시하여 설치 가능
```
$ pip install package
$ pip install package==1.0.0
$ pip install package>=1.0.0

import requests

url = 'https://random-data-api.com/api/v2/users'
response = requests.get(url).json()

print(response)
```

## 패키지 사용 목적

* 모듈들의 이름 공간을 구분하여 충돌 방지, 모듈들을 효율적으로 관리, 재사용

<br>

# 제어문(Control Statement)

* 코드의 실행 흐름을 제어하는 데 사용되는 구문

* **조건**에 따라 코드 블록 실행, 혹은 **반복적** 코드 실행

<br>

# 1. 조건문(Conditional Statement)

* 주어진 조건식을 평가하여 해당 조건이 참인 경우 코드 블록을 실행/건너뜀

## if/elif/else

```
if 표현식:
    코드 블록
elif 표현식:
    코드 블록
else:
    코드 블록
```

* 복수 조건문일 경우, 위에서 순차적으로 비교

# 2. 반복문


## for

* 임의의 시퀀스를 정해진 수 만큼 반복

<br>

### for문 원리

* 리스트 내 첫 항목이 반복 변수에 할당되고 코드 실행

* 이후 두 번째, 세 번째 항목에 반복, 마지막 항목이 할당된 후 종료

```
# 딕셔너리 반복문
my_dict = {'x': 10, 'y': 20, 'z': 30}

for key in my_dict:
    print(key)
    print(my_dict[key])

# x 10 y 20 z 30
```

* 중첩 리스트 반복
    * 안쪽 리스트 요소에 접근하려면 바깥 리스트를 순회하면서 중첩 반복으로 안쪽을 반복

## while

* 주어진 조건식이 참인 동안 계속해서 반복

```
while 조건식:
    코드 블록
```

### 사용자 입력에 따른 반복

* while문을 사용한 특정 입력 값에 대한 종료 조건 활용하기

* while문은 반드시 종료 조건이 필요하다

<br>

## 적절한 반복문 활용하기

* for
    * 반복 횟수가 명확한 경우
    * 리스트, 튜플, 문자열 등의 시퀀스 형식 데이터 처리

* while
    * 반복 횟수가 불분명, 조건에 따라 반복을 종료해야 할 때
    * 사용자의 입력이 특정 조건에 부합할때까지 반복

<br>

# 반복 제어

* for문과 while은 매 반복마다 본문의 코드를 실행하지만, 특정 구간에서 멈추는 방법도 있음
    * break: 반복 즉시 중지
    * continue: 다음 반복으로 건너뜀

## break, continue 주의사항

* 남용할 시 코드 가독성 저하

* 종료조건을 만들어 break 대체, if 문 사용해 continue 대체 가능

<br>

# List Comprehenstion(간결하고 효율적인 리스트 생성법)

```
[expression for 변수 in iterable]

list(expression for 변수 in iterable)

# 예시

numbers = [1, 2, 3, 4, 5]
squared_numbers = [num**2 for num in numbers]

print(squared_numbers) # [1, 4, 9, 16, 25]
```

* if 조건문과 병행
```
[expression for 변수 in iterable if 조건식]

result = [i for i in range(10) if i % 2 ==1]

result = []
for i in range(10):
    if i % 2 == 1:
        result.append(i)
```
* break, continue와 마찬가지로 남용하면 직관성, 유지보수성이 떨어질 수 있다

* 연습 시, comprehension 이전 코드를 먼저 작성 후 연습

> "Simple is better than complex"
> "Keep it simple, stupid"

## pass

* 아무런 동작도 수행하지 않고 넘김
    * 문법적으로 문장이 필요하지만, 실행에는 영향을 주지 않아야 할 때

```
# 구현은 할 계획이지만, 아직 완성하지 않았을 때
def my_function():
    pass

# 조건문에서 진행은 유지할 때
while True:
    if 조건1:
        break
    elif 조건2:
        pass # 루프는 진행
    else 조건3:
        print(something)
```

## enumerate

* 반복문과 병행하여 index를 같이 사용 가능