# OOP 속성
## 속성
- 특정 데이터 타입/클래스의 객체들이 가지게 될 상태/데이터를 의미
- 클래스 변수 / 인스턴스 변수가 존재
```
class Person():
    blood_color = 'red'  # 클래스 변수
    population = 100    # 클래스 변수

    def __init__(self, name):
        self.name = name    # 인스턴스 변수

person1 = Person('지민')
print(person1.name)  # 지민
```

## 인스턴스 변수
- 인스턴스 변수란?
    - 인스턴스가 개인적으로 가지고 있는 속성(Attribute)
    - 각 인스턴스들의 고유한 변수
- 생성자 메서드(__init__)에서 self.<name>으로 정의
- 인스턴스가 생성된 이후 <instance>.<name>으로 접근 및 할당
```
class Person:

    def __init__(self, name):
        self.name = name        # 인스턴스 변수 정의

john = Person('john')
print(john.name)    # john      # 인스턴스 변수 접근 및 할당
john.name = 'John Kim'          # # 인스턴스 변수 접근 및 할당
print(john.name)    # John Kim
```

## 클래스 변수
- 클래스 변수
    - 한 클래스의 모든 인스턴스가 공유하는 값을 의미
    - 같은 클래스의 인스턴스들은 같은 값을 갖게 됨
    - 예) 특정 사이트의 User 수 등은 클래스 변수를 사용해야 함

- 클래스 선언 내부에서 정의
- <classname>.<name>으로 접근 미 할당
```
class Circle():
    pi = 3.14   # 클래스 변수 정의

    def __init__(self, r)
    self.r = r  # 인스턴스 변수

c1 = Circle(5)
c2 = Circle(10)

print(Circle.pi)    # 3.14
print(c1.pi)        # 3.14
print(c2.pi)        # 3.14

Circle.pi = 5
print(Circle.pi)    # 5
print(c1.pi)        # 5
print(c2.pi)        # 5
```

## 클래스 변수 활용(사용자 수 계산하기)
- 사용자가 몇 명인지 확인하고 싶다면?
    - 인스턴스가 생성될 때마다 클래스 변수가 늘어나도록 설정하면 됨
```
class Person():
    count = 0
    # 인스턴스 변수 설정
    def __init__(self, name):
        self.name = name
        Person.count += 1

person1 = Person('아이유')
person2 = Person('이찬혁')

print(Person.count)
```

## 클래스 변수와 인스턴스 변수
- 클래스 변수를 변경할 때는 항상 **클래스.클래스 변수** 형식으로 변경
```
class Circle():
    pi = 3.14   # 클래스 변수 정의

    def __init__(self, r)
    self.r = r  # 인스턴스 변수

c1 = Circle(5)
c2 = Circle(10)
```
```
print(Circle.pi)    # 3.14
print(c1.pi)        # 3.14
print(c2.pi)        # 3.14
```
```
Circle.pi = 5       # 클래스 변수 변경
print(Circle.pi)    # 5
print(c1.pi)        # 5
print(c2.pi)        # 5
```
```
c2.pi = 5           # 인스턴스 변수 변경
print(Circle.pi)    # 3.14(클래스 변수)
print(c1.pi)        # 3.14(클래스 변수)
print(c2.pi)        # 5 (새로운 인스턴스 변수가 생성됨)
```