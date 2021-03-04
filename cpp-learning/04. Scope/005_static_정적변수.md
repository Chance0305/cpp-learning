# static, 정적 변수

`static` 키워드가 전역 변수에서 사용될 때 "내부 연결 속성"을 적용한다는 것을 알았다. `static` 키워드를 사용한 지역 변수는 완전히 다른 의미가 있다.<br>

`static` 키워드를 사용한 지역 변수는 *자동 주기(auto duration)* 에서 *정적 주기(static duration)* 로 바뀐다.<br>
이것을 **정적 변수(static variable)** 라고도 부르는데, 생성된 스코프(범위)가 종료한 이후에도 해당 값을 유지하는 변수다.<br>
또한, 정적 변수는 한 번만 초기화되며 프로그램 수명 내내 지속된다.

```cpp
#include <iostream>

void incrementAndPrint()
{
    int value = 1;
    ++value;
    std::cout << value << '\n';
}

int main()
{   
    incrementAndPrint();
    incrementAndPrint();
    incrementAndPrint();

    return 0;
}

// 2
// 2
// 2
```

```cpp
#include <iostream>

void incrementAndPrint()
{
    static int value = 1; // 'static' 키워드를 사용한 '정적 생명 주기', 이 줄은 한번만 실행된다.
    ++value;
    std::cout << value << '\n';
} // s_value는 여기서 소멸되지 않지만, 접근할 수 없게된다

int main()
{   
    incrementAndPrint();
    incrementAndPrint();
    incrementAndPrint();

    return 0;
}

// 2
// 3
// 4
```

`g_`를 사용하여 전역 변수에 접두어를 지정하는 것처럼 `s_`를 사용하여 정적 변수에 접두사를 지정하는 것이 일반적이다.<br>

정적 변수는 지역 변수와 같은 스코프를 가지면서 전역 변수의 이점을 제공한다.(프로그램이 끝날 때까지 소멸하지 않는다.)<br>
이 특성은 전역 변수를 사용하는 것보다 훨씬 안전하다.