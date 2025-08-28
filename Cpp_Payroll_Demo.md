# 급여관리 시스템으로 배워보는 상속-가상함수

<details>
<summary>
<strong>급여관리 시스템 1 | 상속의 필요성과 상속의 기본 개념, 오버라이딩까지</strong>
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
<strong>급여관리 시스템2를 이해하기 위한 필요한 개념</strong><br>
+상속의 방법<br>
+상속받은 클래스의 생성자 정의<br>
+용어<br>
<talbe>
<tr>
	<th>상위 클래스</th> <th>&lt----></th> <th>하위 클래스(derived class)</th>
</tr>
<tr>
	<th>기초 클래스(base class)</th> <th>&lt----></th> <th>유도 클래스(derived class)</th>
</tr>
</table>

+Derived Class의 객체 생성과정: 유도 클래스의 객체생성 과정에서는 생성자가 두 번 호출된다. 하나는 기초 클래스의 생성자이고, 다른 하나는 유도 클래스의 생성자이다.

<br>+Derived Class 객체의 소멸과정: 유도 클래스의 소멸자가 진행되고 난 다음 기초 클래스의 소멸자가 실행된다. 이러한 객체소멸의 특성 때문에 상속과 연관된 클래스의 소멸자는 다음의 원칙을 지켜서 정의해야 한다. "생성자에서 동적 할당한 메모리 공간은 소멸자에서 해제한다."

<br>+상속을 위한 기본 조건 IS-A관계: 상속관계가 성립하려면 기초 클래스와 유도 클래스간에 IS-A 관계가 성립해야 한다. 예를들면 무선전화기는 전화기다. 노트북 컴퓨터는 컴퓨터다. 와 같은 표현이 성립되어야 한다. 그렇지 않다면 적절한 상속의 관계가 아닐 확률이 높다.

<br>+UML(Unified Modeling Language) : TabletNotebook ---> NotebookComp ---> Computer(화살표의 머리는 기초 클래스를 향하도록 표시해야 한다.)

<br>+객체 포인터 변수: 객체의 주소 값을 저장하는 포인터 변수<br> <strong>Person * ptr;<br>ptr=new Person();<br></strong> 실행시 ptr은 Person 객체를 가리키게 될 뿐 아니라 Person을 상속하는 유도 클래스(Derived class)의 객체도 가리킬 수 있다. <br><strong>"Cpp에서 AAA형 포인터 변수는 AAA객체 또는 AAA를 직접 혹은 간접적으로 상속하는 모든 객체를 가리킬 수 있다.(객체의 주소 값을 저장할 수 있다.)"</strong><br>

<br>+함수 오버라이딩(function overriding): 재정의(overriding)된 기초 클래스의 함수는 오버리이딩을 한 유도 클래스의 함수에 가려진다.<br><strong>PermanentWorker::getPay()</strong><br>오버라이딩 된 기초 클래스의 getPAY() 함수를 호출하는 구문이다. 클래스의 이름을 명시함으로 인해서 기초 클래스의 오버라이딩 된 함수를 호출할 수 있다.
</details>


<!--급여관리 시스템 2 -->

<details>
<summary>
<strong>급여관리 시스템 2 | 객체 포인터 변수,</strong>
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

<strong>급여관리 시스템4를 이해하기 위한 필요한 개념</strong><br>
+Base Class의 포인터로 객체를 참조할때 : C++ 컴파일러는 포인터 연산의 가능성 여부를 판단 할 때 포인터의 자료형을 기준으로 판단하지 실제 가리키는 객체의 자료형을 기준으로 판단하지 않는다.<br>Derived*dptr = new Derived();<br>Base * bptr = dptr;<br> <strong>"dptr은 Derived 클래스의 포인터 변수니까 이 포인터가 가리키는 객체는 분명 Base 클래스를 직접 혹은 간접적으로 상속하는 개체이다. 그러니 Base형 포인터 변수로도 참조가 가능하다."</strong><br>포인터 형에 해당하는 클래스에 정의된 멤버에만 접근이 가능하다. (추가내용 필요)
<br>+가상함수(Virtual Function) : 가상함수의 선언은 virtual 키워드의 선언을 통해서 이뤄진다. 가상함수가 선언되고 나면, 이 함수를 오버라이딩 하는 함수도 가상함수가 된다. 함수가 가상함수로 선언되면, 해당 함수호출 시 포인터의 자료형을 기반으로 호출대상을 결정하지 않고, 포인터 변수가 실제로 가리키는 객체를 참조하여 호출의 대상을 결정한다.




</details><!--급여관리 시스템 3 끝-->

<!--급여관리 시스템 4 -->

<details>
<summary>
<strong>급여관리 시스템 4</strong>
</summary>

>배열을 구성하는 포인터 변수가 Employee형 포인터 변수이므로, Employee 클래스의 멤버가 아닌 getPAY()와 ShowSalaryInfo()의 호출부분에서 컴파일 에러가 발생해서 주석처리 한 것 이다. Employee형 포인터 변수를 대상으로 이 두 함수를 호출 할 수 있도록 Employee클래스에 getPAY함수와 ShowSalaryInfo함수를 추가로 정의하고 가상함수로 선언해보자.
<br>

>

<pre><code class="language-cpp" style="font-size:16px;">
#pragma once

class Employee
{
private:
	char name[100];
public:
	Employee(char* name);
	void ShowNAME()const;
	virtual int getPAY() const;							// 직종마다 다른 임금체계를 갖고 있기 때문에 서로 다른 출력값을 유도클래스에서 
	virtual void ShowSalaryInfo() const;				// 재정의(override)할 수 있도록 가상함수로 선언함.
};
</code></pre>
<pre><code class="language-cpp" style="font-size:16px;">
#define _CRT_SECURE_NO_WARNINGS
#include "Employee.h"
#include<cstring>
#include <iostream>
using namespace std;

Employee::Employee(char* name) 							
{ strcpy(this->name, name); }

void Employee::ShowNAME()const 							
{ cout &lt&lt "이름: " &lt&lt name &lt&lt endl; }

int Employee::getPAY() const 							// Employee 클래스에서는 의미없는 값을 저장해도 된다. 순수 가상함수로 선언하는 것도 방법이다.
{ return 0; }

void Employee::ShowSalaryInfo() const {  }//Employee.cpp
</code></pre>
<pre><code class="language-cpp" style="font-size:16px;">
#include"Employee.h"
#include"EmployeeHandler.h"
#include"PermanentWorker.h"
#include"TemporaryWorker.h"
#include"SalesWorker.h"

int main(void)
{
	//핸들러 컨트롤러
	EmployeeHandler handler;

	//정규직 등록
	handler.AddEmployee(new PermanentWorker("Kim", 1000));
	handler.AddEmployee(new PermanentWorker("Lim", 3000));

	//임시직 등록
	TemporaryWorker* albamon = new TemporaryWorker("Jung", 699);
	albamon->AddWorkTime(5);
	handler.AddEmployee(albamon);

	//영업직 등록
	SalesWorker* seller = new SalesWorker("Hong", 1000, 0.1);
	seller->AddSalesResult(7000);
	handler.AddEmployee(seller);

	//이번 달에 지불해야 할 급여의 정보
	handler.ShowAllSalaryInfo();

	//이번 달에 지불해야 할 급여의 총합
	handler.ShowTotalSalary();

	return 0;
}

</code></pre>
</details><!--급여관리 시스템 4 끝-->

<details><!--급여관리 시스템 5 -->
<summary>급여관리 시스템 5 </summary>

<pre><code class="language-cpp" style="font-size:16px;">
#pragma once
class Employee
{
private:
	char name[100];
public:
	Employee(char*);
	virtual int getPAY()const = 0;
	virtual void ShowSalaryInfo()const = 0;
	void ShowNameInfo()const;
};//Employee.H
</code></pre>

<strong>순수 가상함수로 getPAY(), ShowSalaryInfo()를 선언했다. 순서 가상함수란 함수의 몸체가 정의되지 않는 함수를 의미한다. 위에서 보이듯 '0의 대입'을 표시하면 된다. 단순히 0을 대입한다는 의미가 아니고, 명시적으로 몸체를 정의하지 않았음을 컴파일러에게 알리는 것이다.</strong><br> 그리고 아래처럼 .cpp부분에서는 생략해도 된다.
<pre><code class="language-cpp" style="font-size:16px;">
#define _CRT_SECURE_NO_WARNINGS
#include "Employee.h"
#include &ltcstring>
#include&ltiostream>
using namespace std;
Employee::Employee(char*name){strcpy(this->name, name);}

void Employee::ShowNameInfo()const
{
	cout &lt&lt "이름: " &lt&lt name &lt&lt endl;
} // Employee.cpp
</code></pre>

<pre><code class="language-cpp" style="font-size:16px;">
#pragma once
#include"Employee.h"
class PermanentWorker:public Employee
{
private:
	int salary;
public:
	PermanentWorker(char* name, int money);
	int getPAY()const;
	void ShowSalaryInfo()const;
};//PermanentWorker.h
</code></pre><pre><code class="language-cpp" style="font-size:16px;">
#include "PermanentWorker.h"
#include"Employee.h"
#include&ltiostream>
using namespace std;

PermanentWorker::PermanentWorker(char* name, int money)
	:Employee(name), salary(money){}

int PermanentWorker::getPAY()const{return salary;}

void PermanentWorker::ShowSalaryInfo()const
{cout &lt&lt "salary: " &lt&lt getPAY() &lt&lt endl;}
</code></pre><pre><code class="language-cpp" style="font-size:16px;">
#pragma once
#include "PermanentWorker.h"

class SalesWorker:public PermanentWorker
{
private:
	double bonus;
	int SalesResult;
public:
	SalesWorker(char*name, int money, double ratio);
	int getPAY()const;
	void ShowSalaryInfo()const;
	void AddSalesResult(int value);
};//SalesWorker.h
</code></pre><pre><code class="language-cpp" style="font-size:16px;">
#include "SalesWorker.h"
#include "PermanentWorker.h"
#include&ltiostream>
using namespace std;

SalesWorker::SalesWorker(char* name, int money, double ratio)
	:PermanentWorker(name, money), SalesResult(0), bonus(ratio) { }

void SalesWorker::AddSalesResult(int value){SalesResult += value;}

int SalesWorker::getPAY()const
{
	return PermanentWorker::getPAY()
		+ (int)(SalesResult * bonus);
}

void SalesWorker::ShowSalaryInfo()const
{
	ShowNameInfo();
	cout &lt&lt "salary: " &lt&lt getPAY() &lt&lt endl;
}//SalesWorker.cpp
	
</code></pre><pre><code class="language-cpp" style="font-size:16px;">
#pragma once
#include"SalesWorker.h"

class ForeignSalesWorker :public SalesWorker
{
private:
	const int risk_level;
;public:
	ForeignSalesWorker(char* name, int money, double bonus, int risk);
	int getPAY()const;
	void ShowSalaryInfo()const;
	int getRISK()const;
}; //ForeignSalesWorker.h

</code></pre><pre><code class="language-cpp" style="font-size:16px;">
#include "ForeignSalesWorker.h"
#include"SalesWorker.h"
#include&ltiostream>
using namespace std;

ForeignSalesWorker::ForeignSalesWorker(char* name, int money, double bonus, int risk)
	:SalesWorker(name,money,bonus),risk_level(risk){}

int ForeignSalesWorker::getRISK()const
{
	return (int)((SalesWorker::getPAY()) * ((risk_level) / 100.0));
}

int ForeignSalesWorker::getPAY()const
{
	return SalesWorker::getPAY()+getRISK();
}
void ForeignSalesWorker::ShowSalaryInfo()const
{
	ShowNameInfo();
	cout &lt&lt"salary: "&lt&ltSalesWorker::getPAY()&lt&lt endl;
	cout &lt&lt"risk pay: "&lt&ltgetRISK()&lt&lt endl;
	cout&lt&lt"sum: "&lt&lt getPAY()&lt&lt endl&lt&ltendl;
}//	ForeignSalesWorker.cpp
</code></pre><pre><code class="language-cpp" style="font-size:16px;">
#pragma once
#include"Employee.h"
class TemporaryWorker:public Employee
{
private:
	int worktime;
	int payperhour;
public:
	TemporaryWorker(char* name, int pph);
	int getPAY()const;
	void ShowSalaryInfo()const;
	void AddWorkTime(int wt);
};//TemporaryWorker.h
</code></pre><pre><code class="language-cpp" style="font-size:16px;">
#include"Employee.h"
#include "TemporaryWorker.h"
#include &ltiostream>
using namespace std;

TemporaryWorker::TemporaryWorker(char* name, int pph)
	:Employee(name),worktime(0),payperhour(pph){}

int TemporaryWorker::getPAY()const {return worktime * payperhour;}

void TemporaryWorker::ShowSalaryInfo()const
{
	ShowNameInfo();
	cout &lt&lt "salary"&lt&ltTemporaryWorker::getPAY() &lt&lt endl;
}

void TemporaryWorker::AddWorkTime(int wt)
{worktime += wt;}
//TemporaryWorker.cpp
</code></pre><pre><code class="language-cpp" style="font-size:16px;">
#pragma once
#include"Employee.h"

class EmployeeHandler
{
private:
	Employee* empList[50];
	int empNum;
public:
	EmployeeHandler();
	void AddEmployee(Employee* emp);
	void ShowAllSalaryInfo()const;
	void ShowTotalSalaryInfo()const;
	~EmployeeHandler();
}; //EmployeeHandler.h

</code></pre><pre><code class="language-cpp" style="font-size:16px;">
#include "EmployeeHandler.h"
#include&ltiostream>
using namespace std;

EmployeeHandler::EmployeeHandler():empNum(0){}

void EmployeeHandler::AddEmployee(Employee* emp)
{empList[empNum++] = emp;}

void EmployeeHandler::ShowAllSalaryInfo()const
{
	for (int i = 0; i &lt empNum; i++)
		empList[i]->ShowSalaryInfo();
}

void EmployeeHandler::ShowTotalSalaryInfo()const
{
	int sum = 0;
	for (int i = 0; i &lt empNum; i++)
		sum += empList[i]->getPAY();
	cout &lt&lt "sum: " &lt&lt sum &lt&lt endl;
}

EmployeeHandler::~EmployeeHandler()
{
	delete[]empList;
}
//	EmployeeHandler.cpp
</code></pre><pre><code class="language-cpp" style="font-size:16px;">
#include"Employee.h"
#include"PermanentWorker.h"
#include"TemporaryWorker.h"
#include"SalesWorker.h"
#include"EmployeeHandler.h"
#include"ForeignSalesWorker.h"
#include"RISK_LEVEL.h"

int main(void)
{
	EmployeeHandler handler;

	ForeignSalesWorker* fseller1 = new ForeignSalesWorker
	("HONG", 1000, 0.1, RISK_LEVEL::RISK_A);
	fseller1->AddSalesResult(7000);
	handler.AddEmployee(fseller1);

	ForeignSalesWorker* fseller2 = new ForeignSalesWorker
	("YOON", 1000, 0.1, RISK_LEVEL::RISK_B);
	fseller2->AddSalesResult(7000);
	handler.AddEmployee(fseller2);

	ForeignSalesWorker* fseller3 = new ForeignSalesWorker
	("LEE", 1000, 0.1, RISK_LEVEL::RISK_C);
	fseller3->AddSalesResult(7000);
	handler.AddEmployee(fseller3);

	handler.ShowAllSalaryInfo();
	return 0;
}


	
</code></pre>
 
</details>
