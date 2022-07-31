# OOP 메서드
## 메서드
- 특정 데이터 타입/클래스의 객체에 공통적으로 적용 가능한 행위(함수)
```
class Person():

    def talk(self):
        print('안녕')

    def eat(self, food):
        print(f'{food}를 냠냠')

person1 = Person()
person1.talk()      # 안녕
person1.eat('피자')  # 피자를 냠냠
person1.eat('치킨')  # 치킨를 냠냠
```

# 인스턴스 메서드
## 메서드 종류
- 인스턴스 메서드(Instance Methods)
- 클래스 메서드(Class Methods)
- 정적 메서드(Static Methods)

## 인스턴스 메서드
- 인스턴스 변수를 사용하거나, 인스턴스 변수에 값을 설정하는 메서드
- 클래스 내부에 정의되는 메서드의 기본
- 호출 시, 첫번째 인자로 자기자신(self)이 전달됨
```
class MyClass:

    def instance_method(self, arg1, ...):

my_instance = MyClass()
my_instance.instance_method(...)
```

## Self
- 인스턴스 자기자신
- Python에서 인스턴스 메서드는 호출 시 첫번째 인자로 인스턴스 자신이 전달되게 설계
    - 매개변수 이름으로 self를 첫 번째 인자로 정의
    - 다른 단어로 써도 작동하지만, Python의 암묵적인 규칙

## 생성자(Constructor) 메서드
- 인스턴스 객체가 생성될 때 자동으로 호출되는 메서드
- 인스턴스 변수들의 초기값을 설정
    - 인스턴스 생성
    - __init__메서드 자동 호출
```
class Person():

    def __init__(self):
        print('인스턴스가 생성되었습니다.')

person1 = Person()  # 인스턴스가 생성되었습니다.
```
```
class Person()

    def __init__(self, name):
        print(f'인스턴스가 생성되었습니다. {name}')

person1 = Person('지민')    # 인스턴스가 생성되었습니다. 지민
```

## 매직 매서드
- Double underscore(__)가 있는 메서드는 특수한 동작을 위해 만들어진 메서드로, 스페셜 메서드 혹은 매직 메서드라고 불림
- 특정 상황에 자동으로 불리는 메서드
- 예시

![캡처](https://user-images.githubusercontent.com/104968672/182021960-2e7bbb94-d361-41e1-bc61-ad473f805bc6.PNG)

## 매직 매서드 예시
- 객체의 특수 조작 행위를 지정(함수, 연산자 등)
    - __str__ : 해당 객체의 출력 형태를 지정
        - 프린트 함수를 호출할 때, 자동으로 호출
        - 어떤 인스턴스를 출력하면 __str__의 return 값이 출력
    - __gt__ : 부등호 연산자(> , greater than)

## 소멸자(Destructor) 메서드
- 인스턴스 객체가 소멸(파괴)되기 직전에 호출되는 메서드
```
class Person():

    def __del__(self):
        print('인스턴스가 사라졌습니다.')

person1 = Person()
def person1     # 인스턴스가 사라졌습니다.
```

매직 매서드 예시
```
class Circle:

    def __init__(self, r):
        self.r = r

    def __area(self):
        return 3.14 * self.r * self.r

    def __str__(self):
        return f'[원] radius: {self.r}'

    def __gt__(self, other):
        return self.r > other.r

c1 = Circle(10)
c2 = Circle(1)

print(c1)   # [원] radius 10
print(c2)   # [원] radius 1
print(c1 > c2)  # True
print(c1 < c2>) # False
```