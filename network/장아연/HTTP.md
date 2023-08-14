## HTTP란?
### 정의
1. Hypertext Transfer Protocol
2. 서버와 클라이언트 사이에 TCP/IP 통신 위에서 메세지를 교환하기 위한 프로토콜

### 특징

1. server / client 모델
* client : 리소스 요청 - request 메세지 전송
* server : 리소스 요청을 받아 해당 리소스 제공 - response 메세지 전송
2. stateless
* 과거 정보 저장하지 않음
* 새로운 request에 대해 새로운 response 제공
* 상태 유지하지 않아 용이한 확장
3. connectionless
* 요청을 주고 받을 때만 연결을 유지함 
### 상태 유지가 필요한 경우
1. 세션과 쿠키 이용
2. Request URI로 리소스 식별
* request url에 포함
* 헤더의 host 필드에 네트워크 로케이션 포함
* 자신에게 송신하는 경우 option 와일드카드 지정

## HTTP 메세지

### 정의

### 요청 메세지

1. 요청 라인
* 요청 메서드
* 경로
* HTTP 버전

2. 요청 헤더 / 공통 헤더 / 엔티티 헤더

3. 빈줄
4. 분몬

### 응답 메세지

1. 응답 라인
* HTTP 버전
* 상태 코드
* 상태 메세지

2. 응답 헤더 / 공통 헤더 / 엔티티 헤더

3. 빈줄
4. 본문

## HTTP 헤더
### 정의
### TCP 헤더 vs HTTP 헤더
### HTTP 헤더
1. 공통 헤더
* Date
* Connection
* Cache-Control
* Content-Encoding

2. 요청 헤더
* Host
* User-Agent
* Accept
* Authorization
* Origin
* Referer

3. 응답 헤더
* Access-Control-Allow-Origin
* Allow
* Content-Disposition
* Location
* Content-Security-Policy
* Server

4. 엔티티 헤더
* Content-Length
* Content-Type
* Content-Language
* Content-Encoding


### 요청 헤더 예시 (일부)
```
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/102.0.5005.141
Accept-Encoding: gzip, deflate, br
Accept-Language: ko-KR,ko;q=0.9,en-US;q=0.8,en;q=0.7
cache-control: max-age=0
```

### 응답 헤더 예시 (일부)
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

## HTTP 요청 Method

### GET 
* 리소스 단순 조회
* 데이터를 Query String에 담아 URL에 노출됨
* `안정성` : 서버의 상태 변경되지 않음
* `멱등성` : 여러번 요청 시 서버 상태 동일

### POST
* 리소스 생성/변경
* 데이터를 HTTP 메세지 body에 담음
* `안정성 X` : 서버의 상태 변경됨
* `멱등성 X` : 여러번 요청 시 서버 상태 계속 바뀜

### PUT
* 리소스 전체 수정 (없다면 새로 생성)
* `안정성 X` : 서버 상태 변경됨
* `멱등성 O` : 여러번 요청 시 서버 상태 유지됨

### PATCH
* 리소스 일부 수정 
* `안정성 X` : 서버 상태 변경됨
* `멱등성 ... ` : 멱등성 있을 수도 없을 수도...

### DELETE

### HEAD

### OPTIONS


## 보안
### HTTP 한계
1. 암호화하지 않은 통신 - 도청 가능성 존재
2. 낮은 신뢰성 - 통신 상대 확인 X
### HTTP 보안 문제
1. 중간자 공격 
* 네트워크 통신 도중에 중간자가 침입해 통신 내용을 도청/조작하는 공격 기법

2. 통신 상대 확인하지 않음
* 누가 요청을 보내도 응답해주는 구조
* 요청을 보내는 클라이언트에 대한 확신 없음
* 응답해주는 서버가 의도한 서버인지에 대한 확신 없음

3. HTTP의 암호화를 담당하는 SSL 도입
* 암호화 기반 인터넷 보안 프로토콜인 SSL(Secure Socket Layer) 도입
* 인터넷 통신의 개인정보 보호, 인증, 데이터 무결성을 위해 개발됨

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