# 멤버함수와 가상함수의 동작원리

<details><summary><strong>객체 안에 정말로 멤버함수가 존재하는가</strong></summary>

<pre><code class="language-cpp" style="font-size:16px;">
#include&lt;iostream>
using namespace std;

class Data
{
private:
	int data;
public:
	Data(int num):data(num){}
	void ShowData() { cout &lt;&lt; "Data: " &lt;&lt; data &lt;&lt; endl; }
	void Add(int num) { data += num; }
};

int main(void)
{
	Data obj(15);
	obj.Add(17);
	obj.ShowData();
	
	return 0;
}
</code></pre>
<strong>C언어 스타일의 구조체와 전역함수를 이용해서 흉내내 구현한 아래 예제</strong>
<pre><code class="language-cpp" style="font-size:16px;">
typedef struct Data
{
	int data;
	void (*ShowData)(Data*);		// 함수 포인터 변수는 void ShowData(Data* THIS) {}의 주소 값을 저장하기 위함
	void(*Add)(Data*, int);			// 함수 포인터 변수는 void Add(Data* THIS, int num) {}의 주소 값을 저장하기 위함
}Data;
void ShowData(Data* THIS) { cout&lt;&lt;"Data: "&lt;&lt;THIS->data &lt;&lt; endl; }	//
void Add(Data* THIS, int num) { THIS->data += num; }								//
int main(void)
{
	Data obj1 = { 15, ShowData,Add };
	Data obj2 = { 7, ShowData,Add };
	obj1.Add(&obj1, 17);
	obj2.Add(&obj2, 9);
	obj1.ShowData(&obj1);
	obj2.ShowData(&obj2);
	return 0;
}
</code></pre>
Data obj1 = { 15, ShowData,Add };<br>
			data = 15<br>
			void (*ShowData)(Data*)	----> 	void ShowData(Data*THIS){}<br>
			VOID (*Add)(Data*,int)	---->	void Add(Data*THIS,int num){THIS->data+=num;}<br>

Data obj2 = { 7, ShowData,Add };<br>
			data = 7<br>
   			void (*ShowData)(Data*)	----> 	void ShowData(Data*THIS){}<br>
			VOID (*Add)(Data*,int)	---->	void Add(Data*THIS,int num){THIS->data+=num;}<br>

<strong>[obj1과 obj2의 구성]</strong><br>

위의 핵심은 두 개의 구조체 변수(객체)가 함수를 공유하고 있다는 사실이다. C++의 객체와 멤버함수는 이러한 관계를 갖는다.
<strong>객체가 생성되면 멤버변수는 객체 내에 존재하지만, 멤버함수는 메모리의 한 공간에 별도로 위치하고선 이 함수가 정의된 클래스의 모든 객체가 이를 공유하는 형태를 취한다.</strong>
</details>

<details><summary><strong>가상함수 테이블이 참조되는 방식</strong></summary>
<pre><code class="language-cpp" style="font-size:16px;">
#include&lt;iostream>
using namespace std;
class AAA
{
private:
	int num1;
public:
	virtual void Func1() { cout&lt;&lt;"Func1" &lt;&lt; endl; }
	virtual void Func2() { cout&lt;&lt;"Func2" &lt;&lt; endl; }
};
class BBB :public AAA
{
private:
	int num2;
public:
	virtual void Func1() { cout &lt;&lt;"BBB::Func1" &lt;&lt; endl; }
	void Func3() { cout &lt;&lt;"Func3" &lt;&lt; endl; }
};
int main(void)
{
	AAA* aptr = new AAA();
	aptr->Func1();
	BBB* bptr = new BBB();
	bptr->Func1();
	return 0;
}
</code></pre>
한 개 이사으이 가상함수를 포함하는 클래스에 대해서는 컴파일러가 다음 도표와 같은 형태의 '가상함수 테이블'이란 것을 만든다. 이를 간단히 'V-Table(Virtual Table)'이라고도 하고 실제 호출되어야 할 함수의 위치정보를 담고 있는 테이블이다.
<table>
 <tr>
	 <th>key</th><th>value</th>
 </tr>
 <tr>
	 <th>void AAA::Func1()</th><th>0x1024번지</th>
 </tr>
 <tr>
	 <th>void BBB::Func2()</th><th>0x2048번지</th>
 </tr>
</table>
<strong>[AAA클래스의 가상함수 테이블]</strong>
key는 호출하고자 하는 함수를 구분지어주는 구분자의 역할을 하고 value는 구분자에 해당하는 함수의 주소정보를 알려주는 역할을 한다. 그래서 AAA 객체의 Func1 함수를 호출해야 할 경우, 위의 테이블에 첫 번째 행의 정보를 참조하여, 0x1024번지에 등록되어 있는 Func1 함수를 호출하게 되는 것이다.
<table>
 <tr>
	 <th>key</th><th>value</th>
 </tr>
 <tr>
	 <th>void BBB::Func1()</th><th>0x3072번지</th>
 </tr>
 <tr>
	 <th>void AAA::Func2()</th><th>0x2048번지</th>
 </tr>
 <tr>
	 <th>void BBB::Func3()</th><th>0x4096번지</th>
 </tr>
</table>
<strong>[BBB클래스의 가상함수 테이블]</strong>
위의 가상함수 테이블을 보면<br><strong>"AAA클래스의 오버라이딩 된 가상함수 Func1에 대한 정보가 존재하지 않는다."</strong><br> 오버라이딩 된 가상함수의 주소정보는 유도 클래스의 가상함수 테이블에 포함되지 않는다. 때문에 오버라이딩 된 가상함수를 호출하면, 무조건 가장 마지막에 오버라이딩을 한 유도 클래스의 멤버함수가 호출되는 것이다. 
</details>
