OTA를 위한 Bootloader 설계
====================
## 개요
OTA를 위해 서스펜션 제어기의 Bootloader를 설계하는 Project

|이름|역할|수행 기간|
|---|---|---|
|김도엽|개인 프로젝트|2025.01 - 2025.02|

### 사용 Tool
- AurixStudio
- Trace32(Debugger)
- CAN Message Capture & Reprogramming SW
- 진단기 SW

### MCU
- TC234LP

<img width="619" height="483" alt="개요" src="https://github.com/user-attachments/assets/8ce1b44f-cebd-4727-8fe7-62d10ed9d7f9" />

## Architecture
<img width="829" height="504" alt="Architecture" src="https://github.com/user-attachments/assets/021e78de-06eb-42c0-87eb-774b1a28c66c" />

## 1. 리프로그래밍 Sequence

|<img width="883" height="727" alt="리프로그래밍 과정" src="https://github.com/user-attachments/assets/4891bb62-9182-4bb1-ac50-98cc5aa2770f" />|<img width="899" height="495" alt="실제 CAN Data 리프로그래밍 과정 (Intelligent CAN)" src="https://github.com/user-attachments/assets/45c29ca3-7de0-4846-a8a1-0d252a03cc0c" />|
|-----|-----|


## 2. 단일 물리적 Flash bank 문제

|문제 식별|해결 방법|
|---|---|
|<img width="500" height="289" alt="Trace32" src="https://github.com/user-attachments/assets/91029acf-26be-4de3-8a38-4d17e2e718f0" />|<img width="577" height="399" alt="HTL" src="https://github.com/user-attachments/assets/89de184c-9819-42d2-a51e-58386912e2b3" />|

- TC234LP의 경우 RWW 기능을 지원하지 않아 RAM으로 Erase/Program Code를 이동시켜야함

### 링커스크립트 변경
<img width="670" height="377" alt="linkerScript" src="https://github.com/user-attachments/assets/a6736060-c42e-4fd0-9187-23c04602366f" />


## 3. Binary 위변조 감지

### SHA 256 

- KISA 제공 알고리즘 소스코드
  - https://seed.kisa.or.kr/kisa/Board/21/detailView.do    

<img width="690" height="160" alt="암호화" src="https://github.com/user-attachments/assets/48ec0ee1-1e7b-4d17-8690-36b5ea9b6895" />

### 결과
<img width="1318" height="413" alt="SHA 256 결과" src="https://github.com/user-attachments/assets/11fa7780-66b9-40c6-a52e-ddf086e32290" />

