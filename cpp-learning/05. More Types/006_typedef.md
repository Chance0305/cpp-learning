# typedef

`typedef`를 사용하면 타입의 별칭을 생성하고, 실제 타입 대신 별칭을 사용할 수 있다.<br>
`typedef`를 선언하려면 `typedef` 키워드를 사용하고 자료형 다음에 별칭 이름을 사용하면 된다.

```cpp
typedef double custom_t; // custom_t 를 double 자료형의 별칭으로 정의

// 다음 두 문장은 같다.
double a;
custom_t a;
```

관습적으로 `typedef` 별칭은 `_t` 접미사를 사용하여 선언한다.

`typedef`는 다양한 상황에서 쓰인다.

1. 가독성

반환 값의 목적을 알고 싶은 경우:
```cpp
typedef int testScore_t;

testScore_t GradeTest();
```

2. 플랫폼 독립 코딩

플랫폼에 따라서, 정수는 2바이트 또는 4바이트다. 따라서 `int`를 사용해 2바이트가 넘는 정보를 저장하는 것은 잠재적으로 위험할 수 있다.<br>
`typedef`를 사용하면 실수를 방지하고 변수의 크기에 대해 더욱 명확히 알 수 있다.<br>

일반적으로 `typedef`를 전처리기와 같이 사용해서 올바른 크기로 해석하게 한다.

```cpp
#ifdef INT_2_BYTES
typedef char int8_t;
typedef int int16_t;
typedef long int32_t;
#else
typedef char int8_t;
typedef short int16_t;
typedef int int32_t;
#endif
```

3. 복잡한 타입을 간단하게 만들기

C++에서는 다음과 같이 선언된 변수와 함수를 볼 수 있다.
```cpp
std::vector<std::pair<std::string, int>> pairlist;

bool hasDuplicates(std::vector<std::pair<std::string, int>> pairlist)
{
    // code
}
```

매번 `std::vector<std::pair<std::string, int>>`를 입력하는 건 성가시고 어렵다. 이럴 떄 `typedef`를 사용한다.

```cpp
typedef std::vector<std::pair<std::string, int>> pairlist_t; // make pairlist_t an alias for this crazy type

pairlist_t pairlist; // instantiate a pairlist_t

bool hasDuplicates(pairlist_t pairlist)
{
    // code
}
```

# using C++ 11

C++ 11에서는 새로운 `typedef` 문법을 도입했다. 이 문법을 타입 별칭(type alias)라고 한다.

typedef를 사용하면:
```cpp
typedef double distance_t;
```

C++11 에서는:
```cpp
using distance_t = double; // This type alias syntax is cleaner for more advanced typedefing cases, and should be preferred.
```

위 둘은 기능적으로 같다.
C++11은 using 키워드를 사용하는데, 이는 네임스페이스와 아무런 관련이 없다.