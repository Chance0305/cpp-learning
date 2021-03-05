# 열거형, enum

C++은 프로그래머들이 자신만의 자료형을 만들 수 있게 해주는 기능을 포함하고 있다. 이러한 자료형을 **사용자 정의 자료형** 이라고 한다.<br>
가장 간단한 사용자 정의 자료형은 열거형 `enum` 일 것이다.

```cpp
// Color 라는 새로운 열거형(enum)을 정의한다.
enum Color
{
    COLOR_BLACK,
    COLOR_RED,
    COLOR_BLUE,
    COLOR_GREEN,
    COLOR_WHITE,
    COLOR_CYAN,
    COLOR_YELLOW,
    COLOR_MAGENTA,
}

// 열거형 COlor의 변수들 정의
Color paint = COLOR_WHITE;
Color house(COLOR_BLUE);
Color apple { COLOR_RED };
```

열거형을 정의해도 메모리는 할당되지 않는다. <br>
열거된 유형의 변수가 정의된 경우, 해당 변수에 대해 메모리가 할당된다.

## Naming enums

`enum` 식별자는 대문자로 시작하느 경우가 많으며, 열거자(`enumerator`)는 종종 모두 대문자로 이름이 지어진다.<br>
열거자는 열거와 같은 네임스페이스에 배치되므로, 열거자 이름은 같은 네임스페이스 내의 여러 열거(enum)에서 사용할 수 없다.

```cpp
enum Color
{
    RED,
    BLUE, // BLUE is put into the global namespace
    GREEN
}

enum Feeling
{
    HAPPY,
    TIRED,
    BLUE // error, BLUE was already used in enum Color in the global namespace
}

따라서 이름 충돌을 방지하기 위해 열거자 앞에 ANIMAL_ 또는 COLOR_ 와 같은 접두어를 붙이는 것이 일반적이다.
```

## Enumerator Values

각 열거자는 열거 목록의 위치에 따라 정수 값이 자동으로 할당된다.
```cpp
enum Color
{
    COLOR_BLACK, // assigned 0
    COLOR_RED,   // assigned 1
    COLOR_BLUE,  // assigned 2
    COLOR_GREEN, // assigned 3
    COLOR_WHITE, // assigned 4
    COLOR_CYAN,  // assigned 5
    COLOR_YELLOW,// assigned 6
    COLOR_MAGENTA// assigned 7
};
 
Color paint(COLOR_WHITE);
std::cout << paint;      // 4
```

열거자의 값을 명시적으로 정의할 수도 있다.<br>
정의되지 않은 모든 열거자는 이전 열거자보다 1 더 큰 값이 부여된다.
```cpp
enum Animal
{
    ANIMAL_CAT     = -3,
    ANIMAL_DOG,    // assigned -2
    ANIMAL_PIG,    // assigned -1
    ANIMAL_HORSE   = 5,
    ANIMAL_GIRAFFE = 5, // shares same value as ANIMAL_HORSE
    ANIMAL_CHICKEN // assigned 6
};
```

## Enum type evaluation and input/output

열거형 값은 정수로 평가되므로 정수 변수에 할당할 수 있다. `std::cout`은 정수 출력 방법을 알고 있으므로 정수로 출력할 수도 있다.
```cpp
int mypet = ANIMAL_PIG;
std::cout << ANIMAL_HORSE // evaluates to integer before being passed to std::cout
// 5
```

컴파일러는 정수를 열거형 값으로 변환하지는 않는다. 다음과 같은 경우 컴파일러 오류가 발생한다.
```cpp
Animal animal = 5; // compiler error
```

`state_cast`를 통해 강제로 변환할 수 있다.
```cpp
Color color = static_cast<Color>(5);
```

또한 컴파일러는 `std::cin`을 사용하여 열거형을 입력할 수 없다.<br>

열거형은 고유한 자료형으로 간주한다. 따라서 열거형에 다른 열거형을 할당하려고 하면 컴파일 오류가 발생한다.<br>

상수(const) 변수와 마찬가지로 열거형은 디버거에 표시되므로 `#define`보다 유용하다.

## 열거형은 언제 유용할까 ?

열거형은 특정한 상태 집합을 나타내야 할 때 코드 문서화 및 가독성 목적으로 매우 유용하다.

오류 코드를 나타내기 위해 열거형을 사용하는 예시:
```cpp
enum ParseResult
{
    SUCCESS = 0,
    ERROR_OPENING_FILE = -1,
    ERROR_READING_FILE = -2,
    ERROR_PARSING_FILE = -3
};
 
ParseResult readFileContents()
{
    if (!openFile())
        return ERROR_OPENING_FILE;
    if (!readFile())
        return ERROR_READING_FILE;
    if (!parsefile())
        return ERROR_PARSING_FILE;
 
    return SUCCESS;
}
```