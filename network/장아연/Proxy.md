## Proxy 서버
### 정의
클라이언트와 서버간의 중계 서버로, 통신을 대리 수행하는 서버

### 종류
![](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*xvcdLFcqCTH-GBD6VsnBfg.png)
* Forward Proxy
* Reverse Proxy

## Forward Proxy

### 캐싱
클라이언트가 요청한 내용을 캐싱

**장점**
1. 전송 시간 절약
2. 불필요한 외부 전송 X
3. 외부 요청 감소에 따른 네트워크 병목 현상 방지


### 익명성
클라이언트가 보낸 요청을 감춤
**장점**
Server가 응답 받은 요청을 누가 보냈는지 알지 못하게 함
(Server가 받은 요청 IP = Proxy IP)

## Reverse Proxy

### 캐싱
클라이언트가 요청한 내용을 캐싱
 (forward proxy 내용과 동일)

### 보안
서버 정보를 클라이언트로부터 숨김
**장점**
Client는 Reverse Proxy를 실제 서버라고 생각하여 요청 (실제 서버의 IP가 노출되지 않음)

### Load Balancing
해야할 작업을 나눠 서버의 부하를 분산함

**Load Balancer**
* 여러 대의 서버가 분산 처리할 수 있도록 요청을 나눠주는 서비스
* OSI 7 Layer 기준으로 무엇을 따라 나누는지가 달라짐

`L4 기준`
* Transport layer의 IP와 Port 레벨에서 로드 밸런싱
* 어떤 사이트(www.xxx.com)로 접근 시, 서버 A와 서버 B로 나눠줌

`L7 기준` 
* Application layer의 User Request Level에서 나눠줌
(HTTPS/HTTP/FTP)
* 어떤 사이트(www.xxx.com)로 접근 시, /category와 /search를 담당 서버로 나눠줌
