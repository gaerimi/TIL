# system software(시스템 소프트웨어) 학습

## Chapter 1

### Computer System

- 컴퓨터 시스템의 구성
![구성](../image/computersystem.jpg)   
    - 계층적 구조
    - 사용자, 응용 프로그램, 시스템 소프트웨어, 하드웨어로 이루어짐
    - 사용자는 특정한 응용 프로그램을 실행을 통해 자신의 문제를 해결하려 함
    - 응용 프로그램 실행을 위해선 하드웨어 자원 필요
    - 하드웨어 자원을 운영체제와 같은 시스템 소프트웨어가 적절한 통제를 거쳐 사용 할 수 있게 함

- 컴퓨터 하드웨어
![하드웨어](../image/computerhw.jpg)   
    - CPU, MM(Main Memory), 입출력 장치(CPU와 MM을 제외한 나머지 장치들, 줄여서 I/O device)
    - `CPU`: 프로그램을 실행하는 장치
        - `CU(Control Unit)`: CPU의 전체 동작을 제어하는 장치
        - `ALU(Arithmetic Logical Unit)`: 산술 논리 연산 장치
    - `MM`: 실행 중인 프로그램이 머무르는 곳
    - `I/O device`: 컴퓨터 외부와 데이터를 주고받거나 데이터를 보관하는 역할

- 기본 요소   
![기본 요소](../image/basicelements.jpg)   
    - Processor(CPU)
    - Main Memory
        - 휘발성(전원이 들어와 있을 동안만 기억 유지)
        - real memory 또는 primary memory라고도 함
    - I/O device
        - 보조 기억 장치(예 - 하드디스크)
        - 통신 장치
        - 터미널
    - System bus
        - 프로세서, 메모리, 입출력 장치 사이를 연결해줌

- 작동 방식
![작동 방식](../image/computerworks.jpg)   
    - cache: 프로그램을 실행시키는 성능을 높이기 위해 사용되는 CPU 내부 메모리
    - DMA: 입출력 데이터의 양이 많을 경우 DMA 방식을 걸쳐 메모리에서 직접 데이터를 가져오기도 함
    - interrupt: 입출력 완료 신호

- 컴퓨터 프로그램
    - CPU가 실행해야 할 구체적인 내용을 한 단계씩 순서대로 기술한 명령의 연속

- 기계어
    - 0과 1로 표시된 것으로 컴퓨터의 프로세서가 이해하는 유일한 언어
    - 각 기계간에 호환성이 없음

### Fetch-Execution Cycle

- 에니악은 내장 프로그램이 아님
    - 플러그와 점퍼 케이블을 이용해 연결

- Stored program(내장 프로그램) 방식의 컴퓨터
    - von Neumann(폰 노이만)
    - 현재의 대부분의 컴퓨터
    - computation(계산): 프로그램의 수행
    - memory: 프로그램이 저장된 장소
    - processor: 계산을 수행하는 기계의 부분, CPU
    - computer program: 일련의 컴퓨터 명령들

- 폰 노이만 컴퓨터는 프로세서와 메인 메모리로 구성

- 프로세서에 의한 계산은 Fetch-Execution Cycle을 사용하여 이루어짐
1. 메모리의 명령을 가져옴(`fetch`)
2. 명령 실행(`execution`)
3. 명령 가져오기 단계로 돌아가 반복
![fetch-execution](../image/fetch_execution.jpg)

### Processor Registers

#### User-visible registers

- 프로그래머가 레지스터 사용을 최적화하여 메인 메모리 참조를 최소화할 수 있게 해줌
- 실행이 되는 과정에 직접 접근하는 레지스터
- 기계어로 참조 가능
- 어떤 프로그램이든(응용이던 시스템이던) 마음대로 user-visible register에 접근 가능
- `데이터 레지스터(data register)`
- `주소 레지스터(address register)`
    - `인덱스(index)`
        - 몇 번째에 접근하는지
        - 주소를 얻기 위해 기본값에 인덱스를 추가하는 작업도 포함
    - `세그먼트 포인터(segment pointer)`
        - 세그먼트 기반의 메모리를 사용하는 경우 어느 세그먼트를 접근해야 하는지 지정
    - `스택 포인터(stack pointer)`
        - 스택의 top을 가리킴

#### Control and status registers

- 프로세서의 동작을 제어하기 위해 사용
- `프로그램 카운터(Program Counter, PC)`
    - 다음에 실행할 명령의 메인 메모리상의 주소를 가지고 있는 레지스터
    - 한 번 fetch가 이루어지면 자동으로 다음 명령을 가리키도록 값이 업데이트 됨
- `명령 레지스터(Instruction Register, IR)`
    - fetch단계에서 메모리로부터 복사해온 명령을 담아두는 레지스터
    - 현재 실행 중인 명령을 담고 있음(명령 하나만 담을 수 있는 크기라 덮어쓰기 함)
- `프로그램 상태 워드(Program Status Word, PSW)`
    - 현재 CPU의 상태에 대한 여러가지 정보를 담고 있는 레지스터
    - `Condition Codes` or `Flags`
        - 연산에 의해 발생한 부가적 정보를 나타냄
            - 양수/음수 결과
            - 0인지 아닌지
            - 오버플로우가 발생했는지 아닌지
    - `Interrupt enable/disable`
        - 인터럽트 신호를 받을지 아닐지 상태 조절
    - `Supervisor/user mode`
        - CPU의 실행 모드 제어

#### Program Execution of a Hypothetical Machine

![가상 머신의 프로그램 실행](../image/programexe_hypo.jpg)   
- Memory address register(MAR)
    - 다음에 읽을 또는 쓸 주소 지정
- Memory buffer register(MBR)
    - 메모리에 기록되거나 수신 받은 데이터를 보관
- Accumulator(AC)
- I/O address register
    - 입출력할 데이터의 메모리 주소를 가지고 있는 레지스터
- I/O buffer register

### System software

- 소프트웨어의 구분
    - 응용 소프트웨어: 사용자의 목적을 만족시키는 소프트웨어
    - 시스템 소프트웨어: 다른 프로그램이나 소프트웨어가 필요한 기능 제공
    - 시스템 프로그래밍: 시스템 소프트웨어의 기능을 이용하여 기계를 직접 작동하는 프로그램을 작성하는 일

- `Assembler(어셈블러)`
    - assembly language(어셈블리어)
        - 기계어 대신에 사람이 기억하기 쉽고 연상하기 쉬운 단어로 대체(연상, 심볼)
    - 어셈블리어를 자동적으로 기계어로 번역하는 프로그램
- `Linker(링커)`
    - 여러 개의 모듈 간의 상호 기억 장소 참조를 정리하여 함께 실행될 수 있도록 함
- `Loader(로더)`
    - load module: 링커가 만들어낸 실행 가능한 형태의 프로그램, 실행을 위해서 메모리에 저장이 되는 대상
    - 로드 모듈을 기억 장치에 적재하는 프로그램
    - 어셈블러가 로더의 기능까지 포함하는 경우
        - 기억 장소의 낭비
        - 매번 번역하는 번거로움
- `Macro Processor(매크로 프로세서)`
    - macro(매크로): 정의된 절차에 따라서 입력 시퀸스가 정의되어 있는 대체 출력 시퀸스로 변환이 되는 규칙 또는 패턴
    - 매크로 호출을 매크로에서 정의된 원래 명령어로 대치
- `Compiler(컴파일러)`
    - 고급 언어 프로그램을 받아들여 목적 프로그램을 만듦
    - 목적 프로그램: 고급 언어 프로그램과 동등한 역할을 하는 기계어로 이루어진 프로그램, 링커의 입력으로 사용되기도 함
- `Interpreter(인터프리터)`
    - 고급 언어 프로그램의 각 문장을 기계어로 바꿈

#### 운영체제

- 하드웨어를 관리하고, 응용 프로그램에 실행 환경을 제공하는 시스템 소프트웨어
- 기능
    - 프로세스 관리
    - 메모리 관리
    - CPU 스케줄링
    - 파일 및 I/O 서브 시스템
    - 디스크 스케줄링
    - 유틸리티

## Chapter 2

### Information representation

- Digital form(디지털)
    - 정보를 이산적이고 비연속적인 값으로 표현하는 방식
    - 예 - 디지털 시계(숫자로 시간 표현) 등
    - 정보를 표현하고자 하는 수에 의해 제한됨
- Analog form(아날로그)
    - 정보를 연속적인 값으로 표현하는 방식
    - 예 - 소리, 전압, 전류, 온도 등
- 디지털의 장점
    - 아날로그 보다 더 저렴하고, 신뢰할 수 있으며 범용성이 크다

### Why binary?

- 디지털 컴퓨터/시스템은 처리하고자 하는 정보가 어떤 정보이든지간에 그 정보를 내부적으로 디지털 형태로만 표현하고 처리
    - 아날로그(예 - 전압, 전류) 형태를 컴퓨터에서 처리하기에는 어렵기 때문에 아날로그에서 디지털로 변환(A-to-D)이 필요
- 디지털 컴퓨터는 수만 다름
- 수 형태의 데이터 입력을 받음
- 수들에 대한 연산 수행
- 새로운 수 형성
- 수행하고자 하는 연산은 명령어라고 불리는 수의 형태로 컴퓨터에 주어짐
- 수를 저장하고 조작하는데 용이하고 편리한 수 체계 필요 $\rightarrow$ 2진수 체계 사용
    - 2진수를 표현하고 처리하는 장치를 만드는 것이 10진수 표현 처리 장치를 만드는 것보다 쉽다
    - 0과 1의 2개의 값만 있다

### Binary system

- 10진수
    - 10개의 숫자(0 ~ 9)를 사용하며 각 자리에 따라 10의 거듭제곱을 곱한다
    - $7392 = 7 * 10^3 + 3 * 10^2 + 9 * 10^1 + 2 * 10^0$
- 2진수
    - 2개의 숫자(0, 1)을 사용하며 각 자리에 따라 2의 거듭제곱을 곱한다
    - $1011_2 = 1 * 2^3 + 0 * 2^2 + 1 * 2^1 + 1 * 2^0 = 11$
- 소수점을 가진 수
    - 각 자리에 따라 소수점 기준 왼쪽은 양의 거듭제곱을 곱하고 오른쪽은 음의 거듭제곱을 곱한다
    - $11010.11_2 = 1 * 2^4 + 1 * 2^3 + 0 * 2^2 + 1 * 2^1 + 0 * 2^0 + 1 * 2^{-1} + 1 * 2^{-2} = 26.75$

- binary prefix
    - K(Kilo) = $2^{10} = 1024 \cong 10^3$ thousand
    - M(Mega) = $2^{20} = 1048576 \cong 10^6$ million
    - G(Giga) = $2^{30} = 1073741824 \cong 10^9$ billion
    - T(Tera) = $2^{40} = 1.099 * 10^{12} \cong 10^{12}$ trillion
    - P(Peta) = $2^{50}$
    - E(Exa) = $2^{60}$
    - Z(Zetta) = $2^{70}$
    - Y(Yotta) = $2^{80}$

    - b와 B의 차이
        - b: bits
        - B: bytes(8 bits)

### Base-r system

- 계수에 r의 거듭제곱을 곱한 형태
- 계수의 범위는 0 ~ r - 1
- 진수가 10보다 큰 경우 10자리 숫자에 알파벳을 보충하여 사용

#### Converting decimal to base-r

- r진수 -> 10진수
    - 각 자리에 따라 r의 거듭제곱을 곱한다
- 10진수 -> r진수
    - 주어진 10진수를 r로 나누는 과정을 몫이 0이 될 때까지 반복
        - 처음 구한 나머지가 LSB, 나중에 구한 나머지가 MSB가 된다
    - 10진수의 소수점 부분은 r을 곱하는 과정을 값이 1.0이 될 때까지 반복
        - 처음 구한 나머지가 MSB, 나중에 구한 나머지가 LSB가 된다
    - 정수부와 소수부 둘 다 가진 경우 정수부와 소수부를 각각 구하고 답을 합친다

#### Converting binary to octal

- 2진수 -> 8진수
    - 소수점이 있는 경우에 정수부 쪽으로 왼쪽으로 3자리씩, 소수부 쪽으로 오른쪽으로 3자리씩 묶는다
    - 묶은 3자리를 각각 8진수로 변환한다
- 8진수 -> 2진수
    - 8진수의 각 자릿수를 해당하는 2진수 3자리로 변환한다

#### Converting binary to hexadecimal

- 2진수 -> 16진수
    소수점이 있는 경우에 정수부 쪽으로 왼쪽으로 4자리씩, 소수부 쪽으로 오른쪽으로 4자리씩 묶는다
    - 묶은 4자리를 각각 16진수로 변환한다
- 16진수 -> 2진수
    - 16진수의 각 자릿수를 해당하는 2진수 4자리로 변환한다

### Binary arithmetic

- 덧셈
    - 0 + 0 = 00
    - 1 + 0 = 0 + 1 = 01
    - 1 + 1 = 10
- 뺄셈
    - 0 - 0 = 0
    - 0 - 1 = 1
    - 1 - 0 = 1
    - 1 - 1 = 0
- 곱셈
    - 0 * 0 = 0
    - 1 * 0 = 0 * 1 = 0
    - 1 * 1 = 1

### Complements

- 보수는 뺄셈 연산을 단순화하고 논리적 조작을 위해 사용됨
- 만약 소수점이 있는 수의 보수를 구할 경우 소수점을 임시로 제거후 보수를 구한 뒤 원래 위치에 소수점을 추가한다
- 보수의 보수는 원래의 수이다

#### (r - 1)'s complement

- diminished radix complement
- n자리를 갖는 r진수 숫자 N이 주어졌을 때
    - N의 (r - 1)의 보수는 $(r^n - 1) - N$
- 10진수의 9의 보수는 9에서 각 숫자를 뺀다
- 2진수의 1의 보수는 1에서 각 자리를 뺀다
    - 각 자리에 not 연산을 한 결과와 같다

#### r's complement

- radix complement
- n자리를 갖는 숫자 N이 주어졌을 때
    - N의 r의 보수는 $r^n - N$
- r의 보수 = r - 1의 보수 + 1
- 10진수의 10의 보수
    - 끝에서 앞으로 가면서 처음 나오는 0은 그대로 쓰고, 0이 아닌 수는 10에서 뺀다
    - 그 뒤에 나오는 수는 9에서 뺀다
- 2진수의 2의 보수
    - 끝에서 앞으로 가면서 처음 나오는 1은 그대로 쓴다
    - 그 뒤는 0이면 1, 1이면 0으로 바꾼다

#### Subtraction using complements

- r진수 M - N
    - M + (N의 r의 보수)를 한다
    - M + ( $r^n$ - N) = M - N + $r^n$
    - 만약 M $\ge$ N이라면 end 캐리 무시
    - 만약 M < N이라면 캐리 발생하지 않음
        - 나온 덧셈 값에 r의 보수를 구한 다음 앞에 -기호를 붙여주면 뺄셈의 답을 얻을 수 있음
- 2진수에서 1의 보수를 이용하여 뺄셈을 하는 경우
    - 캐리 발생시 end-around 캐리를 더해준다
    - 나온 덧셈 값에 1의 보수를 구한 다음 앞에 -기호를 붙여준다

### Signed number

- 부호 있는 수를 표현하는 방식
- 음수를 표현하는 3가지 방법
    - signed magnitude
    - 1's complement
    - 2's complement

- Signed magnitude
    - 가장 왼쪽 비트가 사인 비트(부호 비트) 역할
        - 0: 양수
        - 1: 음수
    - 나머지 비트들은 수의 크기의 절댓값
    - 수를 표현하는데 사용되는 비트의 수 n이 정해져 있어야 함
    - n개의 비트가 표시하고 있는 수가 부호가 있는 정수인지 부호가 없는 정수인지 정의되어야 함
        - 부호가 있는 수라면 수를 표현하는 방식 정의되어야 함
- Signed complement
    - 주어진 수의 음수는 주어진 수의 보수
    - 양수는 0으로 시작 보수는 1로 시작

#### Addition signed number

- 8비트 2의 보수의 덧셈
    - 단순한 것은 부호 비교 없이 덧셈만 필요
    - 모든 캐리 무시
    - 만약 음수면 2의 보수 형태
    - 결과값이 음수라면 음수의 2의 보수 앞에 -를 붙이면 답을 확인할 수 있음

#### Subtraction signed number

- M - N
    - N의 2의 보수를 구한다
    - M과 더한다
    - 사인 비트에서 생성된 캐리를 무시한다
    - 음수라면 2의 보수 형태이다
    - 음수의 2의 보수 앞에 -를 붙이면 답을 확인할 수 있다

### Binary codes

- n비트 이진 코드는 0과 1의 $2^n$ 개의 서로 다른 조합을 최대로 가정할 수 있는 n비트의 그룹

- Binary Coded Decimal code(BCD)
    - 각 10진수 기호 0 ~ 9에 4비트의 이진 코드 할당
    - 나머지 6개는 사용하지 않음
    - 10진수가 k개인 숫자는 BCD를 사용할 경우 4k비트 필요
    - 덧셈
        - BCD 숫자 합이 1001보다 작거나 같으면 이진수 덧셈과 유사
        - 합이 1001보다 크면 0110(6)을 더하여 보정한다

- Other Decimal codes
    - 2421, Excess-3, 84-2-1 (BCD는 8421코드)
    - 가중치가 부여된 코드(weighted codes)로 각 비트 위치에 가중치 인자 할당
    - 일부 숫자는 2421에서 가능한 두 가지 방식으로 코딩될 수 있음
        - 예) 4 - 0100 or 1010
    - 2421과 excess-3은 자체 보완
        - 9의 보수는 1을 0으로 0을 1로 바꿈으로 얻을 수 있음
        - 10진수에서 9의 보수 관계가 있다면 해당 2421코드 2개는 서로 1의 보수 관계
    - Gray code
        - 한 숫자에서 다음 숫자로 이동할 때 코드에서 1비트만 변함
        - 너무 많은 비트를 동시에 변경해야 할 때 발생할 수 있는 전자적 계산 오류를 줄여줌
![decimal code](../image/decimalcode.jpg)

- ASCII code
    - American Standard Code for Information Interchange
    - Alphanumeric - 숫자, 알파벳 영문자(소문자, 대문자), 각종 심볼의 128가지 문제에 대한 코드
    - 128가지의 코드이므로 7비트 코드

#### Error detecting codes

- 데이터 또는 모든 종류의 정보를 읽고 쓰는 동안 오류가 발생할 수 있음
- 오류 탐지 방법 - 전송되는 데이터/메시지와 함께 추가 정보 추가
- 예) ASCII문자에 패리티 비트를 추가하여 패리티를 표시한다
    - 짝수 패리티(even parity): 1인 비트의 수가 짝수가 되도록 비트를 추가
    - 홀수 패리티(odd parity): 1인 비트의 수가 홀수가 되도록 비트를 추가

- 송신자와 수신자 모두 특정 유형의 패리티를 사용하는 것에 동의
1. 송신자에서 각 문자에 대한 패리티 생성
2. 수신자가 각 문자의 패리티 검사
3. 만약 패리티가 일치하지 않으면
    - 오류 - 하나 이상의 비트가 변경됨
    - 송신자에게 메시지를 다시 보내달라고 요청

- 오류가 홀수개일 때만 탐지 가능
- 7비트 ASCII문자는 8비트에 저장되므로 추가 비트는 일반적으로 패리티에 사용됨
    - 각 ASCII문자가 올바르게 읽고,쓰고,전송,저장되었는지 확인

## Chapter 3

### 80x86 Evolution

- 4004
    - 1971년에 출시
    - 4비트 마이크로 프로세서
        - CPU가 한 번에 처리할 수 있는 연산이 4비트 연산이다
    - 최초의 산업용 마이크로 프로세서
    - 4KB 메인 메모리 지원
    - 명령어 개수 45개
    - 50 KIPS
        - 1초에 5만 개의 명령을 실행할 수 있는 속도
- 8008
    - 1972년에 출시
    - 4004의 8비트 버전
        - 8비트 마이크로 프로세서
    - 16KB 메인 메모리 지원
    - 명령어 개수 48개
- 8080
    - 1974년에 출시
    - 8비트 마이크로 프로세서
    - 64KB 메인 메모리 지원
    - 2MHz clock rate
        - 1초에 50만 개의 명령을 실행할 수 있는 속도
    - 8008보다 10배 빨라짐
- 8085
    - 1976년에 출시
    - 8비트 마이크로 프로세서
        - 8080의 성능 향상 버전
    - 64KB 메인 메모리 지원
    - 1.3 microseconds clock cycle time
        - 1초에 80만 개의 명령을 실해할 수 있는 속도
    - 1억 개가 넘는 판매량을 기록
- 8086(1978) / 8088(1979)
    - 8088은 8086의 보급형 버전
    - 16비트 마이크로 프로세서
    - 1MB 메인 메모리 지원
    - 2.5 MIPS (400ns)
        - 1초에 250만 개의 명령을 실행할 수 있는 속도
    - 명령 캐시가 있음
    - 더 많은 레지스터와 더 많은 명령 수
- 80286
    - 1982년 출시
    - 16비트 마이크로 프로세서 (8086과 동일)
    - 8086이나 8088과 호환이 되는 명령어 집합
    - 16MB 메인 메모리 지원
    - 4.0 MIPS(250ns/8MHz)
- 80386
    - 1985년 출시
    - 최초의 32비트 마이크로 프로세서
    - 4GB 메인 메모리 지원
    - 12~33MHz
    - 메모리 관리 유닛(MMU)
        - 가상 메모리를 사용할 수 있게 됨
    - variations: DX, EX, SL, SLC, SX
- 80486
    - 1989년 출시
    - 32비트 마이크로 프로세서
    - 32비트 데이터 버스, 32비트 주소 버스
    - 4GM 메인 메모리 지원
    - 20~50MHz later 66~100MHz
    - 80386과 비슷한 기능을 하는 마이크로 프로세서, 80387과 비슷한 기능을 하는 부동소수점 보조 프로세서 내장
        - 80387: 부동 소수점 연산을 전담하는 전용 보조 프로세서
    - 80386에서의 실행 속도가 반으로 줄었다
    - variations: SX, DX2, DX4
- Pentium
    - 1993년 출시
    - 32비트 마이크로 프로세서
    - 64비트 데이터 버스, 32비트 주소 버스
    - 4GB 메인 메모리 지원
    - 60, 66, 90MHz
        - 제일 빠른 버전은 233MHz
    - 16KB L1 캐시(명령/데이터 8KB씩)
    - 메모리 전송 66MHz
    - 정수 프로세서 2개
- Pentium Pro
    - 1995년 출시
    - 32비트 마이크로 프로세서
    - 64비트 데이터 버스, 36비트 주소 버스
    - 64GB 메인 메모리 지원
    - 150MHz에서 시작 이후에 200MHz 정도도 나옴
    - 16KB L1 캐시(명령/데이터 8KB씩)
    - 256KB L2 캐시
    - 메모리 전송 66MHz
    - 정수 프로세서 3개
- Pentium II
    - 1997년 출시
    - 32비트 마이크로 프로세서
    - 64비트 데이터 버스, 36비트 주소 버스
    - 64GM 메인 메모리 지원
    - 233MHZ에서 시작 이후에 450MHz 정도도 나옴
    - 32KB L1 캐시(명령/데이터 16KB씩)
    - module integrated 512KB L2 캐시(전송 속도 133MHz)
        - 모듈화 되어 있지만 CPU와는 떨어져 있음
    - 메모리 전송 66MHz에서 100MHz
- Pentium III
    - 1999년 출시
    - 32비트 마이크로 프로세서
    - 64비트 데이터 버스, 36비트 주소 버스
    - 64GB 메인 메모리 지원
    - 800MHz 이상
    - 32KB L1 캐시(명령/데이터 16KB씩)
    - On-chip 256KB L2 캐시
        - CPU칩 안에 위치

    - 메모리 전송 100MHz에서 133MHz

- The Intel Pentium M Processor(2003~2006)
    - 64KB L1 캐시(명령/데이터 32KB씩)
    - L2 캐시(2MB까지)
    - Advanced Branch Prediction and Data Prefetch Logic
        - 분기 실행에 대한 예측을 해서 미리 fetch하는 성능 향상 로직
    - MMX technology, Streaming SIMD instructions, SSE2 명령어
    - 버스 속도 400 or 533 MHz
    - 인텔 스피드 스텝 기술 적용
- The Intel Core Duo and Intel Core Solo Processors(2006~2007)
    - 2MB L2 캐시: 2개의 코어 사이에 인텔 스마트 캐시 기술 적용
    - 디코딩과 SIMD 실행 상향
    - 인텔 발열 관리 기술 Deep Sleep 기술을 통해 전력 소비 줄임
    - 디지털 열 센서 인터페이스 제공하는 인텍 Advanced Thermal Manager 기술 적용
    - 전력 최적화된 버스 속도 667MHz
- Pentium 4(2000~2006)
    - Netburst 마이크로 아키텍쳐 사용
    - 1.4~1.9GHz 시작 나중에는 3.20, 3.45GHz까지(Hyper-Threading)
    - 1MB/512KB/256KB L2 캐시
    - 최대 800MHz에서 400MHz까지 시스템 버스 지원
    - 144개의 새로운 SIMD 128비트 처리 명령어
- Mobile Pentium 4-M / Pentium 4E / Pentium 4EE

- Itanium / Itanium2(2001/2002~2010)
    - 733, 800MHz(Itanium), 900MHz – 1.6GHz (Itanium2)
    - 최초의 64비트 CPU
    - 기존의 x86과는 전혀 다른 독자적인 명령 집합(IA-64)
- Pentium 4F / Pentium D(2005)
    - Netburst 마이크로 아키텍쳐
    - 인텔 확장 메모리 64 기술
    - AMD의 AMD64 아키텍쳐와 호환 가능
    - PentiumD: Netburst 마이크로 아키텍쳐를 포함한 데스크탑 듀얼 코어 64비트 x86-64 마이크로 아키텍쳐
- Intel Core 2(2006)
    - 코어 마이크로 아키텍쳐
    - 코어의 개수가 2개인 CPU
    - 64KB L1 캐시(코어 당)
    - 인텔 VT-x 지원
        - 가상 머신 기능을 지원하는 CPU의 기능
    - ~3.0GHz clock rate
- Xeon(2004~)
    - 서버나 고급 사양의 컴퓨터에 장착되는 인텔의 64비트 CPU
- Core i3 / Core i5 / Core i7(2010~)
    - 1세대: Nehalem 마이크로 아키텍쳐(2010)
    - 2/3세대: Sandy Bridge/Ivy Bridge 마이크로 아키텍쳐(2011~2012)
    - 4세대: Haswell(2013)
    - 5세대: Broadwell(2014)
    - 6세대: Skylake(2015~2019)
    - Kady lake, coffee lake, cannon lake, ice lake, comet lake, ...

### IA-32 Architecture

- 컴퓨터 아키텍쳐: CPU가 어떻게 작동하고 컴퓨터 메모리를 어떻게 사용하는지에 관한 것
    - 명령어 집합 아키텍쳐(ISA), 마이크로 아키텍쳐(ISA 구현 방식), 시스템 설계(주변 장치들과 어떻게 상호작용 하는지에 대한 것) 포함
- IA-32, IA-64 아키텍쳐: 인텔 사가 사용하는 인텔 32비트 객체, 64비트 객체의 공식 명칭
    - Intel 64 = x86-64 = AMD64

#### IA-32 Basic Execution Environment

- Stack
- 함수가 호출될 때 매개 변수를 담음
- 함수가 수행이 끝나고 복귀할 때 복귀 주소
- 프로그램이 시작할 때 메모리 상에 무조건 주어짐

![Adress Space](../image/IA32_AS.jpg)   
- 메인 메모리 주소 공간
- 전체 주소 공간: $2^{32}$ byte, 0 ~ $2^{32} - 1$, 4GB
- flat하거나 segemented하게 사용할 수 있음
- 실행 중인 모든 작업이나 프로그램은 최대 4GB의 선형 주소 공간과 최대 64GB의 물리적 주소 공간을 처리할 수 있음

![Basic Program Execution Registers](../image/IA32_BPER.jpg)   
- 응용 프로그램이 실행 도중에 접근할 수 있는 기본적인 레지스터 집합
- `General-Purpose Registers(범용 레지스터)`: 피연산자와 포인터를 저장하여 사용하는 레지스터(32비트, 8개), user-visible 레지스터에 해당
- `Segment Registers(세그먼트 레지스터)`: 세그먼트에 대한 정보를 담고 관리하는 레지스터(16비트, 6개)
    - 세그먼트 레지스터에 담기는 16비트 크기의 값은 세그먼트 셀렉터라고 함
- `EFLAGS Register`: 현재 CPU의 상태 정보를 담고 있는 레지스터(32비트, 1개), control and status 레지스터에 해당
    - 제한적이지만 CPU의 동작에 대한 제어를 할 수 있음
- `EIP(Instruction Pointer Register)`: 다음 명령어 실행의 위치를 가리키는 포인터를 갖는 레지스터(32비트, 1개), control and status 레지스터에 해당   
    ![General-Purpose/Segment](../image/IA32_BPER(2).jpg)     
    - General Purpose Registers
        - 논리 연산과 산술 연산을 수행할 때 피연산자를 담음
        - 메모리 포인터를 담음
        - 주소 계산을 위한 피연산자를 담음
    - ESP 레지스터: 스택의 탑을 나타내는 스택 포인터, 다른 용도로 사용하면 안됨
    - 많은 명령어들은 피연산자를 담기 위해 특정 레지스터를 할당
        - `EAX`: Accumulator(누산기) (EAX, AX, AL, AH)
            - 곱셈, 나눗셈 명령을 실행 시 사용
            - 그 외에는 범용
        - `EBX`: Base Index
            - 데이터 포인터에 대한 오프셋
            - 데이터 세그먼트에 대한 포인터
        - `ECX`: Count
            - REP, LOOP 명령 실행 시 반복 횟수를 담을 때 사용
            - 그 외에는 범용
        - `EDX`: Data
            - 곱셈, 나눗셈 명령 실행 시 사용됨
            - 입출력 명령 실행 시 대상 데이터에 대한 포인터
        - `ESI`: Source Index
        - `EDI`: Destination Index
            - 배열 접근 명령 실행 시 소스/대상 포인터
        - `ESP`: Stack Pointer
            - 스택의 탑을 가리키는 포인터
        - `EBP`: Base Pointer
            - 메모리 데이터 전송을 위한 포인터
            - 스택의 탑이 아닌 데이터 포인터
        
        ![범용 레지스터 이름](../image/GPR_altername.jpg)
    
    ![Program Status/Control, Instruction Pointer](../image/IA32_BPER(3).jpg)   
    - EFLAGS Register
        - 32비트, 일련의 상태 플래그, 하나의 제어 플래그, 여러 개의 시스템 플래그를 가지고 있음
        - 플래그 하나는 32비트 레지스터의 비트 하나에 해당(예외로 2비트 플래그 존재)
        - 플래그의 초기값은 00000002H
        - 1, 3, 5, 15, 22 ~ 31까지의 비트 값은 사용되지 않음
        - 플래그를 절차 스택 또는 EAX 레지스터로 이동하는 명령어
            - LAHF, SAHF, PUSHF, PUSHFD, POPF, POPFD
        - 인터럽트/예외를 다루는 절차에 호출이 이루어지면 프로세서는 자동으로 절차 스택에 EFLAGS 레지스터의 상태 저장
        ![EFLAGS Register](../image/EFLAGSr.jpg)   

        - Status flags
            - EFLAGS 레지스터의 상태 플래그(비트 0, 2, 4, 6, 7, 11)는 ADD, SUB, MUL, DIV 명령과 같은 산술 명령의 결과를 나타냄
            - `CF(비트 0) Carry flag`
                - 산술 연산에서 결과의 최상위 비트에서 자리올림수 또는 빌림수를 생성할 경우 설정
                - 부호 없는 정수 산술의 오버플로우 조건을 나타냄
            - `PF(비트 2) Parity flag`
                - 결과의 최하위 바이트가 짝수 개의 1비트를 포함할 경우 설정
            - `AF(비트 4) Adjust flag`
                - 산술 연산으로 결과의 비트 3에서 자리올림수 또는 빌림수가 발생하면 설정
                - BCD 산술 연산에서 사용
            - `ZF(비트 6) Zero flag`
                - 결과가 0이면 설정
            - `SF(비트 7) Sign flag`
                - 부호가 있는 정수에서 부호 비트의 결과의 최상위 비트와 동일하게 설정(0은 양수, 1은 음수)
            - `OF(비트 11) Overflow flag`
                - 정수 결과가 너무 큰 양수 또는 음수(부호 비트 제외)라서 대상 피연산자에 들어가지 않으면 설정
                - 부호 있는 정수 산술의 오버플로우 조건을 나타냄
            
            - 상태 플래그 중 CF 플래그만 STC, CLC, CMC 명령을 사용하여 직접 수정할 수 있음
                - 비트 명령(BT, BTS, BTR, BTC)은 지정된 비트를 CF 플래그에 복사
            - 상태 플래그를 사용하면 단일 산술 연산으로 부호 없는 정수, 부호 있는 정수 및 BCD 정수의 3가지 데이터 유형에 대한 결과 생성 가능
            - 조건 명령 Jcc(jump on condition code cc), SETcc(byte set on condition code cc), LOOPcc, CMOVcc(conditional move)는 상태 플래그 중 하나 이상을 조건 코드로 사용하고 분기, 바이트 설정, 종료 루프 조건에 대해 테스트
        
        - Direction flag
            - 방향 플래그(DF, 비트 10)는 문자열 명령(MOVS, CMPS, SCAS, LODS, STOS)을 제어
            - DF 플래그 설정 시 문자열 명령 자동 감소(높은 주소에서 낮은 주소로 문자열 처리)
            - DF 플래그 미 설정 시 문자열 명령 자동 증가(낮은 주소에서 높은 주소로 문자열 처리)
            - STD는 DF 플래그 설정, CLD는 DF 플래그 지우기
        
    - Instruction Pointer Register
        - 명령 포인터(EIP) 레지스터에는 현재 코드 세그먼트에 다음 실행 명령의 오프셋을 포함
        - JMP, Jcc, CALL, RET, IRET 명령을 실행할 때 한 명령 경계에서 다음 명령 경계로 이동하거나 여러 명령에 의해 앞 또는 뒤로 이동
        - EIP 레지스터는 소프트웨어에서 직접 접근할 수 없으며, 제어-전송 명령, 인터럽트 및 예외에 의해 암묵적으로 제어
            - EIP 레지스터를 읽을 수 있는 유일한 방법은 CALL 명령을 실행한 다음 절차 스택에서 반환 명령 포인터의 값을 읽는 것
        - 절차 스택에서 반환 명령 포인터의 값을 수정하고 반환 명령을 실행함으로써 EIP 레지스터를 간접적으로 로드할 수 있음

![FPU Registers](../image/IA32_FR.jpg)   
- 부동소수점 연산 명령이 사용하는 전용 레지스터
- `Floating-Point Data Registers(부동소수점 데이터 레지스터)`: 80비트, 8개
- `Control Register(제어 레지스터)`: 16비트, 1개
- `Status Register(상태 레지스터)`: 16비트, 1개
- `Tag Register(태그 레지스터)`: 16비트, 1개
- `Opcode Register(연산 코드 레지스터)`: 11비트, 1개
- `FPU Instruction Pointer Register`: 48비트, 1개
- `FPU Data(Operand) Pointer Register`: 48비트, 1개

![MMX/XMM Registers](../image/IA32_MR_XR.jpg)   
- 명령이 사용하는 레지스터
- MMX Registers: 64비트, 8개
- XMM Registers: 128비트, 8개
- MXCSR Registers: 32비트, 1개

#### Modes of Operation

- IA-32 아키텍쳐는 3가지 기본 동작 모드를 지원
    - 동작 모드는 어떤 명령어와 아키텍쳐 특징에 접근할 수 있는지 결정
    - 운영 체제가 컴퓨터를 부팅하는 과정에서 선택
    - 보통 보호 모드와 호환 모드 중 하나 동작
    - `Protected mode`(보호 모드)
        - 32비트 모드
    - `Real-address mode`(리얼 주소 모드, 리얼 모드, 호환 모드)
        - 16비트 모드
    - `System management mode`(시스템 관리 모드)
        - 디버깅 같은 특수한 상황에서 사용
- IA-32 메모리 모델
    - Flat memory model
        - 보호 모드에서 사용할 수 있는 메모리 모델
    - Segmented memory model
        - 보호 모드에서 사용할 수 있는 메모리 모델
    - Real-address memory model
        - 리얼 모드에서만 사용할 수 있는 메모리 모델

##### IA-32 Memory Models

![Flat Model](../image/IA32MM_FM.jpg)   
- 32비트 주소 공간(4GB)을 단순하게 1차원적인 플랫한 주소 공간으로 놓고 사용하는 모델
- linear address space: 4GB 주소 공간을 부르는 공식 용어, 선형 주소 공간
    - 특정한 위치 어딘가를 지칭할 때 사용하는 주소
    - 32비트
    - 가상적인 주소 공간
    - 페이징을 통해 실제 물리 메모리로 매핑이 됨

![Segmented Model](../image/IA32MM_SM.jpg)   
- 선형 주소 공간 4GB가 주어짐
- 여러 개의 세그먼트라고 하는 단위로 나누어서 사용
    - segment(세그먼트): 하나의 프로그램을 구성하는 논리적 단위, 코드, 데이터, 스택 세그먼트 등이 있음, 최대 크기는 선형 주소 공간의 크기와 같음
- 프로그램을 세그먼트로 나눈 다음에 선형 주소 공간에 적절히 배치
- 프로그램이 사용하는 논리 주소가 숫자 2개로 결정(세그먼트 셀렉터, 오프셋)

![Real-Address Mode Model](../image/IA32MM_RAM.jpg)   
- 16비트 주소 공간(64KB)
- 전체 주소 공간 외는 세그먼트 모델과 동일

- Segment Registers
    - 세그먼트 레지스터, CS, DS, ES, SS, FS, GS는 16비트 세그먼트 셀렉터를 보유함
        - 세그먼트 셀렉터: 메모리에서 세그먼트를 식별하는 특수 포인터
    - `CS(Code Segment)`
        - 리얼 모드에서는 64KB 메모리 세그먼트의 시작을 나타냄
        - 보호 모드에서는 셀렉터를 선택
    - `DS(Data Segment)`
        - 데이터 세그먼트에 대해 CS와 비슷한 기능 수행
    - `ES(Extra Segement)`
        - 추가적인 데이터 세그먼트에 대해 셀렉터 기능
        - 몇가지 배열 명령 실행 시 대상 데이터를 담는 기능
    - `SS(Stack Segment)`
        - 스택 세그먼트에 대해 CS와 비슷한 기능 수행
        - ESP와 EBP는 이 세그먼트에 오프셋을 유지
    - `FS and GS`
        - 추가의 세그먼트를 사용할 경우 추가된 세그먼트의 셀렉터를 담음
    - 최대 6개까지의 세그먼트를 정의해서 사용할 수 있다

- Real-Address Memory Model in Real-Address Mode
    - 8086/8088 및 IA-32 아키텍쳐의 리얼 모드에서만 사용 가능
        - 프로세서가 처음 1MB의 메모리만 처리할 수 있도록 함
    - 세그먼트와 오프셋
        - segment:offset
        - 유효 주소 = 세그먼트 주소 + 오프셋
        - 어느 세그먼트에 대한 오프셋이냐에 따라서 그 옵션을 담는 범용 레지스터가 미리 정해져 있음

## Chapter 4

### Assembly language

- 어셈블리 프로그래밍의 이유
    - 성능 향상을 위해
    - 어셈블리어로 작성해야 하는 코드 부분이 있음
    - 특정한 CPU의 동작을 깊게 이해할 수 있음
- 어셈블리어는
    - 기계 의존적
    - 공통적인 형태가 존재(공통적인 문법 등)

#### The four field format

- 어셈블리어 프로그램은 한 줄에 어셈블리 명령을 하나씩 적는다
    - 어셈블리 문장(statement): 어셈블리 명령을 적어 놓은 것
- 경우에 따라서는 문장 하나를 여러 줄에 걸쳐 쓸 수 있다
    - 이어지는 문장임을 표시하기 위해 첫번째 줄 끝에 continution 문자 사용(보통 역슬래시 사용 '\\')
- 어셈블리 문장은 4개의 영역으로 이루어져있다
    - `label field`
        - 어셈블리 문장에서 보통 맨 앞에 놓임
        - 해당 레이블이 붙어 있는 곳의 메모리 주소를 특정한 심볼로 표현한 것(레이블은 주소)
        - 점프 명령의 대상 지정
        - 레이블을 구성하는 문자는 알파벳, 숫자, _, $, # 등 사용 가능
            - 첫번째 글자로 올 수 있는 것은 알파벳, 점(.), 언더바(_), 물음표(?) 4가지
        - $가 앞에 붙으면 레지스터가 아니라는 의미
    - `mnemonic(opcode) field`
        - 어떤 기계 명령을 나타내는지 표시
        - MOV, ADD, SUB 등
        - mnemonic: 기억하기 쉬운, 연상 기호
    - `operand field`
        - 명령어가 동작하는 대상을 표시
        - 각 명령에는 고정된 피연산자 수가 있음
            - ADD는 2개, JMP는 1개 ... 등
        - 피연산자가 둘 이상인 경우 쉼표로 구분
        - 피연산자의 유형은 레지스터, 메모리, immediate, implied 4가지
            - immediate: 산술 피연산자의 경우 모든 피연산자가 레지스터이지만 그 중 하나의 피연산자가 상수값을 갖는 경우
            - implied: 명령 자체에는 표시하지 않는 경우
    - `comment field`
        - 세미콜론(;)으로 시작
        - 코멘트 필드만 있는 라인도 존재 가능
        - 어셈블리 프로그램에서 소스 코드를 읽고 이해하는 것이 힘들기 때문에 코멘트 필드도 중요

#### The MOV instruction

- 데이터 복사 기능
- MOV reg, imm
    - imm값을 reg로 복사하는 동작
    - reg의 값을 특정한 상수값으로 설정하는 기능
    - 한 쪽의 크기가 명확하고 다른 쪽은 아닌 경우 명확한 한 쪽의 크기에 맞춤
    - 레지스터의 범위를 초과하면 복사 불가
- MOV reg, reg
    - 두번째 reg의 값을 첫번째 reg로 복사하는 동작
    - 첫번째 피연산자를 destination operand라고 함
    - 두번째 피연산자를 source operand라고 함
    - 첫번째 reg의 값은 바뀌고 두번째 reg의 값은 안 바뀜
    - 두번째 피연산자의 크기가 작으면 오류 발생
- 모호한 명령: MOV BL, AH
    - AH레지스터 또는 16진수 A 헷갈림
    - NASM: 16진수 숫자는 수로 시작해야함
        - 따라서 16진수 A를 표시하려면 0AH라고 써야함

#### Addition Instruction

- 두 데이터를 덧셈 기능
- ADD reg, imm
    - imm를 reg의 현재 값에 더하는 동작
    - 결과값은 reg에 담김
    - reg = reg + imm
- ADD reg, reg
    - 두번째 reg의 값을 첫번째 reg의 값에 더하는 동작
    - 결과값은 첫번째 reg에 담김
    - 두번째 reg의 값은 바뀌지 않음

#### Subtraction Instruction

- 두 데이터의 뺄셈 기능
- SUB reg, imm
    - reg의 현재 값에서 imm의 값을 빼는 동작
    - 결과값은 reg에 담김
- SUM reg, reg
    - 첫번째 reg의 현재 값에서 두번째 reg의 값을 빼는 동작
    - 결과값은 첫번째 reg에 담김

#### Multiplication Instruction

- MUL reg
    - 승수(곱하는 수)의 값이 레지스터에 있음
    - 피승수(곱해지는 수)는 항상 A 레지스터에 있음
    - 곱셈하는 숫자 2개 중에 하나는 명령 자체에 명시적으로 표시되지 않음(implied)
    - 곱셈 명령을 실행하기 전에 피승수가 A 레지스터 안에 존재하도록 해야함
    - 결과값은 A 레지스터와 D 레지스터에 담김(비트가 클 경우엔 합쳐야 함)

#### Division Instruction

- DIV reg
    - DIV는 MUL구문과 유사하다(본질적으로 그의 역)
    - 젯수(나누는 수)의 값은 레지스터에 있음
    - 피젯수(나뉘는 수)는 A, D 레지스터에 있음
    - 결과값은 몫과 나머지가 A, D 레지스터에 담김

#### Constants

- Numeric constants
    - 숫자 상수
    - 10진수: 일상생활에서 표시하는 방식
    - 16진수
        - 16진수 앞은 0으로 시작하고 뒤는 h로 끝나는 방식
        - 16진수 앞이 $0으로 시작하는 방식
        - 16진수 앞이 0x로 시작하는 방식
    - 8진수: 8진수 뒤가 q 또는 o로 끝나는 방식
    - 2진수: 2진수 뒤가 b로 끝나는 방식

- Character constants
    - 문자 상수
    - 큰 따옴표(")나 작은 따옴표(') 사이에 쓰이면 문자 상수이다
    - 문자 상수가 연속이어도 문자 상수이다(1글자, 2글자, 4글자만)
    - 둘 이상의 문자를 가진 문자 상수는 little-endian(낮은 주소에 최하위비트를 저장)을 사용

- String constants
    - 문자열 상수
    - 임의의 개수의 문자가 연속적으로 이어지는 형태의 상수
    - 의사 명령에서만 사용 가능

- Floating-point constants
    - 부동소수점 상수
    - 의사 명령에서만 사용 가능
    - 숫자, 점, 일련의 숫자나 알파벳 문자 e와 지수로 표현됨

### Pseudo-Instructions and Directives

- 어셈블러에게 무언가를 하도록 지시하거나 무언가를 알려주는 것
    - 상수 정의
    - 데이터를 저장할 메모리 정의
    ----------------------------
    - 메모리를 세그먼트로 그룹화
    - 조건부로 소스 코드 포함
    - 다른 파일 포함

#### Pseudo-Instructions

- `DB`(Define Byte): 초기화된 데이터를 정의하는데 사용
    - 피연산자를 가질 수 있음(여러 개도 가능)
    - 대부분의 경우 레이블이 붙어서 사용(참조를 하기 위해)
    - `DW`(Define Word): 하나의 워드를 할당하는데 사용
        - word: 16비트, 2바이트
    - `DD`(Define Doubleword): 2개의 워드를 할당하는데 사용
        - 2워드 = 32비트 = 4바이트
    - `DQ`(Define Quadword): 4개의 워드를 할당하는데 사용
        - 4워드 = 64비트 = 8바이트

- `RESB`(Reserve Byte): 바이트를 할당하되 초기화되지 않은 값 사용
    - 숫자 상수를 피연산자로 가짐
    - `RESW`(Reserve Word)
    - `RESD`(Reserve Doubleword)
    - `RESQ`(Reserve Quadword)
    - 연속으로 할당됨

- `TIMES`: 명령이나 데이터를 일정하게 반복한다는 의미의 접두어
    - 혼자서 사용 불가

- `EQU`: 심볼을 정의

#### Directives

- `SECTION` or `SEGMENT`
    - 하나의 세그먼트를 정의하는 역할
    - 디렉티브가 사용된 지점부터 새로운 세그먼트 시작
    - 다음번 섹션이 나오거나 프로그램의 끝을 만날 때까지가 하나의 세그먼트
    - 세그먼트의 타입을 지정할 수 있는 피연산자
        - .text
            - 코드 세그먼트 정의
        - .data
            - 데이터가 모여 있는 공간
        - .bss
            - 초기화되지 않은 데이터가 모여 있는 공간

- `GLOBAL`
    - 다른 모듈에 export하는 역할
    - 지금 내가 쓰고 있는 심볼을 다른 모듈에서도 쓸 수 있게 함

- `EXTERN`
    - 다른 모듈에서 import하는 역할
    - 다른 모듈에서 쓰는 심볼을 지금 프로그램에서도 쓰겠다 선언
    - 사용하고자 하는 외부 심볼들을 콤마(,)로 구분

## Chapter 5

### Arithmetic & Logic Operations

- Arithmetic Operations
    - Addition
    - Subtraction
    - Multiplication
    - Division
    - Comparison
    - Negation
    - Increment
    - Decrement

- Logic Operations
    - AND
    - OR
    - XOR
    - NOT
    - shift
    - rotate
    - compare(test)

- Arithmetic & Logic Operations
    - EFLAGS의 몇 개의 비트들은 산술 연산이나 논리 연산에 따라서 바뀔 수 있다
    - 상태 플래그
        - Z(결과가 0인 경우)
            - 0인 경우 1, 0이 아닌 경우 0
        - S(결과가 양수인 경우)
            - 결과값의 최상위 비트의 값과 같음
            - 양수인 경우 0, 음수인 경우 1
        - C(캐리가 발생할 경우)
            - 최상위 비트에서 캐리 발생 시 1, 발생하지 않을 시 0
        - P(결과가 짝수 패리티를 가질 경우)
        - A(보조 캐리가 발생할 경우)
        - O(오버플로우가 발생할 경우)

#### Addition

- **add** (addition)
    - add al, [ARRAY + esi]
    - 캐리를 포함하지 않은 덧셈
- **inc** (increment)
    - inc byte [edi]
    - 피연산자의 값을 1 증가한다
- **adc** (add with carry)
    - adc ecx, ebx
    - 캐리를 포함한 덧셈
    - 레지스터의 값들과 캐리 플래그(CF)의 값을 더한다
    - 64비트 수의 덧셈에 사용된다
- **xadd** (exchange and add)
    - xadd ecx, ebx
    - ecx = ecx + ebx, ebx = original ecx
    - 첫번째 피연산자에는 첫번째 피연산자와 두번째 피연산자의 덧셈 결과의 값이, 두번째 피연산자에는 덧셈 수행 전의 첫번째 피연산자의 값이 저장된다

#### Subtraction

- **sub** (subtraction)
    - sub eax, ebx
    - 캐리를 포함하지 않은 뺄셈
- **dec** (decrement)
    - dec edi
    - 피연산자의 값을 1 감소한다
- **sbb** (subtract with borrow)
    - sbb ecx, ebx
    - 캐리를 포함한 뺄셈
    - 레지스터의 값들과 캐리 플래그의 값을 뺀다
    - ecx = ecx - ebx - carry flag

- Comparison
    - 뺄셈 연산을 하되 결과는 저장하지 않는다
    - 뺄셈 결과로 플래그 값만 영향을 받는다
    - **cmp**
        - cmp al, 10H
        - 뒤에 조건 분기 명령이 나온다
    - **cmpxchg**
        - cmpxchg ecx, edx
        - 만약 ecx == eax 라면 eax = edx
        - ecx != eax라면 eax = ecx
        - 상호 배제 구현 시 사용

#### INC and DEC

- INC
    - INC reg
    - reg의 값을 1 증가 시킨다
    - ADD reg, 1과 같다
- DEC
    - DEC reg
    - reg의 값을 1 감소 시킨다
    - SUB reg, 1과 같다

#### Multiplication and Division

- **mul** / **div** : 부호 없는 수
- **imul** / **idiv** : 부호 있는 수
- al(또는 ax 또는 eax)은 언제나 곱해지는 수를 담고 있다
- 결과는 ax(또는 dx와 ax 또는 edx 또는 eax)에 저장된다
- 16비트 곱셈의 최상위 8비트가 0이면 C비트와 O비트가 0이된다(8비트 곱셈의 결과는 8비트)
- 0과 오버플로우로 나누면 오류가 발생한다
- 오버플로우는 작은 수가 큰 나누어지는 수를 나눌 때 발생한다

#### AND, OR, XOR

- 비트를 1로 설정하거나 0으로 클리어하거나 1이면 0으로 0이면 1로 바꿀 때 사용한다
    - 일반적으로 I/O 장치를 제어하는 데 사용됨
    - 논리 연산은 항상 캐리 및 오버플로우 플래그를 클리어한다

- **AND**
    - 0과의 AND 연산은 항상 0
    - 특정 일부 비트를 0으로 클리어할 때 사용
    - and al, bl
    - 첫번째 피연산자, 두번째 마스크, 결과는 첫번째 피연산자에 저장

- **OR**
    - 1과의 OR 연산은 항상 1
    - 특정 일부 비트를 1로 설정할 때 사용
    - or eax, 10
    - 첫번째 피연산자, 두번째 마스크, 결과는 첫번째 피연산자에 저장

- **XOR**
    - 같으면 0, 다르면 1
    - 0을 1로 1을 0으로 바꾸고 싶을 때 사용
    - xor ah, ch
    - 첫번째 피연산자, 두번째 마스크, 결과는 첫번째 피연산자에 저장

#### TEST

- **TEST**
    - 논리 연산(AND)을 하되 결과를 저장하지 않는다
- **BT**
    - 비트를 테스트 한다
- **BTC**
    - 비트를 테스트하고 보완한다
- **NOT**
    - 논리적 1의 보수
- **NEG**
    - 산술적 2의 보수 - 부호가 바뀜

#### Shift

- Shift
    - logical
        - left: **shl**
        - right: **shr**
    - arithmetic
        - left: **sal**
        - right: **sar**

    - Shift 대상 피연산자와 shift count 피연산자로 구성
        - count 피연산자는 최대 5비트만 유의

- SHL과 SAL은 기본적으로 동작이 동일
    - 목적 피연산자의 부호 없는 2의 거듭제곱 곱셈
    - 부호 있는 값에 대해서는 작동하지 않음
    ![SHL/SAL](../image/shl_sal.jpg)
        - 1비트를 왼쪽으로 쉬프트 할 경우 1비트만 캐리플래그에 저장되고 오른쪽에 0이 1비트 채워진다
        - 10비트를 왼쪽으로 쉬프트 할 경우 10비트 중 제일 오른쪽 비트만 캐리플래그에 저장되고 오른쪽에 0이 10비트 채워진다

- SHR
    - 목적 피연산자의 부호 없는 2의 거듭제곱 나눗셈
    ![SHR](../image/shr.jpg)
        - 1비트를 오른쪽으로 쉬프트 할 경우 1비트만 캐리플래그에 저장되고 왼쪽에 0이 1비트 채워진다
        - 10비트를 오른쪽으로 쉬프트 할 경우 10비트 중 제일 왼쪽에 있는 비트만 캐리플래그에 저장되고 왼쪽에 0이 10비트 채워진다

- SAR
    - 빈자리는 원래 값의 부호 비트로 채움
    - 목적 피연산자의 부호 있는 2의 거듭제곱 나눗셈
    ![SAR](../image/sar.jpg)
        - 1비트를 오른쪽으로 쉬프트 할 경우 1비트만 캐리플래그에 저장되고 왼쪽에는 원래 주어진 수의 부호 비트로 채워진다
            - 부호 비트가 양수이면 0, 음수이면 1이 채워진다
            - 5비트를 쉬프트 할 경우 왼쪽에는 5비트가 모두 부호 비트로 채워진다

#### Double Precision Shift

- **shld** / **shrd**
    - shdl, shdr로 쓰는 경우도 있음
    - shrd eax, ebx, 12
        - eax를 오른쪽으로 12비트 쉬프트 하고 왼쪽을 ebx의 오른쪽 12비트로 채운다
    - shld ax, bx, 14
        - ax를 왼쪽으로 14비트 쉬프트 하고 오른쪽을 bx의 왼쪽 14비트로 채운다
    ![SHLD, SHRD](../image/shld_shrd.jpg)

- shld dst, src, count
    - dst: 레지스터, 메모리
    - src: 레지스터만 가능 (빈공간을 채워주는 값을 가지고 있는 피연산자)
    - count: CL 또는 8비트 immediate
        - count 값을 레지스터에 넣고 싶다면 CL만 사용 가능

#### Rotate

- 한쪽 끝에서 다른 쪽 끝으로 또는 캐리플래그를 통해 비트를 회전한다
- 일반적으로 32비트보다 큰 숫자에서 작동하는데 사용

- Rotate
    - logical
        - left: **rol**
        - right: **ror**
    - arithmetic
        - left: **rcl**
        - right: **rcr**
    ![ROL, ROR, RCL, RCR](../image/rol_ror_rcl_rcr.jpg)
        - ROL: 왼쪽으로 회전하는데 왼쪽으로 빠져나간 값이 캐리플래그로도 들어가고 오른쪽 끝으로도 들어간다
            - 5비트 회전 시 제일 오른쪽 값이 캐리플래그에 들어간다
        - ROR: 오른쪽으로 회전하는데 오른쪽으로 빠져나간 값이 캐리플래그로도 들어가고 왼쪽 끝으로도 들어간다
            - 5비트 회전 시 제일 왼쪽 값이 캐리플래그에 들어간다
        - RCL: 캐리플래그를 포함한 33비트를 왼쪽으로 회전한다
        - RCR: 캐리플래그를 포함한 33비트를 오른쪽으로 회전한다

#### Bit/String Scan

- Bit Scan Instruction (80386 이상)
    - 피연산자를 통해 1인 비트를 검색한다
    - 1인 비트가 발견되면 제로플래그가 클리어되고, 비트의 위치가 목적 피연산자에 저장된다
        - 1인 비트가 없으면 목적 피연산자가 바뀌지 않음
    - **bsl**
        - bls ebx, eax
        - eax를 왼쪽부터 스캔한다
    - **bsr**
        - bsr bl, cl
        - cl을 오른쪽부터 스캔한다

- String Scan Instruction
    - scasb/scasw/scasd는 al/ax/eax 레지스터를 메모리 바이트 블록과 비교하여 플래그를 설정한다
    - repe나 repne와 함께 사용되는 경우가 많다
    - cmpsb/cmpsw/cmpsd는 메모리 데이터의 두 섹션을 비교한다

## Chapter 6

### Control Transfer Instructions

- Control Transfer Instruction
    - 프로그램의 순차적 실행 흐름을 바꿀 수 있는 명령

- 무조건 분기(Unconditional transfers)
    - jump
    - call and return(함수 호출, 함수가 끝나서 복귀)

- 조건 분기(Conditional transfers)

- 소프트웨어 인터럽트
    - 인터럽트
        - 소프트웨어
            - CPU가 동작을 하다가 CPU 내부적으로 어떤 문제가 생겨서 CPU의 상태가 하드웨어 인터럽트를 받은 상태 직후와 유사한 상태로 바뀌는 것
        - 하드웨어
            - 입출력 장치가 CPU에게 보내는 전기적인 신호
            - 하드웨어 인터럽트도 분기 발생

### Unconditional Transfer

- jmp
    - jmp 명령이 지정한 곳으로 실행의 흐름이 넘어감
    - 반환 정보를 기록하지 않고 프로그램 컨트롤을 명령 스트림의 다른 지점으로 전송(복귀하지 않음, 복귀하는 것은 함수 호출하는 call)
    - 목적 피연산자는 상수, 범용 레지스터 또는 메모리 위치(절대 오프셋 vs 상대 오프셋)일 수 있다
    - 코드 레이블로 상수 피연산자를 지정할 수 있다

- Code label
    - 프로그램 컨트롤이 전송되는 코드 세그먼트의 레이블
    - 레이블은 프로그래머에 의해 작성되며, 길고 이해하기 쉬운 레이블은 유용하다
    - 종종 콜론이 붙는다
    - 코드 세그먼트에 중복되는 레이블은 존재할 수 없다

#### Variations of Jump

- Near jump
    - 세그먼트 내(기본 점프)
    - jmp [eax]
    - jmp LABEL

- Far jump
    - 컨트롤이 다른 세그먼트로 이동할 수 있다
    - jmp **far** LABEL

- Short jump
    - 단일 바이트를 사용하여 점프의 변위를 저장한다(범위: -128 ~ +128)
    - 위쪽으로 점프 시 -, 아래쪽으로 점프 시 +

### Conditional Transfer

- 조건부 분기는 진리값에 근거하여 수행된다
- 결정은 eflags의 1비트를 기반으로 한다(ZF, SF, CF, OF, PF, AF)
    - **JZ**: 제로플래그가 설정된 경우에만 분기(ZF = 1)
    - **JNZ**: 제로플래그가 설정되지 않은 경우에만 분기(ZF = 0)
    - **JO**: 오버플로우 비트가 설정된 경우에만 분기(OF = 1)
    - **JNO**: 오버플로우 비트가 설정되지 않은 경우에만 분기(OF = 0)
    - **JS**: 사인플래그가 설정된 경우에만 분기(SF = 1)
    - **JNS**: 사인플래그가 설정되지 않은 경우에만 분기(SF = 0)
    - **JC**: 캐리플래그가 설정된 경우에만 분기(CF = 1)
    - **JNC**: 캐리플래그가 설정되지 않은 경우에만 분기(CF = 0)
    - **JP**: 패리티플래그가 설정된 경우에만 분기(PF = 1)
    - **JNP**: 패리티플래그가 설정되지 않은 경우에만 분기(PF = 0)

#### Comparision-based Jump

- cmp vleft, vright

- 부호 없는 정수: ZF, CF
    - 만약 vleft == vright면 ZF == 1, CF == 0
    - 만약 vleft > vright면 ZF == 0, CF == 0
    - 만약 vleft < vright면 ZF == 0, CF == 1

- 부호 있는 정수: ZF, OF, SF
    - 만약 vleft == vright면 ZF == 1, OF == 0, SF == 0
    - 만약 vleft > vright면 ZF == 0, OF == SF
        - 둘 다 양수인 경우 SF == OF == 0
        - 둘 다 음수인 경우 SF == OF == 0
        - vleft > 0 > vright인 경우 vleft + |vright|가 오버플로우인 경우에만 SF == OF == 1
    - 만약 vleft < vright면 ZF == 0, OF $\neq$ SF
        - 둘 다 양수인 경우 SF == 1, OF == 0
        - 둘 다 음수인 경우 SF == 1, OF == 0
        - vright > 0 > vleft인 경우 오버플로우면 SF == 0, OF == 1, 오버플로우가 아니면 SF == 1, OF == 0

|Signed|Unsigned|
|:---|:---|
|vleft = vright이면 JE 분기|vleft = vright이면 JZ 분기|
|vleft $\neq$ vright이면 JNE 분기|vleft $\neq$ vright이면 JNZ 분기|
|vleft < vright이면 JL, JNGE 분기|vleft < vright이면 JB, JNAE 분기|
|vleft $\le$ vright이면 JLE, JNG 분기|vleft $\le$ vright이면 JBE, JNA 분기|
|vleft > vright이면 JG, JNLE 분기|vleft > vright이면 JA, JNBE 분기|
|vleft $\ge$ vright이면 JGE, JNL 분기||vleft $\ge$ vright이면 JAE, JNB 분기|

    - L: less
    - G: greater
    - B: below
    - A: above

- 부호 없는 조건 분기
    ![unsigned conditional jumps](../image/unsigned_conditional_jumps.jpg)

- 부호 있는 조건 분기
    ![signed conditional jumps](../image/signed_conditional_jumps.jpg)

#### Translating Standard Control Structures

- if
    ```
        ;FLAGS를 설정하는 코드
        jxx endif   ;조건을 불만족 할 경우 분기가 발생하도록 xx 선택

        ;then_block에 들어갈 코드
    endif:
    ```

- if-else
    ```
        ;FLAGS를 설정하는 코드
        jxx else_block  ;조건을 불만족 할 경우 분기가 발생하도록 xx 선택

        ;then_block에 들어갈 코드
        jmp endif
    else_block:
        ;else_block에 들어갈 코드
    endif:
    ```

- while
    ```
    while:
        ;조건에 따라 FLAGS를 설정하는 코드
        jxx end_while   ;조건을 불만족 할 경우 분기가 발생하도록 xx 선택

        ;반복할 코드
        jmp while
    end_while:
    ```

- do-while
    ```
    do:
        ;반복할 코드
        ;조건에 따라 FLAGS를 설정하는 코드
        jxx do  ;조건을 불만족 할 경우 분기가 발생하도록 xx 선택
    ```

#### Loop Instruction

- ecx의 감소와 조건부 분기 jnz의 조합
    - ecx 감소
    - ecx != 0인 경우 레이블로 점프
    - 그렇지 않으면 통가

- LOOP, LOOPE(loop while equal), LOOPZ(loop while zero), LOOPNE(loop while not equal), LOOPNZ(loop while not zero)

- 앞에 ecx(반복 횟수)가 설정되어야 함
    - ecx의 값은 루프의 바디에서는 바꾸지 않는다

## Chapter 7

### Data Transfer Instructions

- 데이터 이동 명령(General data movement)
    - 데이터 복사 명령
- 데이터 교환(Exchange)
- 스택 조작(Stack manipulation)
    - 스택 영역에 저장되어 있는 데이터를 접근하는데 사용
- 타입 변환(Type conversion)
    - 데이터 타입 변환
- 스트링 연산(String operations)
    - 스트링 전용 명령

### General Data Movement

- mov 명령

|데이터 이동 타입|Source -> Destination|
|:---|:---|
|메모리에서 레지스터|메모리 -> 범용 레지스터 <br/>메모리 -> 세그먼트 레지스터|
|레지스터에서 메모리|범용 레지스터 -> 메모리 <br/>세그먼트 레지스터 -> 메모리|
|레지스터에서 레지스터|범용 레지스터 -> 범용 레지스터 <br/>범용 레지스터 -> 세그먼트 레지스터 <br/> 범용 레지스터 -> 컨트롤 레지스터 <br/> 범용 레지스터 -> 디버그 레지스터 <br/> 세그먼트 레지스터 -> 범용 레지스터 <br/> 컨트롤 레지스터 -> 범용 레지스터 <br/> 디버그 레지스터 -> 범용 레지스터|
|상수 데이터에서 레지스터|상수 -> 범용 레지스터|
|상수 데이터에서 메모리|상수 -> 메모리|
 
    - 이외에는 불가

- 조건부 mov 명령
    - **cmov**
        - 조건이 참인 경우에만 데이터 이동
        - 조건은 이전 명령에 의해 설정되면 캐리, 제로, 사인, 오버플로우, 패리티를 포함
        - cmovz eax, ebx
            - 제로플래그가 설정되어 있을 경우 mov
        - 많은 변형이 있음
    ![variations of conditional move](../image/variation_cmov.jpg)
        - A: above
        - E: equal
        - C: carry
        - B: below
        - N: not
        - Z: zero
        - P: parity, PE: parity even, PO: parity odd
        - G: greater
        - L: less
        - O: overflow
        - S: sign

### Exchange Instructions

- **xchg**
    - 레지스터의 내용을 다른 레지스터 또는 메모리 위치의 내용과 교환
    - 세그먼트 레지스터나 메모리에서 메모리로 데이터를 교환할 수 없다
    - 바이트, 워드, 더블 워드는 아무 어드레싱 모드를 사용하여 교환할 수 있다(상수 제외, 교환하는 크기가 같아야 함)
    - xchg edx, esi
        - edx와 esi 교환

- **bswap**
    - 피연산자를 한 개만 갖는다(double word)
    - 1번째 바이트는 4번째 바이트로, 2번째 바이트는 3번째 바이트로 교환한다
    - little endian과 big endian을 변환하는데 사용

#### Endianness

- 엔디안니스(endianness)는 컴퓨터 메모리에서 한 단어를 포함하는 바이트의 순서를 가리킨다, 또한 디지털 링크를 통한 바이트 전송 순서도 기술한다

- 빅-엔디안(big-endian): 단어의 최상위 바이트는 특정 메모리 주소에 저장되며 그 다음 바이트는 다음의 상위 메모리 주소에 저장되고 최하위 바이트는 가장 높은 메모리 주소에 저장된다

- 리틀-엔디안(little-endian): 순서를 반대로 하여 최하위 바이트를 가장 낮은 메모리 주소에 저장하고, 최상위 바이트를 가장 높은 메모리 주소에 저장한다

- 빅-엔디안은 데이터 네트워킹에서 가장 일반적인 형식으로 IPv4, IPv6, TCP, UDP 등의 인터넷 프로토콜 모음의 프로토콜 필드가 빅-엔디안 순서로 전송된다 이러한 이유로 빅-엔디안 바이트 순서는 네트워크 바이트 순서(network byte order)라고도 한다

- 리틀-엔디안 저장은 부분적으로 인텔의 마이크로프로세서 설계에 상당한 영향을 미쳤기 때문에 마이크로프로세서에 인기가 있다 (인텔 x86 프로세서는 리틀-엔디안을 사용한다)

- 혼합된 형태들도 존재하는데, 예를 들어 16비트 워드의 바이트들의 순서는 32비트 워드 내의 16비트 워드들의 순서와 다를 수 있다 그런 경우들은 때때로 혼합-엔디안(mixed-endian) 또는 중간-엔디안(middle-endian)으로 지칭된다

- 리틀-엔디안 또는 빅-엔디안 모드로 동작하는 일부 바이-엔디안(bi-endian) 프로세서들도 있다

### Stack Manipulation

- **push**
    - 데이터의 소스는 임의의 16비트 또는 32비트 레지스터, 상수, 임의의 세그먼트 레지스터, 메모리 데이터의 임의의 워드 또는 더블 워드일 수 있다
    - push
        ![push](../image/push.jpg)
            - ESP를 감소시킨 후 push
    - pusha
        ![pusha](../image/pusha.jpg)
            - pushall
            - 피연산자가 없음
            - 범용 레지스터 8개의 모든 값을 스택에 일정한 순서로 push, CPU 상태를 저장할 때 많이 사용
            - EAX, ECX, EDX, EBX, Old ESP, EBP, ESI, EDI 순서

- **pop**
    - 데이터의 소스는 임의의 16비트 또는 32비트 레지스터, 임의의 세그먼트 레지스터(cs 제외), 메모리 데이터의 임의의 워드 또는 더블 워드일 수 있다
    - pop
        ![pop](../image/pop.jpg)
            - pop을 한 후 ESP 증가
    - popa
        ![popa](../image/popa.jpg)
            - popall
            - 피연산자가 없음
            - ESP를 제외한 범용 레지스터의 값을 복원

### Address Loading Instructions

- lea
    - load effective address
    - 첫번째 피연산자에 있는 32비트 레지스터에 두번째 피연산자에 표시된 데이터 주소를 로드한다
    - lea eax, [ebx+ecx*4+100]
        - 두번째 연산자가 100번지를 의미한다면 eax에는 100이 저장됨

- lds, les, lfs, lgs, lss
    - 32비트 오프셋 주소를 로드한 다음 48비트 메모리 위치에서 ds, es, fs, gs 또는 ss를 로드한다
    - lds edi, LIST
        - edi와 ds를 로드
    - lfs esi, DATA1
        - esi와 fs를 로드

- lea vs mov
    - lea ebx, [edi]
        - 두번째 피연산자가 100번지를 의미하면 ebx에는 100이 저장됨
        - edi의 유효주소를 ebx에 로드한다
    - mov ebx, [edi]
        - 두번재 피연산자가 100번지를 의미하면 ebx에는 100번지에 있는 값이 저장됨
        - edi에 있는 값을 ebx에 로드한다
    - mov ebx, edi
        - edi의 값을 ebx에 복사한다
        - lea ebx, [edi]와 같은 수행을 한다
    - lea는 오른쪽 피연산자에서 제공하는 주소를 계산하여 왼쪽 피연산자에 저장한다

### Type Conversion Instructions

- Simple conversion
    - **cbw** (convert byte to word, 8비트 -> 16비트)
        - AX <- sign-extended of AL
    - **cwde** (convert word to doubleword extended, 16비트 -> 32비트)
        - EAX <- sign-extended of AX
    - **cwd** (convert doubleword, 16비트 -> 32비트)
        - DX:AX <- sign-extended of AX
        - 16비트 나눗셈 전에 사용(16비트 나눗셈의 나뉘는 수 형식)
    - **cdq** (convert doubleword to quadword, 32비트 -> 64비트)
        - EDX:EAX <- sign-extended of EAX
        - 32비트 나눗셈 전에 사용(32비트 나눗셈의 나뉘는 수 형식)

- Move with sign or zero extension
    - movsx와 movzx(80386 이상)
    - **movsx** (move and sign extended)
        - 확장 시 추가되는 값은 부호 비트로 채워짐
    - **movzx** (move and zero extended)
        - 확장 시 추가되는 값은 0으로 채워짐

### String Operations

- movs, lods, stos
    - 바이트, 워드, 더블 워드, 또는 반복되는 경우 각각의 블록 데이터 전송을 허용
    - D 플래그 비트(direction), esi, edi는 암시적으로 사용됨
        - D = 0: edi와 esi 자동 증가
        - cld 명령을 이용해 D 플래그 클리어
        - D = 1: edi와 esi 자동 감소
        - std 명령을 이용해 D 플래그 설정
    - edi: 추가 세그먼트의 데이터에 접근한다, 오버라이드 불가
    - esi: 데이터 세그먼트의 데이터에 접근한다, 접두사로 다른 세그먼트와 짝이 되도록 오버라이드 가능

![string operations](../image/string_operations.jpg)
    - String: 같은 크기의 데이터가 연속적으로 메모리 상에 나열되어 있는 것
    - esi: 데이터 세그먼트 내에서 다음번 스트링 연산이 일어날 곳을 가리킴
    - edi: 추가 세그먼트 내에서 다음번 스트링 연산이 일어날 곳을 가리킴
    - A 레지스터: 로드 스트링이나 스토어 스트링이 동작할 때 실제 데이터가 로드, 스토어 되는데 관여하는 레지스터
    - lods
        - 데이터 세그먼트에 저장되어 있는 스트링 중에 데이터를 eax에 복사해 넣는 것
        - esi가 가리키고 있는 곳에서 로드
    - stos
        - A 레지스터에 저장되어 있는 값을 메모리에 복사하는 것
        - edi가 가리키는 곳으로 저장
    - movs
        - 메모리에서 메모리로 바로 전송
    - esi와 edi는 로드와 스토어 후에 자동적으로 다음 데이터를 가리키도록 갱신

#### lods

- **lods**
    - lodsb(byte), lodsw(word), lodsd(double word)
    - 데이터 세그먼트(또는 추가 세그먼트)에 저장된 데이터로 al, ax 또는 eax가 제공하는 오프셋을 로드한다
    - esi는 그 후에 증가 또는 감소한다
    - lodsb
        - al=ds:[esi];  esi=esi+/-1
    - lodsd
        - eax=ds:[esi]; esi=esi+/-4
    - **es** lodsb DATA1
        - ds 오버라이드

#### stos

- **stos**
    - stosb(byte), stosw(word), stosd(double word)
    - al, ax 또는 eax를 추가 세그먼트(es) + edi가 제공하는 오프셋에 저장한다(edi는 오버라이드 불가)
    - edi는 그 후에 증가 또는 감소한다
    - stosb
        - es:[edi]=al;  edi=edi+/-1
    - stosd
        - es:[edi]=eax; edi=edi+/-4

#### movs

- **movs**
    - movsb(byte), movsw(word), movsd(double word)
    - 바이트, 워드 또는 더블 워드를 데이터 세그먼트 및 오프셋 esi에서 추가 세그먼트 및 오프셋 edi로 이동한다
    - edi 및 esi 모두 증가 또는 감소한다
    - movsb
        - es:[edi]=ds[esi];     edi+/-=1;    esi+/-=1
    - movsd
        - es:[edi]=ds:[esi];    edi+/-=4;    edi+/-=4

#### rep Prefix

- **rep** 접두사
    - 명령을 ecx번 반복
    - lods 명령에는 의미가 없다

## Chapter 8

### Data Addressing Modes

- mov 명령을 사용해서 데이터 주소 지정 모드 설명
    - 데이터 이동 명령어는 레지스터와 레지스터, 레지스터와 메모리 간에 데이터(바이트, 워드, 더블워드)를 이동시킨다
    - 두 개의 피연산자를 모두 메모리로 가질 수 있는 것은 movs(strings) 명령밖에 없다
    - 대부분의 대이터 전송 명령은 EFLAGS 레지스터를 변경하지 않는다

- 스토리지 프로토콜(Storage protocols)
    - n바이트 전송이 주소 a로 표시될 때, 참조되는 메모리들은 a, a+1, ..., a+n-1이다
    - n바이트의 숫자가 메모리에 저장될 때, 리틀 엔디안 방식으로 저장된다

- Register
    - mov eax, ebx

- Immediate
    - mov ch, 0x4b

- Direct(eax), Displacement(other regs)
    - mov [0x1234], eax
    - [](각괄호) 안에 메모리 주소의 상수를 직접 넣는 방식
    - 레지스터 피연산자가 eax인 경우에는 direct, 다른 레지스터인 경우에는 displacement

- Register Indirect
    - mov [ebx], cl
    - 레지스터 값의 메모리 번지
    - eax, ebx, ecx, edx, ebp, edi, esi 사용 가능

- Base-plus-index
    - mov [ebx+esi], ebp
    - 베이스가 되는 레지스터와 인덱스가 되는 레지스터 값의 메모리 번지
    - eax, ebx, ecx, edx, ebp, edi, esi의 조합 사용 가능

- Register relative
    - mov cl, [ebx+4]
    - 베이스가 되는 레지스터와 상수 값의 메모리 번지
    - 상수자리에 심볼이 올 수도 있음

#### x86 Indirect Addressing Modes

- indirection operator인 [](각괄호)를 사용해서 메모리 주소를 나타내는 표현 방식

- **BASE + (INDEX * SCALE) + DISPLACEMENT**
    - BASE
        - base register
        - None, eax, ecx, edx, ebx, esp, ebp, esi, edi 사용 가능
    - INDEX * SCALE
        - index register * scale factor
        - None, eax, ecx, edx, ebx, ebp, esi, edi 사용 가능
        - esp는 사용 불가
        - scale factor에는 1, 2, 4, 8로 네가지만 가능
    - DISPLACEMENT
        - 주소 상수
        - None, 8-bit, 32-bit
    - 위 조합으로 여러 가지 indirect addressing 모드 생성 가능

#### Displacement Addressing

- 각괄호 안에 주소 상수만 사용되는 경우

- Displacement addressing
    - 최대 7바이트로 인코딩(32비트 레지스터, 32비트 주소 상수)
    - 정적으로 할당된 단일 데이터에 대한 접근 시 사용
    - mov cl, [DATA1]   ;DATA1에서 1바이트를 복사
    - mov edi, [SUM]    ;SUM에서 4바이트를 복사

- Direct addressing
    - 메모리와 al, ax, eax 간의 전송
    - 일반적으로 3바이트로 인코딩, 어떤 때는 4바이트
    - mov al, [DATA1]
    - mov al, [0x4321]
    - mov al, ds:[0x1234]
    - mov [DATA2], ax

#### Register Indirect Addressing

- 레지스터에 저장된 오프셋(레지스터에 담긴 수)이 세그먼트의 시작점에 더해진다
    - 변수 및 데이터 구조의 동적 저장을 위해 사용
    - mov ecx, [ebx]
        - ebx에 담겨 있는 주소 값이 최종 접근하고자 하는 메모리 주소가 됨

- 메모리와 메모리간의 mov는 문자열 명령으로 허용됨
    - esp를 제외한 모든 레지스터 사용 가능(80386 이상)
    - eax, ebx, ecx, edx, edi, esi의 경우, 데이터 세그먼트가 기본값
    - ebp의 경우, 스택 세그먼트가 기본값
    - 일부 명령에는 byte, word, dword의 특별한 어셈블러 지시어 필요
        - mov al, [edi]     ;레지스터이므로 크기가 명확(1바이트)
        - mov [edi], 0x10   ;크기가 명확하지 않아 오류 발생
        - mov byte [edi], 0x10  ;1바이트를 복사

![register indirect addressing](../image/register_indirect_addressing.jpg)
    - mov eax, [ebx] 설명하는 그림

#### Register Relative Addressing

- 유효 주소 계산: seg_base + base + constant
- ebp, ebx, edi, esi와 관련하여 기본 세그먼트 규칙 적용
- 주소 상수는 모두 32비트 부호 있는 값

##### Base + Displacement

- 베이스 레지스터 + 주소 상수
- 요소의 크기가 2바이트, 4바이트, 8바이트가 아닌 경우 배열 인덱싱에 적합
- 주소 상수는 배열의 시작점을 나타냄
- 베이스 레지스터는 배열의 특정 요소에 대한 변위를 결정하기 위한 계산 결과 보유
- 레코드의 필드에 접근 시 베이스 레지스터는 레코드의 시작 주소 보유, 주소 상수는 필드에 대한 정적 변위
- 엑티베이션 레코드(activation record)의 매개변수에 대한 접근(기본 레지스터는 ebp)

##### (Index * Scale) + Dispacement

- (인덱스 레지스터 * 상수) + 주소 상수
- 요소의 크기가 2바아트, 4바이트, 8바이트인 경우 정적 배열 인덱싱에 적합

#### Base + Index Addressing

- 유효 주소 계산: seg_base + base + index
- 베이스 레지스터: 배열의 시작 위치
    - 스택의 경우, ebp, esp
    - 데이터의 경우, eax, ebx 등 나머지 레지스터
- 인덱스 레지스터: 오프셋 위치
    - 주로 사용되는 것은 edi, esi
    - esp 제외 32비트 레지스터 가능
- 동적 배열의 요소들에 접근하기 위해 자주 사용
    - 동적 배열: 프로그램 실행 중에 기본 주소가 변경될 수 있는 배열

- mov ecx, [ebx+edi]    ;데이터 세그먼트 복사
- mov ch, [ebp+esi]     ;스택 세그먼트 복사
- mov dl, [eax+ebx]     ;eax가 베이스 레지스터, ebx가 인덱스 레지스터

#### Base + Index + Displacement Addressing

- 유효 주소 계산: seg_base + base + index + constant
- 2차원 배열 접근 시 사용
- 주소 상수는 배열 시작 주소 유지
- 레코드 배열의 여러 인스턴스 중 하나(주소 상수는 레코드 내의 필드에 대한 오프셋)

- mov dh, [ebx+edi+20H]     ;데이터 세그먼트 복사
- mov ax, [FILE+ebx+edi]    ;주소 상수가 FILE(순서가 바뀌어도 됨)
- mov [LIST+ebp+esi+4], dh  ;스택 세그먼트 복사
- mov eax, [FILE+ebx+ecx+2] ;32비트 전송

#### Scaled Index Addressing

- 유효 주소 계산: seg_base + base + constant * index
- 배열 요소의 크기가 2바이트, 4바이트, 8바이트인 경우 2차원 배열 인덱싱에 적합

- mov eax, [ebx+4*ecx]      ;베이스 레지스터는 ebx, 인덱스 레지스터는 ecx, 데이터 세그먼트 더블워드 복사
- mov [eax+2*edi-100H], cx
- mov eax, [ARRAY+4*ecx]

### Summary

|IA-32 SW Developer 매뉴얼|강의 노트 정리|적용|
|:---|:---|:---|
|displacement|Direct <br/>Displacement|정적으로 할당된 단일 데이터에 접근|
|base|Register indirect|변수 및 데이터 구조의 동적 저장에 사용|
|Base+displacement|Register relative|-요소 크기가 2,4,8바이트가 아닌 경우 배열로 인덱싱(displacement: 정적 오프셋을 배열의 시작으로 인코딩, base: 배열 내의 특정 요소로 오프셋을 결정하기 위한 계산 결과 보유) <br/>- 레코드의 필드에 접근(base: 레코드 시작 부분의 주소 유지, displacement: 필드에 대한 정적 오프셋) <br/>- 특수한 경우: 액티베이션 레코드의 매개변수에 대한 접근(기본 레지스터 EBP)|
|(Index*scale)+displacement|Register relative|요소 크기가 2,4,8바이트인 경우 정적 배열로 인덱싱|
|Base+Index+Displacement|Base relative plus index|- 2차원 배열(displacement: 배열 시작 주소 유지) <br/>- 레코드 배열의 여러 인스턴스 중 하나(displacement: 레코드 내의 필드에 대한 오프셋)|
|Base+Index+Displacement|Base plus index|동적 배열|
|Base+(Index*sclae)+Displacement|Scaled index|배열 요소의 크기가 2,4,8바이트인 경우 2차원 배열 인덱싱|

## Chapter 9

### Purpose of Stack

- 스택은 메모리의 한 부분
    - 하위 프로그램(함수) 호출에서 반환 주소를 저장하기 위해
    - 하위 프로그램(C 함수 호출 포함)에 매개 변수를 전달하기 위해
    - 하위 프로그램의 지역 변수 공간을 할당하기 위해
    - 하위 프로그램 호출 간에 레지스터 값을 저장하기 위해

- 리눅스에선
    - ESP는 프로그램이 시작될 때 OS에서 이미 설정됨
    - ESP에 임의의 값을 저장하면 기존 스택 중단
    - ESP: 스택의 탑을 가리키는 포인터

### Push and Pop

- ESP 레지스터
    - 스택 포인터
    - 스택의 탑을 가리킴
- **PUSH** 명령
    - PUSH EAX
        - ESP의 값을 감소시키고, ESP가 가리키고 있는 주소에 EAX의 값을 복사하는 것과 같은 동작
    - PUSHA
        [7장 참조](#stack-manipulation)
- **POP** 명령
    - POP EBX
        - ESP가 가리키고 있는 주소에 있는 값을 EBX에 복사하고, ESP의 값을 증가시키는 것과 같은 동작
    - POPA
        [7장 참조](#stack-manipulation)

- push와 pop의 동작은 대칭적으로 반대
- 스택은 메모리 주소가 감소하는 방향으로 쌓인다

### CALL and RET

- **CALL**
    - 스택에 다음 명령의 주소를 push하고 특정 주소로 분기
    - 다음 명령의 주소 = 복귀 주소
    - 함수 호출 시 사용
    - call ftn(함수 이름)
- **RET**
    - call에서 저장한 복귀 주소를 pop하고 그 주소로 분기
    - 피연산자 없음

- RET 명령에 의해 올바른 숫자가 pop되도록 스택을 올바르게 관리하는 것이 매우 중요

### Calling Convention

- 함수 호출 규칙

- Call and Return
    - Call 명령과 함께 하위 프로그램이 호출되고, RET를 통해 반환됨

- Parameter passing
    - 호출자(caller)가 매개변수를 push
    - 스택의 매개변수는 하위 프로그램별로 EBP를 이용해 접근
    - 호출자에 의해 매개변수 제거

- Local variables
    - 지역 변수가 스택에 할당됨
    - 지역 변수도 EBP를 사용하여 접근

- Return value
    - 반환값은 EAX 레지스터를 통해 전달
    - 복귀 주소를 eax에 담는다 -> 호출자는 복귀 직후 eax에 담긴 값을 ret값으로 간주

#### Parameter Passing

- 하위 프로그램에 대한 매개변수들은 스택 상에서 저장될 수 있다
    - 매개변수는 호출자가 호출에 나타나는 순서의 역순으로 push
    - 스택의 매개변수는 하위 프로그램에 의해 pop되지 않으며, 스택 자체에서 접근된다
    - 스택 상의 매개변수는 베이스 레지스터가 EBP(ESP가 아님)인 간접 주소 지정을 사용하여 [EBP+8]과 같이 접근된다
    - 매개변수는 RET 명령 후에(호출자에 의해서) 제거된다
        - 다양한 수의 인수를 지원하기 위해
        - ADD 또는 POP 명령

![accessing parameters with EBP, ESP](../image/why_ebp_not_esp.jpg)   

- ESP 사용 시
    - 스택에 값이 추가될 때마다 ESP 값도 바뀌기 때문에 매개변수나 복귀 주소에 접근하기가 어려워짐
- EBP 사용 시
    - 모든 함수 실행 시 **push ebp**, **mov ebp, esp** 명령 실행
    - 항상 첫번째 매개변수는 EBP+8에 저장됨
    - 항상 복귀 주소는 EBP+4에 저장됨
    - EBP의 값을 push하면 그 값을 ESP가 가리키고 있는데 그것을 EBP에 복사하면 EBP값이 저장된 곳을 EBP가 가리키게 만들 수 있음

![general caller and callee form - parameter passing](../image/general_caller_callee_form.jpg)
![stack image](../image/parameter_passing_stack.jpg)

#### Local Variables on the Stack

- 스택은 지역 변수의 위치를 편리하게 사용 가능
    - 스택은 C 프로그램이 일반(자동) 변수를 저장하는 위치
    - 하위 프로그램에 재진입하기 위해
    - 지역 변수는 ESP에서 필요한 바이트 수를 감소하여 EBP가 저장된 주소 바로 뒤에 저장됨
    - 베이스 레지스터 EBP를 사용한 간접 주소 지정은 지역 변수에 접근하는데 사용됨

![general caller and callee form - local variables](../image/general_caller_callee_form_2.jpg)
![stack image](../image/local_variables_stack.jpg)

- 항상 첫번째 지역 변수는 EBP-4에 저장됨

#### ENTER and LEAVE instruction

- **ENTER**
    - 피연산자 2개(지역 변수가 차지할 공간, 0)
    ```
    push ebp
    mov ebp, esp
    sub esp, Local_bytes
    ```
    위와 같은 결과

- **LEAVE**
    - 피연산자 없음
    ```
    mov esp, ebp
    pop ebp
    ```
    위와 같은 결과

#### Nested Call Frames

![nested call frame](../image/nested_call_frame.jpg)

#### Subprogram Calls in Assembly Program

- Caller(Before Call)
    - 인자를 push(마지막에서 첫번째 순서 = 역순)
    - 함수 호출

- Callee
    - 호출자의 EBP를 저장하고 호출자의 스택 프레임(또는 ENTER 명령) 설정
    - 지역 변수에 대한 공간 할당
    - 필요에 따라 레지스터 저장(또는 PUSHA 명령)
    - 작업 수행
    - EAX에 반환값 저장
    - 레지스터 복원(또는 POPA 명령)
    - 호출자의 스택 프레임 복원(또는 LEAVE 명령)
    - 반환

- Caller(After Return)
    - 인자를 pop
    - EAX에서 반환값 가져오기

### Multi-module Programs

- 멀티 모듈 프로그램: 두 개 이상의 오브젝트 파일로 구성된 프로그램
- 모듈 A가 B에 정의된 라벨을 사용하려면 **extern** 지시어 사용해야 함
- 레이블은 기본적으로 외부에서 접근 불가, 레이블이 다른 모듈에서 접근해야할 경우 **global** 지시어를 통해 해당 모듈에서 전역으로 선언되어야 함

### Interfacing Assembly with C

- 어셈블리 루틴은 C와 함께 사용 가능
    - C에서 접근하기 어렵거나 불가능한 하드웨어 기능에 대한 직접적인 접근이 필요할 때
    - 성능에 민감해서 빠른 수행이 필요할 때
    - 일부 함수를 어셈블리 코드로 작성 가능
    - C 함수에서 어셈블리 함수 호출 가능(반대의 경우도 가능)
- C 호출 규칙이 이미 지정되어 있음

#### Calling Assembly from C Function

- 레지스터 저장 (Saving registers)
    - C는 함수가 다음 레지스터의 값을 유지한다고 가정한다
        - EBX, ESI, EDI, EBP, CS, DS, SS, ES
    - EBX, ESI, EDI 값은 C가 레지스터 변수로 사용하기 때문에 보존해야 한다

- 함수의 레이블 (Label of function)
    - 대부분의 C 컴파일러는 함수와 전역/정적 변수의 이름 앞에 하나의 밑줄 문자('_')를 붙인다

- 매개변수 전달 (Passing parameters)
    - 함수의 인수는 함수 호출에 나타나는 역순으로 스택에 push된다

- 반환하는 값 (Returning values)
    - 모든 유형(char, int, enum, ...)이 EAX 레지스터에 반환된다
    - 32비트보다 작으면 EAX에 저장할 때 32비트로 확장된다
    - 64비트 값은 EDX:EAX 쌍에서 반환된다

- 다른 호출 규약
    - cdecl을 사용하지만 stdcall을 사용하는 경우도 있음
    - gcc에서 void f ( int ) \_\_attribute\_\_ ((cdecl))

### Command Line Arguments

![command line arguments](../image/command_line_arguments.jpg)

## Chapter 10

### Machine language

- 프로세서가 보는 언어
- 어셈블리어가 기계 코드를 지정
- Assemble(어셈블)
    - 어셈블리 코드를 기계 코드로 변환하는 과정
- Assembler(어셈블러)
    - 어셈블리어를 입력으로 받고 기계어를 출력하는 프로그램

#### Assembling simple program

![base form](../image/assembling_simple1.jpg)

- SSS: 소스 피연산자의 레지스터 코드
- DDD: 목적지 피연산자의 레지스터 코드
- 4 More의 밑줄: 4바이트가 더 사용된다

![example](../image/assembling_simple2.jpg)

- MOV EDX, 0
    - MOV reg, imm 형태
    - 10111010 00 00 00 00
        - 010: EDX 레지스터 코드
        - 0의 32비트 표현: 00 00 00 00
        - 1011: 11 = B
        - 1010: 10 = A
    - BA 00 00 00 00 5바이트

- JZ GCD
    - JZ imm 형태
    - 0F 84 _____
        - GCD의 주소: 24
        - 분기 명령의 다음 주소: 13
        - _____: 분기 명령과 레이블의 상대적 위치 차이 = 24 - 13 = 11
    - 0F 84 00 00 00 11 6바이트
        - 리틀 엔디안으로 저장
        - 0F 84 11 00 00 00

- JMP ORD
    - JMP imm 형태
    - E9 ____
        - ORD의 주소: B
        - 분기 명령의 다음 주소: 24
        - ____: B - 24 = -19 = E7
    - E9 FF FF FF E7 5바이트
        - 리틀 엔디안으로 저장
        - E9 E7 FF FF FF

### General Machine Instruction Format

![general machine instruction format](../image/general_machine_instruction_format.jpg)

- Prefix Byte(s) (0 ~ 4)
    - 옵코드 바이트에 옵션 추가

- Opcode Byte(s) (1 ~ 2)
    - 특정한 명령이 무엇인지 확인하는 값

- ModRM Operand Specifier (0 ~ 2)
    - 피연산자 명시

- Address Displacement (0 ~ 4)
    - 주소 상수

- Immediate Constant (0 ~ 4)
    - 상수

#### Opcode space

- 심볼이나 피연산자 정보 모두 포함
- 피연산자를 위한 문자키
    - 타입
        - **r** 레지스터
        - **m** 메모리
        - **i** 상수
    - 크기
        - **b** 바이트
        - **2** 2바이트
        - **v** 32비트 또는 16비트
        - **e** E인 경우 32비트, 16비트인 경우 표시 안함

![overview of the entire set of x86 machine code](../image/x86_machine_code.jpg)

- 예
    - 옵코드 바이트 03: ADD rv, rmv
        - rv: 첫번째 피연산자가 16비트 또는 32비트인 레지스터
        - rmv: 두번째 피연산자가 16비트 또는 32비트인 레지스터 또는 메모리 피연산자

##### The type of information conveyed by the first byte

- 첫번째 바이트가 전달하는 정보 유형

1. 명령어를 완전히 지정하는데 1바이트면 충분한 경우
    - F4 -> HLT

2. 첫번째 바이트는 어떤 연산을 수행할 것인지 결정하지만 피연산자는 명시하지 않음
    - 두번째(와 세번째) 바이트는 종종 피연산자 정보(ModRM 바이트)를 전달
    - 89 -> MOV rmv, rv

3. 첫번째 바이트는 단지 일반적인 유형의 연산을 지정하고, ModRM 바이트는 연산을 구체화하고 연산자 정보를 가져오는데 사용
    - C1 -> Shift rmv, ib
    - [Nonregister R bits](#nonregister-r-bits)에 대한 포인터

4. 386 space에 대한 포인터
    - 0F

5. 첫번째 바이트가 D8 ~ DF 범위에 있으면, 명령어는 부동 소수점 명령어
    - 부동 소수점 명령에 대한 정보 필요

6. 후속 명령어를 수정하는 접두사 바이트
    - F0 -> LOCK

#### The ModRM byte

- 구성
    ![consist of three parts](../image/modrm_consist.jpg)
    - 7비트와 6비트는 모드 비트
        - 모드 비트가 11일 때, R/M 비트는 레지스터 저장
        - 그렇지 않으면 R/M 비트는 메모리 코딩에 사용
    - 5, 4, 3비트는 레지스터 비트
        - 종종 슬래시 표기 /r을 사용하여 지정됨
    - 2, 1, 0비트는 R/M 비트
        - Mod 비트가 11인 경우를 제외하고 메모리 위치를 지정하거나 위치 특정을 돕기 위해 사용

##### rv, rmv coding

- ADD EDI, EAX
    - 두 개의 모드 비트는 11이어야 한다
        - R/M 비트에 레지스터를 저장해야 하기 때문
    - EDI의 경우 R비트가 111
    - EAX의 경우 R/M비트가 000
    - 전체 코드는 11 111 000 = 1111 1000 = F8(16진수)
    - 옵코드 03과 조합하면 03 F8

- Mod bits usage
    - 11
        - ADD EDI, EAX
        - ADD reg, reg
    - 00
        - ADD EDI, [EAX]
        - 메모리 피연산자가 base 레지스터로만 구성
    - 01
        - ADD EDI, [EAX+5]
            - base 레지스터와 8비트 immediate displacement
    - 10
        - ADD EDI, [EAX+87654321H]
            - base 레지스터와 32비트 immediate displacement

##### One Byte Address Modes - One Byte ModRM

- **Base reg + Displacement**
    - 0 0 _ _ _ R/M
        - R/M != 100b, R/M != 101b
        - R/M: [base]
    - 0 0 _ _ _ 1 0 1 + 32비트 displacement
        - 101: [displacement]
    - 0 1 _ _ _ R/M + 8비트 displacement
        - R/M != 100b
        - R/M: [base+displacement]
    - 1 0 _ _ _ R/M + 32비트 displacement
        - R/M: [base+displacement]
    
- 예
- mod = 00, ADD EAX, [EDX]
    - opcode 00 000 010
- mod = 01, SUB EDI, [EDI+127]
    - opcode 01 111 111 01111111
- mod = 10, ADD ESI, [EDI+12345678h]
    - opcode 10 110 111 01111000 01010110 00110100 00010010
- mod = 00, R/M = 101, MOV ESI, [12345678h]
    - opcode 00 110 101 01111000 01010110 00110100 00010010
- mod = 01, R/M = 101, MOV ESI, [EBP]
    - opcode 01 110 101 00000000
    - ebp를 단독으로 사용하고 싶을 때

##### Two Byte Address Modes - Two Byte ModRM

- **Base reg + Index reg * scale factor + displacement**
    - 0 0 _ _ _ 1 0 0 + scale index base
        - base != 101b
        - base, scale*index
    - 0 0 _ _ _ 1 0 0 + scale index 1 0 1  + 32비트 displacement
        - displacement, scale*index
    - 0 1 _ _ _ 1 0 0 + scale index base  + 8비트 displacement
        - base, scale*index, displacement(8비트)
    - 1 0 _ _ _ 1 0 0 + sclae index base + 32비트 displacement
        - base, scale*index, displacement(32비트)
    
    - s
        - 00, 01, 10, 11만 가능

- 예
- MOV EAX, [EBX+ESI*2]
    - opcode 00 000 100 + 01 110 011
- MOV EAX, [999999+EDI+EAX*4]
    - opcode 10 000 100 + 10 000 111 + 32비트 displacement
- MOV EAX, [TABLE+ESI*4]
    - opcode 00 000 100 + 10 110 101 + 32비트 displacement
- MOV EDI, [ESP+24]
    - opcode 01 111 100 + 00 100 100 + 00011000

##### rmv, rv coding

- MOV EDI, EAX
    - 8B 사용 시 -> 8B F8
        - mov rv, rmv
    - 89 사용 시 -> 89 C7
        - mov rmv, rv
        - EDI가 최하위비트에 들어간다
        - EAX는 R비트로 코딩된다

#### Nonregister R bits

- 첫번째 바이트는 연산을 지정하기에는 부족하지만 ModRM의 R비트를 이용해서 구체화한다

- SUB ECX, 32
    - 83 -> Immed rmv, ib
    - Immed는 SUB를 가지고 있다 /r = /5 = 101
    - Mod = 11
    - M = 001 (ECX)
    - 32 = 20h
    - 83 (11 101 001) 20 = 83 E9 20

![nonregister r bits](../image/nonregister_r_bits.jpg)

#### 386 space

- 0F뒤에 나타남
- 때때로 하나의 엔트리는 정확히 하나의 명령어를 지정
    - 0F CA -> BSWAP EDX
- 연산자 정보를 전달하기 위해서는 ModRM 바이트가 필요
    - XADD 명령어의 처음 2바이트는 0F C1
- 연산을 지정하기 위해 ModRM 바이트가 사용되기도 함
    - ModRM의 R비트를 확인해야 함
- MMX 명령어들

![386 space](../image/386space1.jpg)
![386 space r bits](../image/386space2.jpg)

#### 32-bits vs 16-bit code

- MOV ECX, EAX
    - 32비트: 89 C1
    - 16비트: 66 89 C1
- MOV CX, AX
    - 32비트: 66 89 C1
    - 16비트: 89 C1

- 8비트 레지스터 코드
    - AL 000
    - AH 100
    - CL 001
    - CH 101
    - DL 010
    - DH 110
    - BL 011
    - BH 111
