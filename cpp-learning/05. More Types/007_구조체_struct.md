# 구조체, struct

**구조체(struct)** 는 하나 이상의 변수를 그룹 지어서 새로운 자료형을 정의하는 것이다.

## 구조체 선언 및 정의

**구조체(struct)** 는 사용자 정의 자료형이기 때문에, 그것을 사용하기 전에 구조체가 어떻게 생겼는지 컴파일러에 말해야한다.<br>
이를 위해 struct 키워드를 사용해 구조체를 선언해야 한다.

```cpp
struct Employee
{
    short id;
    int age;
    double wage;
};
```

Employee 구조체는 세 개의 변수를 포함한다. (id, age, wage) 구조체의 일부인 이러한 변수를 **멤버(member)** 또는 **필드(field)** 라고 한다.

 - `Employee`는 단지 선언에 불과하다. 어떤 메모리도 할당되지 않은 상태다. (구조체 변수를 정의하면 메모리 할당)
 - 일반적으로 구조체 이름은 대문자로 시작하여 변수 이름과 구분한다.
 - 구조체 선언의 끝에 세미콜론을 붙여야한다.

## 구조체 멤버 접근 (Accessing struct members)

구조체의 개별 멤버에 접근하기 위해 **멤버 선택 연산자 (member selection operator: `.`)** 를 사용하면 된다.

```cpp
Employee park;

park.id = 210125;
park.age = 19;
park.wage = 999999;
```

## 구조체 초기화 (Initializing structs)

```cpp
struct Employee
{
    short id;
    int age;
    double wage;
};

Employee park = { 210125, 19, 99999 };
Employee lee { 210101, 19, 12345 }; // uniform initialization
```