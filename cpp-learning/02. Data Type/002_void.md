# void

`void` 는 "타입 없음" 을 의미한다.

변수는 void 타입으로 정의할 수 없다.
```cpp
void value; // error
```

void는 아래와 같은 상황에서 사용한다.

1. 함수가 값을 반환하지 않음을 나타낸다.
```cpp
void writeValue(int x) // 리턴 값이 없음을 나타냄.
{
    std::cout << "The value of x is : " << x << std::endl;
}
```

2. 함수가 매개 변수를 사용하지 않음을 나타낸다.
```cpp
int getValue(void) // 매개변수를 받지 않음을 나타낸다.
{
    int x;
    std::cin >> x;
    return x;
}
```

3. void pointer

***포인터 (pointer)*** 를 아직 배우지 않았기 때문에 생략한다.