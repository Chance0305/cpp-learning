# Boolean 값

## Boolean variables

부울 변수 `참(true: 1)` 과 `거짓(false: 0)` 값만 가질 수 있는 변수다. 부울 변수를 선언하려면 키워드 `bool`을 사용한다.

```cpp
bool b;
```

부울 값은 실제로 부울 변수에 "true" 또는 "false"라는 단어로 저장되지 않고 1 과 0 정수로 저장된다.<br>
만약 `std::cout` 을 이용해 0 또는 1 대신 "true" 또는 "false"를 출력하려면 `std::boolalpha` 를 사용하면 된다.

```cpp
#include <iostream>

int main()
{
    std::cout << true << std::endl;

    std::cout << std::boolalpha;

    std::cout << true << std::endl;

    return 0;
}

// 1
// true
```

`std:noboolalpha` 를 이용해 다시 끌 수 있다.

<br>

## 부울 반환 값 (Boolean return values)

부울 값은 어떤 것이 참(true)인지 아닌지 확인하는 함수의 반환 값으로도 사용된다. 이러한 기능을 가진 함수의 이름은 일반적으로 is나 has로 시작한다.

```cpp
#include <iostream>

bool isEqual(int x, int y)
{
    return (x == y);
}

int main()
{
    std:: cout << "Enter an Integer : ";
    int x;
    std::cin >> x;

    std:: cout << "Enter an Integer : ";
    int y;
    std::cin >> y;

    if (isEqual(x, y))
        std::cout << x << " and " << y << " are equal" << std::endl;
    else
        std::cout << x << " and " << y << " are not equal" << std::endl;

    return 0;
}
```