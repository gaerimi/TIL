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
    - $f_s >= 2f_m$
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
- 불 방정식(Boolean Algebra)에서 곱셈과 같음
![AND GATE](../image/and_gate.jpg)
- **입력이 모두 1일 경우 출력이 1**

### OR

- X OR Y = X+Y
- 불 방정식에서 덧셈과 같음
![OR GATE](../image/or_gate.jpg)
- **입력 중 하나라도 1일 경우 출력이 1**
