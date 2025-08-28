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
	void (*ShowData)(Data*);		// 함수 포인터 변수
	void(*Add)(Data*, int);			// 함수 포인터 변수
}Data;
void ShowData(Data* THIS) { cout&lt;&lt;"Data: "&lt;&lt;THIS->data &lt;&lt; endl; }
void Add(Data* THIS, int num) { THIS->data += num; }
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
</details>
<table>
 <tr>obj1객체</tr>
 <tr>data=15</tr>
 <tr>void(*ShowData)(Data*)</tr>
 <tr>void (*Add)(Data*,int)</tr>
</table>
