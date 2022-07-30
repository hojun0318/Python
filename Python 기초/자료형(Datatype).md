# 자료형

## 자료형(Datatype)의 분류
- 프로그래밍에서는 다양한 종류의 값(데이터)을 쓸 수 있음
    - 사용할 수 있는 데이터의 종류들을 자료형(Datatype)이라고 함

**수치형(Numeric Type)**

    - int (정수, interger)
    - float(부동소수점, 실수, floating point number)
    - complex(복소수, complex number)

**문자열(String Type)**

**불린형(Boolean Type)**

**None**

# 수치형(Numeric Type)

## 정수 자료형(int)
- 0, 100, -200과 같은 정수를 표현하는 자료형
    - 일반적인 수학 연산(사칙 연산) 가능

## 진수 표현
- 여러 진수 표현 가능
    - 2진수(binary) : 0b
    - 8진수(octal) : 0o
    - 16진수(hexadeciaml) : 0x

```
print(0b10) # 2
print(0o30) # 24
print(0x10) # 16
```

## 실수 자료형(float)
- 유리수와 무리수를 포함하는 '실수'를 다루는 자료형
    - 0.1, 100.0, -0.001 등

## 실수 연산시 주의할 점(부동 소수점)
- 실수의 값을 처리할 때 의도하지 않은 값이 나올 수 있음
    ```
    print(3.2 - 3.1) # 0.1000000000000009
    print(1.2 - 1.1) # 0.0999999999999987
    ```
    - 연산의 결과가 0.1이 아니다!

**원인은 부동 소수점 때문**

- 컴퓨터는 2진수를 사용, 사람은 10진법을 사용
- 이때 10진수 **0.1**은 2진수로 표현하면 **0.0001100110011001100110...** 같이 무한대로 반복
- 무한대 숫자를 그대로 저장할 수 없어서 사람이 사용하는 10진법의 근사값만 표시
- 0.1의 경우 **3602879701896397 / 2 * 8 55** 이며 **0.1**에 가깝지만 정확히 동일하지는 않다.
- 이런 과정에서 예상치 못한 결과가 나타남(이런 증상을 Floating point rounding error라고 함)

## 실수 연산시 주의할 점(부동 소수점) - 해결책
- 값 비교하는 과정에서 정수가 아닌 실수면 주의할 것!
**매우 작은 수보다 작은지를 확인하거나 math 모듈 사용**
```
a = 3.2 - 3.1 # 0.1000000000000009
b = 1.2 - 1.1 # 0.0999999999999987

# 1. 임의의 작은 수 활용
print(abs(a - b) <= 1e-10) # True

# 2. python 3.5 이상
import math
print(math.isclose(a, b)) # True
```

# 문자열 자료형(String Type)

## 문자열 자료형의 정의
- 모든 문자는 str 타입
- 문자열은 작은 따옴표('')나 큰 따옴표("")를 활용하여 표기
    - 문자열을 묶을 때 동일한 문장 부호를 활용
    - PEP8에서는 소스코드 내에서 하나의 문장 부호를 선택하여 유지하도록 함
    ```
    print('hello') # hello
    print(type('hello)) # <class 'str'>
    print("hello") # hello
    ```

## 중첩 따옴표
- 따옴표 안에 따옴표를 표현할 경우
    - 작은 따옴표가 들어 있는 경우는 큰 따옴표로 문자열 생성
    ```
    print("문자열 안에 '작은 따옴표'를 사용하려면 큰 따옴표로 묶는다.")
    # 문자열 안에 '작은 따옴표'를 사용하려면 큰 따옴표로 묶는다.
    print('문자열 안에 "큰 따옴표"를 사용하려면 작은 따옴표로 묶는다.')
    # 문자열 안에 "큰 따옴표"를 사용하려면 작은 따옴표로 묶는다.
    ```

## 삼중 따옴표(Triple Quotes)
- 작은 따옴표나 큰 따옴표를 삼중으로 사용
    - 따옴표 안에 따옴표를 넣을 때
    - 여러 줄을 나눠 입력할 때 편리
    ```
    print('''문자열 안에 '작은 따옴표'나
    "큰 따옴표"를 사용할 수 있고
    여러 줄을 사용할 때도 편리하다.''')

    # 출력 결과
    문자열 안에 '작은 따옴표'나
    "큰 따옴표"를 사용할 수 있고
    여러 줄을 사용할 때도 편리하다.
    ```

## Escape sequence
- 역슬래시(Backslash) 뒤에 특정 문자가 와서 특수한 기능을 하는 문자 조합
```
\n : 줄 바꿈
\t : 탭(Tab)
\r : 캐리지 리턴
\o : 널(Null)
\\ : \
\' : 단일인용부호(')
\" : 이중인용부호(")
```

## 문자열 연산
- 덧셈
    - 숫자형 연산 7 + 6은 13
    - 그럼 문자열을 더하면? 파이썬에서 문자열 덧셈은 문자열을 연결
    - 영어로는 String Concatenation이라고 함
    ```
    print("Hello" + "World") # HelloWorld

- 곱셈
    - 2 * 3은 2 + 2 + 2랑 같고, 결과는 6
    - 문자열 "Python" * 3은?
    ```
    print("Python" * 3) # PythonPythonPython
    ```

## String Interpolation(문자열을 변수를 활용하여 만드는 법)
- %-formatting
```
name = 'Kim'
score = 4.5

print('Hello, %s' % name) # Hello, Kim
print('내 성적은 $d' % score) # 내 성적은 4
print('내 성적은 %f' % score) # 내 성적은 4.500000
```

- str.fromat()
```
name = 'Kim'
score= 4.5

print('Hello, {}! 성적은 {}'.format(name, score))
# Hello, Kim! 성적은 4.5
```

- f-string : python 3.6+
```
name = 'Kim'
score = 4.5

print(f'Hello, {name}! 성적은 {score}')
# Hello, Kim! 성적은 4.5

import datetime
today = datetime.datetime.now()
print(today) # 2022-07-30 18:24:45.200411

print(f'오늘은 (today:%y)년 {today:%m}월 {today:%d}일')
# 오늘은 22년 07월 30일

pi = 3.141592
print(f'원주율은 {pi:.3}. 반지름이 2일 때 원의 넓이는 {pi * 2 * 2}')
# 원주율은 3.14. 반지름이 2일때 원의 넓이는 12.566368
```

# None

- 파이썬 자료형 중 하나
- 값이 없음을 표현하기 위해 None 타입이 존재
- 일반적으로 반환 값이 없는 함수에서 사용하기도 함

# 불린형(Boolean Type)

## 불린형(Boolean)이란?
- 논리 자료형으로 참과 거짓을 표현하는 자료형
- True 또는 False를 값으로 가짐
- 비교 / 논리 연산에 활용됨

## 비교 연산자
- 수학에서 등호와 부등호와 동일한 개념
- 주로 조건문에 사용되며 값을 비교할 때 사용
- 결과는 True / False 값을 return함
```
< : 미만
<= : 이하
> : 초과
>= : 이상
== : 같음
!= : 같지않음
is : 객체 아이덴티티(OOP)
is not : 객체 아이덴티티가 아닌 경우
```

## 논리 연산자
- 여러 가지 조건이 있을 때
    - 모든 조건을 만족하거나(And), 여러 조건 중 하나만 만족해도 될 때(or) 특정 코드를 실행하고 싶을 때 사용
    - 일반적으로 비교 연산자와 함께 사용됨
        - A and B (A와 B 모두 True시 , True)
        - A or B (A와 B 모두 False시, False)
        - Not (True를 False로, False를 True로)
        ```
        num = 100
        print(num >= 100 and num % 3 == 1) # True
        ```

## 논리 연사자 주의할 점 / not 연산자
- Falsy : False는 아니지만 False로 취급되는 다양한 값
    - 0, 0.0, (), [], {}, None, ""(빈 문자열)
- 논리 연산자도 우선순위가 존재
    - not, and, or 순으로 우선순위가 높음
```
print(not True) # False
print(not 0) # True
print(not 'hi') # False
print(not True and False or not False) # True
# 위와 같음
print(((not True) and False) or (not Fasle)) # True
```

## 논리 연산자의 단축 평가
- 결과가 확실한 경우 두번째 값은 확인하지 않고 첫번째 값 반환
- and 연산에서 첫번째 값이 False인 경우 무조건 False => 첫번째 값 반환
- or 연산에서 첫번째 값이 True인 경우 무조건 True => 첫번째 값 반환
- 0은 False, 1은 True
```
print(3 and 5) # 5
print(3 and 0) # 0
print(0 and 3) # 0
print(0 and 0) # 0

print(5 or 3) # 5
print(3 or 0) # 3
print(0 or 3) # 3
print(0 or 0) # 0
```
```
a = 5 and 4
print(a) # 4

b = 5 or 3
print(b) # 5

c = 0 and 5
print(c) # 0

d = 5 or 0
print(d) # 5
```


