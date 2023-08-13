## HTTP란?
### 정의
1. Hypertext Transfer Protocol
2. 서로 다른 서버 사이에 통신을 주고 받게 하는 프로토콜

### 특징

1. server / client 모델
2. stateless
3. connectionless

## HTTP 메세지

### 정의

### 요청 메세지

1. 요청 라인
* 요청 메서드
* 경로
* HTTP 버전

2. 헤더
* Host
* User-agent
* Accept
* Accept-Language

3. 빈줄
4. 분몬

### 응답 메세지

1. 응답 라인
* HTTP 버전
* 상태 코드
* 상태 메세지

2. 헤더
* ㅜㅏㅣㅟㄴ아ㅜ

3. 빈줄
4. 본문

## HTTP 헤더
### 정의
### TCP 헤더 vs HTTP 헤더
### HTTP 헤더
1. 공통 헤더
* Date
* Cache-Control
2. 요청 헤더
* Host
* User-Agent
3. 응답 헤더
* Server
* Location
4. 엔티티 헤더
* Content-Length
* Content-Type


### 요청 헤더 예시 (일부)
```
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/102.0.5005.141
Accept-Encoding: gzip, deflate, br
Accept-Language: ko-KR,ko;q=0.9,en-US;q=0.8,en;q=0.7
cache-control: max-age=0
```

### 요청 헤더 예시 (일부)
```
server: gws
cache-control: private, max-age=0
content-encoding: br
content-length: 45148
content-type: txt/html; charset=UTF-8
```
## HTTP 상태 코드

1. 1XX
* 조건부 응답
* 웹서버가 요청 수신 후, 작업 진행 중 의미
* `100` : 서버가 첫번째 요청 받았으며, 추가 요청 기다리고 있음

2. 2XX
* 클라이언트 요청 작업을 서버가 성공적으로 처리함
* `200` : OK : 서버가 요청을 제대로 처리함
* `201` : Created : 요청에 의해 데이터 생성됨
* `204` : No Content : 성공적으로 처리했지만, 본문 빼고 전달해 통신 속도 줄임

3. 3XX
* 리다이렉션 완료 응답
* 요청을 완료하기 위해 재전송 필요
* 응답을 받은 클라이언트는 헤더를 확인하고 실제 주소로 이동하는 방식으로 동작
* `301` : Moved Permanently : 추가로 요청한 페이지로 영구 이동
* `302` : Found : 일시적으로 이동

4. 4XX
* 클라이언트 요청에 오류 있음
* `400` : Bad Request : 클라이언트 요청 내용에 문제 있음
* `401` : Unauthorized : 인증되지 않은 사용자
* `404` : Not Found : 요청에 문제 없으나 요청한 데이터 존재하지 않음

5. 5XX
* 서버가 요청 수행하지 못함
* `500` : Internal Server Error : 서버 내부적으로 오류가 발생해 응답에 실패
* `502` : Bad Gateway : 서버 간의 네트워크 문제 발생으로 인한 통신 제대로 되지 않음

## 보안
### HTTP 한계
* 서버에서 브라우저로 전송되는 정보가 암호화 되지 않음 
* 평문 데이터 전송으로 인해 쉽게 도난 당할 수 있음
### HTTP 보안 문제
1. 중간자 공격 
* 네트워크 통신 도중에 중간자가 침입해 통신 내용을 도청/조작하는 공격 기법

2. 통신 상대 확인하지 않음
* 어디에서 보낸 요청인지 파악 불가능
* 통신 중인 상태가 허가된 상대인지 파악 불가능

3. HTTP의 암호화를 담당하는 SSL 도입
* SSL(Secure Socket Layer)를 사용해 서버와 브라우저 사이에 암호화된 연결을 하고, 서버와 브라우저가 민감함 정보를 주고 받을 때 도난 당하는 것 방지

## HTTPS
### 정의
1. HyperText Transfer Protocol Secure
2. 정보를 암호화하는 SSL 프로토콜을 이용하여 클라이언트와 서버가 데이터를 주고 받는 통신 규약

### SSL/TLS
1. 데이터를 암호화해 통신하는 프로토콜

2. 하이브리드 암호화 방식
* 공개키 암호화 방식 : 통신에 사용할 대칭키 교환
* 대칭키 암호화 방식 : 통신 진행

### 암호화 - 대칭키 기법 
* 하나의 키로 암호화/복호화 모두 진행
* 서버와 클라이언트가 동일한 키 사용해 공유하는 문제 존재
* 대칭키 전달 과정에서 탈출할 경우, 암호화된 데이터 알아낼 수 있음

### 암호화 - 공개키 기법
* 공개키, 개인키로 암호화/복호화하는 방식
* 공개키로 암호화한 것은 개인키로 복호화하고, 개인키로 암호화한 것은 공개키로 복호화함
* 공개키 배포로 키 공유 문제 해결
* 처리 속도 느릴 수 있음

### SSL 동작 기법
**SSL 인증서 : 클라이언트와 서버 간의 통신을 제 3자가 보증하는 전자화된 문서, key를 가지고 있어야만 암호화/복호화 가능**
1. Client Hello
* 클라이언트가 서버에게 인사 <br/>
    **전달 내용**
    * 랜덤 데이터
    * 지원 가능한 암호화 방식 

2. Server Hello
* 서버가 클라이언트에게 인사 <br/>
    **전달 내용** 
    * 랜덤 데이터
    * 지원 가능한 암호화 방식  
    * CA 인증서  

3. 서버 인증서 확인 & 임시 대칭키 생성
* CA 발급 인증서 목록 중 서버가 전달한 인증서 있는 지 확인
* CA에서 공유하는 해당 서버의 공개키로 인증서 복호화
* 복호화 성공 =  해당 서버가 본인 개인키로 암화화 한 것이 맞음 = 해당 서버 신뢰 가능
4. 임시 대칭키 전달
* 실제 데이터 통신에 사용할 실제 임시 대칭키 생성
* 클라이언트와 서버가 주고 받은 랜덤 데이터로 임시 대칭키 생성
* 클라이언트가 서버의 공개키로 임시 대칭키 암호화하고 이를 서버에세 전송
5. 개인키로 대칭키 복호화
* 서버는 본인의 개인키로 대칭키 복호화
* 서버와 클라이언트가 동일한 대칭키 갖게 됨
6. 대칭키를 세션키로 변환
7. 세션키 이용한 대칭키 기법으로 데이터 암호화 통신
8. 데이터 전송 완료 후 세션 종료


### HTTPS의 이점
1. 보안 - SSL/TLS
2. SEO - 안전한 웹사이트 평가로 가산점 부여
3. AMP (Accelerate Mobile Pages) 구현

## 언제 사용하는가
* 노출되어도 단순한 정보 조회 OR 민감한 개인 정보 
* 인증서 발급 등 추가 비용 발생

---
## HTTP와 HTTPS 차이 & HTTP 보안
* HTTP 한계
* HTTPS 개념 (HTTP에 무엇이 더해졌는지)
* SSL 암호화 방식
* SSL 동작 기법


## HTTP의 GET과 POST 방식의 차리


## HTTP status code 종류
* 1XX : 정보가 수신되어 처리 중임
* 2XX : 클라이언트 요청을 성공적으로 처리함
* 3XX : 요청을 완료하기 위해 추가 조치 필요
* 4XX : 클라이언트 요청에 문재 있음
* 5XX : 서버 문제로 오류 발생 

----
[HTTP와 HTTPS - 널널한 개발자](https://mangkyu.tistory.com/98)

[HTTP와 HTTPS - 요즘 IT](https://yozm.wishket.com/magazine/detail/130/)