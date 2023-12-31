# algorithm (알고리즘) 학습

## Chapter 1

### What are algorithms?

- 알고리즘은 주어진 문제를 해결하거나 주어진 조건을 달성하기 위해 수행될 수 있는 일련의 단계에 대한 정확하고 명확한 사양이다
- 알고리즘은 잘 정의된 계산 문제를 해결하기 위한 계산 절차이다
- 알고리즘은 일부 값 또는 값 집합을 입력으로 받아들이고 값 또는 값 집합을 출력으로 생성한다
- 알고리즘은 입력을 출력으로 변환한다
- 알고리즘은 입력 및 출력 값의 데이터 구조의 특성과 밀접한 관련이 있다

### Algorithm

- 알고리즘은 주어진 문제를 해결하도록 설계됨
- 알고리즘은 프로그래밍 언어의 복잡성과 한계를 고려하지 않음
- 알고리즘은 모호하지 않아야 함
    - 정확한 단계를 가져야 함
- 알고리즘은 크게 3가지 요소가 있음
    - 입력, 알고리즘, 출력
- 알고리즘은 프로그래밍 언어를 사용하여 구현될 것임
- 알고리즘 디자이너는 건축가와 같고 프로그래머는 석공, 목수, 배관공 등과 같음

### Algorithm vs Program

- Algorithm
    - 실제 프로그램에 대한 추상적인 설명
    - 종료되는 계산 절차
    - 유한한 단계 집합으로 구성
- Program
    - 알고리즘의 구체적인 구현
    - 특정 컴퓨터에서, 특정 언어로

### Presenting Algorithm

- `Desciption`: 알고리즘은 하나 이상의 예제를 사용하여 영어로 설명한다
- `Specification`: 알고리즘은 의사코드(pseudo code)로 제시된다
- `Validation`: 알고리즘이 모든 문제 사례에 대해 올바른 것으로 증명된다
- `Analysis`: 알고리즘의 실행 시간 또는 공간 복잡도를 평가한다

### The algorithms we design should be

- `Simple`: 단순한
    - `Unambiguous`: 모호하지 않은
- `Feasible`: 실현 가능한
    - 프로그래밍을 사용하여 구현할 수 있어야 함
- `Cost effective`
    - `CPU time`
    - `Memory used`
    - `Communication`
    - `Energy`

### Design and Analysis of Algorithms

- 알고리즘을 어떻게 설계할까?
    - `Brute force`: 무차별 대입
        - 발생할 수 있는 모든 경우를 탐색
    - `Divide and conquer`: 분할 및 정복
        - 하나의 문제를 작은 여러 개의 문제로 쪼갠 후 재귀적으로 각 문제를 해결한 후 이를 다시 합쳐 문제를 해결
    - `Dynamic programming`: 동적 프로그래밍
        - 큰 문제를 작은 문제로 나누어 푸는 문제
        - 정답을 구한 작은 문제를 어딘가에 메모해두고, 그보다 큰 문제를 풀 때 똑같은 작은 문제가 나타나면 메모해둔 작은 문제의 결과값 이용
    - `Greedy Algorithm`: 탐욕 알고리즘
        - 선택의 순간마다 최적의 상황만을 쫓아 최종적인 해답에 도달하는 방법
- 어떻게 알고리즘의 효율성을 분석할까?
    - `Time`: 시간
    - `Space`: 공간
    - `Energy`: 에너지

## Chapter 2

### The importance of sorting 

- 컴퓨터는 정렬에 가장 많은 시간을 소비함
- 정렬은 다양한 알고리즘을 가진 컴퓨터과학에서 가장 잘 연구된 문제

### Running time

- 실행 시간은 입력에 따라 다르다: 이미 정렬된 배열은 정렬하기가 더 쉽다
- 주요 단순화 규칙: 짧은 배열이 긴 배열보다 정렬하기 쉽기 때문에 실행 시간을 입력 크기로 매개 변수화한다
    - $T_A(n)$ = 길이 n 입력에서 A의 시간
- 일반적으로, 성능을 보장하기 위해 수행시간의 상한을 찾는다

### Kinds of analysis

- **Worst-case**: $T(n)$ = 크기 n의 입력에 대한 알고리즘의 최대 시간
- **Average-case**: $T(n)$ = 크기 n의 모든 입력에 대한 알고리즘의 예상 시간
- **Best-case**: 어떤 입력에 대해 빠르게 동작

### Analysis of Algorithm

- 알고리즘을 분석할 때 worst-case가 중요한 이유
- 최악의 경우는 알고리즘의 실행 시간에 대한 상한(알고리즘의 성능이 이보다 나쁠 수 없음)
- 일부 알고리즘의 경우 worst-case가 자주 발생

### Insertion Sort

- 삽입 정렬: 자료 배열의 모든 요소를 앞에서부터 차례대로 이미 정렬된 배열 부분과 비교하여, 자신의 위치를 찾아 삽입함으로써 정렬을 완성하는 알고리즘

#### INSERTION-SORT(A)

1. **for** j = 2 to length[A]
2. &nbsp;&nbsp;&nbsp;&nbsp;**do** key $\leftarrow$ A[j]
3. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;//insert A[j] to sorted sequence A[1 ... j - 1]
4. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;i $\leftarrow$ j - 1
5. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**while** i > 0 and A[i] > key
6. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**do** A[i + 1] $\leftarrow$ A[i]  //move A[i] one position right
7. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;i $\leftarrow$ i - 1
8. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;A[i + 1] $\leftarrow$ key

#### Insertion Sort analysis

- Worst case
    - Reverse sorted list: 역으로 정렬된 리스트
    - $O(n^2)$
- Best case
    - Sorted input: 정렬된 리스트
    - $O(n)$
- 삽입 정렬이 빠른 정렬 알고리즘인가?
    - n이 작은 경우에는 적당히 빠름
    - n이 클 경우에는 빠르지 않음

### Merge Sort

- 합병 정렬: 분할 정복 알고리즘의 하나로 n개의 요소의 배열을 정렬하기 위해 배열을 각각 n/2개의 요소를 가진 하위 배열로 분류하고 합병 정렬을 다시 호출하여 하위 배열들을 재귀적으로 정렬함으로써 정복한다. 그 뒤 두 개의 정렬된 배열을 병합하여 결합한다

#### MERGE-SORT(A, p, r)

1. **if** p < r
2. **then** q $\leftarrow \lfloor$ (p + r) / 2 $\rfloor$
3. &nbsp;&nbsp;&nbsp;&nbsp;MERGE-SORT(A, p, q)
4. &nbsp;&nbsp;&nbsp;&nbsp;MERGE-SORT(A, q + 1, r)
5. &nbsp;&nbsp;&nbsp;&nbsp;MERGE(A, p, q, r)

#### Merge

- 병합은 이미 정렬된 2개의 하위 배열과 빈 배열이 있다고 가정하여 작동
- 무한대가 있다고 가정, 무한대는 각 하위 배열의 끝에 있는 마지막 항목보다 더 크며 하위 배열의 끝에 도달했을 때 알려줌
- 각 하위 배열의 첫번째 항목을 보고 가장 작은 항목을 선택, 그 항목을 출력 배열로 이동을 항목의 개수만큼 반복

#### MERGE(A, p, q, r)

1. n1 $\leftarrow$ q - p + 1
2. n2 $\leftarrow$ r - q
3. create arrays L[1 ... n1 + 1] **and** R[1 ... n2 + 1]
4. **for** i $\leftarrow$ 1 **to** n1
5. &nbsp;&nbsp;&nbsp;&nbsp;**do** L[i] $\leftarrow$ A[p + i - 1]
6. **for** j $\leftarrow$ 1 **to** n2
7. &nbsp;&nbsp;&nbsp;&nbsp;**do** R[j] $\leftarrow$ A[q + j]
8. L[n1 + 1] $\leftarrow \infty$ 
9. R[n2 + 1] $\leftarrow \infty$ 
10. i $\leftarrow$ 1
11. j $\leftarrow$ 1
12. **for** k $\leftarrow$ p **to** r
13. &nbsp;&nbsp;&nbsp;&nbsp;**do if** L[i] $\leq$ R[j]
14. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**then** A[k] $\leftarrow$ L[i]
15. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;i $\leftarrow$ i + 1
16. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**else** A[k] $\leftarrow$ R[j]
17. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;j $\leftarrow$ j + 1

#### Analysis of Divide-and-Conquer

- 재귀 방정식으로 기술
- $T(n)$ 을 크기 n의 문제의 실행 시간이라고 가정
- $T(n) = \Theta(1)$ if $n \leq c$   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $aT(n / b) + D(n) + C(n)$ otherwise
    - a: 하위 배열의 수
    - n/b: 하위 배열의 크기
    - D(n): 분할 작업 비용
    - C(n): 정복 작업 비용

#### Analysis of MERGE-SORT

- **Base case**: n = 1, 크기가 1인 배열의 병합 정렬은 일정한 시간이 소요됨, $\Theta(1)$
- **Divide**: 합병 정렬의 분할 단계는 단지 하위 배열의 중간을 계산하는 것으로 일정한 시간이 소요됨, $D(n) = \Theta(1)$
- **Conquer**: 2번의 병합 정렬 호출을 하는데 각 호출은 매개 변수로 전달하는 하위 배열의 1/2을 처리, $2T(n/2)$
- **Combine**: n개의 요소 하위 배열에서 Merge를 실행하면 $\Theta(n)$이 걸리므로 $C(n) = \Theta(n)$
    

- $T(n) = \Theta(1)$ if $n = 1$   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $2T(n / 2) + \Theta(1) + \Theta(n)$ if $n > 1$

- $\Theta(1)$과 $\Theta(n)$은 관계가 없으므로 무시할 수 있다
- $T(n) = c$ if $n = 1$   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $2T(n / 2) + c(n)$ if $n > 1$

- 분할 단계는 얼마나 많은가?
- n이 2의 어떤 거듭제곱이라고 가정하면, 크기 n의 배열에 대해 배열을 크기 1의 하위 배열로 재귀적으로 세분화하는 $log_2n$ 단계가 필요
- 결과적으로 재귀 트리에 $log_2(n) + 1$개의 레이어를 가진다
- 각 배열 내에서 각 배열 항목을 적절한 위치에 배치해야 하기 때문에 반복 트리의 모든 계층은 n단계를 수행해야 한다
- 총 비용은 $cn(log_2n + 1) = cn(log_2n) + cn$
    - 저차항과 상수를 무시하면 $\Theta(n*log_2n)$을 얻을 수 있음

## Chapter 3

### Asymptotic notation

- 필수적인 부분에 초점을 맞추고 관련 없는 세부 사항을 무시하는 알고리즘의 계산 비용에 대해 이야기할 방법 필요
- 실제 단계를 정확하게 계산하는 것은 지루하고 일반적으로 유용하지 않음
- 작업마다 다른 시간이 소요됨(실행할 때마다 캐싱 등의 변화가 발생함)

- Asymtotic: 점근적
- 점근법은 극한에서 함수의 동작을 설명함(그 매개 변수의 값이 충분히 큰 경우)
- 알고리즘의 실행 시간의 증가 순서는 알고리즘의 실행 시간을 설명하는 식의 최상위 항으로 정의됨
- 식의 모든 하위 항뿐만 아니라 최상위 항의 계수 무시

### Big O: Upper bound

- $O(g(n))$ 은 함수들의 집합이다   
$O(g(n)) = f(n)$: 모든 $n \ge n_0$에 대해 $0 \le f(n) \le cg(n)$을 만족하는 양의 상수 $c$ 와 $n_0$이 존재한다
- 일반적으로 빅오 표기법은 수행 시간의 상한이기 때문에 중요
- 예)   
$7n - 2$ is $O(n)$   
모든 $n \ge n_0$에 대해 $7n - 2 \le cn$을 만족하는 $c > 0$과 $n_0 \ge 1$이 필요하다   
이는 $c = 7$과 $n_0 = 1$에 대해 만족한다

### Omega: Lower bound

- $\Omega(g(n))$ 은 함수들의 집합이다   
$\Omega(g(n)) = f(n)$: 모든 $n \ge n_0$에 대해 $0 \le cg(n) \le f(n)$을 만족하는 양의 상수 $c$ 와 $n_0$이 존재한다

### Theta: Upper and Lower bound

-   $\Theta(g(n))$ 은 함수들의 집합이다   
$\Theta(g(n)) = f(n)$: 모든 $n \ge n_0$에 대해 $0 \le c_1g(n) \le f(n) \le c_2g(n)$을 만족하는 양의 상수 $c_1, c_2$ 와 $n_0$이 존재한다
- 함수에서 빅오와 빅오메가의 공통부분 

### Some rules of thumb

- rule of thumb: 경험 법칙
- 곱셈 상수는 생략할 수 있다
    - $14n^2 \rightarrow n^2$, $7logn \rightarrow logn$
- 저차항 함수는 생략할 수 있다
    - $n + 5 \rightarrow n$, $n^2 + n \rightarrow n^2$
- $a > b$일 경우 $n^a$가 $n^b$를 지배한다
    - $n^{1.5}$ dominates $n^{1.4}$, so $n^{1.5} + n^{1.4} \rightarrow n^{1.5}$
- $a > b$일 경우 $a^n$이 $b^n$을 지배한다
    - $3^n$ dominates $2^n$
- 임의의 지수가 임의의 다항식을 지배한다
    - $3^n$ dominates $n^5$
- 임의의 다항식이 임의의 로그를 지배한다
    - $n^2$ dominates $nlogn$, $n$ dominates $log n$ or $log logn$
- 다른 변수들로 이루어진 차항에서 저차항을 생략하면 안된다
    - $(n^2 + m)$ &nbsp; $- \times \rightarrow n^2$

### Some examples of Big O

- $O(1)$: 상수, 투입 규모에 상관없이 고정된 작업량
    - 32비트 숫자 2개를 더한다
    - 숫자가 짝수인지 홀수인지 판별한다
    - 배열의 첫 20개 원소를 합한다
    - 이중 연결 리스트에서 하나의 요소를 삭제한다
- $O(logn)$: 로그와 관련된, 각 반복 시 입력의 일부(즉 절반)를 폐기한다
    - 이진 탐색
- $O(n)$: 선형, 입력의 각 요소에 일정한 양의 작업 수행
    - 연결 리스트에서 항목 찾기
    - 배열에서 가장 큰 요소 결정
- $O(nlogn)$: 로그 선형, 재결합에서 선형 작업량을 가진 분할 정복 알고리즘
    - 병합 정렬로 숫자의 리스트 정렬
- $O(n^2)$: 2차항, 데이터 위에서 반복되는 이중 중첩 루프
    - 삽입 정렬, 선택 정렬, ...
- $O(n^3)$: 3차항, 데이터 위에서 반복되는 삼중 중첩 루프
- $O(2^n)$: 기하급수적인
    - 가능한 모든 하위 집합 열거
    - 동적 프로그래밍을 사용하는 Traveling salesman 문제
- $O(n!)$
    - 모든 순열 열거

### Big O, Omega, Theta

- 병합 정렬 실행 시간을 $O(n(log_2n))$대신 $\Theta(n(log_2n))$으로 표현하는 이유?   
$\rightarrow$ 세타가 빅오보다 정확하기 때문에
- 병합 정렬 실행 시간을 $O(n(log_2n))$라고 하면, 병합 정렬의 점근적 상한에 대한 주장을 하는 것일뿐이지만, 병합 정렬의 실행 시간을 $\Theta(n(log_2n))$라고 하면, 병합 정렬의 점근적 상한과 하한에 대한 주장을 하는 것이다

## Chapter 4

### Divide and Conquer

- 좋은 분할 정복 알고리즘은 일반적으로 알고리즘의 쉬운 재귀적 버전을 의미
- 3단계
    - `Divide`: 문제를 여러 하위 문제로 나눈다
    - `Conquer`: 하위 문제를 재귀적으로 풀어서 정복한다   하위 문제 크기가 충분히 작을 때는 하위 문제만 풀면 됨
    - `Combine`: 하위 문제를 결합하여 원래 문제의 해결책을 만든다

### Recurrence

- 재귀는 더 작은 입력에 대한 함수의 값으로 설명하는 방정식 또는 부등식이다
- 예)   
$T(n) = \Theta(1)$    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;$aT(n/b)+D(n)+C(n)$

- 많은 알고리즘의 복잡성은 쉽게 재귀로 표현된다
- 재귀적 알고리즘의 복잡성은 쉽게 재귀로 표현된다

### Maximum Subarray Problem

- Maximum subarray problem: 숫자들로 이루어진 주어진 1차원 배열 A[1 ... n] 내에서 가장 큰 합을 갖는 연속적인 하위 배열을 찾는 작업
- brute-force방법으로 maximum subarray를 풀면 시간복잡도는 $O(n^2)$   
![brute-force](../image/MSP_bruteforce.jpg)
- brute-force 알고리즘보다 더 나은 알고리즘이 필요 $\rightarrow$ 분할 및 정복 알고리즘은 어떨까?
![divide and conquer](../image/MSP_divideconquer.jpg)
- 배열을 2개의 배열로 나눈다
    - 왼쪽 배열에 속하는 하위 배열
    - 오른쪽 배열에 속하는 하위 배열
    - 중간을 가로지르는 하위 배열
- A[low ... high]의 maximum subarray를 구한다고 가정할 때
    - 분할과 정복은 하위 배열의 중간점(mid)를 찾고 하위 배열 A[low ... mid]와 A[mid + 1 ... high]를 고려
    - 연속된 하위 배열 A[i ... j]는 3 영역 중 하나의 영역에 있어야 한다
        - entirely in A[low ... mid]
        - entirely in A[mid + 1 ... high]
        - crosses the midpoint

#### Find Max Crossing Subarray

- 중간점을 가로지르는 maximum subarray를 쉽게 찾을 수 있음
- A[i ... mid]와 A[mid + 1 ... j]의 maximun subarray를 찾아 결합하면 됨

- FIND-MAX-CROSSING-SUBARRAY(A, low, mid, high)
1. left-sum = $-\infty$
2. sum = 0
3. **for** i = mid **downto** low
4. &nbsp;&nbsp;&nbsp;&nbsp;sum = sum + A[i]
5. &nbsp;&nbsp;&nbsp;&nbsp;**if** sum > left-sum
6. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;left-sum = sum
7. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;max-left = i
8. right-sum = $-\infty$
9. sum = 0
10. **for** j = mid + 1 **to** high
11. &nbsp;&nbsp;&nbsp;&nbsp;sum = sum + A[j]
12. &nbsp;&nbsp;&nbsp;&nbsp;**if** sum > right-sum
13. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;right-sum = sum
14. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;max-right = j
15. **return** (max-left, max-right, left-sum + right-sum)

#### Find Maximum subarray

- 3가지 경우로 나누어 최적의 솔루션을 선택한다
    - 왼쪽 하위 배열
    - 교차 하위 배열
    - 오른쪽 하위 배열

- FIND-MAXIMUM-SUBARRAY(A, low, high)
1. **if** high == low
2. &nbsp;&nbsp;&nbsp;&nbsp;**return** (low, high, A[low])
3. **else** mid = $\lfloor$ (low + high) / 2 $\rfloor$
4. &nbsp;&nbsp;&nbsp;&nbsp;(left-low, left-high, left-sum) = FIND-MAXIMUM-SUBARRAY(A, low, mid)
5. &nbsp;&nbsp;&nbsp;&nbsp;(right-low, right-high, right-sum) = FIND-MAXIMUM-SUBARRAY(A, mid + 1, high)
6. &nbsp;&nbsp;&nbsp;&nbsp;(cross-low, cross-high, cross-sum) = FIND-MAX-CROSSING-SUBARRAY(A, low, mid, high)
7. &nbsp;&nbsp;&nbsp;&nbsp;**if** left-sum $\ge$ right-sum **and** left-sum $\ge$ cross-sum
8. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**return** (left-low, left-high, left-sum)
9. &nbsp;&nbsp;&nbsp;&nbsp;**elseif** right-sum $\ge$ left-sum **and** right-sum $\ge$ cross-sum
10. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**return** (right-low, right-high, right-sum)
11. &nbsp;&nbsp;&nbsp;&nbsp;**else** **return** (cross-low, cross-high, cross-sum)
- 시간복잡도는 $O(nlogn)$

### Methods for Solving Recurrences

#### Substitution Method

1. 풀이의 형태를 추측한다
2. 수학적 귀납법을 이용하여 상수를 찾고 풀이법이 작동함을 보인다
    - 풀이를 추측하기 쉬울 때 잘 작동한다
    - 상한 또는 하한에서 사용할 수 있다
- 예)   
$T(n) = 2T(n/2) + n$ = ?
- $T(n) = O(nlogn)$이라고 추측
- $T(n) \le cnlogn$을 어떤 $c$에 대해 증명
    - Inductive base: 어떤 작은 $n$에 대해 부등식이 성립함을 증명
        - $T(2) = 2T(1) + 2 = 4$
        - $cnlogn = c * 2 * log2 = 2c$   choose any $c \ge 2$
    - Assume true for $n/2$
        - $T(n/2) \ge c(n/2)log(n/2)$
    - Prove
        - $T(n) = 2T(n/2) + n$   
        $\le 2T(c(n/2)log(n/2)) + n$   
        $= cnlog(n/2) + n$   
        $= cnlogn - cn + n$   
        $\le cnlogn$  &nbsp;&nbsp;&nbsp;&nbsp; for $c \ge 2$   
        $= O(nlogn)$  &nbsp;&nbsp;&nbsp;&nbsp; for $c \ge 2$
- 재귀 방정식이 익숙해보인다면 비슷한 풀이를 추측할 수 있다
    - $T(n) = 2T(n/2+17) + n$
    - $T(N) = O(nlogn)$ 추측 가능
        - 왜? 17은 재귀방정식 풀이에 실질적으로 영향을 미칠 수 없다 (단지 상수이기 때문에)

#### Iterative Substitution

- 예)   
$T(n) = 0$ &nbsp;&nbsp;&nbsp;&nbsp; if $n = 0$   
$= T(n-1) + n$ &nbsp;&nbsp;&nbsp;&nbsp; if $n > 0$
- 원래 관계식에서 n을 n-1로 대체하면: $T(n-1) = T(n-2) + (n-1)$
- 원래 관계식에서 n-1을 위에서 구한 식으로 대체하면: $(T(n-2)+(n-1))+n$
- $T(n-2) = T(n-3) + (n-2)$임을 안다
- 위위의 식에서 $T(n-2)$를 위의 식으로 대체하면: $T(n) = (T(n-3)+(n-2))+(n-1)+n$
- 패턴을 확인할 수 있다
    - $T(n) = T(n-1)+n$
    - $T(n) = (T(n-2)+(n-1))+n$
    - $T(n) = (T(n-3)+(n-2))+(n-1)+n$
    - $\dots$
    - $T(n) = T(n-(n-2))+2+3+\dots+(n-2)+(n-1)+n$
    - $T(n) = T(n-(n-1))+2+3+\dots+(n-2)+(n-1)+n$
    - $T(n) = T(n-(n-0))+2+3+\dots+(n-2)+(n-1)+n$
    - $\Rightarrow T(n) = T(0)+1+2+3+\dots+(n-2)+(n-1)+n$
- $T(0) = 0$임을 알고있으므로 $T(n) = 0+1+2+3+\dots+(n-2)+(n-1)+n$
    - $T(n) = T(0)+1+2+3+\dots+(n-2)+(n-1)+n$의 합은 $T(n) = (n(n+1)/2) = 1/2n^2 + 1/2n$
    - 따라서 $O(n^2)$ 

#### Recursion Tree

- 각 노드는 재귀 함수 호출 집합에서 단일 하위 문제의 비용을 나타낸다
- 트리의 각 레벨 내에서 비용을 합산하여 레벨별 비용 집합을 얻는다
- 모든 레벨의 비용을 합산하여 재귀의 총 비용을 결정한다
- substitution method를 위한 좋은 추측을 생성하는 데 유용하다

#### Master Theorem

- $a \ge 1$, $b > 1$이고, $f(n)$이 점근적 양의 함수인 $T(n) = aT(n/b)+f(n)$형태의 재귀를 해결하기 위한 cookbook method를 제공한다
- 분할 정복 알고리즘은 $T(n) = aT(n/b) + D(n) + C(n)$의 형태가 반복되기 때문에 마스터 정리의 형태는 매우 편하다
- $T(n) = aT(n/b)+f(n)$
    - case 1) if $f(n) = O(n^{log_b{a-\varepsilon}})$ for $\varepsilon > 0$, then $T(n) = \Theta(n^{log_ba})$
    - case 2) if $f(n) = \Theta(n^{log_ba})$, then $T(n) = \Theta(n^{log_ba}logn)$
    - case 3) if $f(n) = \Omega(n^{log_b{a+\varepsilon}})$ for $\varepsilon > 0$ and $af(n/b) \le cf(n)$ for $c < 1$ then $T(n) = \Theta(f(n))$
- 위의 정리를 다시 말하면
    - 우선 $f(n)$과 $n^{log_ba}$를 비교한다
    - $f(n)$이 점근적으로 느리게 성장하면(case 1)
        - $T(n) = \Theta(n^{log_ba}$
    - 성장률이 같으면(case 2)
        - $T(n) = \Theta(n^{log_ba}logn)$
    - $f(n)$이 점근적으로 빠르게 성장하면(case 3)
        - $T(n) = \Theta(f(n))$
- 예)   
$T(n) = 16T(n/4)+n$
- $f(n)$과 $n^{log_ba}$를 비교한다
    - $f(n) = n$
    - $a = 16, b = 4$
    - $n^{log_ba} = n^{log_416} = n^2$
- $f(n) = n$은 $n^2$보다 점근적으로 느리게 성장한다
    - case 1) $T(n) = \Theta(n^{log_ba} = \Theta(n^2)$

## Chapter 6

### Heapsort

- 병합 정렬 및 삽입 정렬의 더 나은 특성들을 결합한다
    - 병합 정렬과 같이 실행 시간은 $O(nlogn)$이다
    - 삽입 정렬과 같이 제자리 정렬이다
- 알고리즘을 실행하는 동안 정보를 관리하기 위한 데이터 구조(heap)을 만든다
- 힙에는 정렬 이외에 우선 순위 큐가 있다

### Some Definitions

- In place sorting
    - 추가 메모리를 사용하지 않고, 원래의 데이터 구조 내에서 정렬을 수행
    - 주어진 데이터를 수정하며 정렬하는 방식(배열의 요소 교환 or 재배치)
    - 공간 사용을 줄이는 것이 중요
- Not in place (out of place) sorting
    - 주어진 데이터 구조를 정렬하기 위해 추가 메모리를 사용
    - 주어진 데이터를 수정하지 않고 정렬된 결과를 새로운 데이터 구조에 저장
    - 안정적인 정렬 알고리즘 - 동일한 키(값)를 가진 요소들의 순서 유지

### Full vs Complete Binary Trees

- 이진 트리 T는 각 노드가 단말 노드이거나 2개의 자식 노드가 있으면 전 이진 트리(full binary trees)이다
- n개의 레벨을 갖는 이진 트리 T는 마지막 레벨을 제외한 모든 레벨이 완전히 채워져 있고, 마지막 레벨의 모든 노드는 가능한 한 가장 왼쪽에 있으면 완전 이진 트리(complete binary tree)이다

### Representation of Complete Binary Tree

- 완전 이진 트리는 배열(포인터 없이)로 표현될 수 있음
- 루트 노드로 시작하여 레벨에서 레벨로 이동하는 노드에 레벨 내에서 왼쪽에서 오른쪽으로 번호를 지정
- 노드에 할당된 번호는 배열의 인덱스

### Additional Properties of Complete Binary Trees

- 루트 노드는 A[1]
- 만약 노드의 인덱스가 i라면
    - 부모 노드: $\lfloor i/2 \rfloor$
    - 왼쪽 자식 노드: $2i$
    - 오른쪽 자식 노드: $2i + 1$
- 배열을 완전한 이진 트리로 본다
    - 물리적으로는 선형 배열이지만
    - 논리적으로는 이진 트리(마지막 레벨 제외 모든 레벨이 채워져있는)

### Heap

- 힙(heap): 힙 속성을 만족시키는 완전 이진 트리
- `max-heap`: 루트 이외의 모든 노드 i에 대해 A[부모(i)] $\ge$ A[i] (부모 노드가 더 큼)
- `min-heap`: 루트 이외의 모든 노드 i에 대해 A[부모(i)] $\le$ A[i] (부모 노드가 더 작음)

#### Height

- 트리에서 노드의 높이: 노드에서 단말노드까지의 가장 긴 단순한 하향 경로의 가지 수
- 트리의 높이: 루트의 높이
- 힙의 높이: $\lfloor log n \rfloor$

#### Heap Characteristics

- Height(높이) = $\lfloor log n \rfloor$
- \# of leaves(단말노드의 개수) = $\lceil n/2 \rceil$
- \# of nodes of height h(높이 h에서의 노드의 개수) $\le \lceil n/2^{h+1} \rceil$

#### Heaps have 5 basic procedures

- `HEAPIFY`: 힙 속성을 유지한다
- `BUILD-HEAP`: 정렬되지 않은 배열로 힙을 만든다
- `HEAPSORT`: 배열을 제자리에서 정렬한다
- `EXTRACT-MAX`: 최대 요소를 선택한다
- `INSERT`: 새 요소를 삽입한다

##### Max Heapify

- Assumption: Left(i) and Right(i) are max-heaps
- MAX-HEAPIFY(A, i)
1. l $\leftarrow$ left(i)
2. r $\leftarrow$ right(i)
3. **if** l $\le$ heap-size[A] **and** A[l] > A[i]
4. &nbsp;&nbsp;&nbsp;&nbsp;**then** largest $\leftarrow$ l
5. &nbsp;&nbsp;&nbsp;&nbsp;**else** largest $\leftarrow$ i
6. **if** r $\le$ heap-size[A] **and** A[r] > A[largest]
7. &nbsp;&nbsp;&nbsp;&nbsp;**then** largest $\leftarrow$ r
8. **if** largest $\ne$ i
9. &nbsp;&nbsp;&nbsp;&nbsp;**then** exchange A[i] $\leftrightarrow$ A[largest]
10. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;MAX-HEAPIFY(A, largest)
- 수행 시간: $O(logn)$ or $O(h)$

##### Build Max Heap

- BUILD-MAX-HEAP(A)
1. heap-size[A] $\leftarrow$ length[A]
2. **for** i $\leftarrow \lfloor$ length[A]/2 $\rfloor$ **downto** 1 **do**
3. &nbsp;&nbsp;&nbsp;&nbsp;MAX-HEAPIFY(A, i)
- 수행 시간: $O(n)$

##### Heap Sort

- HEAP-SORT(A)
1. BUILD-MAX-HEAP(A)
2. **for** i $\leftarrow$ length[A] **downto** 2 **do**
3. &nbsp;&nbsp;&nbsp;&nbsp;exchange A[1] $\leftrightarrow$ A[i]
4. &nbsp;&nbsp;&nbsp;&nbsp;heap-size[A] $\leftarrow$ heap-size[A] - 1
5. &nbsp;&nbsp;&nbsp;&nbsp;MAX-HEAPIFY(A, 1)
- 수행 시간: $O(nlogn)$
- 힙 정렬은 힙을 데이터 구조로 사용함
- 힙 정렬은 제자리 정렬임
- 추가로 공간이 필요한가?
    - 아주 적은 양의 공간: 두 개의 배열 요소를 교환할 때 임시 저장소로 한 개의 추가 공간이 필요함

##### Priority Queue

- 속성
    - 각 요소는 값(우선 순위)과 연결됨
    - 우선 순위가 가장 높은(또는 가장 낮은) 키가 먼저 추출됨
    - FIFO(First Input First Out)이 아님!!
- 힙의 대중적이고 중요한 용도로 사용됨
- 최대 및 최소 우선 순위 큐
- 요소의 동적 집합 S를 유지함
- 각 집합 요소에는 키(= 연관된 값)가 있음
- 삽입 및 추출을 효율적으로 지원하는 것이 목표
- 적용
    - 운영 체제에서
        - 작업 예약
        - 운영 체제의 프로세스를 우선 순위에 따라 목록을 준비(목록은 매우 동적임)
    - 시뮬레이터에서
        - 이벤트 중심 시뮬레이터에서 시뮬레이션할 이벤트 목록을 발생 시간의 순서대로 유지   

![process state diagram](../image/priorityqueue_diagram.jpg)

###### Basic Operatioins

- 최대 우선 순위 큐에 대한 작업
    - `Insert(S, x)`: 요소 x를 집합 S에 삽입한다 $S \leftarrow S \cup \{x\}$
    - `Maximum(S)`: 키 값이 가장 큰 S의 요소를 반환한다
    - `Extract-Max(S)`: 키 값이 가장 큰 S의 요소를 제거하고 반환한다
    - `Increase-Key(S, x, k)`: 원소 x의 키 값을 새로운 값 k로 증가시킨다
- 최소 우선 순위 큐도 삽입, 최소, 최소값 추출, 키 감소를 지원한다

###### Heap Maximum

- HEAP-MAXIMUM(A)
1. **return** A[1]
- 힙의 최상위(루트)에 있는 요소를 반환한다
- 수행 시간: $\Theta(1)$

###### Heap Extract Max

- HEAP-EXTRACT-MAX(A)
1. **if** heap-size[A] < 1
2. &nbsp;&nbsp;&nbsp;&nbsp;**then error** "heap-underflow"
3. max $\leftarrow$ A[1]
4. A[1] $\leftarrow$ A[heap-size[A]]
5. heap-size[A] $\leftarrow$ heap-size[A] - 1
6. MAX-HEAPIFY(A, 1)
7. **return** max
- 수행 시간: $O(log n)$ (MaxHeapify의 수행시간에 지배됨)

###### Heap Increase Key

- HEAP-INCREASE-KEY(A, i, key)
1. **if** ket < A[i]
2. &nbsp;&nbsp;&nbsp;&nbsp;**then error** "new key is smaller then the current key"
3. A[i] $\leftarrow$ key
4. **while** i > 1 **and** A[Parent[i]] < A[i]
5. &nbsp;&nbsp;&nbsp;&nbsp;**do** exchange A[i] $\leftrightarrow$ A[Parent[i]]
6. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;i $\leftarrow$ Parent[i]
- 수행 시간: $O(log n)$

###### Heap Insert

- HEAP-INSERT(A, key)
1. heap-size[A] $\leftarrow$ heap-size[A] + 1
2. A[heap-size[A]] $\leftarrow -\infty$
3. HEAP-INCREASE-KEY(A, heap-size[A], key)
- 수행 시간: $O(log n)$

#### Heap Summary

- MAX-HEAPIFY&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $O(log n)$
- BUILD-MAX-HEAP&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $O(n)$
- HEAP-SORT&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $O(nlog n)$
- HEAP-MAXIMUM&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $O(1)$
- HEAP-EXTRACT-MAX&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $O(log n)$
- HEAP-INCREASE_KEY&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $O(log n)$
- HEAP-INSERT&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $O(log n)$

## Chapter 7

### Quick Sort

- 퀵 정렬은 분할 정복 알고리즘이다
- 하지만 병합 정렬과 다르다
    - 배열을 반으로 나누지 않는다
    - 피벗이라는 요소를 기반으로 배열을 나눈다
    - 분할 단계는 모든 작업을 수행한다, 병합 단계는 사소하다
- 하위 배열에 1개의 요소만 포함될 때까지 배열을 두 개의 하위 배열로 분할하여 왼쪽의 모든 값이 오른쪽의 값보다 작아지도록 반복한다

#### Quick Sort Algorithm

- QUICKSORT(A, p, r)
1. **if** p < r
2. &nbsp;&nbsp;&nbsp;&nbsp;**then** q $\leftarrow$ PARTITION(A, p, r)
3. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;QUICKSORT(A, p, q - 1)
4. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;QUICKSORT(A, q + 1, r)

#### Partition Algorithm

- PARTITION(A, p, r)
1. x $\leftarrow$ A[r]
2. i $\leftarrow$ p - 1
3. **for** j $\leftarrow$ p **to** r - 1
4. &nbsp;&nbsp;&nbsp;&nbsp;**do if** A[j] $\le$ x
5. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**then** i $\leftarrow$ i + 1
6. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;exchange A[i] $\leftrightarrow$ A[j]
7. exchange A[i + 1] $\leftrightarrow$ A[r]
8. **return** i + 1

### Performance of Quicksort

- 파티션의 균형 또는 불균형 여부에 따라 달라짐
- 파티션의 균형은 피벗 선택에 따라 달라짐
    - 균형적인 경우 병합 정렬만큼 빨리 실행됨
    - 불균형적인 경우 삽입 정렬만큼 느리게 실행됨

#### Worst/Best case partitioning

- Worst case
    - 하나의 파티션은 n - 1의 크기, 다른 파티션은 1의 크기일 때
- Best case
    - 두 파티션의 크기가 같을 때

#### Worst case performance

- 각 단계에서 최대로 불균형한 파티션이 있다고 가정, 각 단계에서 각 요소를 하나씩만 분할한다고 가정
- 파티션 과정이 n-1번 필요
- 파티션의 비용: $\Theta(n)$
- 퀵 정렬의 재귀방정식   
$T(n) = T(n-1) + T(0) + \Theta(n)$   
= $T(n-1) + \Theta(n)$   
= $\Theta(n^2)$

#### Best case performance

- 각 하위 문제의 크기는 $n/2$ 보다 작음
    - 하위 문제 중 하나의 크기는 $\lfloor n/2 \rfloor$
    - 다른 하위 문제으 ㅣ크기는 $\lceil n/2 \rceil - 1$
- 수행 시간에 대한 재귀방정식   
$T(n) \le 2T(n/2) + PartitionTime(n)$   
= $2T(n/2) + \Theta(n)$   
= $\Theta(nlogn)$

#### Average case

- 평균적 경우의 성능은 최악의 경우보다 최선의 경우에 가깝다
- 분할이 항상 9:1 이라고 가정
- 재귀방정식   
$T(n) \le T(9n/10) + T(n/10) + \Theta(n)$   
= $T(9n/10) + T(n/10) + cn$
- 분할이 99:1 이라면?   
$T(n) \le T(99n/100) + T(n/100) + \Theta(n)$
- 수행 시간은 여전히 $O(nlogn)$
- 상수라면 로그의 밑부분은 점근적 표기법에서 중요하지 않음
- 일정한 비로 분할하면 깊이 $\Theta(log n)$ 인 재귀 트리가 생성됨
- 따라서 일정한 비로 분할할 때마다 퀵 정렬은 $O(n log n)$ 안에서 수행됨

### Picking the Pivot

- 피벗을 어떻게 골라야 할까?
- 방법 1) S의 첫번째 요소 또는 마지막 요소를 선택한다
    - 랜덤으로 채워진 배열에 적합
    - 입력 S가 정렬되거나 대부분 정렬된 경우에는?
        - 나머지 요소들은 모든 S1이나 S2에 들어갈 것임

- 방법 2) 무작위로 피벗을 선택한다
    - 정말로 무작위인 경우에 적합
    - 여전히 최악의 경우를 만들 수 있음
    - 난수 생성기를 실행해야 함

- 방법 3) 3요소의 중간값을 피벗으로 선택한다
    - 피벗을 입력 배열의 중앙값으로 하는 것이 이상적
        - 중앙값: 정렬된 배열에서 중간에 있는 요소
    - 입력을 거의 동일한 크기의 두 파티션으로 나눔
    - 하지만 정렬하지 않고는 중간값을 빠르게 계산하는 것이 어려움
    - 그래서 대략적인 중간값을 구함
        - 피벗 = 제일 왼쪽, 제일 오른쪽, 중앙값 중에서의 중간값

### Quick Sort vs Insertion Sort

- 작은 배열의 경우 (N $\le$ 20)
    - 삽입 정렬이 퀵 정렬보다 빠름
- 퀵 정렬은 재귀적임
    - 작은 크기의 배열을 정렬하는 데 많은 시간을 소비할 수 있음
- 하이브리드 알고리즘
    - 문제의 크기가 작을 때 삽입 정렬을 사용하도록 전환

### Quick Sort vs Merge Sort

- 퀵 정렬의 주요 문제
    - 퀵 정렬은 재귀적 단계마다 입력 배열을 크기 1과 n-1의 하위 문제로 나눌 수 있음(최악의 경우 $\rightarrow O(n^2)$)   
$\Rightarrow$ 피벗을 현명하고 효율적으로 선택해야 함
- 병합 정렬은 일반적으로 병합 단계에서 임시 배열을 사용한 비제자리 정렬로 구현됨
    - 퀵 정렬은 제자리 정렬로 분할함

### Randomized Quick Sort

- 알고리즘의 평균적인 경우와 최악의 경우의 성능이 크게 다를 때, 최악의 경우를 마주칠 확률을 최소화할 수 있음
- 어떻게 임의의 요소를 중심으로 분할할까?
    - 수행 시간과 입력 순서는 무관하도록
    - 입력 분포에 대한 가정 불필요하게
    - 최악의 경우는 난수 생성기의 출력에 의해서만 결정되도록
- 입력을 랜덤화
    - 입력에 대해 주어진 집합에서 퀵 정렬에서 최악의 경우 성능을 내는 순열은 거의 없음
    - 하지만 무작위로 피벗을 선택하면 비효율적인 피벗을 얻는 일은 거의 없을 것
    - A[p...r]에서 임의로 피벗을 선택
    - 입력 배열을 랜덤화하는 초기 단계를 선택
    - 수행 시간과 입력 순서는 독립적이다

#### Randomized Partition

- RANDOMIZED-PARTITION(A, p, r)
1. i $\leftarrow$ RANDOM(p, r)
2. exchange A[r] $\leftrightarrow$ A[i]
3. **return** PARTITION(A, p, r)

#### Randomized Quicksort

- RANDOMIZED-QUICKSORT(A, p, r)
1. **if** p < r
2. **then** q $\leftarrow$ RANDOMIZED-PARTITION(A, p, r)
3. &nbsp;&nbsp;&nbsp;&nbsp;RANDOMIZED-QUICKSORT(A, p, q - 1)
4. &nbsp;&nbsp;&nbsp;&nbsp;RANDOMIZED-QUICKSORT(A, q + 1, r)

## Chapter 8

### Lower Bounds for Sorting

- 지금까지 정리한 정렬은 모두 "키 비교"에 의해 작동
    - 정렬에 사용된 키의 값을 비교함으로써 요소를 올바른 위치에 배치
- 병합 정렬과 힙 정렬 수행 시간 $\Theta(n log n)$
    - 키 비교에 의한 정렬의 하한
        - 어떤 알고리즘일지라도 해를 구하려면 적어도 하한의 시간복잡도만큼 필요!!

### Decision Tree Model

- 의사 결정 트리를 사용하면 비교 정렬을 추상적으로 볼 수 있다
- 의사 결정 트리는 특정 정렬 알고리즘을 사용하여 목록을 정렬할 때 수행되는 모든 가능한 비교를 나타낸다
- 가정
    - 모든 요소는 서로 구별된다
    - 모든 비교는 ai $\le$ aj의 형식이다
- a1: a2는 a1과 a2를 비교한다는 뜻
- <a2, a1, a3>는 a2 $\le$ a1 $\le$ a3라는 뜻
- 의사 결정 트리에서 <a1...a2>로 표현된 단말노드는 순서 a1 $\le$ ... $\le$ a2를 나타낸다

#### Permutations of n elements

- n개 원소의 순열은 n!개
- 원소의 모든 가능한 순열을 생성하는 의사 결정 트리에는 n!개의 단말노드들이 있어야 한다
- 루트 노드에서 단말 노드까지의 가장 긴 경로는 알고리즘의 최악의 경우 성능을 나타낸다
- 최악의 경우 성능은 의사 결정 트리의 높이이다

#### A Lower Bound for Worst Case

- 정리: 모든 비교 정렬 알고리즘은 최악의 경우 $\Omega(nlogn)$ 비교가 필요하다
- 증명
    - n개의 요소를 정렬하는 단말 노드의 수가 l개이고 높이가 h인 결정 트리를 생각해본다
    - n개 원소의 순열을 n!개이고, 입력에 대한 각 순열은 단말 노드여야 하므로 트리에 적어도 n!개의 노드가 있어야 한다
    - 높이가 h인 이진 트리는 $2^h$개 이하의 노드를 갖는다
    - 따라서 결정 트리는 $2^h$개 이하의 노드를 갖는다
    - n! $\le$ l $\le 2^h$
        - n! $\le 2^h$
        - 양변에 로그를 취하면
            - log(n!) $\le$ h
            - n에 스털링 근사값을 사용하면
                - n! > $(n/e)^n$
    - 따라서 h $\le log(n!) \le log(n/e)^n = n log n - n log e = \Omega(n log n)$

### Counting Sort

- Counting Sort(계수 정렬): 데이터 값을 직접 비교하지 않고, 각 숫자가 몇 개 있는지 개수를 세어 저장한 후에 정렬하는 알고리즘
1. A에 A[i]가 나타나는 횟수(빈도)를 찾는다
2. A[i]보다 작은 원소의 개수를 찾는다
3. A의 마지막 요소부터 시작하여 출력 배열의 올바른 위치에 A[i]를 배치하고, C[A[i]]를 하나씩 줄인다

- n개의 입력 요소 각각을 일부 정수 k에 대해 0~k 범위의 정수라고 가정
- 각 원소 x에 대해 x보다 작은 원소들의 개수를 찾는다
- 3개의 배열이 필요
    - 입력 배열 A[1...n]
    - 정렬된 출력을 위한 배열 B[1...n]
    - 각 원소가 발생하는 횟수를 계산하기 위한 배열 C[0...k] (임시 작업 저장소)

- COUNTING-SORT(A, B, k)
1. **for** i $\leftarrow$ 0 **to** k
2. &nbsp;&nbsp;&nbsp;&nbsp;**do** C[i] $\leftarrow$ 0
3. **for** j $\leftarrow$ 1 **to** length[A]
4. &nbsp;&nbsp;&nbsp;&nbsp;**do** C[A[j]] $\leftarrow$ C[A[j]] + 1
5. **for** i $\leftarrow$ 1 **to** k
6. &nbsp;&nbsp;&nbsp;&nbsp;**do** C[i] $\leftarrow$ C[i] + C[i - 1]
7. **for** j $\leftarrow$ length[A] **downto** 1
8. &nbsp;&nbsp;&nbsp;&nbsp;**do** B[C[A[j]]] $\leftarrow$ A[j]
9. &nbsp;&nbsp;&nbsp;&nbsp; C[A[j]] $\leftarrow$ C[A[j]] - 1

- 수행 시간: $\Theta(n+k)$
    - k = $O(n)$ 일 때 최악의 경우는 $O(n)$
    - 비교 정렬이 아니므로 (n log n)의 하한을 넘는다
    - 비교하지 않음: 요소의 실제 값을 사용하여 배열로 인덱싱

### Radix Sort

- Radix Sort(기수 정렬): 기수 별로 비교 없이 수행하는 알고리즘
- 일부 k진수에서 d자리 숫자로 키를 나타냄
    - key = $x_dx_{d-1} \dots x_2x_1$ where $0 \le x_i \le k - 1$
- 가정
    - d = $O(1)$, k = $O(n)$
- 정렬은 한번에 하나의 열만 처리
    - d자리 숫자의 경우, 최하위 숫자를 먼저 정렬
    - 모든 숫자가 정렬될 때까지 다음 최하위 숫자 정렬
    - 목록을 d번만 통과하면 됨

- RADIX-SORT(A, d)
1. **for** i $\leftarrow$ 1 **to** d **do**
2. use a stable sort to sort array A on digit i

- [stable sort algotithms 참조](#stable-sort-algorithms)

- 수행 시간
    - d자리의 수 n개가 주어지고, 각 자리가 최대 k개의 값을 가질 수 있을 때, $O(d(n+k))$
        - 숫자 당 정렬의 한 패스는 계수 정렬을 사용한다고 가정하면 $O(n+k)$
        - 각 자리마다 d번의 패스를 함
    - d = $O(1)$, k = $O(n)$을 가정하면 $O(n)$

### Bucket Sort

- Bucket Sort(버킷 정렬): 배열의 원소를 여러 버킷으로 분산하여 작동하는 정렬 알고리즘
- 가정
    - 원소가 0보다 크거나 같고 1보다 작은 수로 [0, 1) 균일하게 분배하는 과정에 의해 입력이 생성
- 동일한 크기의 n개의 버킷으로 나눈다
    - 1로 시작하면 버킷 1, 5로 시작하면 버킷 5 이런 식
- n개의 입력 값을 버킷에 분배한다
- 각 버킷을 정렬한다
- 각 버킷에 있는 요소를 나열하면서 순서대로 버킷을 살펴본다

- BUCKET-SORT(A)
- 입력: A[1...n], where 0 $\le$ A[i] < 1 for all i
- 보조 배열: 각 목록이 비어있는 연결 리스트 B[0...n - 1]
1. n $\leftarrow$ length[A]
2. **for** i $\leftarrow$ 1 **to** n
3. &nbsp;&nbsp;&nbsp;&nbsp;**do** insert A[i] **into** list B[$\lfloor$ nA[i] $\rfloor$]
4. **for** i $\leftarrow$ 0 **to** n - 1
5. &nbsp;&nbsp;&nbsp;&nbsp;**do** sort list B[i] with insertion sort
6. concatenate the lists B[i]s together in order
7. **return** the concatenated lists

- 수행 시간: $O(n)$

### Stable sort algorithms

- Stable sort(안정 정렬): 중복된 값을 입력 순서와 동일하게 정렬
- 삽입 정렬, 병합 정렬, 버블 정렬

### Unstable sort algorithms

- Unstable sort(불안정 정렬): 중복된 값이 입력 순서와 동일하지 않게 정렬됨
- 퀵 정렬, 선택 정렬, 계수 정렬

## Sorting Conclusion

### The importance of sorting

- [챕터 2의 importance of sorting 참조](#the-importance-of-sorting)

### Applications of Sorting

- 정렬이 매우 중요한 이유 중 하나는 일단 항목이 정렬되면 다른 많은 문제들이 쉬워지기 때문

- 검색
    - 이진 검색을 통해 사전에 항목이 있는지 여부를 $O(lg n)$ 시간 내에 테스트 할 수 있다
    - 검색 속도를 높이는 것은 정렬의 가장 중요한 응용
- 최근접 점의 쌍
    - n개의 숫자들과 서로 가장 가까운 쌍이 주어짐
    - 숫자가 정렬되면 가장 가까운 쌍이 정렬된 순서대로 서로 옆에 있으므로 $O(n)$의 선형 스캔으로 작업이 완료됨
- 요소의 고유성
    - 고유하거나 중복이 있는 n개의 항목들의 집합이 주어짐
    - 위 항목들을 정렬하고 선형 스캔을 수행하여 인접한 모든 쌍 확인
    -  최근접 점의 쌍의 특수한 경우
- 도수 분포
    - n개의 항목 집합이 주어졌을 때 어떤 요소가 가장 많이 발생하는지 여부
    - 위 항목들을 정렬하고 선형 스캔을 수행하여 인접한 동일 항목들의 길이 측정
- 중앙값과 선택
    - 집합에서 k번째로 큰 항목 찾기
    - 키 값이 배열에서 정렬된 순서로 배치되면 배열의 k번째 위치를 보면 k번째로 큰 키 값을 일정한 시간 내에 찾을 수 있음

### In place vs not in place

[챕터 6의 some definitions 참조](#some-definitions)

### Stable vs unstable

[챕터 8의 stable sort algorithms 참조](#stable-sort-algorithms)
[챕터 8의 unstable sort algorithms 참조](#unstable-sort-algorithms)

#### Why Heap sort is unstable?

- 3, 3, 2, 1의 예시가 있을 때
    - 앞의 3을 3(a), 뒤의 3을 3(b)라 한다
    - 3(a), 3(b), 2, 1
- 힙 정렬은 max-heap에서 첫번째 요소인 최댓값을 추출한 후 마지막 위치에 놓는 것으로 시작
    - 3(b), 2, 1, 3(a)
    - 그러면 크기가 1 줄어들고 max-heapify 연산이 적용되므로 새로운 크기는 3이며 힙 속성을 만족하는 3개의 요소가 있다
    - 최종 정렬 결과는 1, 2, 3(b), 3(a)
- 힙 정렬은 안정적이지 않다

#### Why Quick sort is unstable?

- 퀵 정렬은 원래 위치를 고려하지 않고 피벗의 위치에 따라 요소의 자리를 바꾸기 때문에 불안정하다

#### Radix Sort

- RADIX-SORT(A, d)
1. **for** i $\leftarrow$ **to** d **do**
2. use a <U>stable</U> sort to sort array A on digit

- 기수 정렬에서 안정적 정렬을 사용
- 기수 정렬에서 사용할 수 없는 정렬은?
    - 힙 정렬, 퀵 정렬 같은 불안정 정렬

### Types of Sorting Algorithms

- $O(n^2)$ 정렬 알고리즘
    - 삽입 정렬, 선택 정렬, 버블 정렬
- $O(nlogn)$ 정렬 알고리즘
    - 힙 정렬, 병합 정렬, 퀵 정렬

### When to use which sorting algorithm?

- 크기가 큰 배열
    - 병합 정렬, 퀵 정렬
- 크기가 작은 배열
    - 삽입 정렬, 선택 정렬
    - 재귀는 비용이 많이 든다
- 평균적인 경우에서 병합 정렬 또는 퀵 정렬
    - 요소 비교 비용
    - 요소 이동/전환 비용

#### Small Array in Quick Sort

- S가 작은 경우 재귀 호출의 비용이 비싸다(간접적인 처리 시간, 메모리)
- 일반적인 전략
    - 입력 크기가 한계점보다 작으면, 입력 크기가 작을 때 효율적인 정렬(예 - 삽입 정렬)을 사용
    - 양호한 한계 범위는 5 ~ 20
    - 크기가 2인 배열의 대해 3개의 원소 중 중앙값을 피벗으로 하는 것을 피해야 함
    - 위의 전략 사용 시 수행 시간을 15% 단축 가능

#### Merge sort vs Quick sort

- 분할 정복 알고리즘(재귀적)
- 평균적인 경우 $O(nlogn)$
- 병합 정렬의 최악의 경우는 $O(nlogn)$, 퀵 정렬의 최악의 경우는 $O(n^2)$
- 병합 정렬은 2n개의 추가 공간이 필요(비제자리 정렬)
- 퀵 정렬은 추가 공간 불필요(제자리 정렬)

- 병합 정렬
    - 인기 있는 알고리즘 중 가장 적은 비교 횟수
    - 많은 데이터 이동/복사 (합병)
    - 안정 정렬
- 퀵 정렬
    - 비교 횟수가 더 많음
    - 데이터 이동이 더 적음
    - 불안정 정렬

#### Sorting methods

- 비교에 기반한 정렬
    - $O(n^2)$ 방법: 삽입 정렬, 버블 정렬
    - 평균적으로 $O(nlogn)$: 퀵 정렬
    - $O(nlogn)$ 방법: 병합 정렬, 힙 정렬

- 비교에 기반하지 않은 정렬
    - 계수 정렬
    - 버킷 정렬
    - 기수 정렬

### Performance characteristic of sorting algorithm

![sorting algorithm table](../image/sorting_character.jpg)

## Chapter 11

### Review

- 배열 리스트
    - 접근: $O(1)$
    - 삽입(평균): $O(n)$
    - 삭제(평균): $O(n)$
- 연결 리스트
    - 접근: $O(n)$
    - 삽입(평균): $O(n)$
    - 삭제(평균): $O(n)$
- 이진 탐색 트리
    - 접근(균형): $O(log n)$
    - 삽입(균형): $O(log n)$
    - 삭제(균형): $O(log n)$

- 해싱이 무엇이길래 유용한가?
    - 삽입, 검색, 삭제 연산이 필요한 응용 분야가 많음(사전 연산이 필요)
    - 응용
        - 데이터베이스 검색
        - 웹 페이지 캐싱(웹 검색)
        - 조합 탐색(게임 트리)

- 사전 연산의 수행 목표
    - 평균적으로 $O(log n)$ 을 만족 $\Rightarrow$ 이진 탐색 트리(BST)
    - 최악의 경우 $O(log n)$ 을 만족 $\Rightarrow$ 균형 이진 탐색 트리(AVL tree)
    - 평균적으로 $O(1)$ 을 만족 $\Rightarrow$ 해싱(hashing) (하지만 최악의 경우에선 $O(n)$ )

- 해싱(Hashing)
    - 해시(hash)
        - 작은 조각으로 잘게 썰다
        - 혼란시키다, 뒤죽박죽이 되다
    - 사전을 구현할 때 중요하고 유용한 기술
    - 평균적인 경우 $O(1)$ 에서 삽입, 삭제, 검색 연산을 지원하는 기술
    - 요소를 정렬해야 하는 작업(예 - 최소값 찾기)은 효율적이지 않음

### Dictionary & Hash Tables

- Dictionary
    - 키를 사용하여 색인화된 항목을 저장하기 위한 동적 집합 데이터 구조
    - 삽입, 검색, 삭제 연산을 지원
    - 응용
        - 컴파일러의 심볼 테이블(symbol table)
        - 운영 체제의 메모리 관리 테이블
        - 대규모 분산 시스템

- Hash Tables
    - 효과적인 사전 구현 방법
    - 보통의 배열의 일반화

### Direct-address Tables

- 직접 주소 테이블은 일반적인 배열
- 직접 주소 지정을 용이하게 함
    - 키 값이 k인 요소를 배열의 k번째 위치를 인덱싱하여 얻을 수 있음
- 가능한 모든 키에 대해 하나의 위치를 가진 배열을 할당할 여유가 있을 때 적용
    - 키의 전체 집합이 작을 때
- $O(1)$ 인 사전 연산 구현 가능

### Hash Table

- 직접 주소 테이블의 어려움
    - 전체 집합 $U$ 가 크다면 $|U|$ 크기의 테이블 T를 저장하는 것은 비현실적이며 불가능할 수 있음
- 실제 저장된 키들의 집합 $K$ 가 $U$ 에 비해 매우 작을 수 있음
    - 해시 테이블에서는 요소 검색에 $O(1)$ 이 걸리지만 저장공간 요구사항은 $O(|K|)$로 줄일 수 있음

- 표기법
    - $U$ : 모든 가능한 키의 전체 집합
    - $K$ : 실제로 사전에 저장된 키의 집합
    - $|K|$ = n
- $U$ 가 매우 클 때
    - 배열은 실용적이지 않음
    - $|K| << |U|$
- $|K|$ : hash tables 에 비례하는 크기의 테이블을 사용
    - 직접 주소화 능력은 사라짐
    - 해시 테이블의 슬롯에 키를 매핑하는 함수 정의

### Hash function

- 해시 함수 h
    - $U$ 에서 해시 테이블 T[...m - 1]의 슬롯으로 매핑
        - h : $U \rightarrow$ {0, 1, ..., m - 1}
- 배열의 경우, 키 k를 슬롯 A[k]에 매핑
- 해시 테이블의 경우, 키 k는 슬롯 T[h[k]]에 매핑되거나 해시된다
- h[k]는 키 k의 해시 값(hash value)
- 해시 함수는 키를 테이블 주소로 변환
- 무엇이 좋은 해시 함수를 만드는가?
    - 계산 용이
    - 충돌 횟수 최소화
    - 편향 없음
- simple uniform hashing: m개의 슬롯이 있으면 중복 없이 확률적으로 m개의 슬롯에 골고루 나누어지는 것

#### Good Approaches for Hash Functions

- 밀접하게 관련된 키가 동일한 슬롯에 해시될 가능성 최소화
    - pt와 pts같은 문자열은 서로 다른 슬롯에 해시해야 함
- 키 분포에 존재할 수 있는 모든 패턴과 독립적인 해시 값 도출

##### The Division Method

- 아이디어
    - 키 k를 m 개의 슬롯 중 하나에 매핑
    - h(k) = k mod m
- 장점
    - 빠르고, 하나의 연산만 필요
- 단점
    - m의 특정한 값은 별로
        - 2의 거듭제곱, 소수가 아닌 수
- m을 잘 선택하려면?
    - 2나 10의 거듭제곱과 가깝지 않은 소수가 좋음

##### The Multiplication Method

- 아이디어
    - 키 k에 상수 A를 곱한다 (0 < A < 1)
    - kA의 분수 부분을 추출한다
    - 분수에 m을 곱한다
    - 결과의 floor값을 구한다
    - $\lfloor$ m(kA - $\lfloor$ kA $\rfloor$ ) $\rfloor$
- 장점
    - m의 값이 중요하지 않음
- 단점
    - 나눗셈 방법보다 느림

#### Universal Hashing

- 해시 함수 H를 선택하기 위한 확률적 알고리즘
- 두 개의 서로 다른 값 x, y에 대해 h(x) = h(y)일 확률이 H가 랜덤 함수일 경우와 같을 때
- 두 키가 충돌할 확률은 무작위 & 랜덤으로 두 개의 슬롯을 선택하는 1/m 이다

- 장점
    - 저장할 키와 상관없이 평균적으로 좋은 결과
    - 어떤 입력도 최악의 경우를 발생시키지 않음
    - 성능 저하는 무작위 선택이 비효율적인 해시 함수를 반환할 때만 발생(확률이 작음)

### Issue with Hashing

- 여러 키가 같은 슬롯에 해시될 수 있음
    - 충돌(두 키가 동일한 슬롯에 해시됨) 발생 가능
    - 충돌이 최소화되도록 해시 함수 설계
    - 충돌을 피하는 것은 불가능
        - 충돌 해결 기법 설계
- 최악의 경우 $\Theta(n)$ 소요
    - 모든 연산을 $\Theta(1)$ 으로 이루어지게 할 수 있음

### Collision

- Collision(충돌): 두 개 이상의 키가 동일한 슬롯에 해시되는 것
- 키 집합 $K$ 에 대해
    - $|K| \le $ m 이면 해시 함수에 따라 충돌이 발생할 수도 있고 발생하지 않을 수도 있음
    - $|K|$ > m 이면 충돌이 반드시 발생(동일한 해시 값을 가진 키가 최소 2개 이상)
- 좋은 해시 함수를 사용하더라도 충돌을 완전히 피하는 것은 어려움

### Collision Resolution Techniques

- `Chaining(체이닝)`
    - 동일한 슬롯에 해시되는 모든 요소를 연결 리스트에 저장
    - 해시 테이블 슬롯에 연결 리스트의 맨 앞에 있는 포인터를 저장

- `Open Addressing(개방 주소법)`
    - 모든 요소는 해시테이블 자체에 저장됨
    - 충돌이 발생하면 체계적인 절차를 사용하여 요소를 테이블의 빈 슬롯에 저장

#### Hashing with Chaining

- Chained-Hash-Insert(T, x)
    - 리스트 T[h(key[x])]의 맨 앞에 x를 삽입
    - 최악의 경우: $O(1)$
- Chained-Hash-Delete(T, x)
    - 리스트 T[h(key[x])]에서 x를 삭제
    - 최악의 경우: 단일 연결 리스트 - 리스트의 길이에 비례, 이중 연결 리스트 - $O(1)$
- Chained-Hash-Search(T, k)
    - 리스트 T[h(key[x])]에서 k를 탐색
    - 최악의 경우: 리스트의 길이에 비례

##### Analysis of Hashing with Chaining

- 최악의 경우
    - n개의 키가 모두 동일한 슬롯에 해시되었을 경우
    - 탐색 시간은 $\Theta(n)$ + 해시 함수 계산 시간

- 평균적 경우
    - 해시 함수가 n개의 키를 m개의 슬롯에 얼마나 잘 분배하는지에 따라 다름
    - simple uniform hashing이라고 가정
        - 임의의 요소는 동일한 확률로 m개의 슬롯 중 어느 하나에 해시 됨(충돌 가능성은 1/m)
    - 리스트의 길이
        - T[j] = $n_j$, j = 0, 1, ... , m - 1
    - 테이블에 있는 키의 개수
        - n = $n_0 + n_1 + ... + n_{m-1}$
    - $n_j$의 평균
        - E[ $n_j$ ] = $\alpha$ = n/m

##### Load Factor of a Hash Table

- 해시 테이블 T의 부하율(Load factor)
    - $\alpha$ = n/m
    - n = 테이블에 저장된 요소의 개수
    - m = 테이블의 슬롯 수
- $\alpha$ 는 체인에 저장된 요소의 평균 개수를 부호화함
- $\alpha$ 는 1보다 작을 수도, 같을 수도, 클 수도 있음

###### Case 1: Unsuccessful Search

- 정리
    - simple uniform hashing을 가정할 때 해시 테이블에서 검색에 실패하면 수행 시간은 $\Theta(1 + \alpha)$
- 증명
    - 키 k를 검색하지 못함: T[h(k)]
    - 예상 리스트 길이: E[ $n_{h(k)}$ ] = $\alpha$ = n/m
    - 검색에 실패할 경우 검사하는 요소의 예상 개수: $\alpha$
    - 총 수행 시간: $O(1)$ (해시 함수 계산) + $\alpha$ = $\Theta(1 + \alpha)$

###### Case 2: Successful Search

- 정리
    - 검색에 성공하면 수행시간은 $\Theta(1 + \alpha)$
- 증명
    - $x_i$ 를 테이블에 삽입한 i번째 원소라고 하고, $k_i$ = key[ $x_i$ ]라고 한다
    - 모든 i, j에 대해 $X_{ij} = l\{h(k_i) = h(k_j)\}$ 라고 정의
    - simple uniform hashing $\Rightarrow$ $Pr\{h(k_i) = h(k_j)\}$ = 1/m $\Rightarrow$ E[ $X_{ij}$ ] = 1/m
    - 검색에 성공할 경우 검사하는 요소의 예상 개수: $O(1 + 1 + \alpha / 2 - \alpha / 2n)$ = $O(1 + \alpha)$

##### Analysis of Search in Hash Tables

- 만약 n = $O(m)$ 이면 $\alpha$ = n/m = $O(m)$ / m = $O(1)$
    - 탐색은 평균적으로 상수적 시간이 소요
- 최악의 경우 삽입은 $O(1)$
- 이중 연결 리스트일 때 최악의 경우 삭제는 $O(1)$
- 모든 사전 연산은 평균적으로 $O(1)$

#### Open Addressing

- 모든 키를 저장할 수 있는 충분한 연속 메모리가 있는 경우(m > N) $\Rightarrow$ 키를 테이블 자체에 저장
- 연결 리스트를 사용할 필요가 없음
- 아이디어
    - 삽입: 만약 슬롯이 차있으면 빈 슬롯을 찾을 때까지 다른 슬롯에 삽입 시도
    - 탐색: 삽입과 같은 방식 시도
    - 삭제: 어려움..
- 탐색 시간은 탐색 순열 길이에 따라 달라짐

##### Generalize hash function notation

- 해시 함수에는 키 값과 탐색 번호의 두 가지 인수가 포함됨
    - h(k, p), p = 0, 1, ... , m - 1
- 탐색 배열
    - < h(k, 0), h(k, 1), ... , h(k, m - 1) >
    - < 0, 1, ... , m - 1 >의 순열이어야 함
    - 가능한 순열이 m!개 있음
    - 좋은 해시 함수는 m!개의 모든 탐색 순열을 생성할 수 있어야 함

##### Linear probing

- `Linear probing`: 선형 탐색
- 삽입
    - 아이디어
        - 충돌이 있을 때 테이블에서 다음으로 사용 가능한 위치를 확인
        - h(k, i) = ($h_1$(k) + i) mod m, i = 0, 1, 2, ...

- 검색
    - 세 가지 경우
        1. 키 값이 테이블의 위치와 동일한 경우
        2. 테이블의 위치가 비어있는 경우
        3. 키 값이 테이블의 위치와 다른 경우
    - 3번째 경우에는 요소가 발견되거나 빈 위치가 발견될 때까지 다음 상위 인덱스 탐색

- 삭제
    - 문제점
        - 슬롯을 빈 것으로 표시할 수 없음
        - 해당 슬롯이 차지된 후 삽입된 키를 검색할 수 없음
    - 해결
        - 슬롯에 표지값 DELETED 표시
    - 삭제 된 슬롯을 나중에 삽입에 사용할 수 있음
    - 검색을 통해 모든 키를 찾을 수 있음

- Primary Clustering Problem(군집화 문제)
    - 다른 슬롯보다 가능성이 높은 일부 슬롯이 있음
    - 저장된 슬롯이 긴 덩어리가 생김 $\Rightarrow$ 삽입 및 검색의 평균 시간 증가
    - 충돌이 나면 뒤 슬롯에 데이터를 넣어 하나의 데이터 덩어리를 이루기 때문에 특정 위치에만 밀집하는 현상

##### Quadratic probing

- `Quadratic probing`: 제곱 탐색
- h(k, i) = (h'(k) + $c_1i$ + $c_2i^2$) mod m, $c_1 \neq c_2$
- 초기 탐색의 위치는 T[h'(k)]이며 이후 탐색 위치는 탐색 번호 i의 제곱의 양을 더한 위치임
- < 0, 1, ... , m - 1 >의 완전한 순열을 얻으려면 $c_1$, $c_2$, m을 제한해야 함
- 2차 군집화가 생길 수 있음
    - 두 개의 키가 초기 탐색 위치가 같으면 탐색 순열이 동일

##### Double Hashing

- `Double Hashing`: 이중 해싱
1. 하나의 해시 함수를 사용하여 첫번째 슬롯 결정
2. 두번째 해시 함수를 사용하여 탐색 순열 h(k, i) = ( $h_1$(k) + i $h_2$(k)) mod m, i = 0, 1, ... 에 대한 증가량 결정
- 처음 탐색: $h_1$(k)
- 장점: 군집화를 피할 수 있음
- 단점: 요소를 삭제하기 어려움

##### Analysis of Open Addressing

- 분석은 부하율 $\alpha$ 측면에서 이루어짐
- 가정
    - 테이블이 완전히 채워지지 않는다고 가정, n < m, $\alpha$ < 1
    - uniform hashing을 가정
    - 삭제 연산은 없음
    - 모든 탐색 배열이 발생할 가능성이 같음
- 탐색 실패
    - 점유된 셀을 탐색할 확률 = $\alpha$
    - 빈 셀을 탐색할 확률 = 1 - $\alpha$
    - 탐색이 2단계로 종료될 확률 = $\alpha$ (1 - $\alpha$)
    - 탐색이 k단계로 종료될 확률 = $\alpha^{k-1}$ (1 - $\alpha$)
    - 탐색의 평균 단계수 = $1 \over 1 - \alpha$
- 탐색 성공
    - 탐색 성공 시 평균 탐색 수는 최대 ($1 / \alpha$) log ( $1 / (1 - \alpha)$ )

### Other Hashing Application

- content hashing
- Caching(캐싱)
    - 대용량 비디오 파일을 다운로드 한 경우 전체 파일을 다시 다운로드 하는 대신 새 버전을 사용할 수 있는지 확인하고 파일의 해시 값과 서버의 해시 값 비교
- 파일 확인 / 오류 확인
    - 파일 자체 대신 파일의 해시 비교
- 지문 채취

## Chapter 12

### Binary Search Tree Representation

- 트리 표현
    - 각 노드가 객체인 연결 데이터 구조
- 노드 표현
    - 키 영역
    - 위치 데이터
    - Left: 왼쪽 자식을 가리키는 포인터
    - Right: 오른쪽 자식을 가리키는 포인터
    - p: 부모를 가리키는 포인터 (p[root[T]] = NIL)

### Binary Search Tree Property

- 만약 y가 x의 왼쪽 부분 트리에 있다면
    - key [y] $\le$ key [x]
- 만약 y가 x의 오른쪽 부분 트리에 있다면
    - key [y] $\ge$ key [x]

### Binary Search Tree

- 다양한 동적 연산 집합 지원
    - `SEARCH(탐색)`, `MINIMUM(최솟값)`, `MAXIMUM(최댓값)`, `PREDECESSOR(선임자)`, `SUCCESSOR(후임자)`, `INSERT(삽입)`, `DELETE(삭제)`
- 수행 시간
    - 평균적 경우: $\Theta(log n)$
        - 트리의 높이가 log n
    - 최악의 경우: $\Theta(n)$
        - 트리가 n개의 노드로 이루어진 선형 체인일 때

### Traversing a Binary Search Tree

- `Inorder`(중위 순회)
    - 왼쪽 하위 트리 방문 후 루트 방문 후 오른쪽 하위 트리 방문 (left, root, right)
- `Preorder` (전위 순회)
    - 루트 방문 후 왼쪽 하위 트리, 오른쪽 하위 트리 방문 (root, left, right)
- `Postorder` (후위 순회)
    - 왼쪽 하위 트리, 오른쪽 하위 트리 방문 후 루트 방문 (left, right, root)

### Searching for a Key

- 트리의 루트에 대한 포인터와 키 k가 주어졌을 때
    - k 키가 있는 노드의 포인터 반환
    - 그렇지 않으면 NIL 반환
- 아이디어
    - 루트에서 시작: k와 현재 노드의 키를 비교하여 경로 추적
        - 키가 같은 경우: 키 찾음
        - k < key[x]: x의 왼쪽 하위 트리에서 탐색
        - k > key[x]: x의 오른쪽 하위 트리에서 탐색

#### Tree Search

- TREE-SEARCH(x, k)
1. **if** x = NIL or k = key[x]
2. &nbsp;&nbsp;&nbsp;&nbsp;**then return** x
3. **if** k < key[x]
4. &nbsp;&nbsp;&nbsp;&nbsp;**then return** TREE-SEARCH(left[x], k)
5. &nbsp;&nbsp;&nbsp;&nbsp;**else return** TREE-SEARCH(right[x], k)

- 수행 시간: 트리의 높이가 h일 때 $O(h)$

### Finding the Minimum

- NIL에 도달할 때까지 루트에서 왼쪽 자식 포인터를 따라간다

#### Tree Minimum

- TREE-MINIMUM(x)
1. **while** left[x] $\neq$ NIL
2. &nbsp;&nbsp;&nbsp;&nbsp;**do** x $\leftarrow$ left[x]
3. **return** x

- 수행 시간: 트리의 높이가 h일 때 $O(h)$

### Find the Maximum

- NIL에 도달할 때까지 루트에서 오른쪽 자식 포인터를 따라간다

#### Tree Maximum

- TREE-MAXIMUM(x)
1. **while** right[x] $\neq$ NIL
2. &nbsp;&nbsp;&nbsp;&nbsp;**do** x $\leftarrow$ right[x]
3. **return** x

- 수행 시간: 트리의 높이가 h일 때 $O(h)$

### Find the Successor

- 정의: x의 후임 = y, key[y]는 key[x]보다 큰 값들 중에서 가장 작은 키
- case 1: x의 오른쪽이 비어 있지 않을 때
    - x의 후임 = x의 오른쪽에서 최솟값
- case 2: x의 오른쪽이 비어 있을 때
    - 현재 노드가 왼쪽 자식 노드가 될 때까지 트리 위로 이동, x의 후임은 현재 노드의 부모
    - 더 이상 진행할 수 없는 경우(루트에 도달한 경우)에는 x가 가장 큰 원소임

#### Tree Successor

- TREE-SUCCESSOR(x)
1. **if** right[x] $\neq$ NIL
2. &nbsp;&nbsp;&nbsp;&nbsp;**then return** TREE-MINIMUM(right[x])
3. y $\leftarrow$ p[x]
4. **while** y $\neq$ NIL **and** x = right[y]
5. &nbsp;&nbsp;&nbsp;&nbsp;**do** x $\leftarrow$ y
6. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;y $\leftarrow$ p[y]
7. **return** y

- 수행 시간: 트리의 높이가 h일 때 $O(h)$

### Find the Predecessor

- 정의: x의 선임 = y, key[y] 는 key[x]보다 작은 값들 중에서 가장 큰 키
- case 1: x의 왼쪽이 비어 있지 않을 때
    - x의 선임 = x의 왼쪽에서 최댓값
- case 2: x의 왼쪽이 비어 있을 때
    - 현재 노드가 오른쪽 자식 노드가 될 때까지 트리 위로 이동, x의 선임은 현재 노드의 부모
    - 더 이상 진행할 수 없는 경우(루트에 도달한 경우)에는 x가 가장 작은 원소임

### Insertion

- 이진 탐색 트리에 v값을 삽입한다
- 아이디어
    - 만약 key[x] < v라면 x의 오른쪽 자식 노드로 이동, 아니면 왼쪽 자식 노드로 이동
    - x가 NIL이라면 정확한 위치 찾음
    - 만약 v < key[y] 라면 새로운 노드를 y의 왼쪽 자식으로 삽입, 아니면 오른쪽 자식으로 삽입
    - 루트에서 시작하여 트리의 아래로 내려가며 다음을 유지
        - 포인터 x: 하향 경로(현재 노드) 추적
        - 포인터 y: x의 부모(추적 포인터)

#### Tree Insert

- TREE-INSERT (T, z)
1. y $\leftarrow$ NIL
2. x $\leftarrow$ root[T]
3. **while** x $\neq$ NIL
4. &nbsp;&nbsp;&nbsp;&nbsp;**do** y $\leftarrow$ x
5. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**if** key[z] < key[x]
6. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**then** x $\leftarrow$ left[x]
7. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**else** x $\leftarrow$ right[x]
8. p[z] $\leftarrow$ y
9. **if** y = NIL
10. &nbsp;&nbsp;&nbsp;&nbsp;**then** root[T] $\leftarrow$ z
11. &nbsp;&nbsp;&nbsp;&nbsp;**else if** key[z] < key[y]
12. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**then** left[y] $\leftarrow$ z
13. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**else** right[y] $\leftarrow$ z

- 수행 시간: $O(h)$

### Deletion

- 이진 탐색 트리에서 지정된 노드 z를 삭제한다
- 아이디어
    - case 1: z의 자식 노드가 없을 때
        - z의 부모 노드를 NIL로 만들어 z 삭제
    - case 2: z가 하나의 자식 노드만 가질 때
        - z의 부모 노드가 z 대신 z의 자식 노드를 가리키게 해서 z 삭제
    - case 3: z가 두 개의 자식 노드를 가질 때
        - z의 후임 y는 z의 오른쪽 하위 트리에 있는 최소 노드
        - y에는 자식이 없거나 오른쪽 자식이 하나 있음(왼쪽 자식은 없음)
        - y를 트리에서 삭제(case 1 or case 2를 통해)
        - z의 키와 위치 데이터를 y로 대체

### Tree Delete

- TREE-DELETE(T, z)
1. **if** left[z] = NIL or right[z] = NIL
2. &nbsp;&nbsp;&nbsp;&nbsp;**then** y $\leftarrow$ z
3. &nbsp;&nbsp;&nbsp;&nbsp;**else** y $\leftarrow$ TREE-SUCCESSOR(z)
4. **if** left[y] $\neq$ NIL
5. &nbsp;&nbsp;&nbsp;&nbsp;**then** x $\leftarrow$ left[y]
6. &nbsp;&nbsp;&nbsp;&nbsp;**else** x $\leftarrow$ right[y]
7. **if** x $\neq$ NIL
8. &nbsp;&nbsp;&nbsp;&nbsp;**then** p[x] $\leftarrow$ p[y]
9. **if** p[y] = NIL
10. &nbsp;&nbsp;&nbsp;&nbsp;**then** root[T] $\leftarrow$ x
11. &nbsp;&nbsp;&nbsp;&nbsp;**else if** y = left[p[y]]
12. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**then** left[p[y]] $\leftarrow$ x
13. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**else** right[p[y]] $\leftarrow$ x
14. **if** y $\neq$ z
15. &nbsp;&nbsp;&nbsp;&nbsp;**then** key[z] $\leftarrow$ key[y]
16. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;copy y's satellite data into z
17. **return** y

- 수행 시간: $O(h)$

### BST: Summary

- SEARCH &nbsp;&nbsp;&nbsp;&nbsp; $O(h)$
- PREDECESSOR &nbsp;&nbsp;&nbsp;&nbsp; $O(h)$
- SUCCESOR &nbsp;&nbsp;&nbsp;&nbsp; $O(h)$
- MINIMUM &nbsp;&nbsp;&nbsp;&nbsp; $O(h)$
- MAXIMUM &nbsp;&nbsp;&nbsp;&nbsp; $O(h)$
- INSERT &nbsp;&nbsp;&nbsp;&nbsp; $O(h)$
- DELETE &nbsp;&nbsp;&nbsp;&nbsp; $O(h)$

- 트리의 높이가 작으면 위의 작업들이 빠르지만, 그렇지 않으면 연결 리스트의 성능과 비슷함
