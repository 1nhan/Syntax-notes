# Cpp
>Cpp학습 카테코리 정리<br>
>Google Docs      https://docs.google.com/document/d/1Lf5LPqnNvNzQABAKtOLZ1DJLLt6IWisBUlVqftEDTgM/edit?tab=t.v1diwsp23tj9 <br>
>Google Sheets    ? <br>
 ------------
<details><summary>학습 일지</summary>
2025-08-22 <details><summary>const 함수에 대해</summary>

const int num = 10;		//	변수를 상수화
const SoSimple sim(20);	//	객체를 상수화	

객체를 대상으로는 const 멤버함수만 호출이 가능하다. 변경시킬 능력이 있는 함수는 아예 호출을 허용하지 않는다.<br>
멤버변수에 저장된 값을 수정하지 않는 함수는 가급적 const로 선언해서, 객체에서도 호출이 가능하도록 할 필요가 있다.<br>
</details>
<details><summary>const 함수 오버로딩</summary>
<pre><code class = "language-cpp">
void numLock() {}
void numLock() const {} // const의 선언 유무도 함수 오버로딩의 조건에 해당된다.
 
</code></pre>
</details>

2025-08-23 상속(Inheritance) <br>
상속에 들어가기에 앞서, 상속의 문법적인 이해 <br>
2025-08-24 일요일 <br>
2025-08-25 상속(Inheritance) <br>
protected 선언과 세 가지 형태의 상속, 상속을 위한 조건, OOP 단계별 프로젝트 05 <br>
2025-08-26 객체 포인터의 참조관계 <br>
객체 포인터 변수, 함수 오버라이딩, IS-A, HAS-A <br>
2025-08-27 가상함수(Virtual Function) <br>
가상함수, 가상소멸자와 참조자의 참조 가능성, Employee 예제와 문제, Employee 1-4, Quiz에 대한 분석 <br>
</details>
<details>
<summary>
<h3>객체지향의 전개</h3>
</summary>

<details>
<summary>
<strong>급여관리 시스템 1</strong>
</summary>

<pre><code class="language-cpp">
#pragma once
class PermanentWorker
{
private:
	char name[100];
	int salary;
public:
	PermanentWorker(char* name, int money);	// Constructor
	int getPAY()const;						// Access Function
	void showSALARYinfo()const;				// Display Function
};//PermanentWorker.h
</code></pre><!--PermanentWorker.h-->
this->name 정적 할당으로 선언되어있다.

<pre><code class="language-cpp">
#pragma once
#include"PermanentWorker.h"
class EmployeeHandler						//Control(=handler) Class
{
private:
	PermanentWorker* empList[50];			//PermanentWorker Object로 PermanentWorker에 접근
	int empNUM;								//empList에 배열 순서를 저장하기 위한 변수
public:
	EmployeeHandler();						//Constructor
	void addEMPLOYEE(PermanentWorker* emp);	//직원 등록을 위한 클래스
	void showALLSALARYinfo()const;			//직원 급여정보를 보기위한 클래스
	void showTOTALSALARY()const;			//지불할 직원 급여 총합을 보기위한 클래스
	~EmployeeHandler();						//동적 할당으로 생성된 empList를 제거하기 위한 Destructor
};//EmployeeHandler.h
</code></pre><!--EmployeeHandler.h-->


<pre><code class="language-cpp">
#define _CRT_SECURE_NO_WARNINGS
#include "PermanentWorker.h"
#include <cstring>
#include <iostream>
#include "EmployeeHandler.h"
using namespace std;

PermanentWorker::PermanentWorker(char* name, int money)
	:salary(money) {strcpy(this->name, name);}			

int PermanentWorker::getPAY()const { return salary; }

void PermanentWorker::showSALARYinfo()const
{
	cout << "name: " << name << endl;
	cout << "salary: " << salary<< endl;
}//PermanentWorker.cpp
</code></pre>


<pre><code class="language-cpp">
#include "EmployeeHandler.h"
#include <iostream>
using namespace std;
EmployeeHandler::EmployeeHandler():empNUM(0){}

void EmployeeHandler::addEMPLOYEE(PermanentWorker* emp)
{
	empList[empNUM++] = emp;
}

void EmployeeHandler::showALLSALARYinfo()const
{
	for (int i = 0; i < empNUM; i++)
		empList[i]->showSALARYinfo();
}
void EmployeeHandler::showTOTALSALARY()const
{
	int sum = 0;
	for (int i = 0; i < empNUM; i++)
		sum += empList[i]->getPAY();
	cout << "sum: " << sum << endl;
}
EmployeeHandler::~EmployeeHandler()
{
	for (int i = 0; i < empNUM; i++)
		delete empList[i];
}//EmployeeHandler.cpp
</code></pre>


<pre><code class="language-cpp">
#include"EmployeeHandler.h"
#include"PermanentWorker.h"

int main(void)
{
	/*직원관리 목적으로 설계된 컨트롤 클래스의 객체 생성*/
	EmployeeHandler handler;

	/*직원 등록*/
	handler.addEMPLOYEE(new PermanentWorker("KIM", 1000));
	handler.addEMPLOYEE(new PermanentWorker("Lee", 1500));
	handler.addEMPLOYEE(new PermanentWorker("Jun", 2000));

	/*이번달 급여 정보*/
	handler.showALLSALARYinfo();

	/*이번달 지불해야할 급여의 총합*/
	handler.showTOTALSALARY();

	return 0;
}
</code></pre>

</details>

<details>
<summary>
<strong>급여관리 시스템 2</strong>
</summary>


<pre><code class="language-cpp">

</code></pre>

<pre><code class="language-cpp">

</code></pre>

<pre><code class="language-cpp">

</code></pre>


</details>


<details>
<summary>
<strong>급여관리 시스템 3</strong>
</summary>



<pre><code class="language-cpp">

</code></pre>

<pre><code class="language-cpp">

</code></pre>

<pre><code class="language-cpp">

</code></pre>

</details>


<details>
<summary>
<strong>급여관리 시스템 4</strong>
</summary>


<pre><code class="language-cpp">

</code></pre>

<pre><code class="language-cpp">

</code></pre>

<pre><code class="language-cpp">

</code></pre>

</details>


<details>
<summary>
<strong>급여관리 시스템 5</strong>
</summary>


<pre><code class="language-cpp">

</code></pre>

<pre><code class="language-cpp">

</code></pre>

<pre><code class="language-cpp">

</code></pre>

</details>


<details>
<summary>
<strong></strong>
</summary>


<pre><code class="language-cpp">

</code></pre>

<pre><code class="language-cpp">

</code></pre>

<pre><code class="language-cpp">

</code></pre>

</details>

<details>
<summary>
<strong></strong>
</summary>


<pre><code class="language-cpp">

</code></pre>

<pre><code class="language-cpp">

</code></pre>

<pre><code class="language-cpp">

</code></pre>

</details>


</details><!--끝 -->
