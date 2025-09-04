# Programs Common Sense (CPP)

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
<details><sumaary>Q : "Hello, World!" 프로그램의 목적은 무엇인가요?</summary>
A : </details>
<details><sumaary>Q : 함수의 네 가지 구성 요소를 말해보세요.</summary>
A : </details>
<details><sumaary>Q : 모든 C++ 프로그램에 반드시 포함되어야 하는 함수는 무엇인가요?</summary>
A : </details>
<details><sumaary>Q : "Hello, World!" 프로그램에서 return 0;의 목적은 무엇인가요?</summary>
A : </details>
<details><sumaary>Q : 컴파일러의 역할은 무엇인가요?</summary>
A : </details>
<details><sumaary>Q : import 문장의 목적은 무엇인가요?</summary>
A : </details>
<details><sumaary>Q : #include 지시문의 목적은 무엇인가요?</summary>
A : </details>
<details><sumaary>Q : 파일 이름 끝의 .cpp 확장자는 C++에서 무엇을 의미하나요?</summary>
A : </details>
<details><sumaary>Q : 링커(linker)는 프로그램에서 어떤 역할을 하나요?</summary>
A : </details>
<details><sumaary>Q : 소스 파일(source file)과 오브젝트 파일(object file)의 차이는 무엇인가요?</summary>
A : </details>
<details><sumaary>Q : 실행 파일(executable)이란 무엇인가요?</summary>
A : </details>
<details><sumaary>Q : IDE란 무엇이며, 어떤 기능을 제공하나요?</summary>
A : </details>
<details><sumaary>Q : 컴파일된 프로그램을 실행하려면 어떻게 해야 하나요?</summary>
A : </details>
<details><sumaary>Q : 주석(comment)이란 무엇인가요?</summary>
A : </details>
</details>
</details>
