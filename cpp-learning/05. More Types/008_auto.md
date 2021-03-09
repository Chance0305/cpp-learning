# auto

`auto` 키워드는 선언된 변수의 초기화 식을 사용하여 해당 형식을 추론하도록 컴파일러에 지시한다.

```cpp
auto d = 5.0; // d will be type double
auto i = 1 + 2; // i will be type int
```

## auto 키워드는 함수 매개 변수와 함께 사용할 수 없다.

```cpp
#include <iostream>

void addAndPrint(auto x, auto y)
{
    std::cout << x + y; // error
}
```

위 코드는 작동하지 않는다. 컴파일러가 함수 매개 변수 x와 y에 대한 타입을 추론할 수 없기 때문이다.

## C++ 14에서 함수를 위한 타입 추론

C++14 는 `auto` 키워드가 함수의 반환 타입을 자동으로 추론할 수 있도록 확장되었다.
```cpp
auto add(int x, int y)
{
    return x + y;
}
```

위 문법은 사용하지 않는게 좋다. 반환값을 잘못 예상해, 의도하지 않은 오류가 발생할 수 있기 떄문이다.