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

```cpp
void vector_init(Vector& v, int s)
{
    v.elem = new double[s]; // s개의 double 배열을 동적 할당
    v.sz = s;
}
```
Vector&에서 &는 비-상수 참조(non-const reference)로 전달된다는 뜻<br>
 vector_init() 함수가 전달된 Vector를 직접 수정할 수 있다.<br>
new 연산자는 free store라 불리는 영역에서 메모리를 할당한다. 이 영역은 동적 메모리(dynamic memory) 또는 힙(heap)이라고도 한다.<br>
<br>
구조체의 멤버에 접근할 때는 다음과 같은 연산자를 사용한다:<br>
. (점): 이름 또는 참조를 통해 멤버에 접근<br>
->: 포인터를 통해 멤버에 접근<br>

```cpp
void f(Vector v, Vector& rv, Vector* pv)
{
    int i1 = v.sz;     // 이름을 통해 접근
    int i2 = rv.sz;    // 참조를 통해 접근
    int i4 = pv->sz;   // 포인터를 통해 접근
}
```
<br>
구현(implementation)<br>
<br>

```cpp
class Vector {
public:
    Vector(int s) : elem{new double[s]}, sz{s} { } // Vector 생성자
    double& operator[](int i) { return elem[i]; }  // 요소 접근: 인덱스 연산자
    int size() { return sz; }                      // 크기 반환
private:
    double* elem; // 요소들을 가리키는 포인터
    int sz;       // 요소의 개수
};
```
<br>
클래스와 이름이 같은 “함수”는 생성자(constructor)라 한다. 이는 클래스의 객체를 생성하는 데 사용되는 함수이다.<br>
생성자는 클래스 객체를 초기화할 때 반드시 호출된다. 즉, 생성자를 정의하면 초기화되지 않은 변수 문제를 방지할 수 있다.<br>
생성자는 멤버 초기화 리스트(member initializer list)를 사용하여 멤버들을 초기화한다<br>

```cpp
    Vector(int s) : elem{new double[s]}, sz{s} { } // Vector 생성자
```
<br>
초기화시 ( ) { } 중 { }이 () 보다 권장된다고 합니다. <br>
<br>
오류 처리(error handling)<br>
<br>
소멸자(destructor)<br>
<br>
열거형 (Enumerations): C++은 값들을 열거할 수 있는 간단한 형태의 사용자 정의 타입을 지원한다<br>
<br>

```cpp
enum class Color { red, blue, green };
enum class Traffic_light { green, yellow, red };

Color col = Color::red;
Traffic_light light = Traffic_light::red;
```
여기서 red와 같은 열거자(enumerator)는 자신이 속한 enum class의 스코프(scope) 안에 있기 때문에, 서로 다른 열거형에서 중복되어 사용되어도 혼동이 없다.<br>
예를 들어, Color::red는 Color의 red이고, Traffic_light::red는 Traffic_light의 red로, 서로 다른 값이다.<br>

enum 뒤에 class를 붙이면, 해당 열거형은 강한 타입(strongly typed)을 가지며, 열거자들이 스코프에 묶이게 된다.<br>
이렇게 별도의 타입으로 정의된 enum class는 상수의 잘못된 사용을 방지하는 데 도움을 준다.<br>
예를 들어, 다음과 같은 혼용은 허용되지 않는다:<br>
```cpp
Color x = red; // 오류: 어떤 red인지 알 수 없음
Color y = Traffic_light::red; // 오류: 해당 red는 Color가 아님
Color z = Color::red; // OK
```
<br>

마찬가지로, Color와 정수 값을 암묵적으로 혼합하는 것도 허용되지 않는다:<br>
```cpp
int i = Color::red; // 오류: Color::red는 int가 아님
Color c = 2;        // 오류: 2는 Color가 아님
```
<br>

만약 열거자 이름을 명시적으로 지정하지 않고 사용하고 싶거나, 열거자 값을 정수(int)로 다루고 싶다면, enum class에서 class를 제거하여 일반 열거형(plain enum)을 사용할 수 있다.<br>
열거형도 사용자 정의 타입이므로, 원한다면 연산자를 직접 정의할 수 있다.
예를들어, Traffic_light에 대해 전위 증가 연산자(prefix increment)를 정의할 수 있다:<br>
```cpp
Traffic_light& operator++(Traffic_light& t)
{
    switch (t) {
        case Traffic_light::green:  return t = Traffic_light::yellow;
        case Traffic_light::yellow: return t = Traffic_light::red;
        case Traffic_light::red:    return t = Traffic_light::green;
    }
}
```
이제 다음과 같이 사용할 수 있다:<br>
```cpp
Traffic_light next = ++light; // next는 Traffic_light::green이 됨
```
C++은 이처럼 강한 타입을 가진 enum class 외에도, 덜 엄격한 일반 열거형(plain enum)도 제공한다.<br>
<br>
<br>
모듈화 (Modularity)<br>
<br>
C++은 분리 컴파일(separate compilation) 개념을 지원한다.<br>
<br>

네임스페이스 (Namespaces): 일련의 선언들이 서로 관련되어 있음을 표현하고, 이름 충돌(name clash)을 방지하기 위한 메커니즘이다.<br>
```cpp
namespace My_code {
    class complex { /* ... */ };
    complex sqrt(complex);
    // ...
    int main();
}

int My_code::main()
{
    complex z {1, 2};
    auto z2 = sqrt(z);
    std::cout << '{' << z2.real() << ',' << z2.imag() << "}\n";
    // ...
}

int main()
{
    return My_code::main();
}
```
이처럼 내 코드를 My_code라는 네임스페이스 안에 넣으면, 내가 정의한 이름들이 표준 라이브러리의 std 네임스페이스에 있는 이름들과 충돌하지 않도록 할 수 있다. 왜냐하면 표준 라이브러리도 복소수 연산을 지원하기 때문이다. 다른 네임스페이스에 있는 이름에 접근하는 간단한 방법은 네임스페이스 이름을 붙여서 명시적으로 지정하는 것이다. 예: <br>
```cpp
std::cout, My_code::main
```
여기서 “진짜 main()” 함수는 전역 네임스페이스(global namespace)에 정의되어 있으며, 이는 특정 네임스페이스, 클래스, 함수에 속하지 않는 위치를 의미한다.표준 라이브러리의 이름들에 접근하기 위해서는 다음과 같은 using 지시문(using-directive)을 사용할 수 있다.<br>
<br>
