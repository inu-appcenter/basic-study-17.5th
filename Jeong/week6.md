APP Center_Study_Week 6
---
# 네트워크
--- 
## 네트워크란?
컴퓨터나 기타 기기들이 리소스(자원)를 공유하거나 데이터를 주고 받기 위해 유선 혹은 무선으로 연결된 통신체계

### 네트워크가 제공하는 기능
- 애플리케이션 목적에 맞는 통신 방법
- 신뢰할 수 있는 데이터 전송 방법
- 네트워크 간 최적의 통신 경로
- 목적지로 데이터 전송
- 노드 사이의 데이터 전송

### 네트워크 프로토콜
네트워크 통신의 표준 (형식, 절차, 규약 등)

### 인터넷 프로토콜 슈트 (Internet Protocol Suite)
인터넷에서 컴퓨터들이 정보를 주고받는 데 사용되는 프로토콜의 집합
주로 TCP/IP 4계층 모델이나 OSI 7계층 모델로 설명

---
## 네트워크 계층 구조
### 네트워크 계층구조를 나누는 이유
1. 통신이 일어나는 과정에서 데이터의 흐름을 한눈에 파악 가능
2. 통신 과정 중 문제 발생 시 다른 단계의 장비 및 소프트웨어를 건드리지 않고, 통신 장애를 일으킨 단계에서 해결
3. 각 계층이 다른 계층으로부터 영향을 받지 않도록 설계하여 독립적으로 발전시킬 수 있게 하기 위함. - 다양한 유형의 프로토콜에 적응할 수 있는 유연성 제공

---
# OSI 7 계층 모델
![](https://velog.velcdn.com/images/dlwjd8023/post/71d49a5a-3147-4f6c-aa28-f9bd194e3863/image.png)

## 특징
- 각 레이어에 맞게 프로토콜을 세분화하여 구현
- 각 레이어의 프로토콜은 하위 레이어의 프로토콜이 제공하는 기능을 사용하여 동작

---
## 계층구조
---
### 7계층 - 애플리케이션 계층 (Application)
- 사용자들이 사용하는 애플리케이션 목적에 맞는 통신 방법을 제공
- 사용자 - 응용 프로그램 - 네트워크 서비스 간 인터페이스 제공

### 애플리케이션 계층의 대표적인 프로토콜
- FTP: 파일 전송 프로토콜
- SMTP: 이메일 전송 프로토콜
- **HTTP**: 웹 서버 접속 프로토콜
- DNS: 인터넷 주소 변환 프로토콜
  - 도메인 이름 www.naver.com -> IP 주소 192.168.1.0

---
### 6계층 - 프레젠테이션 계층 (Presentation)
- 애플리케이션 간 통신에서 데이터 표현의 차이를 해결
- 송신측에서는 수신자가 이해할 수 있는 형태로 데이터를 인코딩
- 수신측에서는 수신받은 데이터를 응용 계층에 맞는 형태로 변환

#### 기능
- 그래픽 정보를 JPEG 형태로 변환
- 동영상을 MOEG 형태로 변환
- 데이터의 효율적인 전송을 위한 데이터 압축
- 데이터 보안을 위한 데이터 암호화 및 복호화

#### 표현 계층의 대표적인 프로토콜
- JPEG: 그래픽 변환 프로토콜
- MOEG: 동영상 변환 프로토콜

---
### 5계층 - 세션 계층 (Session)
- 애플리케이션 간 통신에서 세션을 관리

#### 기능 
- 포트를 기반으로 애플리케이션 간 통신 연결
- 네트워크 장치간 통신 방식 결정
- 세견 연결 및 해제
- 전송 중단 시 동기화 기능 제공 (데이터 복구)

#### 세션 계층의 대표적인 프로토콜
- SSH: 네트워크 보안 프로토콜 (서버 로그인 및 명령 과정에서의 보안)
- TLS: 네트워크 보안 프로토콜 (애플리케이션 간 통신 암호화)

---
### 4계층 - 전송 계층 (Transport)
- 데이터 전송을 담당

#### 기능
- 포트번호를 기반으로 데이터를 송수신
- 데이터 전송의 흐름제어
- 데이터 전송의 오류제어

#### 전송 계층의 대표적인 프로토콜
- **TCP**: 연결 지향 데이터 전송 프로토콜
- UDP: 비연결 지향 데이터 전송 프로토콜

#### 연결 지향과 비연결 지향의 차이
- 데이터 전송의 신뢰성 확보를 위해, 연결 설정 과정을 추가
- 연결 지향: 신뢰성 향상, 속도 저하
- 비연결 지향: 신뢰성 감소, 속도 상승

---
### 3계층 - 네트워크 계층 (Network)
- 실제 네트워크 간 라우팅을 담당

#### 기능
- IP 주소 등을 통해 데이터를 목적지까지 전송
- 라우터를 통해 경로를 선택하여 패킷 전달

#### 특징
- 데이터 전송의 신뢰성을 보장하지 않음 (전송 계층에서 보완)

#### 라우팅이란?
- IP 주소를 기반으로 통신 데이터를 보낼 최적의 경로를 선택하는 과정
- 라우터라는 기계가 담당

#### 패킷이란?
- 네트워크 통신에서 데이터의 기본 단위
- 헤더(패킷 송수신 위치)와 페이로드(데이터 내용)로 구성
- 데이터를 분할하여 전송, 수신 시 재조립

#### 네트워크 계층의 대표적인 프로토콜
- **IP(Internet Protocol)**: 인터넷에 연결된 기기를 식별하는 논리적 주소
- ARP(Address Resolusion Protocol): IP 주소와 MAC 주소(물리 주소)간 연결을 주관하는 프로토콜

---
### 2계층 - 데이터링크 계층 (Data Link)
장비의 고유 주소인 MAC주소를 이용하여 노드간 데이터를 전송

#### 기능
- IP 주소를 통해 MAC 주소를 탐색(ARP)
- MAC 주소를 통해 IP 주소를 탐색(RARP)
- **이더넷 프레임**을 통해 에러확인, 흐름제어, 접근제어 등의 기능 수행

#### 이더넷이란?
컴퓨터와 기기들이 유선으로 연결되어 데이터를 주고받을 수 있도록 하는 로컬 네트워크(LAN) 기술 규격

#### 이더넷 프레임이란?
- 이더넷 네트워크 데이터 통신의 기본 단위
- 헤더(송신자와 수신자의 MAC 주소 등)와 페이로드(실제 전송 데이터), 트레일러(데이터의 오류 검출)로 구성

#### 노드란?
네트워크에 연결된 모든 개별 장치나 연결 지점

---
### 1계층 - 물리 계층 (Physical)
- 하드웨어와 같은 물리적 매체를 통해 데이터를 bit 단위로 전송한다.

#### 기능
- 데이터 링크 계층으로부터 프레임을 받아 0과 1로 이루어진 전기적 신호로 데이터를 변환함
- 변환한 데이터를 구리나 광섬유, 무선 통신 매체를 통해 전송함

---
# TCP/IP 5계층 모델
![](https://velog.velcdn.com/images/dlwjd8023/post/aededa37-5eca-4021-b302-d6cf405020b5/image.png)

특징
- OSI 7계층 구조는 장비 개발과 네트워크 통신의 표준화를 위해 설계된 개념적인 성향에 모델인 데 비해, TCP/IP 스택은 실제 인터넷 통신 시 기반이 되는 모델임
- 총 5개(혹은 4개)의 계층으로 구성됨

---
## 계층구조
---

### 5계층 - 애플리케이션 계층
OSI 7계층에서, 애플리케이션 계층, 표현 계층, 세션 계층에 해당됨

### 4계층 - 전송 계층
OSI 7계층에서, 전송 계층에 해당됨 (TCP 전송 계층)

### 3계층 - 인터넷 계층
OSI 7계층에서, 네트워크 계층에 해당됨(IP를 통한 패킷 전송)

### 2계층 - 링크 계층(네트워크 접근 계층)
OSI 7계층에서, 데이터 링크 계층에 해당됨

### 1계층 - 물리 계층(네트워크 접근 계층)
OSI 7계층에서, 물리 계층에 해당됨

---
# HTTP
---
## HTTP란?
서버/클라이언트 모델을 따라 데이터를 주고 받기 위한 프로토콜
인터넷에서 하이퍼텍스트를 교환하기 위한 통신 규약 (80번/8080번 포트)

### 포트
서버의 논리적인 접속장소
인터넷 프로토콜인 TCP/IP를 사용할 때, 클라이언트 프로그램이 네트워크 상의 특정 서버 프로그램을 지정하는 수단
하나의 컴퓨터에서 여러 개의 서버가 실행되는데, 어느 서버에 접속해야 하는지 알려주는 수단

### 포트번호
해당 컴퓨터에서 실행되고 있는 서버를 구분짓기 위한 포트의 16비트 논리적 할당

#### 특징
- 0 ~ 65536번 포트가 존재
- 16비트 중 10비트(0 ~ 1023번)까지는 어떤 포트를 사용할지 정해져 있음(well-known port)
- http 통신은 80번 포트임
- 웹 서버를 하나만 쓸 때에는 포트번호 80만을 사용
- 웹 서버를 2개 이상 사용할 경우에는 추가된 서버의 포트번호에 8080을 사용

### TCP/IP

#### - IP
  - 패킷 통신 방식의 인터넷 프로토콜
  - 패킷 전달 여부를 보증하지 않고, 패킷을 보낸 순서와 받는 순서가 다를 수 있음

#### - TCP
  - 전송 조절 프로토콜
  - IP 위에서 동작 (같이 쓰임)
  - 데이터의 전달을 보증하고 보낸 순서대로 받음
---
# HTTPS란?
HTTP에 데이터 암호화가 추가된 프로토콜

### 다른 이름들
- HyperText Transfer Protocol over Secure Socket Layer
- HTTP over TLS
- HTTP over SSL
- HTTP Secure
- etc

### 특징
- 포트번호가 80/8080번인 HTTP와 다르게, 443번 포트를 사용

### 대칭키 암호화와 비대칭키 암호화

#### 대칭키 암호화
- 클라이언트와 서버가 동일한 키를 사용해 암호화/복호화를 진행
- 키가 노출되면 보안 위험
- 연산 속도가 빠름

#### 비대칭키 암호화
- 한 개의 쌍으로 구성된 공개키(대칭키)와 개인키를 암호화/복호화를 진행
- 키가 노출되어도 비교적 안전
- 연산 속도가 느림

### 작동 방식
![](https://velog.velcdn.com/images/dlwjd8023/post/4e56c3d4-25fb-4f3a-8441-8dee36572b31/image.png)
공개키 암호화: 공개키로 암호화하면, 개인키로만 복호화 가능 -> 해당 개인키를 소유한 클라이언트만 확인

개인키 암호화: 개인키로 암호화하면, 공개키로만 복호화 가능 -> 공개키는 모두에게 공개되어 있으므로 내가 인증인 정보임을 알려 신뢰성 보장

---
# HTTP 구조와 작동원리
---
## 웹 주소의 구성

![](https://velog.velcdn.com/images/dlwjd8023/post/7c34871b-dea7-4427-a240-c7ecd7cc75f7/image.png)

- URI - 자원의 식별자
- URL - 위치(Location)
- URN - 이름(Name)

### URI(Uniform Resource Identifier)
웹 서버에서의 리소스 식별자
식별 방식으로 URL과 URN이 존재하나, 
일반적으로 URL을 사용

### URL(Uniform Resource Locator)
![](https://velog.velcdn.com/images/dlwjd8023/post/724461cf-bfac-458f-b763-e68fcfdbd201/image.png)
특정 서버의 한 리소스에 대한 구체적인 위치를 서술

### Base URL
웹 개발에서 상대적인 URL 경로를 위한 기본 기준이 되는 URL
- 예시
  - http://example.com을 base url로 설정했을 경우, 
  /images/pic.jpg의 상대 경로(Endpoint) -> http://example.com/images/pic/jpg

### Endpoint
웹 애플리케이션에서 클라이언트가 서버에 요청을 보내는 특정 URL 경로
- 모든 API의 엔드포인트는 base URL의 상대경로
- 클라이언트는 특정 엔드포인트에 요청을 보낸 뒤(서버에 요청을 보냄) 응답을 받음

### 쿼리 파라미터
- query: 문의, 물음표
- query parameter: URL 뒤에 물음표(?)와 함께 붙는 키-값(Key-Value)쌍
  - 기능
    - 웹 서버 요청에 대한 추가 정보 제공
    - 서버가 추가 데이터를 통해 추가 액션을 취할 수도 있음

- 용도
  - API 요청: API 엔드포인트의 결과 조회 / 필터링
  - 검색: 검색 쿼리를 서버에 전달 -> 결과 필터링

- 예시
![](https://velog.velcdn.com/images/dlwjd8023/post/1ce651cc-73eb-4536-bf2e-6df6fedc1533/image.png)
URL 상에 "?"와 "&"을 사용해서 구분, =을 기준으로 key=value 형식으로 구성

---
# HTTP 요청 구조
---
## 구성 요소
![업로드중..](blob:https://velog.io/31cabfbb-78c0-45eb-a004-9e978f886e69)

![](https://velog.velcdn.com/images/dlwjd8023/post/8f10e409-c4a9-4e75-8cac-f291bad7adf7/image.png)
### 1. startline
  - http method: 해당 request가 의도한 action을 정의하는 부분 (POST)
GET, POST, PUT, DELETE, OPTIONS 등 존재 
  - request target: 해당 request가 전송되는 목표 uri(/test.html)
  - http version: 사용하는 http의 버전 (HTTP/1.1)
### 2. headers
  - request에 대한 추가 정보를 담음
  - key: value로 구성
  - 자주 사용되는 header 정보
    - Host: 요청하려는 서버의 호스트 이름과 포트 번호
    - User-agent: 요청을 보내는 클라이언트에 대한 정보 (웹 브라우저 정보 등)
    - Referer: 바로 직전에 머물렀던 웹 링크 주소
    - Accept: 해당 요청이 받을 수 있는 응답의 타입
    - Accept-encoding: 클라이언트가 지원하는 압축 인코딩의 종류
    - Connection: 해당 요청이 끝난 후에 네크워크의 유지 여부를 표시
    - Content-Type: 해당 요청이 보내는 메시지 body의 타입
    - Content-Length: 메시지 body의 길이
### 3. CRLF(개행)
- header와 body의 구분선. 공백 줄로 표시
### 4. body
  - 해당 request의 실제 메시지/내용
  - 전송하는 데이터가 없다면, body 부분은 공백
  - post 요청의 경우, HTML 폼 데이터가 포함
---
# HTTP 응답 구조
---
## 구성 요소

![](https://velog.velcdn.com/images/dlwjd8023/post/71ab742f-626f-4963-b9d0-0aac4d99d18c/image.png)

1. Status line
- HTTP 버젼 (HTTP/1.1)
- 상태 코드 (200)
- 상태 텍스트 (OK)
2. Headers
- 기본적으로 리퀘스트와 동일
- Server 등의 response 전용 헤더 값들이 존재
3. Status text
- 리퀘스트와 동일

http는 TCP 통신을 사용한다 (인터넷, 유튜브 안끊김)
라이브 스트리밍은 UDP 통신 사용

---
# HTTP Status Code
---
## HTTP status code
HTTP request가 성공적으로 완료되었는지 여부를 나타냄
### 1. 100 ~ 199 Informational
- 임시응답으로 클라이언트의 요청은 처리되었으니 계속 진행하라는 의미
### 2. 200 ~ 299 성공
- 클라이언트의 요청이 성공적으로 처리됨
### 3. 300 ~ 399 리디렉션
- 완전한 처리를 위해 추가 동작이 필요한 경우
- 서버의 주소 혹은 요청한 URI의 웹 문서가 이동됨
### 4. 400 ~ 499 클라이언트 오류
- 클라이언트의 요청 메시지 내용이 잘못된 경우
### 5. 500 ~ 599 서버 오류
- 서버 사정으로 메시지 처리에 문제가 발생함.
- 주로 서버의 부하, DB 처리 과정 오류, 서버에서 익셉션이 발생하는 경우를 의미

참고: https://hongong.hanbit.co.kr/http-%EC%83%81%ED%83%9C-%EC%BD%94%EB%93%9C-%ED%91%9C-1xx-5xx-%EC%A0%84%EC%B2%B4-%EC%9A%94%EC%95%BD-%EC%A0%95%EB%A6%AC/

---
# HTTP 메소드
---
## 주요 메소드의 종류
1. GET: 리소스 조회
2. POST: 요청 데이터 처리 (등록)
3. PUT: 리소스 대체, 부재 시 생성
4. PATCH: 리소스 부분 변경
5. DELETE: 리소스 삭제

## 1. GET

### 기능
- 리소스를 조회 
- 만일 해당 서버에 전달하고 싶은 데이터가 존재한다면, 쿼리스트링을 통해 전달
- 메시지 바디를 사용해 데이터를 전달 가능, but 지원하지 않는 서버가 많음
  - ex> get/members/100**?username=Jeong&height=181**
- post 요청과 달리 캐싱이 가능 => 리소스를 빠르게 가져오는 데 특화

### 종류
1. 정적 데이터 조회 
2. 동적 데이터 조회
3. HTML Form 데이터 조회

---
### 1. 정적 데이터 조회(쿼리 스트링 X)

1-1. 서버의 /members/100 경로에 get 요청 전송
![](https://velog.velcdn.com/images/dlwjd8023/post/f0bed37b-2c06-4fcb-86ba-0634567a8f44/image.png)

1-2. 서버는 해당 경로 탐색 후,
![](https://velog.velcdn.com/images/dlwjd8023/post/dd015355-36fc-4485-8d48-1f9023b53f33/image.png)

1-3. 해당 객체를 HTTP Status 200 OK(정상)과 함께 반환
![](https://velog.velcdn.com/images/dlwjd8023/post/033a660f-0976-4ae6-a088-5cb046f2d19c/image.png)

---
### 2. 동적 데이터 조회(쿼리 스트링 O)

2-1. 요청 URL 뒤에 ?q=hello&hl=ko 쿼리 파라미터를 줘서 상세한 조회 데이터를 얻음
![](https://velog.velcdn.com/images/dlwjd8023/post/d550bb90-6507-4a56-9c95-9932ad56282d/image.png)

---
### 3. HTML Form 데이터 조회

3-1. HTML 문서에 존재하는 form에 항목을 기입한 뒤 제출 (submit)
![](https://velog.velcdn.com/images/dlwjd8023/post/5ffe3e34-8ae6-473d-8bba-51157949a7b4/image.png)

3-2. 클라이언트가 항목을 제출하면, GET 메서드 동작에 따라 input 태그 안의 값들이 쿼리스트링 형태로 변환되어 서버로 전달
![](https://velog.velcdn.com/images/dlwjd8023/post/205f5f6f-a9e8-4450-9193-d8275796e2a5/image.png)

---
## 2. POST

### 기능
- 서버에 데이터를 전달하여 처리하거나, 서버가 데이터를 생성하도록 요청
- 메시지 바디를 통해 서버에 요청 데이터를 전달하면, 서버는 요청 데이터를 처리하여 업데이트
- 서버는 전달된 데이터를 통해 신규 리소스를 등록하거나 프로세스를 처리

### 1. JSON 데이터 전송 과정

1-1. 클라이언트가 request body에 회원 정보 JSON 파일을 만들어 서버에 전송
![](https://velog.velcdn.com/images/dlwjd8023/post/cf0e8aa0-aa1d-4ef7-8e6d-692cacf9edf1/image.png)

1-2. 클라이언트로부터의 데이터를 분석, 처리 (아이디 생성)
![](https://velog.velcdn.com/images/dlwjd8023/post/039a4aa2-cdf5-42c4-86f0-737f7c60a9c1/image.png)

1-3. 신규 데이터에 대한 정보를 바디에 담아 클라이언트에 응답
![](https://velog.velcdn.com/images/dlwjd8023/post/3ac52d9c-6e0b-41f6-9187-f8e9b25870f4/image.png)

### 2. HTML Form 데이터 전송 과정

2-1. 웹 문서에 input에 데이터를 기입한 뒤 전송(submit)
![](https://velog.velcdn.com/images/dlwjd8023/post/af422107-282a-4703-a567-e397426d11b7/image.png)

2-2. 지정한 post 메서드 동작에 따라, Input 태그 안의 값들이 쿼리스트링으로 서버에 전송, 서버는 이를 처리
![](https://velog.velcdn.com/images/dlwjd8023/post/79f135cd-bb6d-4b60-a36e-62ca462be6e9/image.png)

### Content-Type의 종류
1. Content-Type: application/x-www-form-urlencoded
  - form의 내용을 http 메시지 바디를 통해서 전송 (쿼리 파라미터 형식)
  - 전송 데이터를 url encoding
2. Content-Type: multipart/form-data
  - 파일 업로드와 같은 바이너리 데이터 전송 시 사용
  - 다른 종류의 여러 파일과 form의 내용을 함께 전송 가능(multipart)
3. Content-Type: application/json
  - TEXT, **XML**, **JSON** 데이터 전송 시 사용

get은 쿼리 파라미터를 통해 정보 전달 -> 보안 수준 낮음
post는 페이로드를 통해 정보 전달 -> 보안 수준이 상대적으로 높음

## 3. PUT
리소스를 대체 (수정), 해당 리소스가 없으면 새로 생성

### 1. PUT 요청에 리소스가 있는 경우
1-1. /members/100의 리소스를 교체하겠다는 요청을 서버에 전달
![](https://velog.velcdn.com/images/dlwjd8023/post/17935271-9a77-4be1-bf6b-4969759f92a8/image.png)
1-2. 기존에 데이터가 있었을 경우, 완전히 대체
![](https://velog.velcdn.com/images/dlwjd8023/post/73531ebb-02a1-4249-8c22-9a1f7594635a/image.png)

### 2. PUT 요청에 리소스가 없는 경우
2-1. /members/100의 리소스를 교체하겠다는 요청을 서버에 전달
![](https://velog.velcdn.com/images/dlwjd8023/post/3421e164-ff50-4a2a-98e1-854ae0bee36e/image.png)
2-2. 기존에 데이터가 없었을 경우, 신규로 생성
![](https://velog.velcdn.com/images/dlwjd8023/post/64a6840b-a052-47d0-b592-c67858046bd3/image.png)

### 3. PUT 요청에 일부 리소스만 변경하길 원하는 경우
3-1. /member/100의 리소스에서 age의 value만을 교체하겠다는 요청을 서버에 전달
![](https://velog.velcdn.com/images/dlwjd8023/post/9cab5672-6989-459d-9e94-643ea04eeb10/image.png)
3-2. 기존 데이터를 완전히 대체하여, name 데이터 삭제 (이럴 때는 patch 메소드를 사용)
![](https://velog.velcdn.com/images/dlwjd8023/post/59e2236f-9ccc-4ac5-8758-16d3ba623c47/image.png)

## 4. PATCH
리소스 부분 변경 (put은 일반적으로 전체를 변경, patch는 부분을 변경)

4-1. /members/100의 리소스에서 age의 value 만을 patch하겠다는 요청을 서버에 전달
![](https://velog.velcdn.com/images/dlwjd8023/post/69a595d1-a28d-41a9-a6c5-54099e5c1890/image.png)

4-2. PUT과는 다르게 회원 정보에서 age만 변경됨
![](https://velog.velcdn.com/images/dlwjd8023/post/8d239fd2-597c-456c-b2c3-1dd60b89fffa/image.png)

## 5. DELETE
리소스를 제거하는 메소드

5-1. /members/100의 리소스를 delete하겠다는 요청을 서버에 전달
![](https://velog.velcdn.com/images/dlwjd8023/post/bb6c59b8-0ab3-404f-9cd5-bb4cd6697f42/image.png)

5-2. 서버에서 데이터베이스 내의 해당 리소스를 제거
![](https://velog.velcdn.com/images/dlwjd8023/post/656224ad-960c-4975-80ab-c1ef80662e76/image.png)

---
# API
---
## API란?
![](https://velog.velcdn.com/images/dlwjd8023/post/aafc9ea3-f0c1-40a8-af51-1978035a6513/image.png)
- **API**(Application Programming Interface)
운영체제와 응용 프로그램 사이의 통신에 사용되는 언어나 메시지 형식
- 주로 레스토랑 비유가 많이 사용되는데, 클라이언트는 점원, 요리사는 서버, 종업원은 API에 비유된다.
- 웹 API는 클라이언트와 서버 사이에서 양쪽을 연결해주는 역할을 한다.


## API의 역할과 필요성

### API의 주요 역할
1. 서버와 데이터베이스의 보안 관리
API는 허용된 사용자에게만 특정 키값을 부여하고 데이터에 접근할 수 있도록 권한을 부여

2. 모든 접속을 표준화
API는 각기 다른 기기나 운영체제에서 접근해도 동일한 결과를 얻을 수 있도록 접속을 표준화

3. CRUD 처리에 따른 앱 간소화(자동화)
- API를 통한 CRUD 처리에 따라 관련 데이터와 콘텐츠가 자동으로 생성(대신 처리)
- 사용자의 환경에 맞춰 정보가 전달됨에 따라 개발 워크플로우가 간소화됨

### CRUD란?
- Create(생성), Read(조회), Update(갱신), Deleted(삭제)의 준말
- HTTP request 메소드 형식에 따른 개념
  - C: Create | POST
  - R: Read | GET
  - U: Update | PUT or PATCH
  - D: Delete | DELETE

## API의 종류 (간단하게)
| 구분             | 데이터 포맷            | 설계 철학  | 장점       | 단점       | 대표 사례        |
| -------------- | ----------------- | ------ | -------- | -------- | ------------ |
| **SOAP**       | XML               | 프로토콜   | 보안/계약 명확 | 복잡함      | 금융, 정부       |
| **RPC / gRPC** | Binary (Protobuf) | 함수 호출  | 빠름, 효율적  | 유연성 ↓    | 마이크로서비스      |
| **REST**       | JSON              | 리소스 기반 | 단순, 표준   | 오버/언더 페칭 | 일반 웹 API     |
| **GraphQL**    | JSON (쿼리형)        | 데이터 질의 | 클라 주도    | 서버 복잡    | 대형 프론트엔드 서비스 |


- API는 분류 기준에 따라 여러 가지 형식으로 분류 가능.
- 대표적인 분류 방식
  - 접근 방식에 따른 유형
  - 아키텍처 스타일에 따른 유형

### 1. 접근 방식에 따른 유형
  - private API: 내부 API
    - 기업이나 연구 단체 등에서 자체 제품과 운영 개선을 위해 단체 내부에서만 사용
  - Public API: 개방형 API
    - 모두에게 공개되는 API, Public API 중에서도 접속하는 대상에 대한 제약이 업는 경우를 OpenAPI라고 함
  - Partner API: 파트너를 위한 API
    - 특정 비즈니스 파트너 간의 데이터 공유를 위한 API

### 2. 아키텍처 스타일에 따른 유형
  - SOAP(Simple Object Access Protocol)
    - XML 기반의 무겁지만 엄격한 프로토콜형 API
    - 특징
      - 매우 엄격한 규격
      - HTTP뿐만 아니라 SMTP 등 다양한 프로토콜에서도 작동 가능
    - 장점: 엔터프라이즈급 안정성, 형식화된 계약(Contract-first)
    - 단점: XML 처리 부담, 복잡도 ↑, 속도 ↓
    - 예시: 은행, 보험, 정부 시스템

  - RPC(Remote Procedure Call)
    - 클라이언트가 함수를 요청하면, 서버가 결과를 리턴함
    - 전송 포맷: gRPC (Protocol Buffers 기반)
    - 특징
      - 호출 단위가 “리소스”가 아닌 “함수”
      - 장점: 속도 빠름, 바이너리 포맷 지원, 서비스 간 통신 (microservices) 에 적합
    - 예시: gRPC 기반 ML inference server, 분산 시스템 내부 통신

  - **REST(Representational State Transfer) API**
	- 리소스 중심의 URL 설계 + HTTP 규격 자체를 설계 원칙으로 삼음
    - 형식
      - GET(조회)
      - POST(생성)
      - PUT(PATCH)(갱신)
      - DELETE(삭제)
    - 특징
      - HTTP 규칙 자체를 설계 원칙으로 삼음
      - Stateless (무상태) 통신
      - JSON, XML 등 다양한 포맷 가능
      - 장점: 단순, 표준화, 캐싱 쉬움
      - 단점: 과다/과소 요청 문제
      - 예시: 웹 서비스, 모바일 API, 오픈 API

  - GraphQL
    - 필요한 데이터를 지정해서 가져오는 데이터 질의형(query) 설계 
    - 특징
      - 단일 엔드포인트 (/graphql)
      - Over-fetching / Under-fetching 해결
      - 강력한 타입 시스템(schema) 내장
    - 장점: 클라이언트 주도, 효율적 데이터 전송
    - 단점: 캐싱 복잡, 서버 구현 부담 (resolver 구조)
    - 예시: Facebook, GitHub API v4, Shopify
---
# REST API
---
## REST
REST(Representational State Transfer)
- **정의적 개념**: 자원을 이름으로 구분하여 해당 자원의 상태를 주고받는 것
- **기술적 개념**: HTTP URI를 통해 리소스를 명시하고 HTTP Method를 통해 CRUD를 적용하는 것

## REST의 특징
1. Server-Client(서버-클라이언트 구조)
2. Stateless(무상태)
3. Cacheable(캐시 처리 가능)
4. Layered System(계층화)
5. Uniform Interface(인터페이스 일관성)
6. clear(명료성)

## 구성 요소
REST는 크게 1. 자원, 2. 자원에 대한 행위, 3. 자원에 대한 행위의 내용을 표현하는 것으로 구성됨

1. 자원: HTTP URI (BaseURL + EndPoint)
2. 자원에 대한 행위: HTTP Method (GET, POST, etc)
3. 자원에 대한 행위의 내용: HTTP Message Pay Load (2XX, 3XX, etc)

## RESTful 설계 규칙
### restful API(REST API)
- 웹 표준을 기반으로 하는 API 설계 원칙
- TTP URI를 통해 리소스를 명시하고 HTTP Method를 통해 CRUD를 적용
- HTTP 메소드와 URI를 조합하여 리소스에 대한 다양한 작업을 명확하게 표현

> 예시: 사용자 정보를 관리하는 웹 서비스에서의 **CRUD**
GET /users - 사용자 목록 조회
POST /users - 새로운 사용자 생성
PUT /users/{id} - 사용자 정보 수정
DELETE /users/{id} - 사용자 삭제

## REST API의 장단점
### 장점 
- HTTP 프로토콜의 인프라를 그대로 사용하므로 REST API 사용을 위한 별도의 인프라를 구축할 필요가 없음
- HTTP 표준 프로토콜에 따르는 모든 플랫폼에서 사용이 가능
- REST API 메시지가 의도하는 바를 명확하게 나타내므로 의도하는 바를 쉽게 파악 가능
- 서버와 클라이언트의 역할을 명확하게 분리
 

### 단점 
- 표준이 없음
- HTTP Method 형태가 제한적임 (CRUD)
- 구형 브라우저(Internet Explorer)에서 아직 제대로 지원해주지 못하는 부분(PUT, DELETE)이 존재함


---
# 데이터 포맷
---
## XML
### XML(EXtensible Markup Language)
- html형식과 같이 태그를 통해 데이터를 표현하는 방식의 **마크업 언어**

### 마크업 언어란?
- 태그('<>')를 사용하여 문서의 구조와 표현을 설명하는 언어


### 기본 구조와 태그 사용 방식

#### XML 코드의 예시
![](https://velog.velcdn.com/images/dlwjd8023/post/49696a3b-80c2-4a73-a3d6-6b767eabb9fe/image.png)

- 계층적 트리 구조를 가짐 (idols-idol)
- 전반적으로 HTML과 유사한 구조를 가지며, 크게 헤더와 바디로 구성됨.
  - 헤더: xml의 버전 정보, 인코딩 방식 기재
  - 바디: 태그를 통한 데이터 본문 기재

### 특징
- 태그를 사용자가 직접 정의할 수 있음
- 텍스트 기반의 마크업 언어로 구성되어 인간과 기계 모두가 다루기 쉬움
- 여러 인코딩 방식을 지원함

---
## JSON
### JSON(JavaScript Object Notation)
자바스크립트 객체 표기법으로 데이터를 전달할 때 사용하는 표준

### 기본 구조와 표현 방식
![](https://velog.velcdn.com/images/dlwjd8023/post/bb81320a-42fc-4e9d-aab7-ef3633ea8eab/image.png)

- key: value 형식으로 구성, 중괄호({})로 둘러쌓아 표현
- 데이터는 쉼표(,)를 통해 나열

### 특징
- 자바스크립트뿐만 아니라 C, C++, Java, python 등 다른 프로그래밍 언어에서도 많이 사용됨
- 타입을 가지고 있어, 따입에 따른 표현 방식이 다름
- UTF-8 인코딩만을 지원

---
## XML vs JSON
### 차이점
#### 1. 표현 형식
- xml: 트리 패턴으로 데이터를 나타냄
- JSON: 키: 밸류 페어를 사용함

#### 2. 구문
- 일반적으로 JSON 파일이 더욱 간결 (태그의 포함 여부)
- XML 파일은 특정 문자를 엔터티 참조로 대체 ('<' 대신 &lt;를 사용)

#### 3. 구문 분석
- XML: 구문 분석기를 사용해서 분석 => 프로세스 속도 저하
- JSON: 표준 JavaScript 함수로 분석 가능 + 더 가벼운 파일이라 간결함

#### 4. 데이터 유형 지원
- XML: 사용자 정의 태그를 통해 다양한 유형의 데이터를 정의하고 표현할 수 있음
- JSON: 문자열, 숫자, 객체, 부울 배열 등의 한정된 범위의 데이터 유형만을 지원

#### 5. 보안
- XML: DTD(Document Type Definitoin)을 활용한 엔티티 수정을 통한 공격에 취약함
- JSON: 일반적으로 XML보다 안전한 것으로 간주되지만, 악성 페이로드 삽입으로 인한 보안 취약점 존재

### REST API에서 주로 사용되는 데이터 포맷

최신 REST API에서는 주로 **JSON**을 사용, 그러나 여전히 XML 포맷도 사용이 되고 있음

### 사용 근거
- 파일 크기가 작음(태그 포함 x)
- 구조가 단순함 (key: value 페어)
- 보안이 XML보다 비교적 안전함


---
# 웹 환경에서의 API 요청
---
## 브라우저에서 API 요청이 이루어지는 과정
![](https://velog.velcdn.com/images/dlwjd8023/post/ca9324d0-d566-474a-9056-5a2d3f191165/image.png)

1. 클라이언트가 인터넷 네트워크 상의URI(BaseURL+Endpoint)를 통해 API 요청(HTTP Method)을 보냄
2. API는 제공받은 URI를 통해 해당 웹 서버에 요청을 전달하고, 서버는 해당 요청에 따라 데이터베이스로부터 자원을 파싱해 전달
3. API는 서버로부터 제공받은 리소스와 처리 결과에 따른 상태 정보를 클라이언트에게 전달
## fetch / async-await

### fetch 
![](https://velog.velcdn.com/images/dlwjd8023/post/b9acd78c-3a87-4da1-925a-07264d088bed/image.png)

- 개념: JavaScript에서, 네트워크를 통해 자원을 요청하고 응답을 받는 역할을 하는 web API
- 역할: 서버에서 데이터를 가져올 때 사용
- 기능
  - 특정 URL로 HTTP 요청을 보냄 (기본적으로 GET 방식)
  - fetch 함수를 호출하면 즉시 결과를 반환하지 않고, 비동기적으로 동작하며, Promise 객체를 반환
- 사용법
  1. fetch('url')을 호출하면, Response 객체를 resolve하는 promise 반환
  2. response 객체에서 실제 데이터를 추출하기 위해 .json()이나 .text() 등의 메서드를 사용

### async/await
![](https://velog.velcdn.com/images/dlwjd8023/post/4e8d78ba-6061-4934-8f5b-18c9c246920a/image.png)

- 개념: promise 기반의 비동기 코드를 보다 동기적인 코드처럼 읽기 쉽고 간결하게 작성할 수 있도록 해주는 JavaScript 문법

### async
- 함수 앞에 붙여서 해당 함수가 항상 promise를 반환하도록 선언
- 함수 내에서 await키워드를 사용할 수 있게 해줌
- async가 붙은 함수 밖의 구문의 경우는 여전히 비동기로 실행

### await
- promise 앞에 붙여서 promise가 이행될 때까지 기다림
- await는 async함수 내부에서만 사용 가능
- await는 promise의 결과를 반환하고, 기다리는 동안 함수 밖의 코드는 계속 실행



## CORS
### CORS(Cross-Origin Resource Sharing)
교차 출처 리소스 공유 정책으로, 서로 다른 출처 간의 리소스 공유를 허용하도록 하는 정책

### 출처(Origin)란?
![](https://velog.velcdn.com/images/dlwjd8023/post/7312ef07-c4b1-43a8-b25a-4cd180d8b5cf/image.png)
URL에서, 프로토콜과 호스트, 포트 번호까지를 포함

### 등장 배경
1. 이전 웹 사이트들은 프론트엔드와 백엔드의 구분없이 통합해서 서비스를 구현하는 경우가 많아, 대부분의 리소스 관리를 동일한 사이트에서 관리했으며, 다른 출처와의 통신을 정책적으로 금지하고, 의심스럽게 여김(SOP) (보안적인 이유)
2. 기술이 발전되어 백엔드와 프론트엔드가 구별됨에 따라, 다른 출처로부터 리소스를 가져올 일이 많아졌고 이 과정에서 서로 다른 출처 간의 리소스 공류를 허용시킬 정책이 필요해졌음 -> CORS의 탄생

### 동일 출처 정책(Same-Origin Policy, SOP)
- 동일한 출처에 대한 정책
- 내부적으로 동일한 출처에서만 리소스를 공유할 수 있다는 법률을 가지고 있음.
- Promise 기반의 then()의 경우, SOP 정책을 따름
- 별도의 HTTP 응답 헤더의 변경 없이, SOP 정책을 따르는 요청을 다른 출처로부터 수행하려고 할 경우 CORS 에러가 발생


### 브라우저에서의 CORS 기본 동작
1. 클라이언트(브라우저)에서 HTTP 요청의 헤더에 Origin을 담아 전달
![](https://velog.velcdn.com/images/dlwjd8023/post/7953a856-ecda-43c2-abee-2ab16d665709/image.png)

2. 서버는 응답헤더에 Access-Control-Allow-Origin을 담아 클라이언트로 전달
![](https://velog.velcdn.com/images/dlwjd8023/post/a3b6db2d-7ef0-423a-ac8e-b47b7ec8c65c/image.png)

3. 클라이언트에서 출처 서버가 보내준 Access-Control-Allow-Origin을 비교
  - 출처와 Access-Cotrol-Allow-Origin이 일치한다면,  리소스 전달
  - 출처와 Access-Cotrol-Allow-Origin이 일치하지 않는다면, CORS 에러 발생
  
### CORS 오류 발생 시 해결방법
1. 백엔드 측에서 HTTP 응답 헤더의 Access-Control-Allow-Origin에 클라이언트의 출처를 명시, (와일드카드 사용 시, 쿠키발급 X)
2. 모든 출처를 허용한 프록시 서버를 경유하여 리소스를 전달

---
## POSTMAN을 이용한 News API 요청
---
![](https://velog.velcdn.com/images/dlwjd8023/post/ca0175f0-9077-4d29-bb80-fb2ce02e4c20/image.png)