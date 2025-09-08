#PPP4_Drill&Exercises

<details><summary>Ex3_2</summary>
C++로 마일(mile)을 킬로미터(kilometer)로 변환하는 프로그램을 작성하시오.
사용자에게 마일 수를 입력하도록 적절한 프롬프트(prompt)를 제공해야 합니다.힌트: 1마일은 1.609킬로미터입니다.

```cpp
import std;
using namespace std;
int main(void)
{
	double mile = -1;
	double kilometer = 1.609;

	cout << "Input mile: ";
	cin >> mile;

	cout << (kilometer)*mile << "mile" << endl;
	return 0;
}
```
</details><!-- Ex3_2 -->
 <details><summary>Ex3_4,5</summary>
사용자에게 두 개의 정수 값을 입력하도록 요청(prompt)하는 프로그램을 작성하시오.
입력된 값을 int 타입 변수 val1과 val2에 저장하고, 두 값의 작은 값, 큰 값, 합(sum), 차(difference), 곱(product), 비율(ratio)을 계산하여 출력하시오.
위 프로그램을 수정하여, 사용자에게 부동소수점 값(floating - point value)을 입력받고 이를 double 타입 변수에 저장하도록 하시오. 동일한 입력값에 대해 두 프로그램의 출력을 비교해보십시오.
결과가 같은가 ? 같아야 하는가 ? 차이는 무엇인가 ?

```cpp	 
import std;
using namespace std;

int main(void)
{
	//int val1 = -1, val2 = -1; 수정 전
	double val1 = -1, val2 = -1; //수정 후

	cin >> val1 >> val2;
	//if (val1 > val2)cout << "큰 값 : " << val1 << endl << "작은 값 : " << val2 << endl;
	if (val1 > val2)cout << "큰 값 : " << (double)val1 << endl << "작은 값 : " << (double)val2 << endl;
	//else cout << "큰 값 : " << val2 << endl << "작은 값 : " << val1 << endl;
	else cout << "큰 값 : " << (double)val2 << endl << "작은 값 : " << (double)val1 << endl;

	/*cout << "합(sum) : " << val1 + val2 << endl;
	cout << "차(difference) : " << val1 - val2 << endl;
	cout << "곱(product) : " << val1 * val2 << endl;
	cout << "비율(ratio) : " << (double)val1 / val2 << endl;*/
	cout << "합(sum) : " << (double)val1 + val2 << endl;
	cout << "차(difference) : " << (double)val1 - val2 << endl;
	cout << "곱(product) : " << (double)val1 * val2 << endl;
	cout << "비율(ratio) : " << (double)val1 / val2 << endl;

	return 0;
}
```
 </details><!-- Ex3_4,5 -->
<details><summary>Ex6</summary>
사용자에게 세 개의 정수 값을 입력받아, 이를 숫자 순서대로 정렬하여 쉼표로 구분된 형태로 출력하는 프로그램을 작성하시오.
예 : 입력값이 10 4 6이면 출력은 4, 6, 10 동일한 값이 있을 경우 함께 정렬하시오.
예 : 4 5 4 → 4, 4, 5

```cpp
import std;
using namespace std;
int main(void)
{
	int val1 = -1, val2 = -1, val3 = -1;
	cout << "세 개의 정수 값을 입력하세요 : ";
	cin >> val1 >> val2 >> val3;

	/*if (val1 <= val2 && val1 <= val3)
	{
		if (val2 <= val3)cout << val1 << ", " << val2 << ", " << val3;
		else cout << val1 << ", " << val3 << ", " << val2;
	}
	else if (val2 <= val1 && val2 <= val3)
	{
		if (val1 <= val3)cout<<val2<<", "<<val1<<", "<<val3;
		else cout << val2 << ", " << val3 << ", " << val1;

	}
	else if (val3 <= val1 && val3 <= val2)
	{
		if (val1 <= val2)cout<<val3<<", "<<val1<<", "<<val2;
		else cout << val3 << ", " << val2 << ", " << val1;
	} // 방법 1*/

	/*방법 2 swap*/
	if (val1 > val2) { int temp = val1; val1 = val2; val2 = temp; };// val1과 val2를 비교하여 val1이 더 크면 두 값을 교환함 → val1이 더 작은 값을 갖게 됨
	if (val1 > val3) { int temp = val1; val1 = val3; val3 = temp; };// val1과 val3를 비교하여 val1이 더 크면 두 값을 교환함 → val1이 가장 작은 값이 됨
	if (val2 > val3) { int temp = val2; val2 = val3; val3 = temp; };// val2와 val3를 비교하여 val2가 더 크면 두 값을 교환함 → val3이 가장 큰 값이 됨

	cout << val1 << ", " << val2 << ", " << val3 << endl;
	return 0;
}
```
</details><!-- Ex6 -->
<details><summary></summary>
 
 </details>
<details><summary></summary>
 
 </details>
<details><summary></summary>
 
 </details>
<details><summary></summary>
 
 </details>
<details><summary></summary>
 
 </details>
<details><summary></summary>
 
 </details>
<details><summary></summary>
 
 </details>
<details><summary></summary>
 
 </details>
<details><summary></summary>
 
 </details>
<details><summary></summary>
 
 </details>
<details><summary></summary>
 
 </details>
<details><summary></summary>
 
 </details>
<details><summary></summary>
 
 </details>
<details><summary></summary>
 
 </details>
<details><summary></summary>
 
 </details>
<details><summary></summary>
 
 </details>
<details><summary></summary>
 
 </details>
<details><summary></summary>
 
 </details>
<details><summary></summary>
 
 </details>
