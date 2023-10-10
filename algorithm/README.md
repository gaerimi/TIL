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
    - $(n^2 + m)$ &nbsp;&nbsp;$- \times \rightarrow n^2$

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
