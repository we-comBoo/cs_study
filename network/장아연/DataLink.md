
## 네트워크 구성요소
* 프로토콜은 이미 네크워크 환경이 구축된 이후 통신에 관여
* 출발지에서 도착지까지 전기 신호를 전달하고 각 컴퓨터로 데이터를 전달하는 네트워크 그 자체를 만드는데 필요한 장치와 기술 

## Router 
**라우팅 테이블에 경로 정보 정리 + 최적의 경로로 데이터 전달**
1. 네트워크 중계자
* 데이터가 원하는 목적지로 원활하게 도착할 수 있도록 적절한 통신 경로 안내 장치
* 데이터가 가장 빠르게 도착할 수 있는 최적의 경로 찾아 안내

2. 라우팅 테이블
* 최족 목적지 IP 주소와 목적지에 도달하기 위해 경유해야 할 인근 라이터 정보 담긴 테이블
* 관리자가 직접 라우팅 테이블에 내용 추가
* 인근 라우터와 정보를 교환해 자동으로 경로 정보 갱신하는 방식

3. 라우팅 테이블 활용한 데이터 이동
    ```
    1. 데이터가 출발지에서 가장 가까운 라우터 도착
    
    2. 라우터는 데이터에 적힌 목적지 정보 확인
    라우팅 테이블 안에서 목적지로 라우터 경로 정보 유무 확인
    2-1. 정보 찾음 
    2-2. IP 주소를 보고 목적지와 유사한 주소 형태 가진 정보 찾음

    3. 그 장소로 가기 위해 거치는 라우터 정보 찾아 데이터 전달

    4. 반복하다가 목적지 도달
    ```
4. TTL (Time to Live)
* 데이터 유효기간을 나타내는 방법
* 데이터가 무한히 네트워크를 순환하는 상황 방지
* 0 ~ 255의 숫자 표기
* 데이터가 하나의 라우터 거칠 때마다 일정량 감소하며 0이 되면 목적지 도달 여부와 무관하게 데이터 폐기
## Ethernet이란?

### 특징
1. 같은 지역의 네트워크인 LAN을 유선으로 구현하는 방식
2. 적은 비용과 빠른 속도
3. 성능과 환경 따른 이더넷 규격 선택 가능
* 속도 
* 채널 종류
* 케이블 종류 
4. 주로 사용하는 구성요소
* 허브, 스위치 : 자신에게 연결된 컴퓨터가 전송하는 데이터를 담아 다른 컴퓨터에게 전송하는 중간 장치
* 케이블 : 유선으로 네트워크 연결
* 네트워크 인터페이스 카드 : 각 기기 구분하는 MAC 주소가 붙은 장치

### 네트워크 인터페이스 카드
1. 컴퓨터를 네트워크에 연결하기 위한 장치
2. 직렬화 수행

* 데이터->전기 신호 <br/>
* 전기 신호 -> 데이터 <br/>

### MAC 주소
1. 네트워크 인터페이스 카드는 MAC 주소 가짐
2. 고정적인 물리적 주소
* IP 주소는 논리적이며 바뀔 수 잇음
3. 역할
* 기기 내부에서 자신에게 온 데이터가 맞는지 판별
(헤더에 적힌 도착지 MAC 주소 확인)
* 스위치에서 MAC 주소 확인을 통해 자신에게 연결된 컴퓨터로 데이터 전달

### 허브

### 스위치

### 케이블

### CSMA/CD
1. 이더넷에서 각 단말이 데이터 공유 매체에 접근하는 방식
2. CSMA 
* 현재 전송 중인 신호 있는지 확인
3. CD
* 충동 감지하고 이를 해결하기 위한 대책
4. 동작 과정
    ```
    1. 데이터 보내기 전 네트워크 상 전송 중인 신호 존재 여부 감지
    2. 랜덤한 시간 동안 기다린 뒤 다시 신호 확인 후 전송
    3. 충돌 감지된 경우, 단말은 데이터 충돌 발생을 모든 컴퓨터에게 알리기 위해 신호 전송
    4. 일정 시간 동안 데이터 전송 중지
    5. 전송된 데이터가 없는 경우 자신의 데이터 전송
    5-1. 이 때 충돌 발생하면 이전에 기다린 시간의 2배 기다림
    ```
5. 스위치 등장으로 MAC 주소로 특정 포트로만 데이터 보내는 것이 대중화 되며 CSMA/CD 없이 네트워크 통신 가능

## DataLink 계층의 역할

### 특징
1. 데이터 -> 전기 신호 (캡슐화), 전기 신호 -> 데이터 (역캡슐화)
2. MAC 주소를 이용해 데이터를 **정확한 목적지**로 전달
3. 이더넷, 스위치, NIC

**Network 계층 : 데이터가 목적지까지 도달하기 위한 `최적의 경로` 제공**

### 안전한 데이터 도달을 위한 수단
1. 오류 검출
* 전송 중 오류/손실 발생 시 해결을 위한 제어 방식
* 후진 오류 수정 방식, 전진 오류 수정 방식
2. 흐름 제어 
* 송신 노드가 수신 노드의 처리 속도 고려해 초과하지 않도록 전송 제어
* 수신 노드가 송신 노드에게 수신 확인 응답 제공
* stop and wait 방식, sliding window 방식

---
## LAN이란

## Ethernet이란

## DataLink 계층이란?
