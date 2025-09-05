# Programs Common Sense (CPP)

<details><summary>Day 1</summary>
프로그래밍에서는 이러한 약어(abbreviation)가 흔히 사용됩니다.<br>

```cpp
// 이 프로그램은 "Hello, World!" 메시지를 모니터에 출력합니다
import std; // C++ 표준 라이브러리 접근
int main() // C++ 프로그램은 main 함수부터 실행됩니다
{
    std::cout << "Hello, World!\n"; // "Hello, World!" 출력
    return 0;
}
```

\n은 줄 바꿈을 나타내는 특수 문자(special character)<br>
문자열 리터럴(string literal)은 큰따옴표(")로 감싸며, "Hello, World!\n"은 문자들의 집합입니다.<br>
cout은 표준 출력 스트림(standard output stream)을 의미<br>
cout은 “see-out”으로 발음되며, “character output stream”의 약어입니다.<br>
std::cout에서 std::는 cout이 표준 라이브러리(standard library)에 속해 있음을 나타냅니다.<br>

<details><summary>주석에 대하여</summary>
//(슬래시 두 번) 이후에 작성된 내용은 컴파일러가 무시하며, 코드를 읽는 프로그래머를 위한 설명입니다. <br>
코드의 주요 독자(primary audience)를 인간으로 간주하는 것이 타당합니다.<br>
가능한 모든 방법을 동원해 코드를 읽기 쉽게 만드세요.<br>
무엇을 의도하는지, 무엇을 하려는지 상기시켜주는 역할을 합니다 <br> 
</details>

모듈 가져오기(module import) 문
```cpp
import std;
```
컴퓨터에게 std라는 모듈에서 기능을 가져오도록(import) 지시합니다. std는 C++ 표준 라이브러리(standard library)의 모든 기능을 사용할 수 있게 해주는 표준 모듈입니다. <br>

<details><summary>main이라는 이름의 함수</summary>
모든 C++ 프로그램은 반드시 main이라는 이름의 함수를 가져야 합니다. 그래야 컴퓨터가 어디서부터 실행을 시작해야 하는지 알 수 있습니다. 함수란 기본적으로 이름이 붙은 명령의 순서(sequence of instructions)이며, 컴퓨터는 그 명령들을 작성된 순서대로 실행합니다.<br>
함수는 네 가지 구성 요소를 가집니다:
반환 타입(return type) — 여기서는 int(정수)를 의미하며, 함수가 실행 요청자에게 어떤 결과를 반환할지를 지정합니다. int는 C++의 예약어(reserved word)이므로, 다른 이름으로 사용할 수 없습니다.
이름(name) — 여기서는 main.
매개변수 목록(parameter list) — 괄호 ()로 감싸며, 여기서는 비어 있습니다. 자세한 내용은 §7.2 및 §7.4에서 다룹니다.
함수 본문(function body) — 중괄호 {}로 감싸며, 함수가 수행할 행동들(statement)을 나열합니다

```cpp
int main() { }
```
이 코드는 아무것도 하지 않기 때문에 실용적이지 않습니다.<br>
main()이 0을 반환하면, 프로그램이 정상적으로 종료되었음을 의미합니다.<br>
</details>

C++ 프로그램에서 어떤 동작을 지정하는 코드 조각은 문장(statement)이라고 부릅니다.<br>

<details><summary>컴파일(Compilation)</summary>
C++는 컴파일 언어(compiled language)입니다. 즉, 프로그램을 실행하려면 먼저 사람이 읽을 수 있는 형태(human-readable form)에서 컴퓨터가 “이해할 수 있는” 형태로 번역(translation)해야 합니다. 이 번역 작업은 컴파일러(compiler)라는 프로그램이 수행합니다.<br>
우리가 읽고 쓰는 것은 소스 코드(source code) 또는 프로그램 텍스트(program text)라고 하며, 컴퓨터가 실제로 실행하는 것은 오브젝트 코드(object code) 또는 기계어(machine code)라고 합니다.<br>
일반적으로 C++의 소스 코드 파일은 .cpp 확장자(suffix)를 가지며(예: hello_world.cpp), 오브젝트 코드 파일은 Windows에서는 .obj, Linux에서는 .o 확장자를 사용합니다.<br>
컴파일러(compiler)는 당신의 소스 코드(source code)를 읽고, 그 의미를 파악하려고 시도합니다. 컴파일러는 프로그램이 문법적으로 올바른지, 각 단어가 정의된 의미를 갖고 있는지, 그리고 실행하지 않고도 명백하게 잘못된 부분이 있는지를 검사합니다. 컴파일러는 문법(syntax)에 대해 매우 까다롭습니다. 모듈을 가져오지 않거나, 세미콜론(;)이나 중괄호({})를 빠뜨리는 등 작은 세부 사항 하나만 누락해도 오류가 발생합니다. 또한, 컴파일러는 철자 오류(spelling mistake)에 대해 전혀 관용이 없습니다.<br>
    
</details>

C++에서는 integer 대신 약어 int를 사용해야 합니다. integer는 C++에서 정의된 타입이 아니므로 컴파일러가 이를 인식하지 못합니다.<br>

<details><summary>링크(Linking)</summary>
하나의 프로그램은 보통 여러 개의 독립된 부분(separate parts)으로 구성되며, 이들은 종종 서로 다른 사람들에 의해 개발됩니다. <br>
이러한 독립된 부분들은 모듈(module) 또는 번역 단위(translation unit)라고 불리며, 각각 개별적으로 컴파일(compilation)된 후, 생성된 오브젝트 코드(object code) 파일들을 하나의 실행 가능한 프로그램(executable program)으로 결합해야 합니다.<br>
이처럼 여러 부분을 결합하는 작업을 수행하는 프로그램을 링커(linker)라고 합니다. 이름 그대로, 링커는 코드 조각들을 연결(link)하여 하나의 완성된 실행 파일을 만들어냅니다.<br>
링커(linker)의 출력 결과는 실행 파일(executable file)이라고 하며, Windows에서는 보통 .exe 확장자(suffix)를 갖습니다.<br>
주의할 점은, 오브젝트 코드(object code)와 실행 파일(executable)은 시스템 간 이식되지 않는다(non-portable)는 것입니다.<br>
또한, 라이브러리(library)란 단순히 코드의 집합이며, 보통 다른 사람이 작성한 코드입니다. 우리는 이러한 라이브러리를 가져온 모듈(imported module)에 포함된 선언(declaration)을 통해 접근합니다.<br>
선언(declaration)이란 코드의 특정 부분을 어떻게 사용할 수 있는지를 지정하는 프로그램 문장(statement)입니다.<br>

컴파일러가 발견하는 오류는 컴파일 타임 오류(compile-time errors), 링커가 발견하는 오류는 링크 타임 오류(link-time errors), 프로그램 실행 중에 발견되는 오류는 런타임 오류(run-time errors) 또는 논리 오류(logic errors)라고 합니다. 일반적으로 컴파일 타임 오류는 링크 타임 오류보다 이해하고 수정하기 쉬우며, 링크 타임 오류는 런타임 오류보다 찾고 해결하기 쉽습니다.<br>
</details>

<details><summary>프로그래밍 환경(Programming environments)</summary>
프로그래밍을 하기 위해 우리는 프로그래밍 언어(programming language)를 사용합니다. 또한, 소스 코드를 오브젝트 코드(object code)로 번역하기 위해 컴파일러(compiler)를 사용하고, 오브젝트 코드를 실행 가능한 프로그램(executable program)으로 결합하기 위해 링커(linker)를 사용합니다.<br>
이 외에도, 소스 코드 텍스트를 컴퓨터에 입력하고 편집하기 위한 프로그램이 필요합니다. 이들은 모두 프로그래머의 도구 상자(tool chest) 또는 프로그램 개발 환경(program development environment)을 구성하는 가장 기본적이고 중요한 도구들입니다.<br>
명령줄(command-line) 환경에서 작업한다면, 컴파일 및 링크 명령을 직접 입력해야 합니다. IDE(통합 개발 환경, Integrated Development Environment 또는 대화형 개발 환경, Interactive Development Environment)를 사용할 경우, 버튼 클릭 한 번으로 컴파일과 링크 작업을 수행할 수 있습니다.<br>
IDE는 일반적으로 다음과 같은 기능을 포함합니다:<br>
<strong>편집기(editor): 주석, 키워드, 기타 코드 요소를 구분하기 위한 색상 구분(color coding) 기능<br>
디버깅 도구(debugging tools): 오류를 찾고 수정하는 데 도움을 줌<br>
컴파일 및 실행 기능: 코드 작성 후 바로 실행 가능<br></strong>
프로그램의 오류는 흔히 버그(bug)라고 불리며, 이로 인해 “디버깅”이라는 용어가 생겼습니다. 이 용어의 유래는 초기 컴퓨터 시스템에서 실제 곤충(insect)이 컴퓨터 내부에 들어가 프로그램이 실패한 사건에서 비롯되었습니다. <br>
</details>

프로그래밍에서 반복과 실습(repetition and practice)은 기술을 개발하는 데 필수적입니다.<br>

<details><summary>질문과 대답 1</summary>
<details><summary>Q : "Hello, World!" 프로그램의 목적은 무엇인가요?</summary>
A : 컴파일러(compiler)를 통해 기계 명령(machine instructions)으로 번역하는 과정, 그리고 그 명령을 실행(execute)하는 과정을 소개합니다. 문자열 출력과 개행, 표준 출력 스트림과 이를 위한 표준 라이브러리에 대해 알려줍니다. 또한 주석을 사용하는 방법을 소개합니다.</details>
<details><summary>Q : 함수의 네 가지 구성 요소를 말해보세요.</summary>
A : 반환 타입(return type), 이름(name), 매개변수 목록(parameter list), 함수 본문(function body)</details>
<details><summary>Q : 모든 C++ 프로그램에 반드시 포함되어야 하는 함수는 무엇인가요?</summary>
A : main함수</details>
<details><summary>Q : "Hello, World!" 프로그램에서 return 0;의 목적은 무엇인가요?</summary>
A : 프로그램이 정상적으로 종료되었음을 의미합니다.</details>
<details><summary>Q : 컴파일러의 역할은 무엇인가요?</summary>
A : 프로그램을 실행하려면 먼저 사람이 읽을 수 있는 형태(human-readable form)에서 컴퓨터가 “이해할 수 있는” 형태로 번역(translation)해야 합니다. 이 번역 작업은 컴파일러(compiler)라는 프로그램이 수행합니다.</details>
<details><summary>Q : import 문장의 목적은 무엇인가요?</summary>
A : 모듈 가져오기(module import) 문입니다. 컴퓨터에게 std라는 모듈에서 기능을 가져오도록(import) 지시합니다.</details>
<details><summary>Q : #include 지시문의 목적은 무엇인가요?</summary>
A : 소스코드를 포함시키는 </details>
<details><summary>Q : 파일 이름 끝의 .cpp 확장자는 C++에서 무엇을 의미하나요?</summary>
A : C++의 소스코드 확장자입니다.</details>
<details><summary>Q : 링커(linker)는 프로그램에서 어떤 역할을 하나요?</summary>
A : 여러 오브젝트 코드 파일을 하나의 실행 가능한 프로그램으로 결합시키는데 이 작업을 수행하는 프로그램을 링커라고 합니다.</details>
<details><summary>Q : 소스 파일(source file)과 오브젝트 파일(object file)의 차이는 무엇인가요?</summary>
A : 컴파일이 되기 전과 된 후의 차이입니다.</details>
<details><summary>Q : 실행 파일(executable)이란 무엇인가요?</summary>
A : 실행 파일은 윈도우 환경에서 .exe확장자를 갖고, 소스코드 파일을 컴파일러가 컴파일해 오브젝트 파일로 만든 후 여러 오브젝트 파일을 묶는 역할을 하는 링커의 일이 끝나면 .exe확장자파일을 갖습니다.</details>
<details><summary>Q : IDE란 무엇이며, 어떤 기능을 제공하나요?</summary>
A : 편집기, 디버깅, 컴파일 및 실행 기능을 제공합니다.</details>
<details><summary>Q : 컴파일된 프로그램을 실행하려면 어떻게 해야 하나요?</summary>
A : 오브젝트 파일들을 하나로 연결할 링커를 실행시킨 후 성공적으로 마치면 .exe를 갖게 됩니다.</details>
<details><summary>Q : 주석(comment)이란 무엇인가요?</summary>
A : 주석은 컴파일러에게 전달하는 말이 아닌 프로그래머에게 전달할 수 있는 메세지기능힙니다. //두개를 사용하거나 /**/를 이용해서 소스코드가 어떤 목적으로 만들어졌는지 혹은 도움이 되는 메세지를 전달할 수 있습니다.</details>
</details>

<details><summary>용어집(glossary)</summary>
    
// : 주석(comment)을 시작하는 기호. 해당 줄의 나머지 부분은 컴파일러가 무시함.
executable : 실행 파일. 컴파일과 링크 과정을 거쳐 생성된, 실제로 실행 가능한 프로그램 파일.
main() : 모든 C++ 프로그램의 시작점(entry point)이 되는 함수.
<< : 출력 연산자(output operator). 데이터를 출력 스트림에 전달할 때 사용.
function : 함수. 이름이 붙은 명령 집합으로, 특정 작업을 수행함.
object code : 오브젝트 코드. 컴파일된 기계어 코드로, 실행 파일 생성에 사용됨.
C++ : 이 책에서 사용하는 프로그래밍 언어. 고성능과 추상화를 동시에 지원함.
header file : 헤더 파일. 함수 선언과 상수 정의 등을 포함하며, #include로 불러옴.
output : 출력. 프로그램이 사용자나 다른 시스템에 정보를 전달하는 행위.
comment : 주석. 코드에 대한 설명을 작성하며, 컴파일러는 이를 무시함.
IDE : 통합 개발 환경(Integrated Development Environment). 코드 작성, 컴파일, 디버깅 등을 하나의 인터페이스에서 수행할 수 있게 해줌.
program : 프로그램. 컴퓨터가 수행할 수 있도록 작성된 명령 집합.
compiler : 컴파일러. 소스 코드를 오브젝트 코드로 번역하는 도구.
import : 모듈 가져오기 문장. 특정 모듈의 기능을 사용할 수 있도록 설정함.
source code : 소스 코드. 사람이 읽을 수 있는 형태로 작성된 프로그램 코드.
compile-time : 컴파일 시간. 컴파일러가 코드를 분석하고 번역하는 시점.
error : 오류. 프로그램이 의도대로 작동하지 않게 만드는 문제.
library : 라이브러리. 재사용 가능한 코드 집합으로, 다른 프로그램에서 호출 가능.
statement : 문장. 프로그램 내에서 하나의 동작을 지정하는 코드 단위.
cout : 표준 출력 스트림. 화면에 텍스트를 출력할 때 사용.
linker : 링커. 여러 오브젝트 파일을 하나의 실행 파일로 결합하는 도구.
module : 모듈. 기능을 캡슐화한 코드 집합으로, import를 통해 불러옴.
#include : 헤더 포함 지시문. 외부 파일의 선언을 현재 코드에 포함시킴.
std : 표준 네임스페이스(namespace). C++ 표준 라이브러리의 기능들이 정의된 공간.
command line : 명령줄 인터페이스. 텍스트 기반으로 명령을 입력하고 실행하는 환경.
bug : 버그. 프로그램 내의 오류 또는 결함.
debugging : 디버깅. 버그를 찾아내고 수정하는 과정.
</details>
</details>

<details><summary>Day 2</summary>

객체란 특정 타입(type)을 가진 메모리 영역(region of memory)이며, 그 타입은 해당 객체에 어떤 종류의 정보가 저장될 수 있는지를 지정합니다. 이러한 객체에 이름(name)이 붙어 있으면, 우리는 그것을 변수(variable)라고 부릅니다.<br>
```cpp
// 이름을 입력받고 출력하는 프로그램
#include "PPP.h"
int main()
{
    cout << "Please enter your first name (followed by \"enter\"):\n";
    string first_name;       // first_name은 string 타입의 변수
    cin >> first_name;       // 키보드로부터 문자열을 읽어 first_name에 저장
    cout << "Hello, " << first_name << "!\n";
}
```
<details><summary>프롬프트(prompt)</summary>

```cpp
cout << "Please enter your first name (followed by 'enter'):\n";
```
main() 함수의 첫 번째 줄은 사용자에게 이름을 입력하라는 메시지를 출력합니다. 이러한 메시지는 일반적으로 프롬프트(prompt)라고 불리며, 사용자가 행동을 취하도록 유도하는 역할을 합니다.
</details>

<details><summary>정의문(definition)</summary>

```cpp
string first_name; // first_name은 string 타입의 변수
```
이 문장은 문자열을 저장할 수 있는 메모리 공간을 확보하고, 그 공간에 first_name이라는 이름을 부여합니다. 변수에 이름을 부여하고 메모리를 할당하는 문장(statement)을 정의문(definition)이라고 합니다.
</details>

<details><summary>cin(Standard Input Stream)</summary>

```cpp
cin >> first_name; // 키보드 입력을 first_name에 저장
```
 cin은 표준 입력 스트림(standard input stream)을 의미하며, “see-in”으로 발음됩니다. 이는 character input의 약어입니다. cin은 C++ 표준 라이브러리(standard library)에 정의되어 있습니다.<br>
>> 연산자는 “어디로부터 가져온다(get from)”는 의미를 가지며, 두 번째 피연산자(여기서는 first_name)는 입력된 값이 저장될 위치를 지정합니다.<br>
</details>

줄 바꿈(newline)은 컴퓨터의 입력 처리를 시작하게 만드는 신호입니다. 사용자가 Enter 키를 누르기 전까지, 컴퓨터는 단지 문자들을 수집할 뿐입니다. 이 “지연(delay)” 덕분에 사용자는 입력을 수정하거나 삭제할 수 있는 기회를 갖게 됩니다. 입력된 줄 바꿈 문자는 메모리에 저장되는 문자열에는 포함되지 않습니다.<br>

<details><summary>변수(variable)</summary>
데이터를 저장하는 공간을 우리는 객체(object)라고 부릅니다. 객체에 접근하려면 이름(name)이 필요하며, 이름이 붙은 객체를 변수(variable)라고 합니다.<br>
변수는 특정한 타입(type)을 가지며, 이 타입은 다음을 결정합니다:<br>
어떤 값을 저장할 수 있는가, 예: 123은 int에 저장 가능, "Hello, World!\n"은 string에 저장 가능<br>
어떤 연산을 수행할 수 있는가, 예: int는 * 연산자로 곱셈 가능, string은 <= 연산자로 비교 가능<br>
변수에 저장되는 데이터 항목은 값(value)이라고 합니다.<br>
변수를 정의하는 문장은 정의문(definition)이라고 하며, 정의문은 초기값(initial value)을 제공할 수 있고, 제공하는 것이 바람직합니다.<br>

```cpp
string name = "Inhan";
int number_of_steps = 20;
```
여기서 = 뒤에 오는 값은 초기화자(initializer)라고 부릅니다.
</details>
    
<details><summary>double(double-precision floating point)</summary>
“배정밀도 부동소수(double-precision floating point)”의 줄임말입니다. 부동소수점(floating point)은 컴퓨터가 실수(real number) 개념을 근사하여 표현하는 방식입니다.
</details>

<details><summary>고유한 리터럴(literal) 스타일</summary>

```cpp
39           // int: 정수
3.5          // double: 부동소수점 숫자
'.'          // char: 홑따옴표로 감싼 개별 문자
"Annemarie"  // string: 큰따옴표로 감싼 문자열
true         // bool: true 또는 false
```
숫자만으로 이루어진 문자열(예: 1234, 2, 976)은 정수(int)를 나타냅니다.<br>
홑따옴표로 감싼 단일 문자(예: '1', '@', 'x')는 문자(char)를 나타냅니다.<br>
소수점이 포함된 숫자(예: 1.234, 0.12, .98)는 부동소수점(double) 값을 나타냅니다.<br>
큰따옴표로 감싼 문자 시퀀스(예: "1234", "Howdy!", "Annemarie")는 문자열(string)을 나타냅니다.<br>
</details>

<details><summary>type-sensitive</summary>
입력 연산자 >>(“get from”)는 타입에 민감합니다. 입력된 값은 읽어들이는 변수의 타입에 따라 해석됩니다.<br>

```cpp
int main() // 이름과 나이를 입력받음
{
    cout << "Please enter your first name and age\n";
    string first_name = "???"; // string 변수 ("???"는 이름을 모른다는 의미)
    int age = -1;              // int 변수 (-1은 나이를 모른다는 의미)
    cin >> first_name >> age;  // 문자열 다음에 정수를 입력받음
    cout << "Hello, " << first_name << " (age " << age << ")\n";
}
```
위 프로그램에서 Inhan 20를 입력하면, >> 연산자는 "Inhan"를 first_name에, 20를 age에 저장하고 다음과 같은 출력을 생성합니다:
```출력결과
출력결과
Hello, Inhan (age 20)
```
그렇다면 왜 "Inhan 20" 전체가 first_name에 들어가지 않을까요? 그 이유는 문자열 입력은 공백(whitespace)에서 종료되는 것이 관례이기 때문입니다. 공백에는 스페이스(space), 줄 바꿈(newline), 탭(tab) 문자가 포함됩니다. 반면, >>는 기본적으로 공백을 무시하고 건너뜁니다. <br>
출력 연산자 &lt;&lt;도 >>처럼 타입에 민감합니다. 만약 사용자가 20 Inhan를 입력한다면, 

```출력결과
출력결과
Hello, 20 (age -1)
```
왜 이런 일이 발생할까요?<br>
20는 문자 시퀀스이므로 first_name에 저장됩니다.<br>
Inhan는 정수가 아니므로 age에 저장되지 않습니다.<br>
따라서 age는 초기값인 -1을 그대로 유지합니다.<br>
즉, 입력이 타입에 맞지 않으면 해당 변수는 값을 받지 못하고 초기값을 유지하게 됩니다.<br>
</details>

<details><summary>>>를 사용한 문자열 입력</summary>
>>를 사용한 문자열 입력은 기본적으로 공백에서 종료되므로 한 단어만 읽습니다. 하지만 때로는 여러 단어를 입력받고 싶을 때도 있습니다. 이를 위한 방법은 여러 가지가 있으며, 그 중 하나는 다음과 같습니다:

```cpp
int main()
{
    cout << "Please enter your first and second names\n";
    string first;
    string second;
    cin >> first >> second; // 두 개의 문자열을 입력받음
    cout << "Hello, " << first << " " << second << '\n';
}
```
여기서는 >>를 두 번 사용하여 각각의 이름을 입력받습니다. 출력 시에는 이름 사이에 공백을 직접 삽입해야 합니다.
또한, first와 second 변수에는 초기값이 명시되어 있지 않지만, C++에서는 string 타입의 변수는 기본적으로 빈 문자열("")로 초기화됩니다.<br>    
</details>

<details><summary>문자열 이어붙임(concatenate)</summary>
```cpp
string n1 = name + " 이 "; // +는 문자열을 이어붙임(concatenate)
string n1 = name - " 이 "; // 오류: 문자열에는 - 연산이 정의되어 있지 않음
```
“오류(error)”란, 컴파일러가 문자열끼리의 뺄셈 연산을 시도하는 프로그램을 거부(reject)한다는 뜻입니다.<br>
</details>
<details><summary>연산자(operator)</summary>

| Operator | bool | char | int | double | string |
|:-------:|:-------:|:-------:|:-------:|:-------:|:-------:|
|Assighment|  =  |    =    |    =    |    =    |    =    |
|addition|     |     | +    | +    |     |
|concatenation|||||+|
|subtraction|||-|-||
|multiplication|||*|*||
|division|||/|/||
|reminder(modulo)|||%||
|increment by 1|||++|++||
|decrement by 1|||--|--||

|increment by n|||+=n|+=n||
|decrement by n|||-=n|-=n||
|add to end|||||+=|
|multiply and assign|||*=n|*=n||
|divide and assign|||/=n|/=n||
|read from s into x|s>>x|s>>x|s>>x|s>>x|s>>x|
|write x to s|s>>x|s>>x|s>>x|s>>x|s>>x|
|equals|==|==|==|==|==|
|not equals|!=|!=|!=|!=|!=|
|greater than|>|>|>|>|>|
|greater than or equal|>=|>=|>=|>=|>=|
|less than|<|<|<|<|<|
|less than or equal|<=|<=|<=|<=|<=|





</details>



</details>
