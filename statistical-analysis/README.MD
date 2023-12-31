# statistical analysis(통계적 분석) 학습

## Chapter 1 데이터

- 파이썬으로 실습할 때를 가정
- import pandas as pd
    - pandas라는 라이브러리를 pd라는 이름으로 가져온다
- `pd.read_csv`
    - csv 파일을 읽어들일 수 있다
    - pandas의 DataFrame이라는 데이터 구조로 반환 - 2차원 표 데이터 구조
        - 하나의 열만 추출할 경우 Series라는 데이터 구조 반환 - 1차원 데이터 구조

### 데이터의 크기

- DataFrame(df라고 하겠음)의 크기는 shape를 참조해 알 수 있음
- `df.shape`
- 첫번째: 데이터에 대한 수(레코드 수)
- 두번째: 변수에 대한 수(칼럼 수)

### 변수의 종류

- 질적 변수: 선택이 필요한 변수, 종류를 구별하기 위한 변수
    - 명의 척도: 단순히 분류하기 위한 변수
    - 순서 척도: 순서 관계나 대소 관계에 의미가 있는 변수

- 양적 변수: 양을 표현하는 변수
    - 간격 척도: 대소 관계와 함께 그 차이에도 의미를 두는 변수
    - 비례 척도: 대소 관계, 차이, 비 모두에 의미가 있는 변수


- 이산형 변수
    - 하나하나의 값을 취하는 변수
    - 서로 인접한 숫자 사이에 값이 존재하지 않음
    - 주사위 눈, 결석 횟수, 결석 학생 수

- 연속형 변수
    - 연속적인 값을 취할 수 있는 변수
    - 어떤 두 숫자 사이에도 반드시 숫자가 존재
    - 길이, 무게, 시간

## Chapter 2 1차원 데이터 정리

- import numpy as np
    - numpy라는 라이브러리를 np라는 이름으로 가져온다
- %precision 3
    - 주피터 노트북에서 실습할 때 출력을 소수점 이하 3자리로 제한한다
- pd.set_option( ' precision ' , 3)
    - DataFrame의 출력을 소수점 이하 3자리로 제한
    - 오류 발생 시 pd.options.display.precision = 3 또는 pd.set_option('display.precision', 3)
- `df.head()`
    - df의 처음 5행을 표시

### 데이터 중심의 지표

- 평균값
    - 데이터를 모두 더한 뒤, 데이터의 개수로 나누어 구한다
    - sum(scores) / len(scores)
    - `np.mean(scores)`
    - `scores.mean()`
    - `scores_df.mean()`

    ![공식](../image/mean.jpg)
    - $\bar x$ (엑스 바)

- 중앙값
    - 데이터를 크기 순서대로 나열할 때 정확하게 중앙에 위치한 값
    - 이상값에 영향을 덜 받음
    - 데이터의 개수 n이 홀수라면 $(n + 1) \over 2$
    - 데이터의 개수 n이 짝수라면 $n \over 2$ 와 $n \over 2 + 1$ 의 평균
    - `np.median(scores)`
    - `scores_df.median()`


    - 절사평균
        - 양쪽을 좀 자르고 남은 요소들의 평균
        - 이상값에 영향을 덜 받음
        - 정보의 손실이 적음

- 최빈값
    - 데이터에서 가장 많이 나타나는 값
    - `pd.Series([배열]).mode()`

### 데이터의 산포도 지표

- 편차
    - 각 데이터가 평균으로부터 떨어져 있는 정도
    - 평균 - 데이터 값
    - mean = np.mean(scores)
        - deviation = scores - mean
    - 편차 평균은 항상 0

- 분산
    - 편차 제곱의 평균
    - `np.mean(deviation ** 2)`
    - `np.var(scores)`
    - `scores_df.var()`
    - Numpy의 기본 분산은 표본분산
    - Pandas의 기본 분산은 불편분산
        - ddor = 1일 경우 불편분산, 0이면 표본분산
    
    ![공식](../image/variation.jpg)

- 표준편차
    - 분산에 제곱근을 취한 것 = 편차 제곱의 평균에 제곱근을 취한 것
    - `np.sqrt(np.var(scores, ddof = 0))`
    - `np.std(scores, ddof = 0)`

    ![공식](../image/stddev.jpg)

-----------
- 범위
    - 데이터의 최댓값과 최솟값만으로 산포도를 표현하는 방법
    - `np.max(scores) - np.min(scores)`
    - $Rg = x_{max} - x_{min}$

- 사분위 범위
    - 데이터의 상위수%에 위치하는 값과 하위수%에 위치하는 값의 차이를 취하는 방법
    - 하위 25%: 제1사분위수 Q1
        - scores_Q1 = np.percentile(scores, 25)
    - 하위 50%: 제2사분위수 Q2
        - scores_Q2 = np.percentile(scores, 50)
    - 하위 75%: 제3사분위수 Q3
        - scores_Q3 = np.percentile(scores, 75)
    - 사분위 범위 $IQR = Q3 - Q1$
        - scores_IQR = scores_Q3 - scores_Q1

------------
- `pd.Series(scores).describe()`
    - 데이터 개수
    - 평균
    - 표준편차
    - 최솟값
    - 하위 25%
    - 하위 50%
    - 하위 75%
    - 최댓값

### 데이터의 정규화

- 표준화
    - 데이터에서 평균을 빼고 표준편차로 나누는 작업
    - 표준화된 데이터 = 표준화 변량 = Z 점수
    - $z_i = \frac{x_i - \bar x}{S}$
    - z = (scores - np.mean(scores)) / np.std(scores)
    - 표준화된 데이터의 평균은 0, 표준편차는 1

- 편찻값
    - 평균이 50, 표준편차가 10이 되도록 정규화한 값
    - $z_i = 50 + 10 \times \frac{x_i - \bar x}{S}$
    - z = 50 + 10 * (scores - np.mean(scores)) / np.std(scores)

### 1차원 데이터의 시각화

- 도수분포표
    - 분할된 구간과 데이터의 개수를 표로 정리한 것
    - 계급: 구간
    - 도수: 각 계급에 속한 데이터 수
    - 계급폭: 각 구간의 폭
    - 계급수: 계급의 수
    - `np.histogram(...)`
        - freq, _ = np.histogram(scores, bins = 10, range = (0, 100))
        - bins: 계급수
        - range: 최솟값, 최댓값 지정



    - 계급값: 계급의 중앙값
    - 상대도수: 전체 데이터에 대해서 해당 계급의 데이터가 차지하는 비율
        - $도수 \over 전체 도수$ 
    - 누적상대도수: 해당 계급까지의 상대도수의 합
        - `np.cumsum`
    - 최빈값: 최대가 되는 계급의 계급값
        - 도수분포표를 만드는 방법에 좌우됨(계급폭이 달라지면 최빈값도 달라짐)

- 히스토그램
    - 도수분포표를 막대그래프로 나타낸 것
    - Matplotlib 라이브러리 필요
        - import matplotlib.pyplot as plt
            - Matplotlib의 pyplot 모듈을 plt라는 이름으로 가져온다
        - %matplotlib inline
            - 그래프가 주피터 노트북 위에 표시된다
    - `ax.hist(...)`

- 상자그림
    - 데이터의 분포와 이상값을 시각적으로 파악 가능
    - 분위수 범위의 Q1, Q2, Q3, IQR 사용
    - 상자는 IQR을 나타냄, 수염은 Q1 - 1.5IQR부터 Q3 + 1.5IQR을 나타냄

## Chapter 3 2차원 데이터 정리

### 두 데이터 사이의 관계를 나타내는 지표

- 양의 상관관계
    - 하나가 높을 때 다른 하나도 높은 경향
- 음의 상관관계
    - 하나가 높을 때 다른 하나는 낮은 경향
- 무상관
    - 하나가 다른 하나에 직접적으로 영향을 미치지 않을 때


- 공분산
    ![공식](../image/covariance.jpg)

    - `np.cov(A,B,ddof = 0)`
        - 공분산 행렬(분산공분산 행렬)

- 상관계수
    ![공식](../image/correlatioincoefficient.jpg)

    - 공분산을 각 데이터의 표준편차로 나눈 값
    - 항상 -1 ~ 1 사이의 값을 취함
        - 양의 상관관계일수록 1에 가까워짐
        - 음의 상관관계일수록 -1에 가까워짐
        - 무상관이면 0이 됨
    - `np.corrcoef(A,B)`
        - 상관행렬
    - `scores_df.corr()`
        - 상관행렬

### 2차원 데이터의 시각화

- 산점도
    - `ax.scatter(A, B)`
        - A가 x축의 데이터, B가 y축의 데이터

- 회귀직선
    - $y = \beta _0 + \beta _1x$
    - A를 x, B를 y라 했을 때
    - `np.polyfit(A, B, 1)`
        - 계수 $\beta _0$, $\beta _1$ 을 구한다
    - `np.poly1d(polyfit)`
        - 회귀직선을 반환한다

- 히트맵
    - 히스토그램의 2차원 버전으로 색을 이용해 표현하는 그래프
    - `ax.hist2d(A, B, bin, range)`
    - 색이 진할 수록 많은 데이터를 가지고 있다

### 앤스컴의 예

- 동일한 지표를 가지고 있어도 그림으로 표현하면 달라질 수 있다

## Chapter 4 추측통계의 기본

### 모집단과 표본

- 모집단: 추측하고 싶은 관측 대상 전체
- 표본: 추측에 사용하는 관측 대상의 일부분
- 표본추출: 모집단에서 표본을 골라내는 일
- 표본 크기(샘플 사이즈): 골라낸 표본의 수
- 표본통계량: 표본을 바탕으로 계산한 평균이나 분산, 상관계수 등
- 모수: 모집단의 평균이나 분산, 상관계수 등
- 추정량: 표본평균으로 모평균을 추측할 때, 표본평균을 모평균의 추정량이라고 한다
- 추정값: 표본의 데이터를 이용하여 계산한 결과
-----------------

- 무작위추출: 임의로 표본을 추출하는 방법
    - seed(시드)를 0으로 하는 무작위추출은 항상 동일한 결과
- 복원추출: 여러 차례 동일한 표본을 선택하는 방법
    - `np.random.choice(배열, 수)`
- 비복원추출: 동일한 표본은 한 번만 선택하는 방법
    - `np.random.choice(배열, 수, replace=False)`

### 확률 모형

- 확률: 무작위추출과 같은 불확정성을 수반한 현상을 해석하기 위해 사용하는 것
- 확률 모형: 무작위추출 혹은 주사위를 모델링한 것
---------------

- 확률변수: 취하는 값과 그 값이 나올 확률이 결정되어 있는 것(결과를 맞힐 수는 없음)
- 시행: 확률변수의 결과를 관측하는 것
- 실현값: 시행에 의해 관측되는 값
- 사건: 시행 결과로 나타날 수 있는 일
- 근원 사건: 세부적으로 분해할 수 없는 사건
- 상호배반: 동시에 일어날 수 없는 사건
---------------

- 확률분포: 확률변수가 어떻게 움직이는지를 나타낸 것
- 공정한 주사위의 확률분포
    - 모든 눈의 확률이 $1 \over 6$ 로 같다
- 불공정한 주사위의 확률분포
    - 눈의 확률은 $눈 \over 21$ 이다

### 추측통계의 확률

- 무작위추출에서 표본의 크기가 커지면, 표본 데이터의 상대도수는 실제의 확률분포에 근사
- 표본 평균은 모평균을 중심으로 분포
    - 무작위추출에 의한 표본평균으로 모평균 추측 가능

## Chapter 5 이산형 확률변수

### 1차원 이산형 확률변수

- 확률변수 x가 취할 수 있는 값의 집합 $\{ x_1, x_2, ... \}$
- X가 $x_k$ 라는 값을 취하는 확률 $P(X = x_k) = p_k$ (k = 1, 2, ...)
- 확률질량함수(확률함수)
    - $f(x) = P(X = x)$
- 확률분포: 확률변수가 취할 수 있는 값과 그 확률의 구체적인 대응
    - 확률변수의 확률분포가 결정되면 그 확률변수의 움직임이 정해짐


- 확률의 성질
    - 확률은 0 이상이다
    - 모든 확률을 더하면 1이다

- 누적분포 함수
    - X가 x이하가 될 때의 확률을 반환하는 함수
    - $F(x) = P(X \le x) = \sum_{x_k \le x} f(x_k)$

- 확률변수의 변환
    - 확률변수 X에 2를 곱하고 3을 더한 2X + 3도 확률변수
    - 확률변수를 표준화할 때 중요한 연산

----------------

- 1차원 이산형 확률변수의 지표

- 기댓값
    - 확률변수의 평균
    - 확률변수를 무제한 시행하여 얻어진 실현값의 평균
    - 무제한 시행이 불가하므로 확률변수가 취할 수 있는 값과 확률의 곱의 총합
        - $E(x) = \sum_k x_kf(x_k)$
    - $\mu$ 또는 $E(x)$
    - 확률변수 X를 2X + 3으로 변환한 Y의 기댓값
        - $E(Y) = E(2X + 3) = \sum_k (2X_k + 3)f(x_k)$
        - $E(g(X)) = \sum_k g(x_k)f(x_k)$
    - 기댓값의 선형성
        - a,b를 실수 X를 확률변수로 했을 때
            - $E(aX + b) = aE(x) + b$

- 분산
    - $V(X) = \sum_k (x_k - \mu)^2f(x_k)$
        - $\mu$ 는 확률변수 X의 기댓값
        - 기호로 $\sigma$ 사용 $\sigma^2$ 이나 $V(X)$로 표기
            - $\sigma$ 는 확률변수 X의 표준편차
    - 이산형 확률변수의 분산
        - $V(g(X)) = \sum_k (g(x_k) - E(g(X)))^2f(x_k)$
    - 분산의 공식
        - a,b를 실수, X를 확률변수라고 하면
            - $V(aX + b) = a^2V(X)$

### 2차원 이산형 확률변수

- 결합확률분포
    - 1차원 확률분포 2개를 동시에 다룸(X, Y)
    - (X, Y)가 취할 수 있는 값의 조합으로 이루어진 집합 $\{(x_i, y_j) | i = 1, 2, ... ; j = 1, 2, ...) \}$
    - 확률변수 X가 $x_i$, 확률변수 Y가 $y_j$를 취하는 확률
        - $P(X = x_i, Y = y_i) = p_{ij}$ (i = 1, 2, ... ; j = 1, 2, ...)

- 확률의 성질
    - 확률은 반드시 0이상
    - 전체 확률은 1

- 주변확률분포
    - 확률변수 (X, Y)는 결합확률분포에 의해 동시에 정의되지만, 개별 확률변수에만 흥미가 있을 때
    - $f_X(x) = \sum_k f_{XY}(x, y_k)$

-----------

- 2차원 이산형 확률변수의 지표
- 기댓값
    - $\mu_X = E(X) = \sum_i \sum_j x_if_{XY}(x_i, y_j)$
    - 기댓값의 선형성
        - $E(aX + bY) = aE(X) + bE(Y)$

- 분산
    - X에 관한 편차 제곱의 기댓값
    - $\sigma^2_X = V(X) = \sum_i \sum_j (x_i - \mu_X)^2f_{XY}(x_i, y_j)$
    - $V(g(X, Y)) = \sum_i \sum_j (g(x_i, y_j) - E(g(X, Y)))^2f_{XY}(x_i, y_i)$

- 공분산
    - 두 확률변수 X, Y 사이의 상관
    - $\sigma_{XY} = Cov(X, Y) = \sum_i \sum_j (x_i - \mu_X)(y_j - \mu_Y)f_{XY}(x_i, y_j)$
    - 분산과 공분산의 공식
        - $V(aX + bY) = a^2V(X) + b^2V(Y) + 2abCov(X, Y)$

- 상관계수
    - $\rho_{XY} = \rho(X, Y) = \frac{\sigma_{XY}}{\sigma_X \sigma_Y}$

## Chapter 6 대표적인 이산형 확률분포

- 비모수적 기법: 모집단의 확률분포에 어떠한 가정도 하지 않는 것
- 모수적 기법: '모집단이 이와 같은 성질일 것이므로 이러한 형태를 가지는 확률분포일 것이다'라는 가정을 하고, 그 뒤에 확률분포의 기댓값이나 분산을 결정하는 소수의 파라미터를 추측하는 방법
- `from scipy import stats`
    - 통계 계산을 할 때 편리한 라이브러리

### 베르누이 분포

- 가장 기본적인 이산형 확률분포
- 확률변수가 취할 수 있는 값이 0과 1밖에 없음
- 베르누이 시행: 베르누이 분포를 따르는 확률변수의 시행
    - 1은 성공, 0은 실패
- 1이 나오는 확률은 p, 0이 나오는 확률은 1 - p
- 파라미터가 p인 베르누이 분포 Bern(p)
- 확률함수
    ![확률함수](../image/bernfunc.jpg)

- 베르누이 분포의 기댓값과 분산
    - X ~ Bern(p)라고 할 때
    - 기댓값: E(X) = p
    - 분산: V(X) = p(1-p)

- `rv = stats.bernoulli(p)`
    - 인수로 매개변수 p를 취하고 Bern(p)를 따르는 rv_frozen object 반환
- `rv.pmf()`
    - 확률함수 계산 (매개변수로 0 또는 1)
    - 인수로 리스트 사용 가능
- `rv.cdf()`
    - 누적 밀도함수 계산
    - 인수로 리스트 사용 가능
- `rv.mean()`
    - 기댓값 계산
- `rv.var()`
    - 분산 계산

![요약 정리](../image/bernsummary.jpg)

### 이항분포

- 성공 확률인 p인 베르누이 시행을 n번 했을 때의 성공 횟수가 따르는 분포
- 확률함수
    ![확률함수](../image/binfunc.jpg)
- 이항분포의 기댓값과 분산
    - X ~ Bin(n, p)라고 할 때
    - 기댓값: E(X) = np
    - 분산: V(X) = np(1 - p)

- `rv = stats.binom(n, p)`
    - 이항분포를 따르는 확률변수 생성

![요약 정리](../image/binsummary.jpg)

### 기하분포

- 베르누이 시행에서 처음 성공할 때까지 반복한 시행 횟수가 따르는 분포
- 확률함수
    ![확률함수](../image/gefunc.jpg)
- 기하분포의 기댓값과 분산
    - X ~ Ge(p)라고 할 때
    - 기댓값: E(X) = $1 \over p$
    - 분산: V(X) = $(1 - p) \over p^2$

![요약 정리](../image/gesummary.jpg)

### 포아송 분포

- 임의의 사건이 단위 시간당 발생하는 건수가 따르는 확률분포
- 확률함수
    ![확률함수](../image/poifunc.jpg)
- $Poi(\lambda)$ 는 단위 시간당 평균 $\lambda$ 번 발생하는 임의의 사건이 단위 시간에 발생하는 건수가 따르는 분포
- 포아송 분포의 기댓값과 분산
    - X ~ $Poi(\lambda)$ 라고 할 때
    - 기댓값: E(X) = $\lambda$
    - 분산: V(X) = $\lambda$

![요약 정리](../image/poisummary.jpg)

## Chapter 7 연속형 확률변수

- 적분
    - SciPy의 integral 모듈 사용
    - from scipy import integrate
    - 적분 계산 결과에 문제가 없다는 warning 출력
        - warnings.filterwarnings('ignore', category=integrate.IntegrationWarning) warning이 출력되지 않도록 함

### 1차원 연속형 확률변수

- 연속형 확률변수
    - 확률변수가 취할 수 있는 값이 연속적인 확률변수
    - 예) 룰렛

- 확률밀도함수
    - 확률변수가 취할 수 있는 값: 구간 [a, b]
    - 확률은 확률밀도함수(PDF) 또는 밀도함수 f(x)에 의해 정의
    - 어떤 특정 값을 취하는 확률로는 정의되지 않음
    - 확률변수 X가 $x_0 \le x_1$ 의 구간에 들어가 확률 $P(x_0 \le X \le x_1)$ 로 정의됨
    - $P(x_0 \le X \le x_1) = \int_{x_0}^{x_1} f(x)dx$
    - 밀도함수 f(x)와 x축, 두 직선 $x = x_0$, $x = x_1$ 으로 둘러싸인 영역의 면적

- `integrate.quad`(피적분함수, 적분 시작 범위, 적분 끝 범위)
    - 적분값과 추정오차 반환 (적분값, 추정오차)

- 확률의 성질
    - $f(x) \ge 0$
    - $\int_{-\infty}^\infty f(x)dx = 1$

- 함수의 최솟값
    - scipy.optimize의 minimize_scalar 사용
    - from scipy.optimize import minimize_scalar
    - min = `minimize_scalar`(f)
    - min.fun
        - 함수의 최솟값은 fun이라는 인스턴스 변수에

- 확률밀도함수 삼각형의 면적을 적분으로 구하기
    - integrate.quad(f, -np.inf, np.inf)[0]
        - `np.inf`: 무한대
        - 0번째 요소가 적분값이므로 0번째 요소만 확인

---------

- 누적분포함수(분포함수)
    - 확률변수 X가 x이하가 될 때의 확률을 반환하는 함수
    - $F(x) = P(X \le x) = \int_{-\infty}^x f(x)dx$
    - 단조증가함수
        - x가 증가할 때 y는 감소하지 않는 함수

--------

- 확률변수의 변환
    - X가 연속형 확률변수이면
    - Y = 2X + 3인 Y도 연속형 확률변수
    - Y의 확률밀도함수 g(y)
    - $g(y) = \{^{\frac{(y - 3)}{2} \quad (3 \le y \le 5)}_{0 \quad (otherwise)}$
    - 확률분포함수 G(y)
    - $G(y) = P(Y \le y) = \int_{-\infty}^y g(y)dy$
    
```python
y_range = [3, 5]
def g(y):   //확률밀도함수
    if y_range <= y <= y_range[1]:
        return (y - 3) / 2
    else:
        return 0

def G(y):   //누적분포함수
    return integrate.quad(g, -np.inf, y)[0]
```
------------------

- 1차원 연속형 확률변수의 지표

- 기댓값
    - $\mu = E(X) = \int_{-\infty}^{\infty} xf(x)dx$
    - $E(g(X)) = \int_{-\infty}^{\infty} g(x)f(x)dx$
    - 기댓값의 선형성 성립
        - E(2X + 3) = 2E(X) + 3

- 분산
    - $\sigma^2 = V(X) = \int_{-\infty}^{\infty} (x - \mu)^2 f(x)dx$
    - $V(g(X)) = \int_{-\infty}^{\infty} (g(x) - E(g(X)))^2 f(x)dx$
    - 분산의 공식 성립
        - $V(aX + b) = a^2V(X)$

### 2차원 연속형 확률변수

- 결합확률밀도함수
    - 확률변수가 취할 수 있는 값의 조합: $\{(x,y)|a \le x \le b; c \le y \le d \}$
    - 위를 정의역으로 하는 함수 f(x,y)에 의해 2차원 연속형 확률변수 (X,Y)가 정의됨
    - f(x,y)를 결합확률밀도함수라고 함
    - $P(x_0 \le X \le x_1, y_0 \le Y \le y_1) = \int_{x_0}^{x_1} \int_{y_0}^{y_1} f(x,y)dxdy$
    - 예) 불공정한 룰렛 A, B에서 A + B = X, A = Y로 한 2차원 확률변수 (X,Y)

- 확률의 성질
    - $f(x,y) \ge 0$
    - $\int_{-\infty}^{\infty} \int_{-\infty}^{\infty} f(x,y) = 1$

- 적분 결과가 1인지 확인
    - `integrate.nquad`(피적분함수, x의 적분구간, y의 적분구간)[0]

- 주변확률밀도함수 (주변밀도함수)
    - 하나의 확률변수에 대해서만 밀도함수를 알고 싶을 때
    - 확률변수 X의 밀도함수 $f_X(x)$
    - $f_X(x) = \int_{-\infty}{\infty} f(x,y)dy$
    - X의 주변밀도함수는 결합확률밀도함수를 y로 적분하면 구할 수 있음
        - 하지만 integrate는 2변수 중 1변수만 적분하는 함수가 구현되지 않음
        - functools의 partial함수 사용
            - 인수의 일부를 고정한 새로운 함수를 만들 수 있는 함수
```python
from functools import partial

def f_X(x):
    return integrate.quad(partial(f_xy, x), -np.inf, np.inf)[0]

def f_Y(y):
    return integrate.quad(partial(f_xy, y), -np.inf, np.inf)[0]

X = [x_range, f_X]
Y = [y_range, f_Y]
```
------------

- 2차원 연속형 확률변수의 지표

- 기댓값
    - $\mu_X = E(X) = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} xf(x,y)dxdy$
    - 기댓값의 선형성 성립
        - E(2X + 3Y) = 2E(X) + 3E(Y)

- 분산
    - $V(g(X,Y)) = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} (g(x,y) - E(g(X,Y)))^2 f(x,y)dxdy$

- 공분산
    - $\sigma_{XY} = Cov(X,Y) = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} (x - \mu_X)(y - \mu_Y) f(x,y)dxdy$
    - 분산과 공분산의 공식 성립
        - $V(aX + bY) = a^2V(X) + b^2V(Y) + 2abCov(X,Y)$

- 상관계수
    - $\rho_{XY} = \rho(X,Y) = \frac{\sigma_{XY}}{\sigma_X \sigma_Y}$

## Chapter 8 대표적인 연속형 확률분포

- 라이브러리 선언
```python
import numpy as np
import matplotlib.pyplot as plt
from scipy import stats, integrate
from scipy.optimize import minimize_scalar

%precision 3
%matplotlib inline
```

- 연속형 확률분포의 성질 확인을 쉽게 하기 위한 함수 준비
```python
linestyles = ['-','--',':']

def E(X, g=lambda x: x):    //기댓값 함수
    x_range, f = X
    def integrand(x):
        return g(x) * f(x)
    return integrate.quad(integrand, -np.inf, np.inf)[0]

def V(X, g=lambda x: x):    //분산 함수
    x_range, f = X
    mean = E(X, g)
    def integrand(x):
        return (g(x) - mean) ** 2 * f(x)
    return integrate.quad(integrand, -np.inf, np.inf)[0]

def check_prob(X):  //확률변수를 인수로 취하여 확률의 성질을 만족하는지 확인 후 기댓값, 분산 반환
    x_range, f = X
    f_min = minimize_scalar(f).fun
    assert f_min >= 0, ' density function is minus value '
    prob_sum = np.round(integrate.quad(f, -np.inf, np.inf)[0], 6)
    assert prob_sum == 1, f ' sum of probability is {prob_sum} '
    print(f ' expected value {E(X):.3f} ')
    print(f ' variance {V(X):.3f} ')

def plot_prob(X, x_min, x_max):     //확률변수와 구간을 인수로 취하고 밀도함수와 분포함수를 그리는 함수
    x_range, f = X
    def F(X):
        return integrate.quad(f, -np.inf, x)[0]
    
    xs = np.linspace(x_min, x_max, 100)

    fig = plt.figure(figsize=(10, 6))
    ax = fig.add_subplot(111)
    ax.plot(xs, [f(x) for x in xs],
            label=' f(x) ' , color=' gray ')
    ax.plot(xs, [F(x) for x in xs],
            label=' F(x) ', ls='--', color=' gray ')
    
    ax.legend()
    plt.show()
```
