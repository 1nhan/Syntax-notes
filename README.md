# 멤버함수와 가상함수의 동작원리

<details><summary><strong></strong></summary>

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

</details>
