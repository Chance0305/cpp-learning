# enum class

C++ 11은 새로운 컨셉, **열거형 클래스(enum class)** 를 정의했다. **열거형 클래스(enum class)** 는 강한 형식과 범위(scope)를 가진다.<br>
**열거형 클래스(enum class)** 를 만들려면, `enum` 키워드 뒤에 `class` 키워드를 사용하면 된다.

```cpp
#include <iostream>

int main()
{
    enum class Color
    {
        RED,
        BLUE
    };

    enum class Fruit
    {
        BANANA,
        APPLE
    };

    Color color = Color::RED; // RED is not directly accessible any more, have to use Color::RED
    Fruit fruit = Fruit::BANANA;

    if (color == fruit) // compile error, as the compiler doesn't know how to compare different types Color and Fruit
        std::cout << "color and fruit are equal\n";
    else
        std::cout << "color and fruit are not equal\n";

    return 0;
}
```

열거형 클래스(enum class)의 강력한 형식 규칙은 고유한 자료형으로 간주함을 의미한다.<br>
그래서 컴파일러가 다른 열거형의 열거자와 암시적으로 비교하지 않는다. 그러나 같은 열거형 클래스 내의 열거자 끼리는 비교할 수 있다.

```cpp
enum class Color
{
    RED,
    BLUE
};

Color color == Color::RED;

if (color == Color::RED)
    std::cout << "The color is Red!\n";
```

`class` 키워드는 `static` 키워드와 함께 C++에서 가장 의미가 많은 키워드 중 하나다.<br>
열거형 클래스는 `class` 키워드를 사용하지만, 전통적인 C++의 class로 간주하지는 않는다.