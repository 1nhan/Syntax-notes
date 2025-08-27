# 급여관리 시스템으로 배워보는 상속-가상함수

<details>
<summary>
<strong>급여관리 시스템 1</strong>
</summary>

<pre><code class="language-cpp" style="font-size:16px;">
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

<pre><code class="language-cpp" style="font-size:16px;">
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


<pre><code class="language-cpp" style="font-size:16px;">
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


<pre><code class="language-cpp" style="font-size:16px;">
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


<pre><code class="language-cpp" style="font-size:16px;">
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
>위 프로그램은 프로그램의 유연성이나 확장성의 확보가 쉽지 않다.<br>
>영업직 클래스와 임시직 클래스를 추가하고, 영업직 객체와 임시직 객체의 저장을 위한 배열을 추가하고 각각 배열에 저장된 객체의 수를 별도로 세어보고, 정수형 변수도 멤버로 추가하는 등, 많은 것들을 바꿔줘야 한다. 또 addEMPLOYEE함수는 영업직용과 임시직 객체용을 각각 추가하고, 급여정보를 출력하는 나머지 두 멤버함수는 총 3개의 배열을 대상으로 연산을 진행하고, 반복문이 추가로 각각 두 개씩 더 삽입해야 한다. 결과적으로 확장하려면 다시 만들어야해서 위 코드는 확장성에 있어 좋지 못하다.
------------

>요구조건에 맞게 급여관리 시스템 2로 변경해보자.<br>>직원 고용형태가 '정규직(PermanentWorker)'하나였지만 영업직(Sales), 임시직(Temporary)등 등장했다.영업직(Sales)는 기본급여+인센티브를, 임시직(Temporary)에는 시간당 급여 x 일한 시간의 급여 계산방식이 적용이 된다.

</details>


<!--급여관리 시스템 2 -->

<details>
<summary>
<strong>급여관리 시스템 2</strong>
</summary>

[상속 관계 구조]
>SalesWorker --> PermanentWorker --> Employee<br>
>TemporaryWorker --> Employee<br>
>EmployeeHandler 클래스가 저장 및 관리하는 대상이 Employee 객체가 되면 이후에 Employee클래스를 직접 혹은 간접적으로 상속하는 클래스가 추가되었을때, EmployeeHandler클래스에는 변화가 발생하지 않는다.

>EmployeeHandler 클래스가 저장 및 관리하는 대상이 Employee 객체가 되면 이후에 Employee클래스를 직접 혹은 간접적으로 상속하는 클래스가 추가되었을때, EmployeeHandler클래스에는 변화가 발생하지 않는다.


</table>
<pre><code class="language-cpp" style="font-size:16px;">
#pragma once
class Employee									//Base Class		
{
private:
	char name[100];
public:
	Employee(char* name);						//Constructor
	void showNAME()const;						//멤버변수 출력 함수
};//Employee.h
</code></pre>

<pre><code class="language-cpp" style="font-size:16px;">
#pragma once
#include "Employee.h"
class PermanentWorker:public Employee			//Derived Class
{
private:
	int salary;
public:
	PermanentWorker(char* name, int money);		//Constructor
	int getPAY()const;							//Access Function, getter
	void showSALARYinfo()const;					//멤버변수 출력 함수
}; //PermanentWorker.h
</code></pre>

<pre><code class="language-cpp" style="font-size:16px;">
#pragma once
#include"Employee.h"
class EmployeeHandler							//Control Class
{
private:
	Employee* empLIST[50];						//Employee 객체의 주소 값을 저장하는 방식으로 객체에 저장
	int empNUM;									//empLIST[]에 Len을 위한 변수 선언
public:
	EmployeeHandler();							//Constructor, 멤버변수 초기화 목적
	void AddEmployee(Employee* emp);			//직원 등록
	void ShowAllSalaryiInfo()const;				//직원 급여정보를 보기위한 함수
	void ShowTotalSalary()const;				//직원 급여 총합계를 보기위한 함수
	~EmployeeHandler();							//Destructor
};//EmployeeHandler.h
</code></pre>

<pre><code class="language-cpp" style="font-size:16px;">
#define _CRT_SECURE_NO_WARNINGS
#include "Employee.h"
#include&ltcstring>
#include&ltiostream>
using namespace std;

Employee::Employee(char* name)
{
	strcpy(this->name, name);
}
void Employee::showNAME()const
{
	cout &lt&lt"이름: "&lt&ltname &lt&lt endl;
}//Employee.cpp
</code></pre>

<pre><code class="language-cpp" style="font-size:16px;">
#include "PermanentWorker.h"
#include &ltcstring>
#include &ltiostream>
using namespace std;

PermanentWorker::PermanentWorker(char* name, int money)
	:Employee(name),salary(money)
{}
int PermanentWorker::getPAY()const
{
	return salary;
}
void PermanentWorker::showSALARYinfo()const
{
	showNAME();
	cout &lt&lt "SALARY: " &lt&lt getPAY() &lt&lt endl&lt&ltendl;
}//PermanentWorker.cpp
</code></pre>

<pre><code class="language-cpp" style="font-size:16px;">
#include "EmployeeHandler.h"
#include&ltcstring>
#include&ltiostream>
using namespace std;
EmployeeHandler::EmployeeHandler():empNUM(0)
{}
void EmployeeHandler::AddEmployee(Employee* emp)
{
	empLIST[empNUM++] = emp;
}
void EmployeeHandler::ShowAllSalaryiInfo()const
{
	//for (int i = 0; i &lt empNUM; i++)
	//	empLIST[i]->showSALARYinfo();
}
void EmployeeHandler::ShowTotalSalary()const
{
	int sum = 0;
	//for (int i = 0; i &lt empNUM; i++)
	//	sum+=empLIST[i]->getPAY();
	cout &lt&lt "salary sum: " &lt&lt sum &lt&lt endl;
}
EmployeeHandler::~EmployeeHandler()
{
	for (int i = 0; i &lt empNUM; i++)
		delete empLIST[i];
}//EmployeeHandler.cpp
</code></pre>
<pre><code class="language-cpp" style="font-size:16px;">
#include"Employee.h"
#include"EmployeeHandler.h"
#include"PermanentWorker.h"

int main(void)
{
	
	/* 
	직원 관리를 목적으로 설계된 컨트롤 클래스의 객체생성
	Employee객체의 주소 값을 저장하는 방식으로 객체 저장한다.
	Employee 클래스를 상속하는 클래스의 객체도 이 배열에 저장이 가능하다.*/
	EmployeeHandler handler;

	//직원 등록
	handler.AddEmployee(new PermanentWorker("Kim", 1000));
	handler.AddEmployee(new PermanentWorker("Lim", 3000));
	handler.AddEmployee(new PermanentWorker("Jun", 2500));
	
	//이번 달에 지불해야 할 급여의 정보
	handler.ShowAllSalaryiInfo();
	
	//이번 달에 지불해야 할 급여의 총합
	handler.ShowTotalSalary();

	return 0;
}
</code></pre>

</details><!--급여관리 시스템 2 끝-->

<!--급여관리 시스템 3 -->

<details>
<summary>
<strong>급여관리 시스템 3</strong>
</summary>

<table>
<tr>
<th>고용형태</th><th>급여계산</th>
</tr>
<tr>
<th>PermanentWorker</th><th>기본급여</th>
</tr>
<tr>
<th>TemporaryWorker</th><th>시간당급여x일한시간</th>
</tr>
<tr>
<th>SalesWorker</th><th>기본급여+인센티브(bonus)</th>
</tr>
</table>

<pre><code class="language-cpp" style="font-size:16px;">
/*SalesWorker*/
#pragma once
#include"PermanentWorker.h"
class SalesWorker :public PermanentWorker				//Derived Class -> PermanentWorker (Base Class)
{
private:												//m_value 기본급여와 인센티브를 위한 멤버선언
	int salesResult;			
	double bonusRatio;			
public:
	SalesWorker(char* name, int money, double ratio);	//Constructor
	void AddSalesResult(int value);						//인센티브
	int getPAY()const;									//Access Function getter(Function Overriding)
	void ShowSalaryInfo()const;							//출력 함수				(Function Overriding)
};//SalesWorker.h
</code></pre>

<pre><code class="language-cpp" style="font-size:16px;">
/*TemporaryWorker*/
#pragma once
#include "Employee.h"
class TemporaryWorker :public Employee					//Derived Class -> Employee (Base Class)
{
private:												// 시간당급여x일한시간을 위한 멤버변수선언
	int worktime;
	int payperhour;
public:
	TemporaryWorker(char* name, int pay);				//Constructor
	void AddWorkTime(int time);							//일한시간 합계를 위한 함수
	int getPAY()const;									//Access Function getter(Function Overriding) 
	void ShowSalaryInfo()const;							//출력 함수				(Function Overriding)
};//TemporaryWorker.h

</code></pre>

<pre><code class="language-cpp" style="font-size:16px;">
/*SalesWorker*/
#include "SalesWorker.h"
#include&ltiostream>
using namespace std;

SalesWorker::SalesWorker(char* name, int money, double ratio)
	:PermanentWorker(name, money), salesResult(0), bonusRatio(ratio){}	//이니셜라이즈 Base Class로 name,money를 초기화,
																		//멤버변수 salesResult를 0으로 초기화, bonusRatio에 ratio초기화
void SalesWorker::AddSalesResult(int value){salesResult += value;}		//매게변수 value를 0으로 초기화되었던 salesResult에 합산시키는 함수

int SalesWorker::getPAY()const											//Access Function getter
{
	return PermanentWorker::getPAY()									//오버라이딩된 기초함수(PermanentWorker)를 호출하는 방식
		+ (int)(salesResult * bonusRatio);								//double형 bonusRatio의 결과를 int로 형변환(type casting)
}
void SalesWorker::ShowSalaryInfo()const									//오버라이딩된 함수
{
	showNAME();															//BaseClass에 showName()함수 호출후 출력(showName은 출력함수)
	cout &lt&lt "salary: " &lt&lt getPAY() &lt&lt endl &lt&lt endl;		//클래스내 getPAY()출력
}//SalesWorker.cpp

</code></pre>

<pre><code class="language-cpp" style="font-size:16px;">
/*TemporaryWorker*/
#include "TemporaryWorker.h"	
#include&ltiostream>
using namespace std;

TemporaryWorker::TemporaryWorker(char* name, int pay)					//TemporaryWorker클래스는 PermanentWorker 클래스와 유사함.
	:Employee(name), worktime(0), payperhour(pay){}

void TemporaryWorker::AddWorkTime(int time){worktime += time;}

int TemporaryWorker::getPAY()const{return worktime * payperhour;}

void TemporaryWorker::ShowSalaryInfo()const
{
	showNAME();
	cout &lt&lt "salary: " &lt&lt getPAY() &lt&lt endl &lt&lt endl;
}

</code></pre>

</details><!--급여관리 시스템 3 끝-->
