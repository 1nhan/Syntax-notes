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

<details><summary>용어집(glossary) 1</summary>
    
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
</details><!-- Day 1 /details -->

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
|assignment|  =  |    =    |    =    |    =    |    =    |
|addition|     |     | +    | +    |     |
|concatenation|||||+|
|subtraction|||-|-||
|multiplication|||*|*||
|division|||/|/||
|reminder(modulo)|||%||
|increment by 1|||++|++||
|decrement by 1|||--|--||
|increment by n|||+=n|+=n||
|add to end|||||+=|
|decrement by n|||-=n|-=n||
|multiply and assign|||*=n|*=n||
|divide and assign|||/=n|/=n||
|read from s into x|s>>x|s>>x|s>>x|s>>x|s>>x|
|write x to s|s<<x|s<<x|s<<x|s<<x|s<<x|
|equals|==|==|==|==|==|
|not equals|!=|!=|!=|!=|!=|
|greater than|>|>|>|>|>|
|greater than or equal|>=|>=|>=|>=|>=|
|less than|<|<|<|<|<|
|less than or equal|<=|<=|<=|<=|<=|

빈 칸(blank square)은 해당 타입에 대해 직접적인 연산이 정의되어 있지 않음을 의미합니다.  
같음(equal)을 비교할 때는 ==를 사용하며, =는 대입(assign)을 의미합니다.  
모든 연산이 연산자로 표현되는 것은 아닙니다. 예를 들어, 제곱근(square root)을 구하는 연산은 sqrt()라는 함수(function)로 표현됩니다.  
</details>
<details><summary>문자열 비교(string comparison)</summary>
문자열은 비교 연산자(comparison operators)도 지원합니다:
    
```cpp
int main() // 이름 비교
{
    cout << "Please enter two names\n";
    string first;
    string second;
    cin >> first >> second; // 두 문자열 입력
    if (first == second)
        cout << "that's the same name twice\n";
    if (first < second)
        cout << first << " is alphabetically before " << second << '\n';
    if (first > second)
        cout << first << " is alphabetically after " << second << '\n';
}
```
</details>


<details><summary>대입 연산자(assignment operator)</summary>
C++에서는 = 기호로 표현되며, 변수에 새로운 값을 할당(assign)합니다.  

```cpp
int a = 3;
a = 4;
int b = a;
b = a + 3;
a = a + 7;
```
마지막 대입문은 주목할 만합니다. 무엇보다도, =는 “같음(equal)”을 의미하지 않는다는 점을 분명히 보여줍니다—분명히 a는 a + 7과 같지 않죠. =는 대입(assignment)을 의미하며, 이는 변수에 새로운 값을 넣는 것입니다.

유사하지만 논리적으로는 구별되는 두 가지 연산을 구분한다:  
초기화(initialization): 변수에 최초의 값을 부여하는 것  
대입(assignment): 변수에 새로운 값을 부여하는 것  
논리적으로 초기화와 대입은 서로 다르다. 원칙적으로 초기화는 항상 변수가 비어 있는 상태에서 시작된다. 반면, 대입은 기존 값을 제거한 후 새로운 값을 넣는 과정이 필요하다.  
<details><summary>문법 검사기(grammar checker)</summary>
대입 연산은 객체에 새 값을 넣고자 할 때 필요합니다. 생각해보면, 대입은 반복적인 작업을 수행할 때 가장 유용합니다. 즉, 다른 값으로 다시 무언가를 수행하고자 할 때 대입이 필요합니다.
다음은 단어 시퀀스에서 인접한 중복 단어를 감지하는 프로그램입니다. 이런 코드는 대부분의 문법 검사기(grammar checker)에서 사용됩니다:

```cpp
int main()
{
    string previous; // 이전 단어; 기본값은 ""
    string current;  // 현재 단어
    while (cin >> current) { // 단어 스트림을 읽음
        if (previous == current) // 이전 단어와 같으면
            cout << "repeated word: " << current << '\n';
        previous = current; // 현재 단어를 이전 단어로 저장
    }
}
```

```cpp
string current; // 현재 단어
```
string 타입은 기본적으로 빈 문자열("")로 초기화되므로, 명시적으로 초기값을 줄 필요는 없습니다.

```cpp
while (cin >> current)
```
이 구문은 while 문(while-statement)이라고 합니다.  
while 문은 cin >> current가 성공하는 동안 다음 문장을 반복 실행합니다. cin >> current는 표준 입력으로부터 공백으로 구분된 단어를 읽어들이며, 입력 스트림에 더 이상 읽을 문자가 없을 때 실패합니다.  
입력 종료(end-of-input)는 다음 키 조합으로 수행할 수 있습니다:  
Windows: Ctrl + Z → Enter  
Linux/macOS: Ctrl + D  

```cpp
if (previous == current)
    cout << "repeated word: " << current << '\n';

previous = current;
```
이제 프로그램의 핵심 동작을 살펴보면:  
1.current에 단어를 입력받음  
2.previous와 비교  
3.같으면 중복 단어로 간주하고 출력  
4.previous = current로 다음 비교를 준비  
이 구조는 모든 경우를 처리할 수 있습니다. 단, 첫 번째 단어는 비교 대상이 없기 때문에 예외입니다.  
이 문제는 다음 정의로 해결됩니다:  

```cpp
string previous; // 이전 단어; 초기값은 ""
```

빈 문자열은 실제 단어가 아니므로, 첫 번째 반복에서 previous == current는 false가 되어, 중복 단어로 잘못 인식되지 않습니다.  
</details><!-- 문법 검사기 /details-->
</details><!-- 대입연선자 /details-->
<details><summary>복합 대입 연산자(Composite assignment operators)</summary>
변수에 1을 더하는 작업(incrementing)은 프로그램에서 매우 자주 사용되므로, C++에서는 이를 위한 특별한 문법(special syntax)을 제공합니다:
    
```cpp
++counter; // counter = counter + 1 과 동일
```
일반적으로, 이항 연산자(binary operator) oper에 대해 다음 규칙이 성립합니다:   
```
a oper= b  ≡  a = a oper b
```
이 규칙을 통해 다음과 같은 연산자들을 사용할 수 있습니다:   
+= (덧셈 후 대입)   
-= (뺄셈 후 대입)   
*= (곱셈 후 대입)   
/= (나눗셈 후 대입)   
%= (나머지 후 대입)   
이러한 표기법은 간결하고 직관적이며, 특히 *=와 /=는 많은 분야에서 스케일링(scaling) 연산으로 사용됩니다.   

<details><summary>중복 단어 감지 프로그램</summary>

```cpp
int main()
{
    int number_of_words = 0;
    string previous; // 이전 단어; 초기값은 ""
    string current;

    while (cin >> current) {
        ++number_of_words; // 단어 수 증가
        if (previous == current)
            cout << "word number " << number_of_words << " repeated: " << current << '\n';
        previous = current;
    }
}
```
단어 카운터는 0에서 시작합니다.   
단어를 하나 읽을 때마다 ++number_of_words로 카운터를 증가시킵니다.   
첫 번째 단어는 1번, 두 번째는 2번… 이런 식으로 번호가 매겨집니다.   
다음과 같이 작성해도 같은 결과를 얻을 수 있습니다:   
```cpp
number_of_words += 1;
```
혹은:   
```cpp  
number_of_words = number_of_words + 1;
```
하지만 ++number_of_words는 더 짧고, 증가(increment)의 의미를 직접적으로 표현합니다.   
</details><!-- 중복 단어 감지 프로그램/details -->
</details><!--복합대입연산자 /details-->

<details><summary>이름(Names)</summary>
변수에 이름(name)을 붙입니다. 이름을 붙이는 이유는 기억하기 쉽고, 프로그램의 다른 부분에서 참조(reference)할 수 있도록 하기 위함입니다.  
C++ 프로그램에서 이름은 다음 규칙을 따릅니다:  
문자로 시작해야 하며, 문자(letter), 숫자(digit), 밑줄(underscore)만 포함할 수 있습니다.  

다음은 유효하지 않은 이름(invalid names)입니다:

```cpp
2x              // 오류: 숫자로 시작할 수 없음
time@to@market  // 오류: '@'는 허용되지 않는 문자
Start menu      // 오류: 공백(space)은 허용되지 않음
```
“유효하지 않다”는 말은, C++ 컴파일러가 해당 이름을 받아들이지 않는다는 뜻입니다.

 시스템 코드나 자동 생성된 코드(machine-generated code)를 보면, 이름이 밑줄(_)로 시작하는 경우가 있습니다. 예: _foo 이런 이름은 구현체나 시스템 내부 용도로 예약(reserved)되어 있으므로, 직접 작성하지 마세요.  
밑줄로 시작하는 이름을 피하면, 여러분이 만든 이름이 시스템에서 자동 생성한 이름과 충돌할 가능성을 줄일 수 있습니다.  
C++에서 이름은 대소문자를 구분(case-sensitive)합니다. 즉, x와 X는 서로 다른 이름입니다.  
다음 프로그램은 최소 네 가지 오류를 포함하고 있습니다:  

```cpp
import std;
int Main()
{
    STRING s = "Goodbye, cruel world! ";
    cOut << S << '\n';
}
```
1. Main → C++에서는 main이어야 함 (대소문자 구분)  
2. STRING → C++에는 string 타입이 존재하지만, 대문자 STRING은 정의되지 않음  
3. cOut → 올바른 출력 스트림은 cout  
4. S → 변수는 s로 선언되었으므로, S는 정의되지 않음

C++ 언어는 많은 이름을 키워드(keyword)로 예약해두었습니다. 예:
```코드
if, else, class, int, module
```
이러한 키워드는 변수, 타입, 함수 등의 이름으로 사용할 수 없습니다.
예:
```cpp
int if = 7; // 오류: if는 키워드
```
또한, C++ 표준 라이브러리의 이름(예: string)을 사용자 정의 변수 이름으로 사용하는 것도 피해야 합니다. 이런 이름을 재사용하면, 표준 라이브러리를 사용하려 할 때 충돌이 발생할 수 있습니다.  
변수, 함수, 타입 등에 이름을 붙일 때는 의미 있는 이름(meaningful names)을 선택하세요. 즉, 프로그램을 이해하는 데 도움이 되는 이름을 사용해야 합니다.  

짧은 이름은 관례적으로 사용될 때 의미가 있습니다:  
x는 지역 변수(local variable) 또는 매개변수(parameter)로 사용  
i는 반복문 인덱스(loop index)로 사용  

모두 대문자로 된 이름(ALL_CAPITAL_LETTERS)은 사용하지 않습니다. 이런 스타일은 일반적으로 매크로(macros)에 예약되어 있으며 우리는 매크로 사용을 지양합니다.

정의하는 타입에는 첫 글자를 대문자로 사용합니다:  
예: Square, Graph  
단어 사이를 밑줄(_)로 구분하는 방식입니다:  
예: element_count  

</details><!-- 이름(Names)/details -->

<details><summary>타입(type)과 객체(object)</summary>
타입(type)이라는 개념은 C++뿐만 아니라 대부분의 프로그래밍 언어에서 중심적인 역할을 합니다. 이제 타입에 대해 조금 더 기술적으로 깊이 있는 시각으로 살펴보겠습니다:
타입(type)은 객체에 대해 어떤 값(value)들이 들어갈 수 있는지, 어떤 연산(operation)들이 적용될 수 있는지를 정의합니다.  
객체(object)는 특정 타입의 값을 저장하는 메모리 공간(memory)입니다.  
값(value)은 메모리에 저장된 비트(bit)들의 집합이며 해당 타입에 따라 해석됩니다.  
변수(variable)는 이름이 붙은 객체입니다.  
선언문(declaration)은 객체에 이름과 타입을 지정하는 문장입니다.  
정의문(definition)은 선언문 중에서도 메모리를 실제로 할당하는 문장입니다.  

```cpp
int a = 7;
int b = 9;
char c = 'a';
double x = 1.2;
string s1 = "hello";
string s2 = "1.2";
```
문자열(string)의 표현 방식은 정수(int)보다 조금 더 복잡합니다. 그 이유는 문자열이 자신이 포함하는 문자 수를 추적하기 때문입니다.  
문자 리터럴(character literal)과 문자열 리터럴(string literal)을 감싸는 따옴표(quote)는 메모리에 저장되지 않습니다.  
-int는 4바이트(32비트)  
-bool과 char는 1바이트(8비트)  
-double은 8바이트(64비트)  
메모리에 저장된 비트(bit)의 의미는 접근할 때 사용하는 타입에 전적으로 의존합니다.  
이처럼 타입에 따라 객체가 차지하는 메모리 공간의 크기가 다릅니다.  
다르게 말하면:  
-컴퓨터 메모리 자체는 타입을 알지 못합니다.  
-메모리는 단지 비트의 집합일 뿐이며,  
-우리가 어떻게 해석할지를 결정할 때 비로소 의미가 부여됩니다.  
이것은 우리가 일상에서 숫자를 사용할 때와 비슷합니다:  
-12.5라는 숫자는 단독으로는 의미가 없습니다.  
-그것이 $12.5, 12.5cm, 12.5갤런인지에 따라 의미가 달라집니다.  
-단위를 제공해야만 숫자에 의미가 생깁니다.  
예를 들어:  
-메모리의 동일한 비트 집합이  
-int로 보면 120이라는 정수로 해석되고, 
-char로 보면 문자 'x'로 해석될 수 있습니다.  
이를 string으로 해석하려 하면 말이 되지 않으며, 실제로 그렇게 사용하려 하면 런타임 오류(run-time error)가 발생합니다.  

</details><!-- 타입(type)과 객체(object)/details -->
<details><summary>타입 안전성(Type safety)</summary>
모든 객체는 정의될 때 타입(type)이 부여되며, 그 타입은 절대 변경되지 않습니다.  
프로그램(또는 프로그램의 일부)이 타입 안전(type-safe)하다는 것은, 모든 객체가 자신의 타입 규칙에 따라 올바르게 사용되고 있다는 것을 의미합니다.  
완전한 타입 안전성(complete type safety)은 C++의 이상적인 목표이자 일반적인 규칙입니다. 하지만 현실적으로, C++ 컴파일러는 임의의 코드에 대해 완전한 타입 안전성을 보장할 수 없습니다. 따라서 우리는 위험한 기법(unsafe techniques)을 피해야 하며, 타입 안전성을 확보하기 위한 코딩 규칙(coding rules)을 반드시 따라야 합니다.  
현대 C++과 정적 분석 도구(static analysis tools)를 활용하면, 대부분의 C++ 코드에 대해 타입 안전성을 검증할 수 있습니다.  
이상적인 방식은, 프로그램이 실행되기 전에 타입 안전성이 입증될 수 없는 언어 기능을 사용하지 않는 것입니다. 이를 정적 타입 안전성(static type safety)이라고 합니다.  

예를 들어, 초기화되지 않은 변수(uninitialized variable)를 사용하는 것은 타입 안전하지 않습니다:

```cpp
int main()
{
    double x;           // 초기화를 "잊음": x의 값은 정의되지 않음
    double y = x;       // y의 값도 정의되지 않음
    double z = 2.0 + x; // + 연산의 의미와 z의 값도 정의되지 않음
}
```
항상 변수를 초기화하세요!  
string과 vector 같은 타입은 기본 초기화(default initialization)가 보장됩니다.  
컴파일러 경고를 활성화하는 방법을 알아보세요.  
예: -Wall 옵션을 사용하면 대부분의 경고를 표시할 수 있습니다.  
</details><!-- 타입 안전성(Type safety)/details -->

<details><summary>변환(Conversions)</summary>
char 타입끼리 직접 덧셈을 하거나 double과 int를 직접 비교할 수 없다는 것을 배웠습니다. 하지만 C++에서는 이러한 작업을 간접적으로 수행할 수 있는 방법을 제공합니다.
표현식에서 필요할 경우:
char는 int로 변환(promoted)되고
int는 double로 변환(promoted)됩니다.
예를 들어:
    
```cpp
char c = 'x';
int i1 = c;           // i1은 c의 정수값을 받음
int i2 = c + 1000;    // i2는 c의 정수값에 1000을 더한 값
double d = i2 + 7.3;  // d는 i2에 7.3을 더한 부동소수점 값
```
    
여기서 i1은 120이라는 값을 갖습니다. 이는 'x'라는 문자의 ASCII 코드값(8비트 문자 집합)입니다. 이 방식은 문자의 숫자 표현(numeric representation)을 얻는 간단한 방법입니다.  
i2의 경우, 덧셈은 정수 연산(integer arithmetic)으로 수행되며, 결과는 1120입니다. 즉, char는 덧셈 전에 int로 승격(promoted)됩니다.  
마찬가지로, double과 int가 혼합된 연산에서는 int가 double로 승격되어 예상 가능한 결과(unexpected surprises 없는 결과)를 제공합니다. 따라서 d는 1127.3이라는 값을 갖습니다.  
변환은 두 가지 종류로 나뉩니다:
    
|종류|설명|
|:-:|:-:|
|확장 변환(widening)|정보를 보존하는 변환. 예: char → int|
|축소 변환(narrowing)|정보를 손실할 수 있는 변환. 예: int → char|

확장 변환(widening conversion)은 값을 동일한 값 또는 가장 근접한 값으로 변환하며, 대개 프로그래머에게 유익하고 코드 작성도 간편하게 해줍니다.  

불행히도, C++에서는 암시적 축소 변환(implicit narrowing conversion)도 허용됩니다. 축소 변환(narrowing)이란, 값이 다른 타입으로 변환되면서 원래 값과 같지 않게 되는 경우를 말합니다.  
예를 들어:  
char → int 변환은 축소 문제 없이 안전합니다.  
하지만 char는 작은 정수값만 저장 가능합니다.  
일반적으로:  
-char는 1바이트(8비트)  
-int는 4바이트(32비트)  
따라서 int 값을 char로 변환하면 값이 잘릴 수 있으며, 이로 인해 예상치 못한 결과나 오류가 발생할 수 있습니다.  

우리는 char에 1000 같은 큰 숫자를 넣을 수 없습니다. 이러한 변환은 축소 변환(narrowing conversion)이라고 하며, 값을 너무 작은 객체(“좁은” 공간)에 넣으려는 시도를 의미합니다.  
문제는, double → int, int → char 같은 축소 변환이 대부분의 컴파일러에서 기본적으로 허용된다는 점입니다. 왜 문제가 될까요?  
그 이유는, 축소 변환이 일어나고 있다는 사실을 종종 인지하지 못하기 때문입니다.  
예를 들어:  

```cpp
double x = 2.7;
// ... 많은 코드 ...
int y = x; // y는 2가 됨
```
이 시점에서 우리는 x가 double이었다는 사실을 잊었을 수도 있고, double → int 변환이 소수점 이하를 버리는(truncates) 방식이라는 것도 잊었을 수 있습니다. (즉, 0 방향으로 내림, 일반적인 반올림 규칙과 다름)  
y = x;는 정의된 동작(well-defined behavior)이지만, 정보(.7)가 손실된다는 사실을 코드가 알려주지 않습니다.  

역사적, 실용적 이유로 인해 C++에서는 네 가지 초기화 표기법(initialization syntax)을 제공합니다:  
```cpp
int x0 = 7.8;     // 축소 변환 발생, 일부 컴파일러는 경고
int x1 {7.8};     // 오류: {}는 축소 변환을 허용하지 않음
int x2 = {7.8};   // 오류: ={}도 축소 변환을 허용하지 않음
int x3 (7.8);     // 축소 변환 발생, 일부 컴파일러는 경고
```
= 및 ={} 표기법은 C 초기 시절부터 사용된 방식입니다.  
우리는 = 표기법을 단순 복사 초기화(copy initialization)에 사용하고, {} 및 ={} 표기법은 복잡한 초기화 또는 축소 방지 목적에 사용합니다.  
</details><!-- 변환(Conversions) -->

<details><summary>타입 유추: auto(Type deduction: auto)</summary>
예를 들어:  

```cpp
int x = 7;
double d = 7.7;
```
우리는 7이 정수이고 7.7이 부동소수점 숫자라는 것을 알고 있으며, 컴파일러도 그 사실을 알고 있습니다.  
그렇다면 왜 굳이 int와 double을 명시해야 할까요? 사실, 명시하지 않아도 됩니다. 초기화 값(initializer)의 타입을 기반으로 컴파일러가 타입을 유추(deduce)할 수 있습니다:  

```cpp
auto x = 7;     // x는 int (7이 정수이므로)
auto d = 7.7;   // d는 double (7.7이 부동소수이므로)
```
auto를 사용한 버전은 명시적 타입을 사용한 것과 정확히 동일한 의미를 갖습니다. 우리는 다음과 같은 경우에만 auto를 사용합니다:  
*초기화 값으로부터 타입이 명확하게 유추될 수 있을 때  
*타입 변환(conversion)을 원하지 않을 때  
특히, 긴 타입 이름을 사용할 때나 제네릭 프로그래밍(generic programming)에서는 auto의 표기 간결성(notational convenience)이 매우 유용합니다.

예:
```cpp
auto z = complex<double>{1.3, 3.4};
auto p = make_unique<Pair<string, int>>{"Harlem", 10027}; // unique_ptr<Pair<string,int>>
auto b = lst.begin(); // lst.begin은 vector<int>::iterator
```
</details><!-- 타입 유추: auto(Type deduction: auto) -->

<details><summary>질문과 대답 2</summary>
<details><summary>Q : prompt라는 용어는 무엇을 의미하는가?</summary>
A : </details>
<details><summary>Q : 객체를 초기화할 수 있는 표기법에는 어떤 것들이 있는가?</summary>
A : </details>
<details><summary>Q : 사용자로부터 정수 값을 입력받아 변수 number에 저장하려면, 어떤 두 줄의 코드를 작성할 수 있는가?</summary>
A : </details>
<details><summary>Q : \n은 무엇이라 불리며, 어떤 역할을 하는가?</summary>
A : </details>
<details><summary>Q : 문자열(string) 입력은 무엇에 의해 종료되는가?</summary>
A : </details>
<details><summary>Q : 정수(integer) 입력은 무엇에 의해 종료되는가?</summary>
A : </details>
<details><summary>Q : 다음 세 줄을 한 줄로 작성하면 어떻게 되는가?

```cpp
cout << "Hello, ";  
cout << first_name;  
cout << "!\n";
```  
</summary>
A : </details>
<details><summary>Q : 객체(object)란 무엇인가?</summary>
A : </details>
<details><summary>Q : 리터럴(literal)이란 무엇인가?</summary>
A : </details>
<details><summary>Q : 리터럴에는 어떤 종류들이 있는가?</summary>
A : </details>
<details><summary>Q : 변수(variable)란 무엇인가?</summary>
A : </details>
<details><summary>Q : char, int, double의 일반적인 크기는 얼마인가?</summary>
A : </details>
<details><summary>Q : 메모리에서 int나 string과 같은 작은 단위의 크기를 측정할 때 사용하는 기준은 무엇인가?</summary>
A : </details>

<details><summary>Q : =와 ==의 차이는 무엇인가?</summary>
A : </details>
<details><summary>Q : 정의(definition)란 무엇인가?</summary>
A : </details>
<details><summary>Q : 초기화(initialization)란 무엇이며, 대입(assignment)과 어떻게 다른가?</summary>
A : </details>

<details><summary>Q : 문자열 연결(string concatenation)이란 무엇이며, C++에서는 어떻게 구현하는가?</summary>
A : </details>
<details><summary>Q : int 타입에 적용할 수 있는 연산자(operator)에는 어떤 것들이 있는가?</summary>
A : </details>
<details><summary>Q : 다음 이름 중 C++에서 합법적인 이름은 무엇이며, 그렇지 않은 경우 그 이유는 무엇인가?
<br>이름 목록: This_little_pig,<br> This_1_is,<br> fine,<br> 2_For_1_special,<br> latest thing,<br> George@home,<br> _this_is_ok,<br> MineMineMine,<br> number,<br> correct?,<br> stroustrup.com,<br> $PATH<br>
</summary>
A : </details>
<details><summary>Q : 혼란을 유발할 수 있으므로 사용하지 말아야 할 합법적인 이름 다섯 가지를 제시하시오.</summary>
A : </details>
<details><summary>Q : 좋은 이름을 선택하기 위한 규칙에는 어떤 것들이 있는가?</summary>
A : </details>
<details><summary>Q : 타입 안전성(type safety)이란 무엇이며, 왜 중요한가?</summary>
A : </details>

<details><summary>Q : double에서 int로의 변환이 문제가 될 수 있는 이유는 무엇인가?</summary>
A : </details>

<details><summary>Q : 한 타입에서 다른 타입으로의 변환이 안전한지 여부를 판단하기 위한 규칙을 정의하시오.</summary>
A : </details>

<details><summary>Q : 바람직하지 않은 변환을 피하기 위한 방법에는 어떤 것들이 있는가?</summary>
A : </details>

<details><summary>Q : auto의 용도는 무엇인가?</summary>
A : </details>

</details><!-- 질문과 대답 2 -->

<details><summary>용어집(glossary) 2</summary>
assignment (대입)<br>
definition (정의)<br>
operation (연산)<br>
cin (표준 입력 스트림)  <br>
increment (증가)  <br>
operator (연산자)  <br>
concatenation (문자열 연결)<br>  
initialization (초기화)  <br>
type conversion (타입 변환)  <br>
name (이름)  <br>
type safety (타입 안전성)  <br>
declaration (선언)  <br>
narrowing (축소 변환)  <br>
value (값)  <br>
decrement (감소)<br>  
object (객체)  <br>
variable (변수)  <br>
widening (확장 변환) <br> 
truncation (절삭)  <br>
int (정수형)  <br>
double (부동소수점형)<br>  
string (문자열형)  <br>
auto (자동 타입 유추)  <br>
== (같음 비교 연산자)  <br>
!= (같지 않음 비교 연산자) <br> 
= (대입 연산자)  <br>
++ (전위/후위 증가 연산자)<br>  
< (작음 비교 연산자)<br>  
<= (작거나 같음 비교 연산자)  <br>
> (큼 비교 연산자)  <br>
>= (크거나 같음 비교 연산자)<br>  
</details><!-- 용어집(glossary) 2 -->
</details><!-- Day 2 /details -->

> [!TIP]
> 프로그래밍 재사용은 매우 흔한 기법입니다.새로운 문제를 해결할 때, 유사한 문제에 대한 기존 해결책을 찾아 수정하여 사용합니다. 정말 필요한 경우가 아니라면 처음부터 새로 시작하지 마세요. 기존 프로그램을 기반으로 수정하는 방식은 시간 절약에 매우 효과적이며, 원래 프로그램에 들인 노력의 혜택을 그대로 이어받을 수 있습니다.

