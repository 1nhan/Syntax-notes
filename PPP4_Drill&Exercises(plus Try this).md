#PPP4_Drill&Exercises

<details><summary>Ex2_2</summary>
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
 <details><summary>Ex2_4,5</summary>
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
 </details><!-- Ex2_4,5 -->
<details><summary>Ex2_6</summary>
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
</details><!-- Ex2_6 -->
<details><summary>Ex2_7</summary>

연습 문제 6을 문자열(string) 값으로 수행하시오.
예: 입력값이 Steinbeck, Hemingway, Fitzgerald이면 출력은 Fitzgerald, Hemingway, Steinbeck

```cpp
import std;
using namespace std;
int main(void)
{
	string val1, val2, val3 ;
	cout << "세 개의 문자열 값을 입력하세요 : ";
	cin >> val1 >> val2 >> val3;

	if (val1 <= val2 && val1 <= val3)
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
	} // 방법 1

	/*방법 2 swap*/
	//if (val1 > val2) { string temp = val1; val1 = val2; val2 = temp; };// val1과 val2를 비교하여 val1이 더 크면 두 값을 교환함 → val1이 더 작은 값을 갖게 됨
	//if (val1 > val3) { string temp = val1; val1 = val3; val3 = temp; };// val1과 val3를 비교하여 val1이 더 크면 두 값을 교환함 → val1이 가장 작은 값이 됨
	//if (val2 > val3) { string temp = val2; val2 = val3; val3 = temp; };// val2와 val3를 비교하여 val2가 더 크면 두 값을 교환함 → val3이 가장 큰 값이 됨

	//cout << val1 << ", " << val2 << ", " << val3 << endl;
	return 0;
}
```
 </details><!-- Ex2_7 -->
<details><summary>Ex2_8</summary>
 정수 값을 입력받아 홀수(odd)인지 짝수(even)인지 판별하는 프로그램을 작성하시오. 출력은 명확하고 완전해야 하며, 단순히 yes 또는 no를 출력하지 마십시오. 예: "The value 4 is an even number." 힌트: §2.4의 나머지 연산자(modulo operator)를 참고하십시오.

```cpp
import std;
using namespace std;

int main(void)
{
	int val = -1;
	cout << "정수를 입력하세요." << endl;
	cin >> val;

	if (val % 2 == 0) cout << "The value " << val << " is an even number.";
	else cout << "The value " << val << " is an odd number.";

	return 0;
}
```
 </details><!-- Ex2_8 -->
<details><summary>Ex2_9</summary>
 사용자가 철자로 입력한 숫자 이름(예: "zero", "two")을 숫자(0, 2 등)로 변환하는 프로그램을 작성하시오. 변환 대상은 "zero"부터 "four"까지, 즉 0~4에 해당하는 숫자 이름만 처리합니다. 사용자가 "stupid computer!"처럼 정의되지 않은 입력을 하면, "not a number I know"라는 메시지를 출력해야 합니다.

```cpp
import std;
using namespace std;

int main(void)
{
	string val;
	cout << "숫자를 영어로 소문자로 입력하세요." << endl;
	cin >> val;

	if (val == "zero") cout << "0" << endl;
	else if (val == "one") cout << "1" << endl;
	else if (val == "two") cout << "2" << endl;
	else if (val == "three") cout << "3" << endl;
	else if (val == "four") cout << "4" << endl;
	else cout << "not a number I know" << endl;

	return 0;
}
```
 </details><!--  Ex2_9 -->
<details><summary>Ex2_10</summary>
연산자와 두 개의 피연산자를 입력받아 결과를 출력하는 프로그램을 작성하시오. 예를 들어: + 100 3.14 * 45
연산자를 operation이라는 이름의 문자열로 읽고, if문을 사용하여 사용자가 원하는 연산을 판별하시오. 
예를 들어: if (operation == "+") 피연산자는 double 타입의 변수에 저장하시오. 다음과 같은 연산자에 대해 구현하시오: +, −, *, /, plus, minus, mul, div 각 연산자는 그 의미에 따라 동작해야 한다.

```cpp
import std;
using namespace std;

int main(void)
{
	double val1 = -1, val2 = -1;
	string operation = " ";
	cout << "연산자(+,-,*,/,plus,minus,mul,div)와 두 개의 숫자를 입력하세요" << endl;
	cin >> operation >> val1 >> val2;;
	cout << endl;

	if (operation == "+") cout << val1 + val2 << endl;
	else if (operation == "plus") cout << val1 + val2 << endl;
	else if (operation == "-") cout << val1 - val2 << endl;
	else if (operation == "minus") cout << val1 - val2 << endl;
	else if (operation == "*") cout << val1 * val2 << endl;
	else if (operation == "mul") cout << val1 * val2 << endl;
	else if (operation == "/") cout << val1 / val2 << endl;
	else if (operation == "div") cout << val1 / val2 << endl;
	else cout << "Invalid operation" << endl;

	return 0;
}
```
 </details><!--  Ex2_10 -->
<details><summary>Ex2_11</summary>

사용자에게 다음 동전의 개수를 각각 입력받는 프로그램을 작성하시오:
penny (1센트)
nickel (5센트)
dime (10센트)
quarter (25센트)
half dollar (50센트)
one-dollar coin (100센트)
각 동전에 대해 별도로 질문하십시오. 예: "How many pennies do you have?" 출력 예시:
```코드
You have 23 pennies.  
You have 17 nickels.  
You have 14 dimes.  
You have 7 quarters.  
You have 3 half dollars.  
The value of all of your coins is 573 cents.
```
개선 사항:
동전이 1개일 경우 문법적으로 올바른 단수 표현을 사용하십시오. 예: "1 dime" (아닌 "1 dimes")
총액은 달러와 센트 단위로 변환하여 출력하십시오. 예: 573 cents → $5.73

```cpp
import std;
using namespace std;

int main(void)
{
	int pennies = -1, nickels = -1, dimes = -1, quarters = -1, half_dollars = -1, dollar = -1;

	cout << "How many pennies do you have?" << endl;
	cin >> pennies;
	cout << "How many nickels do you have?" << endl;
	cin >> nickels;
	cout << "How many dimes do you have?" << endl;
	cin >> dimes;
	cout << "How many quarters do you have?" << endl;
	cin >> quarters;
	cout << "How many half dollars do you have?" << endl;
	cin >> half_dollars;
	cout << "How many dollars do you have?" << endl;
	cin >> dollar;

	cout << "You have " << pennies << " " <<
		((pennies == 1) ? "penny." : "pennies.") << endl;
	cout << "You have " << nickels << " " <<
		((nickels == 1) ? "nickel." : "nickels.") << endl;
	cout << "You have " << dimes << " " <<
		((dimes == 1) ? "dime." : "dimes.") << endl;
	cout << "You have " << quarters << " " <<
		((quarters == 1) ? "quarter." : "quarters.") << endl;
	cout << "You have " << half_dollars << " " <<
		((half_dollars == 1) ? "half dollar." : "half dollars.") << endl;
	cout << "You have " << dollar << " " <<
		((dollar == 1) ? "dollar." : "dollars.") << endl;
	double total = pennies + nickels * 5 + dimes * 10 + quarters * 25 + half_dollars * 50 + dollar * 100;
	cout << "The value of all of  your coins is "
		<< total << endl;
	cout << "The value of all of  your dollors is "
		<< total / 100 << endl;
	return 0;
}
```
 </details><!-- Ex2_11 -->
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
