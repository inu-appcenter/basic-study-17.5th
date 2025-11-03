# week6 내용 발표 자료

### 1. HTTP

- **HTTP**
    
    : **웹에서 클라이언트와 서버가 데이터를 주고받을 때 사용하는 프로토콜**
    
    - 특징
        - 비연결성 (Connectionless) : 요청과 응답이 끝나면 연결을 끊음
        - 무상태성 (Stateless) : 이전 요청의 상태 정보를 서버가 기억 X
        - 기본 포트 : `80`
        
- **HTTPS**
    
    **: HTTP에 보안(SSL/TLS) 기능이 추가된 버전 → 데이터를 주고받을 때 암호화하여 제3자가 내용을 볼 수 없게 함**
    
    - 특징
        - 데이터 암호화 (Encryption) : 모든 정보가 암호화되어 전송 ⇒ 중간에 가로채도 내용을 알 수 없음
        - 데이터 무결성 (Integrity) : 전송 중 데이터가 변조되지 않도록 보호
        - 인증 (Authentication) : 접속하려는 사이트가 신뢰할 수 있는 진짜 사이트인지(위조되지 않았는지) 인증서를 통해 확인
        - 기본 포트 : `443`

### 2. HTTP 구조와 작동 원리

- **웹 주소의 구성**
    
    > 웹 주소는 특정 자원(Resource)이 어디에 있는지 나타내는 문자열
    
    - **URI (Uniform Resource Identifier)** : 자원을 식별하는 전체 개념 (URL 포함)
    - **URL (Uniform Resource Locator)** : 자원의 위치를 알려주는 주소
        
        <aside>
        💡
        
        ex. [https://www.example.com:443/path/to/resource?query=1#fragment](https://www.example.com/path/to/resource?query=1#fragment)
        
        </aside>
        
        - Scheme (프로토콜) : 데이터를 주고받는 규칙
        - Host (호스트) : 자원이 위치한 서버의 도메인 이름 또는 IP 주소
        - Port (포트) : 서버 내에서 특정 서비스로 연결되는 문의 번호
        - Path (경로) : 서버 내에서 자원의 구체적 경로
        - Query String (쿼리 문자열) : 서버에 전달할 추가적 정보
        - Fragment (프래그먼트) : 페이지 내의 특정 섹션을 가리킴
    - **Base URL** : 웹 사이트의 주요 주소 (보통 프로토콜 + 호스트) → 모든 상대 경로를 절대 경로로 변환하는 데 사용되는 기준이 되는 경로
    - **Endpoint** : 서버에서 특정 기능이나 자원에 접근하는 경로 (Base URL 뒤에 붙는 세부 경로)
    - **Query Parameter** : 추가적인 조건이나 데이터를 전달할 때 사용
        - `?`로 시작
        - `key=value` 쌍으로 구성
        - 여러 개의 파라미터는 `&` 기호로 연결
        
        → ex. `?q=http&page=2` 는 q(검색어)는 http이고, page(페이지 번호)는 2라는 옵션을 서버에 전달한 것
        
- **HTTP 요청 구조**
    - **구성 요소**
        
        <aside>
        💡
        
        [ 요청 라인 (Start Line) ]
        
        [ 헤더 (Header) ]
        
        [ 본문 (Body) ]
        
        </aside>
        
        - 요청 라인 : 메소드, 경로, 프로토콜 버전 포함
        - 헤더 : 요청의 추가 정보(ex. 인증, 데이터 타입 등)를 담은 `key:value` 쌍
        - 본문 : 전송할 실제 데이터
    - **HTTP 메소드**
        - `GET` : 데이터 조회 → 서버로부터 리소스를 가져옴 (보통 본문이 없음)
        - `POST` : 서버에 새로운 데이터 생성 → 데이터를 요청 본문에 담아 전송
        - `PUT` : 전체 수정 → 기존 리소스를 덮어쓰기로 수정, 데이터를 본문에 담아 전송
        - `PATCH` : 부분 수정 → 리소스의 일부만 수정, 데이터를 본문에 담아 전송
        - `DELETE` : 데이터 삭제 → 서버의 리소스 삭제
        
- **HTTP 응답 구조**
    - **구성 요소**
        
        <aside>
        💡
        
        [ 상태 라인 (Status Line) ]
        
        [ 헤더 (Header) ]
        
        [ 본문 (Body) ]
        
        </aside>
        
        - 상태 라인 : 프로토콜 버전 + 상태 코드 + 메시지(상태 코드의 설명)
        - 헤더 : 응답의 추가 정보를 담은 `key:value` 쌍
        - 본문 : 서버가 전송하는 실제 데이터 ⇒ 클라이언트가 요청한 실제 데이터
    - **HTTP 상태 코드 (Status Code)**
        - `2xx` - 성공 ✅
            - `200 OK` : 요청이 성공적으로 처리
            - `201 Created` : 요청이 성공하여 새로운 리소스가 생성
        - `4xx` - 클라이언트 오류 ❌
            - `400 Bad Request` : 요청 메시지 형식이 잘못되어서 서버가 이해할 수 없음 (ex. 필수 데이터 누락)
            - `401 Unauthorized` : 인증(로그인) 필요
            - `403 Forbidden` : 인증은 되었으나 해당 리소스에 접근할 권한이 없음
            - `404 Not Found` : 요청한 리소스(페이지, 파일)를 서버에서 찾을 수 없음 (가장 흔히 보는 오류)
        - `5xx` - 서버 오류 ❌
            - `500 Internal Server Error` : 서버 내부 로직에 알 수 없는 오류가 발생
            

<aside>
💡

URL 입력 → 브라우저가 URL을 해석해서 HTTP 요청 전송 → 서버가 요청 처리 후 응답 → 브라우저가 결과 표시

</aside>

### 3. API

- **API (Application Programming Interface)**
    
    **: 서로 다른 소프트웨어 프로그램들이 소통할 수 있게 해주는 통로**
    
    ![스크린샷 2025-10-27 오후 5.15.58.png](week6%20%EB%82%B4%EC%9A%A9%20%EB%B0%9C%ED%91%9C%20%EC%9E%90%EB%A3%8C/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2025-10-27_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_5.15.58.png)
    
    - **기능**
        - 데이터 중개 및 통신 : 프로그램이 서버나 데이터베이스와 정보를 주고받을 수 있도록 중간 매개체 역할 수행
        - 정보 제공 : 다른 사람이 이미 만들어둔 기능을 API를 통해 재사용 가능
        - 보안 : 서버 내부나 DB를 직접 노출하지 않고, 허용된 요청만 받고 정해진 데이터만 전달함으로써 내부 시스템 보호
    - **종류**
        
        
        | **분류** | **종류** | **설명** | **예시** |
        | --- | --- | --- | --- |
        | 공개 범위 | Public API (Open AI) | 누구나 사용할 수 있도록 공개된 API | 구글 맵 API, 네이버 번역 API |
        |  | Private API | 특정 기업이나 조직 내부에서만 사용하는 API | 자사 모바일 앱과 서버간의 통신 |
        | 통신 방식 | REST API | HTTP 기반의 가장 일반적인 웹 API 설계 방식 |  |
        |  | GraphQL API | 클라이언트가 필요한 데이터만 선택적으로 요청 가능 (**쿼리 언어) | ** 쿼리 언어 : 정보를 얻기 위해 보내는 질의문을 만들기 위해 사용되는 컴퓨터 언어 |

### 4. REST API

- **REST (Representational State Transfer)**
    
    **: 웹 서비스 API를 설계하는 데 사용되는 소프트웨어 아키텍처 스타일**
    
    - **구성 요소**
        - 자원 (Resource) : 서버가 관리하는 모든 것 → URI (웹 주소)로 표현
        - 행위 (Verb) : 자원에 대해 수행할 행동 → HTTP 메소드로 표현
        - 표현 (Representation) : 자원을 어떤 형태로 주고받을지 → HTTP 본문과 헤더 (ex. JSON 형식)
        
- **RESTful 설계 규칙**
    
    > ‘REST API’를 제공하는 웹 서비스를 ‘RESTful’ 하다고 할 수 있음
    
    1. 자원은 명사로 표현 : URI는 동사가 아닌 명사 형태 (복수형으로 작성)
    2. 행위는 HTTP 메소드로 구분
    3. 계층적 구조 표현 : `/` 사용
    4. 응답 형식은 일관성 있게
    5. 상태 코드 명확히 사용
    
- **HTTP 메소드와의 관계**
    
    > HTTP 메소드는 REST가 자원을 조작하는 행위를 표현하는 데 사용
    
    - `GET` → 자원 조회
    - `POST` → 새 자원 생성
    - `PUT` → 자원 전체 수정
    - `PATCH` → 자원 일부 수정
    - `DELETE` → 자원 삭제
    
- **REST API 장단점**
    - 장점
        - **직관성** : REST API 메시지가 의도하는 바를 명확하게 나타내므로 의도하는 바를 쉽게 파악 가능
        - **클라이언트 - 서버의 완전 분리** : 서버와 클라이언트의 역할을 분리
        - **기존 인프라 활용** : HTTP 프로토콜의 인프라를 그대로 사용하므로 REST API 사용을 위한 별도의 인프라를 구축할 필요가 없음
        - **범용성** : HTTP 표준 프로토콜에 따르는 모든 플랫폼에서 사용 가능
    - 단점
        - **표준 존재 X** : 설계자마다 구조나 규칙이 다를 수 있음
        - **HTTP 메소드 한정적** : 복잡한 처리에 한계가 있음
        - **요청마다 상태 전달 (Stateless)** : 서버에 부하가 늘거나 클라이언트 구현이 복잡해질 수 있음
        

### 5. 데이터 포맷

**: 데이터를 저장하거나 전송할 때 그 구조와 표현 방식을 정해 놓은 규칙**

- **XML**
    - **태그**(`< >`)로 데이터를 감싸서 표현
    - 시작 태그와 종료 태그가 **쌍으로 존재**
    - 데이터는 **계층적 구조**
    
    ```xml
    <student>
      <name>송영의</name>
      <age>20</age>
      <major>Computer Engineering</major>
    </student>
    ```
    
    - 특징
        - 구조 표현 명확, 데이터 의미 전달 명확
        - 계층 구조를 쉽게 표현 가능 → 복잡한 데이터 표현에 유리
        - 태그가 많아 데이터 크기가 큼 → 전송 효율 낮음
        
- **JSON**
    - `{ }` 안에 `key:value` 쌍으로 이루어진 데이터 구조
    - 배열은 `[ ]`로 묶음
    
    ```json
    {
      "name": "송영의",
      "age": 20,
      "major": "Computer Engineering"
    }
    ```
    
    - 특징
        - 중첩 구조를 통해 복잡한 데이터도 표현 가능
        - 구조가 단순 → 파일 크기가 작고 데이터 전송 속도가 빠름
    
- **XML** vs **JSON**
    
    
    | **구분** | **XML** | **JSON** |
    | --- | --- | --- |
    | 구조 | 태그 기반 (트리 구조) | 키-값 쌍 기반 (객체 구조) |
    | 데이터 크기 | 큼 (태그 포함) | 작음 (간결한 표현) |
    | 속도 | 느림 | 빠름 |
    | 데이터 표현 | 복잡한 계층 구조 표현 용이 | 간단한 구조에 적합 |
    | REST API 적합성 | 낮음 (무겁고 복잡) | 높음 (가볍고 직관적) |
    
    **REST API에서 주로 사용되는 데이터 포맷 ⇒ JSON**
    
    - 전송량이 적어 효율적이고, 대부분의 언어에서 쉽게 파싱이 가능
    - 읽고 쓰기가 간단해 디버깅도 편리
    

### 6. 웹 환경에서의 API 요청

- **브라우저에서 API 요청이 이루어지는 과정**
    
    > 웹 브라우저(클라이언트)와 서버 간의 데이터 교환 흐름
    
    1. 사용자 행동 (이벤트 발생) → 사용자가 버튼 클릭 등으로 API 요청을 발생시킴
    2. HTTP 요청 전송 → 브라우저가 서버 주소로 요청을 보냄
    3. 서버 처리 → 서버가 요청을 받고 필요한 작업 수행
    4. HTTP 응답 반환 → 서버는 결과를 브라우저로 보냄
    5. 브라우저에서 결과 표시 → 받은 데이터를 JavaScript가 화면에 표시
    
    <aside>
    💡
    
    ex.
    
    브라우저 → “/api/weather?city=Incheon” 요청
    
    서버 → `{ "temperature": 17, "condition": "cloudy" }` 응답
    
    브라우저 → 웹 페이지에 “현재 인천 기온 17도” 출력
    
    </aside>
    
- **fetch / async-await**
    - **fetch()** : JavaScript 내장 함수로, HTTP 요청을 보낼 때 사용
        - 브라우저가 서버에 요청하고 응답을 받음
        - 비동기(async) 함수로 동작 ⇒ 결과를 바로 반환하지 않고 나중에 `then()`으로 처리
        
        ```jsx
        fetch('https://api.example.com/data')
          .then(response => response.json()) // 1. 응답을 받으면 JSON으로 파싱
          .then(data => { // 2. 파싱된 데이터를 가지고
            console.log(data); // 3. 실제 작업 수행
          })
          .catch(error => console.error('에러 발생!', error));
        ```
        
    - **async / await** : `fetch`를 더 깔끔하게 쓸 수 있게 해주는 문법
        
        ```jsx
        // 1. 함수 앞에 async를 붙임 -> 이 함수에는 비동기 작업(시간이 걸리는 일)이 있음
        async function getData() {
          try {
            // 2. fetch가 끝날 때까지 '기다림' (await)
            const response = await fetch('https://api.example.com/data');
            // 3. json() 파싱이 끝날 때까지 '기다림' (await)
            const data = await response.json();
            
            console.log(data); // 4. 데이터를 가지고 작업 수행
          } catch (error) {
            console.error('에러 발생!', error);
          }
        }
        ```
        
- **CORS (Cross-Origin Resource Sharing)**
    
    **: 브라우저가 다른 출처의 서버에 요청을 보낼 때, 그 요청이 안전한지 확인하는 보안 규칙**
    
    → 악성 웹사이트가 다른 사이트의 데이터를 몰래 가져가지 못하도록 보호
    
    - **SOP** : 브라우저의 기본 보안 정책 ⇒ 다른 출처로의 요청을 제한
    - 출처(Origin)
        - `프로토콜 + 도메인 + 포트` → 이 3개가 완전히 같을 때만 “같은 출처”로 봄
        - 출처가 다르면 API 요청 허락 X → CORS가 이를 해결
    - CORS 해결 방법
        
        ⇒ 서버가 응답 헤더에 `Access-Control-Allow-Origin: *` (→ 쿠키 전송 X) 또는 특정 도메인을 지정해서 허용 (만약 이를 보내주지 않으면 CORS error 발생)
        

### 7. Postman 실습

- 실습 화면
    - [`https://api.openweathermap.org/data/2.5/weather?q=Incheon&appid=98f23ec3a2c1f21bf54e5c81f3563eb3&units=metric`](https://api.openweathermap.org/data/2.5/weather?q=Incheon&appid=98f23ec3a2c1f21bf54e5c81f3563eb3&units=metric)
    - q : 도시 이름 / appid : 발급받은 API 키 / units : 단위
    
    ![스크린샷 2025-10-28 오후 7.31.18.png](week6%20%EB%82%B4%EC%9A%A9%20%EB%B0%9C%ED%91%9C%20%EC%9E%90%EB%A3%8C/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2025-10-28_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_7.31.18.png)