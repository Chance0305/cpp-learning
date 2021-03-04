# using 명령문

## using 선언문

```cpp
#include <iostream>

int main()
{
    using std::cout;
    cout << "Hello world!";
    return 0;
}
```

**using 선언문** `using std::cout;`을 사용하면 컴파일러에 std namespace에서 cout을 사용할 것이라고 알려준다.<br>
cout을 많이 사용하는 경우 using 선언을 사용하여 코드를 더 읽기 쉽게 만들어준다.

## using 지시문

```cpp
#include <iostream>

int main()
{
    using namespace std; // std 네임스페이스의 모든 것을 사용하고 싶다는 것을 컴파일러에 말해준다.
    cout << "Hello world!";
    return 0;
}
```

`using namespace std;`는 컴파일러에 "std 네임스페이스의 모든 것을 사용하고 싶다"고 말하므로<br>
컴파일러가 인식하지 못하는 이름을 찾으면 std 네임스페이스를 검사한다.

```cpp
#include <iostream>

int cout()
{
    return 5;
}

int main()
{
    using namespace std;
    cout << "Hello, World";
    return 0;
}
```

위의 예에서 컴파일러는 std:cout 함수와 정의한 cout함수 중 어떤 것을 의미했는지 결정할 수 없어, "모호한 기호" 오류로 컴파일하지 못한다.