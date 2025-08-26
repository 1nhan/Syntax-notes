# Cpp
>Cpp학습 카테코리 정리<br>
>Google Docs      https://docs.google.com/document/d/1Lf5LPqnNvNzQABAKtOLZ1DJLLt6IWisBUlVqftEDTgM/edit?tab=t.v1diwsp23tj9 <br>
>Google Sheets    ? <br>
 ------------
<details><summary>학습 일지</summary>
2025-08-22 <details><summary>const 함수에 대해</summary>

const int num = 10;		//	변수를 상수화
const SoSimple sim(20);	//	객체를 상수화	

객체를 대상으로는 const 멤버함수만 호출이 가능하다. 변경시킬 능력이 있는 함수는 아예 호출을 허용하지 않는다.<br>
멤버변수에 저장된 값을 수정하지 않는 함수는 가급적 const로 선언해서, 객체에서도 호출이 가능하도록 할 필요가 있다.<br>
</details><br>
<detail><summary><strong>const 함수 오버로딩</strong></summary>
```c++
void numLock(){} <br>
void numLock()const{}	// const의 선언 유무도 함수 오버로딩의 조건에 해당된다. <br>
```
</detail>

2025-08-23 상속(Inheritance) <br>
상속에 들어가기에 앞서, 상속의 문법적인 이해 <br>
2025-08-24 일요일 <br>
2025-08-25 상속(Inheritance) <br>
protected 선언과 세 가지 형태의 상속, 상속을 위한 조건, OOP 단계별 프로젝트 05 <br>
2025-08-26 객체 포인터의 참조관계 <br>
객체 포인터 변수, 함수 오버라이딩, IS-A, HAS-A <br>
2025-08-27 가상함수(Virtual Function) <br>
가상함수, 가상소멸자와 참조자의 참조 가능성, Employee 예제와 문제, Employee 1-4, Quiz에 대한 분석 <br>
</details>
