# sizeof , 조건부 연산자 (Conditional operators)

## sizeof operator
| Operator | Symbol | Form                          | Operation                                 |
| -------- | ------ | ----------------------------- | ----------------------------------------- |
| Sizeof   | sizeof | sizeof(type) sizeof(variable) | Returns size of type or variable in bytes |

`sizeof` 연산자는 변수형의 크기 또는 변수의 크기를 반환한다.

## 조건부 연산자 (conditional operator)
| Operator    | Symbol | Form      | Operation                                                    |
| ----------- | ------ | --------- | ------------------------------------------------------------ |
| Conditional | ? :    | c ? x : y | If c is nonzero (true) then evaluate x, otherwise evaluate y |

조건부 연산자 `? :`는 C++의 유일한 삼항 연산자(피연산자 3개)이기 때문에 *삼항 연산자* 라고도 한다.

```cpp
if (condition)
    expression;
else
    other_expression;
```

다음과 같이 작성할 수 있다.
```cpp
(condition) ? expression : other_expression;
```

`? :` 연산자는 우선순위가 매우 낮다.
```cpp
std::cout << ((x > y) ? x : y);
```
`<<`연산자가 `? :`연산자보다 우선순위가 더 높으므로 만약 `()`가 없다면 다음과 같이 평가된다.
```cpp
(std::cout << (x > y)) ? x : y;
```