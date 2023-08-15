# Protocol Architecture

## Protocol

<details>
<summary>Protocol이란?</summary>

- 같은 레이어 간의 통신을 위한 규칙들의 집합
- Syntax(데이터의 포맷), Semantics(데이터의 의미나 데이터에 대해 취할 액션), Timing(데이터 처리 속도나 데이터를 주고 받는 순서) 등의 내용을 명시하고 있음

</details>

<details>
<summary>PDU란?</summary>

- Protocol Data Unit
- 계층에서 처리하는 데이터 단위

</details>

## Layered Structure

<details>
<summary>Layered structure란?</summary>

- 네트워크를 통한 통신 과정은 layered structure로 이루어짐
- 레이어란 전체 기능의 일부분을 수행하는 서브 모듈
- 통신이라는 하나의 태스크는 여러 서브 태스크로 쪼개져서 각각의 레이어가 이를 독립적으로 수행하는 구조

</details>

<details>
<summary>Layered architecture의 특징</summary>

- 각 레이어는 모두 독립적 → 한 레이어의 변경이 다른 레이어에게 영향을 주지 않음
- 레이어는 스택처럼 수직적인 구조
  - 아랫 계층은 윗 계층에게 서비스를 제공
  - 윗 계층은 아랫 계층에서 제공 받는 서비스에 의존
- 서비스란?
  - 서비스는 Primitive와 Parameter로 이루어짐
    - Primitive: 해당 계층에서 수행한 function (Request, Response, Confirm 등)
    - Parameter: 레이어가 주고 받는 data

</details>

<details>
<summary>계층화는 왜 하는 걸까?</summary>

- 복잡한 시스템을 잘 다루기 위해서
- 거대한 태스크를 모두 한번에 처리하는 것보다, 서브 태스크로 쪼개 각각의 독립적인 레이어에서 처리하는 경우, 각 단계별로, 통신이 일어나는 과정과 문제 발생 시 그 원인을 알아 보기 쉬움
- 그리고 각 레이어를 독립적으로 발전시킬 수 있음 
- 한 레이어를 변경해도 다른 레이어에 영향을 주지 않기 때문에 전체 시스템을 유지보수하기 좋음

</details>

## OSI 7 Layer Model

<details>
<summary>OSI model이란?</summary>

- 다양한 종류의 네트워크 장비들을 상호 운용적으로 연결하기 위해서 개발한 표준 네트워크 모델

</details>

<details>
<summary>Physical Layer의 역할과 대표적인 프로토콜은?</summary>

- 데이터 bit를 전기적인 signal로 변환해 전송하는 역할
  - 또는 반대로 signal을 bit로 변환해 윗 계층인 Data link layer에 전달
- 주요 기술과 프로토콜: signal encoding, multiplexing, 여러 종류의 통신 매체(twisted pair, coaxible cable, optical fiber)
- PDU: bit (physical layer header는 없음)

</details>

<details>
<summary>Data Link Layer의 역할과 대표적인 프로토콜은?</summary>

- MAC 주소를 이용해 하나의 네트워크 내에서 데이터를 전송하는 역할
- 신뢰성 있는 전송을 위해 error control, flow confrol 등을 수행
- 2계층의 통신 장비: 스위치(L2 switch)
- 주요 기술과 프로토콜: Ethernet(유선), WiFi(무선)
- PDU: frame (data link layer의 header와 trailer + payload)

</details>

<details>
<summary>Network Layer의 역할과 대표적인 프로토콜은?</summary>

- host-to-host 데이터 전송을 수행
  - 서로 다른 네트워크 간의 데이터 전송을 다룸
- 주요 기능은 routing과 forwarding
  - routing: 목적지까지의 최적 경로를 계산하는 일
  - forwarding: 패킷을 다음 노드로 전송하는 일
- 주요 기술과 프로토콜: IP, ICMP, BGP, ARP 등
- PDU: datagram 또는 packet

</details>

<details>
<summary>Transport Layer의 역할과 대표적인 프로토콜은?</summary>

- end-to-end 데이터 전송을 수행
  - Network layer와의 차이점
    - network layer는 호스트 간 데이터 전송을 수행
    - transport layer는 프로세스 간 데이터 전송을 수행
- 신뢰성 있는 전송을 위해 error control, flow control 등을 수행
  - Data link layer와의 차이점
    - data link layer의 error control, flow control은 hop 단위로 + packet 하나의 관점에서 수행
    - transport layer의 error control, flow control은 end-to-end 단위로 + 전체 메세지의 관점에서 수행
  - error control, flow control을 두 번 하는 이유(두 레이어의 태스크가 중복되는 이유)
    - 홉 단위로만 수행할 경우 end-to-end에서 신뢰성을 보장할 수 없음
    - ex: 한 라우터 내에서 비트가 바뀌는 에러가 나는 경우 2계층에서 확인하는 것만으로는 알아챌 수 없음
- 주요 기술과 프로토콜: TCP, UDP
- PDU: TCP segment, UDP datagram

</details>

<details>
<summary>Session Layer의 역할</summary>

- 애플리케이션 간 통신 세션을 관리하는 역할

</details>

<details>
<summary>Presentation Layer의 역할</summary>

- 애플리케이션 데이터의 형식 변환(ex: 문자 인코딩 변환), 암호화, 압축 등과 같은 데이터의 표현을 관리하는 역할

</details>

<details>
<summary>Application Layer의 역할과 대표적인 프로토콜은?</summary>

- 엔드 유저와 애플리케이션이 네트워크를 활용할 수 있도록 사용자 인터페이스나 데이터, 파일, 이메일 전송 등 다양한 네트워크 서비스를 제공하는 역할
- 주요 기술과 프로토콜: HTTP, FTP, SMTP, POP3, IMAP, DNS 등
- PDU: message

</details>

## TCP/IP Model

<details>
<summary>TCP/IP model이란?</summary>

- 인터넷 프로토콜 스택을 나타내는 네트워크 모델
- 5 계층으로 구성됨
  - physical layer: 데이터를 물리적인 전기 신호로 변환해 전송하는 역할
  - network access layer: 물리적인 네트워크 장비에 대한 인터페이스를 제공. 같은 네트워크 내의 데이터 전송을 담당
  - internet layer: 
  - transport layer: 
  - application layer:

</details>

## OSI vs. TCP/IP

[![OSI vs. TCP/IP Model](https://www.imperva.com/learn/wp-content/uploads/sites/13/2020/02/OSI-vs.-TCPIP-models.jpg)](https://www.imperva.com/learn/application-security/osi-model/)

<details>
<summary>OSI 모델과 TCP/IP 모델의 차이는?</summary>

- OSI 모델은 전체적인 통신 전반에 대한 표준이며, 7계층으로 이루어져 있음
- TCP/IP 모델은 데이터 전송에 특화된 모델이고, 5계층으로 이루어져 있어서 실무에 사용하기 더 적합함

</details>

<details>
<summary>인터넷에서 OSI 7 계층 모델 대신 TCP/IP 모델을 사용하는 이유는?</summary>

- OSI 모델은 전체적인 통신 전반에 대한 표준이며, 7계층으로 이루어져 있음
- 따라서 TCP/IP 모델보다 데이터 전송 속도가 조금 더 느림
- 현대에서 요구하는 고속 데이터 전송에 적합하지 않음
- OSI 모델은 이론적인 표준 모델로만 남게 되었고, 인터넷은 TCP/IP 모델을 기반으로 동작함

</details>

## 예상 질문

<details>
<summary>웹 서버는 몇 계층에서 동작하는가?</summary>

- 웹 서버는 HTTP를 사용해 클라이언트(웹 브라우저)로부터 요청을 받아들이고, 응답을 보내기 때문에 주로 Application layer에서 작동
- 그러나 실제 데이터 통신은 TCP/IP 프로토콜을 통해 동작하기 때문에 Transport layer, internet layer로 활용해 작동

</details>

<details>
<summary>웹 서버의 라우팅 기능은 몇 계층에서 동작하는가?</summary>

- 웹 서버는 Transport layer에서의 라우팅과 Application layer에서의 라우팅, 두 가지를 제공
- Transport layer에서의 라우팅은 전달 받은 요청을 특정 포트로 분산하는 로드 밸런싱 기능을 의미
- Application layer에서의 라우팅은 HTTP 요청을 URI에 따라 라우팅하는 것
  - 예를 들어 HTTP 요청이 어떤 서브 도메인에 들어왔는지에 따라 스태틱 파일을 응답하거나 API 서버로 연결하는 등의 라우팅을 수행할 수 있음

</details>

