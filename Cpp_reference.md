# <strong>C++ 의 참조자 (reference)</strong>
C++ 에서는 다른 변수나 상수를 가리키는 방법으로 또 다른 방식을 제공하는데, 이를 바로 참조자(레퍼 런스 - reference) 라고 부릅니다<br>
<pre><code class="language-cpp" style="font-size:16px;">
#include &lt;iostream>

int main() 
{ 
int a = 3;
int& another_a = a; //가리키고자 하는 타입 뒤에 & 를 붙이면 됩니다
another_a = 5; 

std::cout &lt;&lt; "a : " &lt;&lt; a &lt;&lt; std::endl; 
std::cout &lt;&lt; "another_a : " &lt;&lt; another_a &lt;&lt; std::endl; return 0; 
} 
</code></pre><br>
int a = 3; <br>
먼저 우리는 위와 같이 간단히 int 형 변수인 a 를 정의하였고 그 안에 3 이란 값을 
넣어주었습니다. <br>
int& another_a = a;<br> 
그 후에 우리는 a 의 참조자 another_a 를 정의하였습니다. 이 때 참조자를 정하는 방법은, 가리 키고자 하는 타입 뒤에 & 를 붙이면 됩니다. another_a 는 a 의 또다른 이름 이라고 컴파일러에게 알려주는 것입니다.<br>
참조자와 포인터는 상당히 유사한 개념이지만 몇 가지 중요한 차이점이 있습니다.<br>

레퍼런스는 정의 시에 반드시 누구의 별명인지 명시 해야 합니다. 따라서 <br>
int& another_a; 	와 같은 문장은 불가능 합니다. 반면의 포인터의 경우 <br>
int* p; 		는 전혀 문제가 없는 코드 입니다. <br>

레퍼런스의 또 한 가지 중요한 특징으로 한 번 어떤 변수의 참조자가 되버린다면, 이 더이상 다른 변수를 참조할 수 없게 됩니다.<br>

int a = 10; <br>
int &another_a = a; // another_a 는 이제 a 의 참조자!<br> 
int b = 3; <br>
another_a = b;	// 그냥 a 에 b 의 값을 대입하라는 의미<br>

참고로 <br>
&another_a = b; 	// &a = b; 가 되어서 말이 안되는 문장이 됩니다.<br>



반면에 포인터는<br>

int a = 10; int* p = &a; 	// p 는 a 를 가리킨다. <br>
int b = 3; p = &b 		// 이제 p 는 a 를 버리고 b 를 가리킨다<br>

위와 같이 누구를 가리키는지 자유롭게 바뀔 수 있습니다.<br>

레퍼런스는 메모리 상에 존재하지 않을 수 도 있다. <br>

포인터의 경우<br>
int a = 10; <br>
int* p = &a; // p 는 메모리 상에서 당당히 8 바이트를 차지하게 됩니다.<br>

레퍼런스의 경우<br>
int a = 10; <br>
int &another_a = a; // another_a 가 자리를 차지할 필요가 있을까?<br>

<details><summary><strong>함수 인자로 레퍼런스 받기</strong></summary>

<pre><code class="language-cpp" style="font-size:16px;">
#include &lt;iostream>
int change_val(int &p) 
{
 p = 3; 
return 0; 
} 
int main() 
{ 
int number = 5; 
std::cout &lt;&lt; number &lt;&lt; std::endl; change_val(number); 
std::cout &lt;&lt; number &lt;&lt; std::endl; 
}
</code></pre>
int change_val(int &p) { 	와 같이 함수의 인자로 참조자를 받게 하였습니다.<br>

 p 가 정의되는 순간은 change_val(number) 로 호출할 때 이므로 사실상 int& p = number 가 실행된다고 생각하면 됩니다. <br>

change_val(number);  <br>
참조자 p 에게 너는 앞으로 number 의 새로운 별명이야 라고 알려주게 됩니다. 여기서 중요한 점은 포인터가 인자일 때와는 다르게 number 앞에 & 를 붙일 필요가 없다는 점입니다. 이는 참조자를 정의할 때 그냥 int& a = b 와 같이 한 것과 일맥상통합니다.
change_val 안에서 p = 3; 이라 하는 것은 main 함수의 number 에 number = 3; 을 하는 것과 정확히 같은 작업입니다.<br>



<pre><code class="language-cpp" style="font-size:16px;">

</code></pre>

</details>

<details><summary><strong>여러가지 참조자 예시들</strong></summary>

<pre><code class="language-cpp" style="font-size:16px;">
#include &lt;iostream>
int main() {
	int x;
	int& y = x;
	int& z = y;
	x = 1;	//x =1 y = 1 z = 1;
	std::cout &lt;&lt; "x : " &lt;&lt; x &lt;&lt; " y : " &lt;&lt; y &lt;&lt; " z : " &lt;&lt; z &lt;&lt; std::endl;
	y = 2;	//x = 2 y = 2 z = 2
	std::cout &lt;&lt; "x : " &lt;&lt; x &lt;&lt; " y : " &lt;&lt; y &lt;&lt; " z : " &lt;&lt; z &lt;&lt; std::endl;
	z = 3;	//x=3 y=3 z=3
	std::cout &lt;&lt; "x : " &lt;&lt; x &lt;&lt; " y : " &lt;&lt; y &lt;&lt; " z : " &lt;&lt; z &lt;&lt; std::endl;

	return 0;
}
</code></pre>
아까 어떤 타입 T 의 참조자 타입은 T& 래매. 그런데 여기서 y 가 int& 니까 y 의 참조자 타입은 int&& 가 되야 하지 않을까? <br>

<strong>C++ 문법 상 참조자의 참조자를 만드는 것은 금지되어 있습니다. </strong><br>

왜 굳이 포인터로 할 수 있는 것을 왜 참조자로 해야 하냐?<br>

참조자를 사용하게 되면 불필요한 & 와 * 가 필요 없기 때문에 코드를 훨씬 간결하게 나타낼 수 있습니다.<br>

변수 입력시 배웠던 cin 을 기억하시나요?<br>

scanf 로 이용할 때 분명히 <br>

scanf("%d", &user_input);<br>

</details>
<details><summary><strong>상수에 대한 참조자 </strong></summary>

<pre><code class="language-cpp" style="font-size:16px;">
#include 
int main() 
{ 
int &ref = 4; 
std::cout &lt;&lt; ref &lt;&lt; std::endl; 
}
</code></pre>
컴파일 오류 error C2440: 'initializing' : cannot convert from 'int' to 'int &' <br>
C++ 문법 상 상수 리터럴을 일반적인 레퍼런스가 참조하는 것은 불가능하게 되어 있습니다.<br>

<strong>레퍼런스의 배열과 배열의 레퍼런스 </strong><br>
레퍼런스는 반드시 정의와 함께 초기화를 해주어야 한다고 했습니다.<br>

int a, b; <br>
int& arr[2] = {a, b}; <br>

컴파일을 해보면 <br>
컴파일 오류 error C2234: 'arr' : arrays of references are illegal <br>
레퍼런스의 배열을 불법(illegal) 이라고 합니다.<br>

C++ 규정<br>
There shall be no references to references, no arrays of references, and no pointers to references <br>
(레퍼런스의 레퍼런스,레퍼런스의 배열, 레퍼런스의 포인터는 존재할 수 없다.)<br>

먼저 C++ 상에서 배열이 어떤 식으로 처리되는지 생각해봅시다.<br>

문법 상 배열의 이름은 (arr) 첫 번째 원소의 주소값으로 변환이 될 수 있어야 합니다. 이 때문에 arr[1] 과 같은 문장이 *(arr + 1) 로 바뀌어서 처리될 수 있기 때문이죠. 그런데 주소값이 존재한다라는 의미는 해당 원소가 메모리 상에서 존재한다 라는 의미와 같습니다. 하지만 레퍼런스는 특별한 경우가 아닌 이상 메모리 상에서 공간을 차지 하지 않습니다. 따라서 이러한 모순 때문에 레퍼런스들의 배열을 정의하는 것은 언어 차원에서 금지가 되어 있는 것입니다.<br>

<details><summary><strong>배열들의 레퍼런스</strong></summary>

<pre><code class="language-cpp" style="font-size:16px;">
#include &lt;iostream>
int main() 
{
	int arr[3] = { 1, 2, 3 };
	int(&ref)[3] = arr;

	ref[0] = 2;
	ref[1] = 3;
	ref[2] = 1;

	std::cout &lt;&lt; arr[0] &lt;&lt; arr[1] &lt;&lt; arr[2] &lt;&lt; std::endl;

	return 0;
}
</code></pre>
int arr[3] = { 1, 2, 3 };<br>
int(&ref)[3] = arr;<br>

포인터와는 다르게 배열의 레퍼런스의 경우 참조하기 위해선 반드시 배열의 크기를 명시해야 합니다. 따라서 int (&ref)[3] 이라면 반드시 크기가 3 인 int 배열의 별명이 되어야 하고 int (&ref) [5] 라면 크기가 5 인 int 배열의 별명이 되어야 합니다.<br>

</details>
<details><summary><strong></strong></summary>

<pre><code class="language-cpp" style="font-size:16px;">

</code></pre>
<pre><code class="language-cpp" style="font-size:16px;">

</code></pre>

</details>
<details><summary><strong></strong></summary>

<pre><code class="language-cpp" style="font-size:16px;">

</code></pre>
<pre><code class="language-cpp" style="font-size:16px;">

</code></pre>

</details>
<details><summary><strong></strong></summary>

<pre><code class="language-cpp" style="font-size:16px;">

</code></pre>
<pre><code class="language-cpp" style="font-size:16px;">

</code></pre>

</details>
