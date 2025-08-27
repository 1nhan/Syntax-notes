# Object-Oriented


<details>
<summary>
<h3>상속(Inheritance)</h3>
</summary>

<details>
<summary>
<strong>급여관리 시스템 1</strong>
</summary>

<pre><code class="language-cpp" style="font-size:16px;>
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

<pre><code class="language-cpp" style="font-size:16px;>
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


<pre><code class="language-cpp" style="font-size:16px;>
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


<pre><code class="language-cpp" style="font-size:16px;>
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


<pre><code class="language-cpp" style="font-size:16px;>
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

<details>
<summary>
<strong>급여관리 시스템 2</strong>
</summary>
[상속구조]<br>
>근로자(Employee) <- 정규직(PermanentWorker) <- 영업직(SalesWorker)<br>
>근로자(Employee) <- 임시직(TemporaryWorker)<br>

<table border="1">
<tr>
<th>고용형태</th><th>임금방식</th>
</tr>
<tr>
<th>근로자(Employee)</th><th>Base Class</th>
</tr>
<tr>
<th>정규직(PermanentWorker)</th><th>기본급여</th>
</tr>
<tr>
<th>임시직(TemporaryWorker)</th><th>시간급여x일한시간</th>
</tr>
<tr>
<th>영업직(Sales)</th><th>기본급여x인센티브</th>
</tr>
</table><!--테이블-->


<pre><code class="language-cpp" style="font-size:16px;>
#pragma once
class EMPLOYEE
{
private:
	char name[100];
public:
	EMPLOYEE(char* name);
	void showNAME()const;
};//EMPLOYEE.h
</code></pre>

<pre><code class="language-cpp" style="font-size:16px;>
#pragma once
#include "Employee.h"
class PermanentWorker:public Employee
{
private:
	int salary;
public:
	PermanentWorker(char* name, int money);
	int getPAY()const;
	void showSALARYinfo()const;
}; //PermanentWorker.h
</code></pre>


<pre><code class="language-cpp" style="font-size:16px;>
#pragma once
#include"PermanentWorker.h"
class SalesWorker:public PermanentWorker
{
private:
	int salesResult;
	double bonusRatio;
public:
	SalesWorker(char* name, int money, double ratio);
	void AddSalesResult(int value);
	int getPAY()const;
	void showSALARYinfo()const;
};//SalesWorker.h
</code></pre>


<pre><code class="language-cpp" style="font-size:16px;>
#pragma once
#include "Employee.h"
class TemporaryWorker:public Employee
{
private:
	int worktime;
	int payperhour;
public:
	TemporaryWorker(char*name,int pay);
	void AddWorkTime(int time);
	int getPAY()const;
	void showSALARYinfo()const;
};//TemporaryWorker.h
</code></pre>


<pre><code class="language-cpp" style="font-size:16px;>
#pragma once
#include"Employee.h"
class EmployeeHandler				//Control Class
{
private:
	Employee* empLIST[50];
	int empNUM;
public:
	EmployeeHandler();
	void AddEmployee(Employee* emp);
	void ShowAllSalaryiInfo()const;
	void ShowTotalSalary()const;
	~EmployeeHandler();
};//EmployeeHandler.h
</code></pre>


<pre><code class="language-cpp" style="font-size:16px;>
#define _CRT_SECURE_NO_WARNINGS
#include "Employee.h"
#include<cstring>
#include <iostream>
using namespace std;

Employee::Employee(char* name)
{
	strcpy(this->name, name);
}
void Employee::showNAME()const
{
	cout <<"이름: "<<name << endl;
}//Employee.cpp
</code></pre>


<pre><code class="language-cpp" style="font-size:16px;>
#include "PermanentWorker.h"
#include<cstring>
#include <iostream>
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
	cout << "SALARY: " << getPAY() << endl<<endl;
}//PermanentWorker.cpp
</code></pre>


<pre><code class="language-cpp" style="font-size:16px;>
#include "SalesWorker.h"
#include<iostream>
using namespace std;

SalesWorker::SalesWorker(char* name, int money, double ratio)
	:PermanentWorker(name, money), salesResult(0), bonusRatio(ratio)
{}
void SalesWorker::AddSalesResult(int value)
{
	salesResult += value;
}
int SalesWorker::getPAY()const
{
	return PermanentWorker::getPAY() 
		+ (int)(salesResult * bonusRatio);
}
void SalesWorker::showSALARYinfo()const
{
	showNAME();
	cout <<"salary: "<<getPAY() << endl << endl;
}//SalesWorker.cpp
</code></pre>


<pre><code class="language-cpp" style="font-size:16px;>
#include "TemporaryWorker.h"
#include<iostream>
using namespace std;

TemporaryWorker::TemporaryWorker(char* name, int pay)
	:Employee(name),worktime(0), payperhour(pay)
{}
void TemporaryWorker::AddWorkTime(int time)
{
	worktime += time;
}
int TemporaryWorker::getPAY()const
{
	return worktime * payperhour;
}
void TemporaryWorker::showSALARYinfo()const
{
	showNAME();
	cout << "salary: " << getPAY() << endl << endl;
}//TemporaryWorker.cpp
</code></pre>


<pre><code class="language-cpp" style="font-size:16px;>

#include "EmployeeHandler.h"
#include<cstring>
#include <iostream>
using namespace std;
EmployeeHandler::EmployeeHandler():empNUM(0)
{}
void EmployeeHandler::AddEmployee(Employee* emp)
{
	empLIST[empNUM++] = emp;
}
void EmployeeHandler::ShowAllSalaryiInfo()const
{
	//for (int i = 0; i < empNUM; i++)
	//	empLIST[i]->showSALARYinfo();
}
void EmployeeHandler::ShowTotalSalary()const
{
	int sum = 0;
	//for (int i = 0; i < empNUM; i++)
	//	sum+=empLIST[i]->getPAY();
	cout << "salary sum: " << sum << endl;
}
EmployeeHandler::~EmployeeHandler()
{
	for (int i = 0; i < empNUM; i++)
		delete empLIST[i];
}//EmployeeHandler.cpp
</code></pre>


<pre><code class="language-cpp" style="font-size:16px;>

#include"Employee.h"
#include"EmployeeHandler.h"
#include"PermanentWorker.h"

int main(void)
{
	//직원 관리를 목적으로 설계된 컨트롤 클래스의 객체 생성
	EmployeeHandler handler;

	//직원 등록
	handler.AddEmployee(new PermanentWorker("Kim", 1000));
	handler.AddEmployee(new PermanentWorker("Lim", 3000));
	handler.AddEmployee(new PermanentWorker("Jun", 2500));
	
	//이 달에 지불할 급여의 정보
	handler.ShowAllSalaryiInfo();
	
	//이 달에 지불 할 급여의 총합
	handler.ShowTotalSalary();

	return 0;
}
</code></pre>

</details><!--급여관리시스템2 끝-->



</details><!--끝 -->
