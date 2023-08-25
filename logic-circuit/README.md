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

![샘플링과 양자화](image\sampling_quantizing.jpg)