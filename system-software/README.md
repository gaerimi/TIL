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
