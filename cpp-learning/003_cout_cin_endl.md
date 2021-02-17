# cout / cin / endl

<br>

## std::cout

std::cout 객체(iostream library)를 사용하여 콘솔에 텍스트를 출력할 수 있다.

```cpp
#include <iostream>

int main()
{
    std::cout << "Hello world!";
    // Hello world!

    int x = 4;
    std::cout << "x is equal to : " << x;
    // x is equal to : 4

    std::cout << "Hi!";
    std::cout << "My name is Parkchanhyeong";
    // Hi!My name is Parkchanhyeong

    return 0;
}
```

<br>

## std::endl

여러 줄을 출력하려면 std::endl을 사용하면 된다.

```cpp
#include <iostream>

int main()
{
    std::cout << "Hi!"; << std::endl;
    std::cout << "My name is Parkchanhyeong";

    // Hi!
    // My name is Parkchanhyeong

    return 0;
}
```

## std::cin

std::cin은 std::cout의 반대이다.<br>
std::cin은 입력 연산자(>>)를 사용하여 콘솔로부터 사용자의 입력을 읽는다.

```cpp
#include <iostream>

int main() {
    std::cout << "Enter a number : ";
    int x;
    std::cin >> x;
    std::cout << "You entered : " << x << std::endl;

    // Enter a number : 20 (user input)
    // You entered : 20
    
    return 0;
}
```