#CPP_Algorithm

하루 한개의 알고리즘을 간단하게 알아보자.<br>

## 알고리즘(Algorithm)

알고리즘은 ‘문제를 해결하기 위한 일련의 절차(단계)’를 뜻해요. 입력(input)을 받아 출력(output)을 만들어내는 명확한 단계들의 모임, 문제 해결 방식이니, 간단한 계산에서부터 복잡한 그래프 탐색까지 모두 포함해요 알고리즘을 배우면 문제를 구조적으로 이해하고 효율적인 해결책을 설계할 수 있게 됩니다.

 <details><summary>탐색 알고리즘 (Search Algorithms)</summary>


<details><summary>Day 1 선형 탐색 (Linear Search)</summary>
오늘은 배열의 처음부터 끝까지 순서대로 값을 비교하며 찾는 가장 단순한 탐색 방법인 선형 탐색에 대해 배워봅니다.<br>

#### 개념
선형 탐색은 정렬 여부와 관계없이 배열의 첫 원소부터 마지막 원소까지 차례대로 목표 값(target)을 비교하면서 찾는 알고리즘입니다.<br>

#### 동작 단계
인덱스 i = 0부터 시작<br>
현재 원소 arr[i]가 target과 같은지 확인<br>
같으면 인덱스 i를 반환하며 종료<br>
마지막 원소까지 비교했는데 찾지 못하면 -1 반환<br>

예제 코드
```
cpp
#include <vector>

// arr에서 target을 찾으면 인덱스, 못 찾으면 -1 반환
int linearSearch(const std::vector<int>& arr, int target) {
    for (int i = 0; i < arr.size(); ++i) {
        if (arr[i] == target) {
            return i;
        }
    }
    return -1;
}
```

#### 시간 복잡도
최선의 경우: O(1)<br>
평균 및 최악의 경우: O(n)<br>
데이터가 많아질수록 탐색 비용이 선형적으로 증가합니다.<br><br>

#### 언제 사용할까?
배열이 정렬되지 않은 상태이거나<br>
데이터 크기가 작아 간단히 처리할 때<br>
빠른 구현이 더 중요하고 성능 요구가 낮을 때<br>

#### 확장 학습
센티널 기법: 배열 끝에 target을 미리 삽입해 경계 체크를 줄여 성능 소폭 개선<br>
std::find: <algorithm> 헤더에 구현된 선형 탐색 템플릿 함수 사용하기<br>
다음 학습: 정렬된 배열에서 O(log n)만에 값을 찾는 이진 탐색(Binary Search)<br>


</details><!-- 선형 탐색 (Linear Search) -->

<details><summary>이진 탐색 (Binary Search)</summary>
  
</details><!-- 이진 탐색 (Binary Search) -->

<details><summary>점프 탐색 (Jump Search)</summary>

</details><!-- 점프 탐색 (Jump Search) -->

<details><summary>보간 탐색 (Interpolation Search)</summary>

</details><!-- 보간 탐색 (Interpolation Search) -->

<details><summary>지수 탐색 (Exponential Search)</summary>

</details><!-- 지수 탐색 (Exponential Search) -->

<details><summary>삼진 탐색 (Ternary Search)</summary>

</details><!-- 삼진 탐색 (Ternary Search) -->

</details><!-- 탐색 알고리즘(Search Algorithms) -->
