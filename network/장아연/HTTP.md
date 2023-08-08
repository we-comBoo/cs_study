## HTTP란?
### 정의
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

## 보안
### HTTP 보안
### SSL/TLS
### 암호화 - 대칭키 기법 
### 암호화 - 공개키 기법
### SSL 동작 기법
