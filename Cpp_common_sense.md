#Cpp common sense
Cpp에 용어와 상식(!?)을 아주 간략하게 정리하는 노트.<br>

<< 연산자는 두 번째 인자를 첫 번째 인자에 “넣는(put to)” 역할<br><br>

기본 타입(fundamental types)<br>
bool // 불리언 타입, 가능한 값: true, false<br>
char // 문자 타입, 예: 'a', 'z', '9'<br>
int  // 정수 타입, 예: 1, 42, 1066<br>
double // 배정밀도 부동소수점 타입, 예: 3.14, 299793.0<br><b>

정보 손실(narrowing conversion):타입 변환 시 발생할 수 있는 정밀도나 범위 손실을 강조할 때 적합<br><br>

auto는 명시적으로 타입을 지정할 특별한 이유가 없을 때 사용<br><br>

C++은 두 가지 형태의 불변성(immutability)을 지원<br>
const<br>constexpr<br><br>

입력에는 &lt;&lt; 연산자(“get from”)를 사용<br>

[ ]는 “~의 배열(array of)”을 의미<br>
 *는 “~를 가리키는 포인터(pointer to)”를 의미<br><br>
선언자 연산자(declarator operators) : 연산자들(&, *, [ ]) <br><br>

모든 배열은 0부터 시작하는 인덱스(lower bound)를 가진다. <br><br>
<strong>배열의 크기</strong>는 반드시 상수 표현식(constant expression)이어야 한다.<br>
<strong>=switch 문에서의 case 라벨</strong><br>
<strong>=일부 템플릿 인자</strong><br>
<strong>=constexpr로 선언된 상수</strong><br><br>
```cpp
for (auto x : v) // v의 각 요소에 대해
```
범위 기반 for 문은 모든 시퀀스 타입(sequence type)에 사용할 수 있다.<br>

접미 연산자 &는 “참조(reference) 대상”을 의미<br>
nullptr는 모든 포인터 타입에 공통으로 사용되는 null 포인터<br>

포인터 인자가 실제로 무언가를 가리키고 있는지 확인하는 것은 종종 현명한 선택이다. 예:<br>
```cpp
int count_x(char* p, char x)
// p[]에서 x가 등장하는 횟수를 센다
// p는 null 또는 null 종료된 char 배열을 가리킨다고 가정
{
    if (p == nullptr) return 0;
    int count = 0;
    for (; *p != 0; ++p)
        if (*p == x)
            ++count;
    return count;
}
```
<br>
기본 타입, const 한정자, 선언자 연산자를 조합하여 만든 타입들을 우리는 내장 타입(built-in types)이라고 부른다<br>

C++의 추상화 메커니즘은 주로 다음을 위해 설계되었다:<br>
프로그래머가 자신만의 타입을 설계하고 구현할 수 있도록<br>
그 타입을 간결하고 우아하게 사용할 수 있도록<br>
추상화 메커니즘을 통해 내장 타입을 기반으로 만들어진 타입을 사용자 정의 타입(user-defined types)<br>
주로 클래스(class)와 열거형(enumeration)으로 표현된다.<br>
<br>
```
cpp
void vector_init(Vector& v, int s)
{
    v.elem = new double[s]; // s개의 double 배열을 동적 할당
    v.sz = s;
}
```
Vector&에서 &는 비-상수 참조(non-const reference)로 전달된다는 뜻<br>
 vector_init() 함수가 전달된 Vector를 직접 수정할 수 있다.<br>
new 연산자는 free store라 불리는 영역에서 메모리를 할당한다. 이 영역은 동적 메모리(dynamic memory) 또는 힙(heap)이라고도 한다.<br>






