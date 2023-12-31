# logic circuit (논리회로) 학습


## Digital Design

- 컴퓨터를 포함한 많은 디지털 기기에서 디지털 하드웨어 내에 있는 디지털 전자 회로의 설계
- 회로는 논리라고도 불린다

## Definition of the **Digital**

- Digit: 사람의 손가락이나 발가락
    - 아라비아 숫자 (0, 1, 2, ... , 9)

- Digital: 사람의 손가락으로 셀 수 있는
    - 디지털(digital)과 이산(discrete)을 동의어로 사용

## Analog signal

- 아날로그 신호는 연속적인 변수를 가진다
    - 예) 소리, 목소리, 영상
- 자연에서 측정될 수 있는 대부분은 아날로그 형태로 나타난다
    - 예) 하루 동안의 기온

### How to convert analog signal -> digital signal

1. 아날로그 신호를 샘플링(Sampling)한다
    - 이산 시간 신호를 생성한다
2. 샘플링된 데이터를 양자화(Quantization)한다
    - 샘플링된 데이터 정밀도를 설명하기 위해 제한된 수의 비트를 사용하는 양자화가 필수

- 아날로그 데이터를 디지털로 표현하는 것은 샘플링과 양자화를 통해 가능하다

![샘플링과 양자화](../image/sampling_quantizing.jpg)

## Sampling theorem

- 데이터가 **가장 높은 데이터 빈도의 2배 이상의 비율** 로 **일정한 시간 간격** 으로 샘플링된 경우, 샘플에는 원본 데이터의 모든 정보가 포함된다
- Nyquistrate(나이키스트 레이트): 원신호를 복원할 수 있는 최소의 주파수
    - $f_s \ge 2f_m$
- 예) 사람이 들을 수 있는 가장 높은 빈도는 20kHz
    - 40kHz이상으로 샘플링하면 샘플은 모든 정보를 가진다

### Sampling theorem & Quantization Error

- 샘플을 충분히 자주 추출하면 원본 아날로그 데이터를 완벽하게 복원할 수 있음
- 하지만 양자화 에러로 인해 원본을 완벽하게 복원할 수 없음...

## Example of Audio Coding

- `cd(compact disc)`
    - PCM(Pulse Coded Modulation): 16bit/44.1kHz(1411.2kbps)
    - CD ripping: waveform audio format(.wav)
    - 무손실 압축: FLAC(Free Lossless Audio Coding), ALAC(Apple Lossless Audio Coding),(.ape)
    - 손실 압축: MP3(56kbps, 196kbps)

- `sacd(super audio cd)`
    - 24bit/192kHz(9.216mbps)

- `dsd(direct stream digital)`
    - PDM(Pulse Density Modulation)
        - dsd64: 1bit 2.8224mHz
        - dsd128: 1bit 5.6448mHz
    - 32bit/768kHz(49.152mbps)
    - 확장자: .dff, .dsf

## Digital advantages

- `Data Processing`(데이터 처리): 더 효율적이게
- `Data Transmission`(데이터 전송): 더 믿을 수 있게
- `Data Storage`(데이터 저장): 더 작게

- 복사본은 원본과 완전히 같을 수 있다 -> 정보 공유
- 우리의 삶에서 디지털(digital)은 공유(sharing)와 같다

## Digital Hardware System

- Computer: Power supply, PCBs(Printed circuit boards, mother board), storage units(Hard disk, Solid state disk, DVD, CD-ROM, ...)
- Mother board: CPU, storage(ROM/RAM), I/O interface, plugged-in slots
- **Chip: sub-circuit(logic gates)**

### Digital Hardware Components

- Standard Chip
    - 1980년대 초까지 논리 회로를 구축하는데 자주 사용됨
    - Drawback: 고정적 기능과 비효율적 공간
- Programmable Logic Devices
    - FPGA(Field-Programmable Gate Array)
- Custom-Designed Chips
    - custom or semi-custom design
    - ASIC(Application Specific Integrated Circuit)

## Binary Number

- $a_5a_4a_3a_2a_1a_0 . a_{-1}a_{-2}a_{-3}$  
    = $a_nr^n+a_{n-1}r^{n-1}+\dots+a_2r^2+a_1r+a_0+a_{-1}r^{-1}+a_{-2}r^{-2}+\dots+a_{-m}r^{-m}$
- $a_i$: coefficient(계수)
- $r$: base(진수)

### Number Base Conversions

- 10진수 -> 2진수
    1. 주어진 수를 2로 나눈다
    2. 나누었을 때의 몫이 0이 될 때까지 1.을 반복한다
    3. 나머지를 뒤에서부터 적는다

![10진수->2진수](../image/decimal_to_binary.jpg)

- 10진수 -> 8진수
    1. 주어진 수를 8로 나눈다
    2. 나누었을 때의 몫이 0이 될 때까지 1.을 반복한다
    3. 나머지를 뒤에서부터 적는다

![10진수->8진수](../image/decimal_to_octal.jpg)

- 10진수(소수 0.xxxx) -> 2진수
    1. 주어진 수에 2를 곱한다
    2. 소수점 뒤의 수가 0이 될 때까지 1.을 반복한다
    3. 소수점 앞 숫자들을 앞에서부터 적는다

![10진수(소수)->2진수](../image/decimal_to_binary(2).jpg)

## Logic Gates

- Basic Logic Gates
    - `AND`
    - `OR`
    - `NOT`
- Related Logic Gates
    - `NAND(AND-NOT)`
    - `NOR(OR-NOT)`
    - `X-OR`
    - `X-NOR`

### AND

- X AND Y = XY or X*Y
- 불 대수(Boolean Algebra)에서 곱셈과 같음
![AND GATE](../image/and_gate.jpg)
- **입력이 모두 1일 경우 출력이 1**

### OR

- X OR Y = X+Y
- 불 대수에서 덧셈과 같음
![OR GATE](../image/or_gate.jpg)
- **입력 중 하나라도 1일 경우 출력이 1**

### NOT(Inverter)

- X = $\bar A$ or X = A'
- Not A = A complement = A prime = A bar
![NOT GATE](../image/not_gate.jpg)

### NAND

- X NAND Y = (XY)'
![NAND GATE](../image/nand_gate.jpg)

### NOR

- X NOR Y = (X+Y)'
![NOR GATE](../image/nor_gate.jpg)

### Exclusive-OR(X-OR)

- X XOR Y = XY'+X'Y = X⊕Y
- Mod 2 addition
![XOR GATE](../image/xor_gate.jpg)

### Exclusive-NOR(equivalence)

- X XNOR Y = XY+X'Y' = (X⊕Y)'
- 두 입력이 서로 같으면 1, 다르면 0
![XNOR GATE](../image/xnor_gate.jpg)

## Boolean Algebra

- 1850년대에 George Boole이 개발한 기호로 논리 진술을 공식화하는 시스템
- 논리 문제를 일반적인 대수처럼 쓰고 풀 수 있음
- Constants(상수)
    - True and False
    - 1 and 0
- Variables(변수)
    - 불 상수인 값을 저장하는 변수

### Properties of Boolean Algebra

- Duality
    - Interchange OR and AND operators
    - 예) $X + 0 = X ↔ X * 1 = X$
        - X OR 0일 때 0은 False이므로 X의 값에 따라 X + 0이 결정됨   
        즉, X가 0이면 0이고 X가 1이면 1이됨
        - X AND 1일 때 X가 1인 경우에만 XY가 1이 되고 나머지 X가 0인 경우에는 XY가 0이 됨
    
- Operator precedence(연산자 우선순위)
1. Parentheses(괄호)
2. NOT
3. AND
4. OR

- Basic OR, AND operation
    - $x + 0 = x ↔ x * 1 = x$
    - $x + x' = 1 ↔ x * x' = 0$
    - $x + x = x ↔ x * x = x$
    - $x + 1 = 1 ↔ x * 0 = 0$

- Involution
    - (영한사전) 거듭제곱법, 누승법
        - 불 대수에선 이중 부정으로 이해
    - $(x')' = x$

- Commutative
    - (영한사전) 가환성의(제시된 수의 순서에 상관없이 결과가 동일한)
        - 수학에서의 교환법칙이라고 이해
    - $x + y = y + x ↔ xy = yx$

- Associative
    - (영한사전) 결합의
        - 수학에서의 결합법칙이라고 이해
    - $x + (y + z) = (x + y) + z ↔ x(yz) = (xy)z$

- Distributive
    - (영한사전) 분배적
        - 수학에서의 분배법칙이라고 이해
    - $x(y + z) = xy + xz ↔ x + yz = (x + y)(x + z)$
    ![x + yz](../image/distributive_proof.jpg)

- DeMorgan(드모르간 법칙)
    - $(x + y)' = x'y' ↔ (xy)' = x' + y'$

- Absorption
    - (영한사전) 흡수, 통합
    - $x + xy = x ↔ x(x+y) = x$

### Complement of a Function

1. Find its dual(AND↔OR, 1↔0)
2. Complement of each literal
![complement_func](../image/not_func.jpg)
- AND를 OR로 OR을 AND로 바꾼 뒤 1을 0으로 0을 1로 바꾸면 된다

### Minimization by Boolean Function

- 예)   
![Truth Table](../image/mini_exam_truth_table.jpg)
![F1](../image/mini_exam_f1.jpg)
![F2](../image/mini_exam_f2.jpg)
- 진리표에서 최소화하기
    1. 진리표에서 True인 부분의 변수를 찾는다
    2. 공통 부분을 찾아 묶는다
    3. 식 정리

## Canonical And Standard Forms

### Canonical Forms

- Minterms and Maxterms   
![Canonical Forms](../image/canonical_forms.jpg)   
    - minterms에서는 AND로 연결되어있으며 0을 '으로 표시하고 소문자로 표시
    - maxterms에서는 OR로 연결되어있으며 1을 '으로 표시하고 대문자로 표시

- Canonical SOP/POS Forms
    - SOP: Sum Of Product
    - POS: Product Of Sum
    - 예)   
    ![Canonical exam](../image/canonical_exam.jpg)
        - Canonical SOP   
        ![Canonical SOP](../image/canonical_exam_sop.jpg)   
        - Canonical POS   
        ![Canonical POS](../image/canonical_exam_pos.jpg)

#### Conversion between Canonical Forms

- Relation between SOP and POS
    - $m_i = M_i'$ and $m_i' = M_i$
    - 예) $F(x,y,z) = \Sigma(1,3,6,7)$일 때 $F(x,y,z) = \Pi(0,2,4,5)$와 같다

### Standard SOP/POS Forms

- 예)   
![Standard SOP](../image/standard_sop.jpg)   
![Standard POS](../image/standard_pos.jpg)   

## NAND And NOR Logic Networks

### DeMorgan's Theorem

![DeMorgan](../image/de_morgan.jpg)   

### Basic Gates Using NAND

![Basic_NAND](../image/bg_use_nand.jpg)

### Basic Gates Using NOR

![Basic_NOR](../image/bg_use_nor.jpg)

## Karnaugh Map(카르노 맵)

- 논리식을 최소화 하는 과정에서 주어진 진리표에 대한 최적의 답인지 판단하기 위해 사용

### Two-Variable Map

![2-karnaugh](../image/karnaugh_2.jpg)

### Three-Variable Map

![3-karnaugh](../image/karnaugh_3.jpg)

### Four-Variable Map

![4-karnaugh](../image/karnaugh_4.jpg)

### Five-Variable Map

![5-karnaugh](../image/karnaugh_5.jpg)

## Strategy For Minimization

- `Literal(문자)`: 변수
- `Implicant(항)`: 1이나 1의 묶음들
- `Prime implicant`: 다른 항들과 묶이지 않는 항
- `Cover`: 함숫값을 1로 만드는 모든 항들
- `Cost`: 회로의 게이트와 입력의 개수의 합
- 예)   
    - Literal
        - $x_1x_2'x_3$: 3 literals
        - $x_1'x_3x_4'x_6$: 4 literals   
    ![Implicant](../image/implicant_exam.jpg)   
    ![Prime-Implicants_Cover](../image/prime_implicant_exam.jpg)   
    ![Cover_Cost](../image/cover_cost_exam.jpg)   

### Minimization Procedure

1. 주어진 함수 f에 대한 모든 주요 항(prime implicant)을 생성한다
2. 다른 항과 겹치지 않는 항이 있는 주요 항(essential prime implicant)들의 집합을 찾는다
3. 위에서 찾은 항이 f = 1에 대한 모든 값을 포함하는 경우 이 집합은 f의 cover이다

- 위의 방식은 SOP form을 위한 방식이므로 POS form을 원한다면 f = 0인 항에 대해 적용하면 된다

## Incompletely Specified Funtion

- 예)   
![Truth Table](../image/dont_care_term_tt.jpg)   
![SOP](../image/dont_care_term_sop.jpg)   
![POS](../image/dont_care_term_pos.jpg)   
- don't care term을 포함하면 식이 간결해질 수 있음

## Multiple-Output Circuit

- 예)   
![Multiple Output](../image/multi_output(1).jpg)   
![Multiple Output(2)](../image/multi_output(2).jpg)   
![Multiple Output(3)](../image/multi_output(3).jpg)

## Multilevel Sythesis

- Fan-in problem
    - 입력의 개수가 제한되어있음
    - Fan-out problem: 출력의 개수가 제한되어 있음
- Implementation
    - CPLD: two-level logic expression(SOP)
    - FPGA: multilevel logic expression(LogicCell)
- Techniques for synthesis of multilevel circyit
    - `Factoring`
    - `Functional Decomposition`

### Factoring

- 예)   
![Factoring](../image/factoring.jpg)   

### Functional Decomposition

- 예)   
![Functional Decomposition(1)](../image/func_decomp(1).jpg)   
![Functional Decomposition(2)](../image/func_decomp(2).jpg)   
![Functional Decomposition(3)](../image/func_decomp(3).jpg)   
![Functional Decomposition(4)](../image/func_decomp(4).jpg)   
![Functional Decomposition(5)](../image/func_decomp(5).jpg)   

## Conversion Decimal, Binary

- [10진수 -> 2진수, 10진수 -> 8진수, 10진수(소수 0.xxxx) -> 2진수](#number-base-conversions)
- 2진수 -> 8진수
    1. 주어진 수를 뒤에서부터 3자리씩 나눈다
    2. 나누어진 3자리를 앞에서부터 4,2,1로 1인 부분만 더한다
    3. 각 8진수로 변환된 숫자들을 적는다
![2진수->8진수](../image/binary_to_octal.jpg)
- 2진수 -> 16진수
    1. 주어진 수를 뒤에서부터 4자리씩 나눈다
    2. 나누어진 4자리를 앞에서부터 8,4,2,1로 1인 부분만 더한다
    3. 각 16진수로 변환된 숫자들을 적는다
![2진수->16진수](../image/binary_to_hexa.jpg)

## Addition of Unsigned Numbers

### Half-adder(반가산기)

![half-adder](../image/half-adder.jpg)

### Full-adder(전가산기)

![full-adder](../image/full-adder.jpg)

- Decomposed Full-adder

![decomposed FA](../image/decomposed_fa.jpg)

### Ripple Carry Adder

![ripple carry adder](../image/ripple_carry_adder.jpg)
- MSB: Most Significant Bit (최상위 비트)
- LSB: Least Significant Bit (최하위 비트)
- FA(Full Adder) 연산 후 그 캐리 값을 다음 FA로 전달하는 Adder => 속도가 느림
- 숫자의 크기에 따라 지연 시간이 달라짐
- $\Delta t$가 한 비트의 지연 시간이라면, 전체 지연 시간은 $n\Delta t$

## Signed Numbers

### Formats for representation of integers

![formats of integers](../image/unsign_sign.jpg)
- Unsigned Number의 범위: $0$ ~ $2^n-1$
- Signed Number의 범위: $-2^{n-1}$ ~ $2^{n-1}-1$
- Signed Number에서 Sign(부호 비트)가 존재한다    
    - Sign이 0이라면 +, 1이라면 -를 나타낸다

### 1's Complement(1의 보수)

- $N$: 바꿀 수, $n$: 비트의 수
- $N$의 1의 보수 = $-N$ = $(2^n-1)-N$
- 예)   
![1's complement](../image/1complement.jpg)

### 2's Complement(2의 보수)

- $N$: 바꿀 수, $n$: 비트의 수
- $N$의 2의 보수 = $-N$ = $(2^n)-N$ = $((2^n-1)-N)+1$ = N의 1의 보수 + 1
- 예)   
![2's complement](../image/2complement.jpg)

### 1's complement addition

- $M>N$일 때, $M+N\le(2^4-1)$: unsigned,  $M+N\le(2^3-1)$: signed
- $-M+N=(2^4-1)-M+N=(2^4-1)-(M-N)$
- $M-N=M+(2^4-1)-N=M-N+(2^4-1)$
- $-M-N=(2^4-1)-M+(2^4-1)-N=(2^4-1)-(M+N)+(2^4-1)$
- carry 발생 시 carry를 더해줘야 함

### 2's complement addition

- $-M+N=2^4-M+N=2^4-(M-N)$
- $M-N=M+2^4-N=M-N+2^4$
- $-M-N=2^4-M+2^4-N=2^4-(M+N)+2^4$
- carry 발생 시 carry 무시

### 2's complement subtraction

- 양수 - 음수 = 음수를 보수로 바꾸고 더함
- 음수 - 음수 = 뒤의 음수를 보수로 바꾸고 더함
- 양수 - 양수 = 뒤의 양수를 보수로 바꾸고 더함
- 음수 - 양수 = 양수를 보수로 바꾸고 더함

### Adder/Subtractor Unit

![adder/subtractor unit(1)](../image/adder_subtractor(1).jpg)
![adder/subtractor unit(2)](../image/adder_subtractor(2).jpg)

### Arithmetic Overflow

- Overflow: Out of range
    - $c_{n-1}⊕c_n$
    - 1: overflow, 0: normal
    - 마지막 캐리와 그 전 캐리가 같은 값이면 normal 다른 값이면 overflow

### Performance Issues

- 디지털 시스템 구매 시, 구매자에게 성능과 비용이 특히 중요함
- 우수한 성능은 높은 비용으로 실현됨
- $n$비트 리플캐리 가산기에서 지연 시간이 대략 $n\Delta t$임
- => 컴퓨터 성능을 높이기 위해서는 덧셈을 수행할 더 빠른 회로를 찾는 것이 중요함

## Fast Adder

### Carry-Lookahead Adder(자리올림수 예측 가산기)

- ripple-carry adder에서 $c_{i+1} = x_iy_i+c_i(x_i+y_i)$
- carry-lookahead adder에서는 다음의 연산을 수행하여 g와 p를 구한다
    - $g_i = x_iy_i$
        - `generate(자리올림수 생성)`: 기존의 연산과 관계 없이 반드시 carry가 생기는 경우를 확인
    - $p_i = x_i+y_i$
        - `propagate(자리올림수 전파)`: 추가로 carry가 생기는 경우 확인
- g와 p를 활용한 가산기의 carry
    - $c_{i+1} = g_i+p_ic_i$
    - $c_{i+1} = g_i+p_ic_i+p_ip_{i-1}g_{i-2}+\cdots+p_ip_{i-1}\cdots p_2p_1g_0+p_ip_{i-1}\cdots p_1p_0c_0$
- $n$이 커질수록 $n$비트 carry-lookahead adder의 복잡성이 급격히 증가한다   
=> 복잡성을 줄이기 위해 계층적 접근 방식을 사용할 수 있다

#### hierarchical carry-lookahead adder

- 비트들을 여러 블록으로 나누고 각 블록은 비트들을 그룹화하여 병렬로 계산
- 각 블록에서 carry-lookahead를 미리 계산(해당 블록에서 덧셈 결과에 대한 캐리값)
- 각 블록은 carry-lookahead를 계산 후 다음 블록으로 전달(이전 블록의 carry가 다음 블록에서 사용됨)
- 블록 내부는 carry-lookahead, 블록 사이는 ripple carry

## Multiplication

### Multiplication

- $n$ $bit \times n$ $bit = 2n$ $bit$
![multiplicaion](../image/multiplication.jpg)

### 4 $\times$ 4 multiplier circuit

- structure of the circuit
![structure of the circuit](../image/4x4multiple_structure.jpg)
- a block in the top row
![a block in the top row](../image/4x4multiple_block_top.jpg)
- a block in the top row
![a block in the top row](../image/4x4multiple_block_bottom.jpg)

## Other Number Representations

### Fixed-Point Numbers

- 기수점의 위치가 가정되기 때문에 Fixed-point라는 이름이 붙는다
- `radix point`: 기수점(소수에서 정수와 분수 부분을 분리하는 십진법의 소수점과 같은 지점)
- 기수점이 표시되지 않으면 최하위 숫자의 오른쪽에 있는 것으로 가정되며, 이는 숫자가 정수임을 의미
- 예)   
    [fixed-point numbers](#formats-for-representation-of-integers)

### Floating-Point Numbers

- excess-127을 사용하면 부동소수점 숫자를 더하고 뺄 때 편리함
- single precision(32비트 단정밀도)
    - exponent: E-127
    - value = $\pm$ 1.M $\times$ $2^{E-127}$
    - 부호 1비트, 지수부 8비트, 가수부 23비트
     ![single precision](../image/single_precision.jpg)

- double precision(64비트 배정밀도)
    - exponent: E-1023
    - value = $\pm$ 1.M $\times$ $2^{E-1023}$
    - 부호 1비트, 지수부 11비트, 가수부 52비트
     ![double precision](../image/double_precision.jpg)

- single precision example
     ![single precision example](../image/single_precision_example.jpg)

### Binary-Coded-Decimal Representation

- binary-coded decimal digits
    ![BCD digits](../image/BCD_digits.jpg)
- addition of BCD digits
    ![addition of BCD digits](../image/BCD_addition.jpg)
    - 결과가 9를 초과하면 $(0110)_2 = (6)_{10}$ 을 더한다
- BCD adder
    ![BCD adder block diagram](../image/BCD_adder_blockdiagram.jpg)
