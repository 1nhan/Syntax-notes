#PPP4_Drill&Exercises

<details><summary>C++로 마일(mile)을 킬로미터(kilometer)로 변환하는 프로그램을 작성하시오.
사용자에게 마일 수를 입력하도록 적절한 프롬프트(prompt)를 제공해야 합니다.힌트: 1마일은 1.609킬로미터입니다.
</summary>

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
 <details><summary>사용자에게 두 개의 정수 값을 입력하도록 요청(prompt)하는 프로그램을 작성하시오.<br>
입력된 값을 int 타입 변수 val1과 val2에 저장하고, 두 값의 작은 값, 큰 값, 합(sum), 차(difference), 곱(product), 비율(ratio)을 계산하여 출력하시오.<br>
위 프로그램을 수정하여, 사용자에게 부동소수점 값(floating - point value)을 입력받고 이를 double 타입 변수에 저장하도록 하시오. 동일한 입력값에 대해 두 프로그램의 출력을 비교해보십시오.<br>
결과가 같은가 ? 같아야 하는가 ? 차이는 무엇인가 ?<br>
</summary>

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
<details><summary>사용자에게 세 개의 정수 값을 입력받아, 이를 숫자 순서대로 정렬하여 쉼표로 구분된 형태로 출력하는 프로그램을 작성하시오.<br>
예 : 입력값이 10 4 6이면 출력은 4, 6, 10 동일한 값이 있을 경우 함께 정렬하시오.<br>
예 : 4 5 4 → 4, 4, 5</summary>


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
<details><summary>문자열(string) 값으로 수행하시오.<br>
예: 입력값이 Steinbeck, Hemingway, Fitzgerald이면 출력은 Fitzgerald, Hemingway, Steinbeck</summary>


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
<details><summary> 정수 값을 입력받아 홀수(odd)인지 짝수(even)인지 판별하는 프로그램을 작성하시오. 출력은 명확하고 완전해야 하며, 단순히 yes 또는 no를 출력하지 마십시오. 예: "The value 4 is an even number." 힌트: §2.4의 나머지 연산자(modulo operator)를 참고하십시오.</summary>


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
<details><summary> 사용자가 철자로 입력한 숫자 이름(예: "zero", "two")을 숫자(0, 2 등)로 변환하는 프로그램을 작성하시오. 변환 대상은 "zero"부터 "four"까지, 즉 0~4에 해당하는 숫자 이름만 처리합니다. 사용자가 "stupid computer!"처럼 정의되지 않은 입력을 하면, "not a number I know"라는 메시지를 출력해야 합니다.</summary>


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
<details><summary>연산자와 두 개의 피연산자를 입력받아 결과를 출력하는 프로그램을 작성하시오. 예를 들어: + 100 3.14 * 45
연산자를 operation이라는 이름의 문자열로 읽고, if문을 사용하여 사용자가 원하는 연산을 판별하시오. 
예를 들어: if (operation == "+") 피연산자는 double 타입의 변수에 저장하시오. 다음과 같은 연산자에 대해 구현하시오: +, −, *, /, plus, minus, mul, div 각 연산자는 그 의미에 따라 동작해야 한다.
</summary>
	
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
<details><summary>사용자에게 다음 동전의 개수를 각각 입력받는 프로그램을 작성하시오:<br>
penny (1센트)<br>
nickel (5센트)<br>
dime (10센트)<br>
quarter (25센트)<br>
half dollar (50센트)<br>
one-dollar coin (100센트)<br>
각 동전에 대해 별도로 질문하십시오. 예: "How many pennies do you have?" 출력 예시:<br>

```코드
You have 23 pennies.  
You have 17 nickels.  
You have 14 dimes.  
You have 7 quarters.  
You have 3 half dollars.  
The value of all of your coins is 573 cents.
```
개선 사항:<br>
동전이 1개일 경우 문법적으로 올바른 단수 표현을 사용하십시오. 예: "1 dime" (아닌 "1 dimes")<br>
총액은 달러와 센트 단위로 변환하여 출력하십시오. 예: 573 cents → $5.73<br>
</summary>


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
<details><summary>Drill<br>[1]while 루프를 사용해 두 개의 int를 입력받고 출력.<br>
[2]더 작은 값과 더 큰 값을 각각 출력.<br>
[3]두 값이 같을 경우 "the numbers are equal" 출력<br>
[4]int 대신 double 사용<br>
[5]두 값의 차이가 1.0 / 100보다 작으면 "numbers are almost equal" 출력<br>
[6]한 번에 하나의 double 입력.지금까지 본 가장 작은 / 큰 값 추적 및 출력<br>
[7]단위(unit)를 함께 입력 : cm, m, in, ft 허용.변환 기준 : 1m = 100cm, 1in = 2.54cm, 1ft = 12in<br>
[8]단위가 없거나 잘못된 단위(y, yard, meter, km, gallons)는 거부<br>
[9]입력된 값의 합계, 최소값, 최대값, 개수 출력.합계는 meter 기준<br>
[10]입력된 모든 값을 meter로 변환하여 vector에 저장<br>
[11]벡터를 정렬한 후 값들을 출력(오름차순)</summary>

```cpp
#include <algorithm>
import std;
using namespace std;
int main(void)
{
	vector<double> val; 
	vector<string> unit;
	string temp_string;
	double minimum=-1,maximum=-1,temp_double=-1,sum = 0;
	int count = 0;
	
	/*입력*/
	while (cin >> temp_double >> temp_string)
	{
		val.push_back(temp_double);
		if (temp_string == "cm")unit.push_back(temp_string);
		else if(temp_string == "m")unit.push_back(temp_string);
		else if(temp_string == "in")unit.push_back(temp_string);
		else if(temp_string == "ft")unit.push_back(temp_string);
		else cout << "reject" << '\n';
	}
	/*동작*/
	for (int x =0; x < val.size();++x)
	{
		/*입력된 모든 값을 meter로 변환하여 vector에 저장*/
		if (unit[x] == "cm")val[x] = val[x] / 100;
		else if (unit[x] == "m")val[x] = val[x] * 1;
		else if (unit[x] == "in")val[x] = (val[x] / 100) * 2.54 * 12;
		else if (unit[x] == "ft")val[x] = (val[x] / 100) * 2.54;	

		/*합계, 갯수, 최소값, 최대값*/
		sum += val[x];							
		++count;								
		if (minimum < 0 || minimum > val[x])minimum = val[x];	
		if (maximum < 0 || maximum <val[x])maximum = val[x];
	}

	/*출력*/
	cout << "최대 값 : " << maximum << '\n';
	cout << "최소 값 : " << minimum<< '\n';
	cout << "총합 : " << sum << '\n';
	cout << "총 갯수: " << count<< '\n';

	/*오름차순 정렬후 출력*/
	ranges::sort(val);
	for (double x : val) cout<<x<<'\n';

	return 0;
}
```

 </details>
<details><summary>문자열을 입력받고, 입력된 각 문자에 대해 해당 문자와 그 문자의 정수 값을 한 줄씩 출력하는 프로그램을 작성하세요.
</summary>

```cpp
import std;
using namespace std;

int main(void)
{
	string words;
	cin >> words;
	for (char x : words)
		cout << x << ' ' << (int)x << '\n';

	return 0;
}
```
 </details>
<details><summary>수열의 중앙값(median)을 “수열에서 그 앞에 오는 요소의 개수와 뒤에 오는 요소의 개수가 정확히 같은 값”으로 정의한다면, 

```cpp
int main()
// 평균 및 중앙값 계산
{
    vector<double> temps;
    for (double temp; cin >> temp;)
        temps.push_back(temp);

    // 평균 계산
    double sum = 0;
    for (double x : temps)
        sum += x;
    cout << "Average temperature: " << sum / temps.size() << '\n';

    // 중앙값 계산
    ranges::sort(temps); // 정렬
    cout << "Median temperature: " << temps[temps.size() / 2] << '\n';
}
```
의 프로그램을 수정하여 항상 중앙값을 출력하도록 하세요. 힌트: 중앙값은 수열의 요소일 필요는 없습니다.
</summary>

```cpp
#include <algorithm>
import std;
using namespace std;

int main()
// 평균 및 중앙값 계산
{
    vector<double> temps;
    for (double temp; cin >> temp;)
        temps.push_back(temp);

    // 평균 계산
    double sum = 0;
    for (double x : temps)
        sum += x;
    cout << "Average temperature: " << sum / temps.size() << '\n';

    // 중앙값 계산
    ranges::sort(temps); // 정렬
    if (temps.size() % 2 == 1) cout << "Median temperature: " << temps[temps.size() / 2] << '\n';
    else cout << "Median temperature: " << (temps[((temps.size() - 1) / 2)] + temps[(temps.size() / 2)])/2 << '\n';
}
``` 
 </details>
<details><summary>double 값들의 수열을 벡터(vector)로 입력받으세요. 각 값은 도시 간 거리라고 생각합니다. 전체 거리(모든 거리의 합)를 계산하고 출력하세요. 인접한 도시 간의 최소 거리와 최대 거리도 출력하세요. 인접한 도시 간 평균 거리도 계산하여 출력하세요.
</summary>

```cpp
#include <algorithm>
import std;
using namespace std;
double my_abs(double val);

int main(void)
{
	vector<double> city;
	double sum = 0;
	/*double 값들의 수열을 벡터(vector)로 입력*/
	for (double distance; cin >> distance;) //각 값은 도시 간 거리
	{
		if (distance > 0)city.push_back(distance);
		else cout << "reject" << '\n';
	}

	/*전체 거리(모든 거리의 합)를 계산*/
	for (double x : city) sum += x;
	cout << "모든 거리의 합 : " << sum << '\n';


	/*거리 계산시 -산출시 절대값*/
	
	// 인접한 도시 간의 최소 거리와 최대 거리도 출력하세요.
	double min_distance = my_abs(city[1] - city[0]),
		max_distance = min_distance;
	for (int x = 0; x < city.size() - 1; ++x)
	{
		if(min_distance > my_abs(city[x + 1] - city[x])) min_distance = my_abs(city[x + 1] - city[x]);
		else if(max_distance < my_abs(city[x + 1] - city[x])) max_distance = my_abs(city[x + 1] - city[x]);
	}
	cout << "최소 거리 : " << min_distance << '\n';
	cout << "최대 거리 : " << max_distance<< '\n';
	// 인접한 도시 간 평균 거리도 계산하여 출력하세요.
	cout << "평균 거리 : " << sum / city.size()-1 << '\n';
}
double my_abs(double val)
{
	return val > 0 ? val : -val;
}
```

 </details>
<details><summary>숫자 맞히기 게임 프로그램을 작성하세요. 사용자가 1부터 100 사이의 숫자를 생각하면, 프로그램이 질문을 통해 그 숫자를 알아내야 합니다. 예: “당신이 생각한 숫자는 50보다 작습니까?” 프로그램은 최대 7번의 질문으로 숫자를 알아내야 합니다.
</summary>

```cpp
import std;
using namespace std;

int main(void)
{
	int low = 1;
	int high = 100;
	int mid = (low + high) / 2;
	char answer = ' ';
	/*프롬프트*/
	cout << "1부터 100 사이의 숫자를 생각해주세요... 제가 맞춰볼게요." << '\n';

	for (int count = 7; count > 0; --count)
	{
		mid = (high + low) / 2;
		cout << "당신이 생각한 숫자는" << mid << "보다 작습니까 ?(press y/n) " << '\n';
		cin >> answer;
		if (answer == 'y' || answer == 'Y')
		{
			cout << "남은 기회: " << count - 1 << '\n';
			high = mid - 1;
		}
		else if (answer == 'n' || answer == 'N')
		{
			cout << "남은 기회: " << count - 1 << '\n';
			low = mid;
		}
		else { cout << "again press y/n" << '\n'; count++; }

		if (low == high) { cout << "정답! " << low<< '\n'; break; }
		else if (low > high ) { cout << "정답! " << mid << '\n'; break; }
	}
	return 0;
}
```
정답부분이 출력이 안되는데.. 이유를 잘 모르겠다. 일단 보류
 </details>
<details><summary>아주 간단한 계산기 프로그램을 작성하세요. 덧셈, 뺄셈, 곱셈, 나눗셈의 네 가지 기본 연산을 두 개의 입력값에 대해 수행할 수 있어야 합니다. 사용자에게 두 개의 double 값과 연산을 나타내는 문자 하나를 입력받도록 하세요. 예: 입력값이 35.6, 24.1, '+'이면 출력은 “The sum of 35.6 and 24.1 is 59.7”<br> +문제“미니 계산기”를 수정하여, 한 자리 숫자를 숫자 형태 또는 영어 단어 형태로 입력받을 수 있도록 하세요.
</summary>

```cpp
int main(void)
{
	double val1 = -1, val2 = -1;
	char op = ' ';
	
	while (cin >> val1 >> val2 >> op)
	{
		if (op == '+')cout << "The sum of " << val1 << " and " << val2 << " is " << val1 + val2 << '\n';
		else if (op == '-')cout << "The sum of " << val1 << " and " << val2 << " is " << val1 - val2 << '\n';
		else if (op == '*')cout << "The sum of " << val1 << " and " << val2 << " is " << val1 * val2 << '\n';
		else if (op == '/')cout << "The sum of " << val1 << " and " << val2 << " is " << val1 / val2 << '\n';
		else cout << "Reject" << '\n';
	}

	return 0;
}
```
“미니 계산기”를 수정하여, 한 자리 숫자를 숫자 형태 또는 영어 단어 형태로 입력받을 수 있도록 하세요.

```cpp
아직
```

 </details>
<details><summary>문자열 "zero"부터 "nine"까지 10개의 값을 담은 벡터를 만드세요. 이 벡터를 사용하여 숫자를 해당하는 영어 단어로 변환하는 프로그램을 작성하세요. 예: 입력 7 → 출력 "seven" 같은 입력 루프를 사용하여 영어 단어를 숫자로 변환하는 기능도 추가하세요. 예: 입력 "seven" → 출력 7
</summary>

```cpp
import std;
using namespace std;

int main(void)
{
	vector<string>eng_numb =
	{ "zero", "one", "two", "three", "four", "five", "six", "seven", "eight", "nine" };
	int val = -1;
	string eng_val = " ";
	while(cin >> val >> eng_val)
	{

		if(val>=0&&val<10)
		{
			cout<<eng_numb[val]<<'\n';
		}
		for (int x = 0; x < eng_numb.size(); ++x) if (eng_val == eng_numb[x])cout << x << '\n';
	}

	return 0;
}
```
 
 </details>
<details><summary>체스를 발명한 사람이 황제에게 보상을 요구한 고전 이야기가 있습니다. 첫 번째 칸에는 쌀 한 톨, 두 번째에는 두 톨, 세 번째에는 네 톨… 이렇게 64칸까지 매번 두 배로 늘어납니다. 이 이야기를 바탕으로, 다음을 계산하는 프로그램을 작성하세요:
<br>최소 1,000 톨을 받기 위해 필요한 칸 수
<br>최소 1,000,000 톨을 받기 위해 필요한 칸 수
<br>최소 1,000,000,000 톨을 받기 위해 필요한 칸 수 반복문을 사용하고, 현재 칸 번호, 해당 칸의 쌀 수, 누적 쌀 수를 추적하는 변수를 사용하세요. 각 반복마다 변수 값을 출력하여 진행 상황을 확인하세요.
<br>또한 발명자가 요구한 총 쌀 수를 계산해보세요. 이 수는 너무 커서 int나 double로 정확히 표현할 수 없습니다. 값이 너무 커졌을 때 int와 double에서 어떤 일이 발생하는지 관찰하세요.
int로 정확히 계산 가능한 최대 칸 수는?
double로 근사 계산 가능한 최대 칸 수는?
</summary>

```cpp
import std;
using namespace std;

int main(void)
{
	int val_int = 1;
	int total_int = val_int;
	double val_double = 1;
	double total_double = val_double;

	for (int x = 1; x <= 40; ++x)
	{
		if (total_int > 1000) cout << "1000톨을 넘은 칸(int): " <<				x << '\n';
		if (total_int > 1000000) cout << "1000000톨을 넘은 칸(int): " <<			x << '\n';
		if (total_int > 1000000000) cout << "1000000000톨을 넘은 칸(int): " <<	x << '\n';
		if (total_double > 1000) cout << "1000톨을 넘은 칸(double): " <<				x << '\n';
		if (total_double > 1000000) cout << "1000000톨을 넘은 칸(double): " <<		x << '\n';
		if (total_double > 1000000000) cout << "1000000000톨을 넘은 칸(double): " <<	x << '\n';
		
		val_int *= 2;
		val_double *= 2;

		total_int += val_int;
		total_double += val_double;
		cout << "현재 방칸의 쌀의 갯수(int): " << val_int << '\n';
		cout << "현재 방칸의 쌀의 갯수(double): " << val_double << '\n';
	}
	return 0;
}
```
값이 너무 커졌을 때 int와 double에서 어떤 일이 발생하는지 관찰하세요. int는 음수로 출력한 뒤 0으로 출력이 되는 현상이 일어난다. double의 경우 반복문이 40칸일때 정지가 되고 41칸부터는 출력되지 않았다.
int로 정확히 계산 가능한 최대 칸 수는 ?	답: 30<br>
double로 근사 계산 가능한 최대 칸 수는 ?	답: 40<br>
 
 </details>
<details><summary>“가위, 바위, 보” 게임을 구현하세요. 게임을 모른다면 웹에서 검색해보세요. 프로그래머에게는 조사(research)도 중요한 작업입니다. 이 문제는 switch 문을 사용하여 해결하세요. 컴퓨터는 무작위로 가위, 바위, 보 중 하나를 선택해야 합니다. 진짜 난수는 어렵기 때문에, 미리 값들을 담은 벡터를 만들어 사용하세요. 벡터를 프로그램에 고정하면 항상 같은 게임이 되므로, 사용자에게 값을 입력받는 방식도 고려하세요. 사용자가 컴퓨터의 다음 선택을 예측하기 어렵도록 다양한 변형을 시도해보세요.
</summary>

미완성
```cpp 

int main(void)
{
	int round = 0;
	int computer_pick = round % 3;
	int user_input = -1;
	vector<string>rpssuffle = { "가위","바위","보" };

	cout << "press 1(가위),2(바위),3(보)" << '\n';
	while (cin >> user_input)
	{
		if (user_input > 2 || user_input < 0) cout<<"reject" << '\n';
		round++;
		switch (user_input)
		{
		case 0:	if		(computer_pick == 0)	{cout << "컴퓨터는 " << rpssuffle[round%3] << "를 내었다!" << '\n';break;}
				else if (computer_pick == 1)	{cout << "컴퓨터는 " << rpssuffle[round%3] << "를 내었다!" << '\n';break;}
				else							{cout << "컴퓨터는 " << rpssuffle[round%3] << "를 내었다!" << '\n';break;}
		case 1:	if		(computer_pick == 0)	{cout << "컴퓨터는 " << rpssuffle[round%3] << "를 내었다!" << '\n';break;}
				else if (computer_pick == 1)	{cout << "컴퓨터는 " << rpssuffle[round%3] << "를 내었다!" << '\n';break;}
				else							{cout << "컴퓨터는 " << rpssuffle[round%3] << "를 내었다!" << '\n';break;}
		case 2:	if		(computer_pick == 0)	{cout << "컴퓨터는 " << rpssuffle[round%3] << "를 내었다!" << '\n';break;}
				else if (computer_pick == 1)	{cout << "컴퓨터는 " << rpssuffle[round%3] << "를 내었다!" << '\n';break;}
				else							{cout << "컴퓨터는 " << rpssuffle[round%3] << "를 내었다!" << '\n';break;}
		}
	}


	return 0;
}
```
</details>
<details><summary>1부터 100 사이의 모든 소수(prime number)를 찾는 프로그램을 작성하세요. 방법: 소수인지 확인하는 함수를 작성하고, 소수들을 담은 벡터를 사용하여 작은 소수로 나눠지는지 검사하세요. 예: primes[0]==2, primes[1]==3, primes[2]==5 등 1부터 100까지 반복하면서 소수인지 확인하고, 소수는 벡터에 저장하세요. 저장된 소수를 출력하는 루프도 작성하세요. 결과를 기존 소수 목록과 비교하여 검증해보세요. 참고: 2는 첫 번째 소수입니다.
</summary>

```cpp
import std;
using namespace std;

int main(void)
{
	vector<int> prime_vector;

	for (int x = 2; x <= 100; ++x)
	{
		int i;
		for (i = 2; i < x; ++i)
			if (x % i == 0) { break; }
		if(x==i){cout << x << '\n'; prime_vector.push_back(x);}
	}

	return 0;
}
```
 
 </details>
<details><summary>1부터 100 사이의 모든 소수를 찾는 프로그램을 작성하세요. 고전적인 방법인 “에라토스테네스의 체(Sieve of Eratosthenes)”를 사용하세요. 이 방법을 모른다면 웹에서 검색해보세요. 해당 방법을 사용하여 프로그램을 작성하세요.
</summary>
	
```cpp
import std;
using namespace std;

int main(void)
{
	int num = 100;
	vector<bool>isprime(num + 1, true);

	for (int x = 2; x * x <= num; ++x)
		if (isprime[x])
			for (int y = x * x; y <= num; y += x)
				isprime[y] = false;
	for (int x = 2; x <= num; ++x)
		if (isprime[x]) cout << x << '\n';
	return 0;
}
```
개인적으로 이해하기 힘든 예제였지만 매달려서 이해하길 잘했다고 생각한 문제
 </details>
<details><summary>입력값 n을 받아, 처음 n개의 소수를 찾는 프로그램을 작성하세요.</summary>


```cpp
import std;
using namespace std;

int main(void)
{
	int num = 100;
	int input = -1;
	int count = 0;

	vector<bool>isprime(num + 1, true);

	for (int x = 2; x * x < num; ++x)
		if (isprime[x])
			for (int i = x*x; i<num; i += x)
				isprime[i] = false;
	cin >> input;
	for (int x = 2; x < num; ++x)
	{
		if (isprime[x])
		{
			cout << x << '\n';
			++count;
			if(count==input) break;
		}
	}
	return 0;
}

```
 
 </details>
<details><summary>수열에서 가장 많이 등장하는 값은 최빈값(mode)이라고 합니다. 양의 정수 집합에서 최빈값을 찾는 프로그램을 작성하세요.
</summary>

미완
```cpp
import std;
using namespace std;
#include<algorithm>

int main(void)
{
	int scale_matrix;

	/*specify matrix_int.size()*/
	cin >> scale_matrix;
	vector<int> matrix_int(scale_matrix);
	vector<int>freq;
	
	/*add matrix_element*/
	for (int x = 0; x<scale_matrix;++x)
		cin >> matrix_int[x];

	/*sort*/
	ranges::sort(matrix_int);


	/*check mode*/
	int count = 1;
	for (int x = 1; x < scale_matrix; ++x)
	{
		if (matrix_int[x] == matrix_int[x - 1]) count++;
		else if (matrix_int[x] != matrix_int[x - 1]) { freq.push_back(count); count = 1;}
	}

	for (int x = 1; x < freq.size(); ++x)
		if (freq[x] < freq[x - 1]) freq[x] = freq[x - 1];
	return 0;
}
```

 
</details>
<details><summary>문자열 시퀀스(sequence of strings)에서 최소값(min), 최대값(max), 최빈값(mode)을 찾는 프로그램(program)을 작성하시오.
</summary>


 
</details>
<details><summary>이차방정식(quadratic equation)을 푸는 프로그램을 작성하세요. 형태: ax² + bx + c = 0 이 방정식을 푸는 공식을 모른다면 조사해보세요. 문제 해결 방법을 알아내는 것은 프로그래머가 컴퓨터에게 문제 해결을 가르치기 위한 필수 과정입니다. 사용자 입력값 a, b, c는 double로 처리하세요. 해는 두 개이므로 x₁, x₂를 모두 출력하세요.

</summary>


```cpp


import std;
using namespace std;

double my_sqrt(double S)
{
	if (S <= 0) return 0 ;
	double valx = S;

	for (int i = 0; i < 20; ++i)
		valx = (0.5) * (valx * S / valx);
	return valx;
}

int main(void)
{
	double a=-1, b=-1, c=-1, d=-1;
	double valx1=-1, valx2=-1;

	cin >> a>> b>> c;
	/*판별식*/
	d = (b * b) - 4 * (a * c);

	/*1차 방정식*/
	if (a == 0)
	{
		if (b != 0) { double valx = (-c) / b; cout <<"x = " << valx << '\n'; }
		else cout << ((c == 0) ? "무수히 많은 해" : "해 없음") << '\n';
		return 0;
	}

	/*2차 방정식*/
	if (a != 0)
	{
		if (d > 0)
		{
			valx1 = (-b + my_sqrt(d)) / (2 * a);
			valx2 = (-b - my_sqrt(d)) / (2 * a);
			cout <<"X1 = " << valx1 << ", X2 = " << valx2 << '\n';
		}
		else if (d == 0)cout<<-b/(2*a) << '\n';
		else 
		{ 
			double valxreal = (-b) / (2 * a);
			double valximage = (my_sqrt(-d)) / (2 * a);
			cout<<"X1&X2 = " << valxreal << "±" << valximage << 'i\n';
		}
	}
	return 0;
}

```

 
 </details>
<details><summary>이름과 값 쌍(name-value pair)을 입력받는 프로그램을 작성하세요. 예: Joe 17, Barbara 22 각 이름은 names 벡터에, 각 값은 scores 벡터에 같은 위치로 저장하세요. 예: names[7] == "Joe"이면 scores[7] == 17 입력 종료 조건: NoName 0 이름이 중복되면 오류 메시지를 출력하고 종료하세요. 모든 (이름, 점수) 쌍을 한 줄씩 출력하세요.<br>프로그램을 수정하여, 이름과 값 쌍을 입력한 후 루프를 통해 이름을 입력하면 해당 점수를 출력하거나 "name not found"를 출력하세요.<br>프로그램을 수정하여, 이름과 값 쌍을 입력한 후 루프를 통해 점수를 입력하면 해당 점수를 가진 모든 이름을 출력하거나 "score not found"를 출력하세요.
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
<details><summary>
</summary>
 
 </details>
