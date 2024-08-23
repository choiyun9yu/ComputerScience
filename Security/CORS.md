# CORS, Cross-Origin Resource Sharing

## 1. What is CORS(교차 출처 리소스 공유)?
- CORS는 웹 페이지가 다른 도메인의 리소스에 접근할 수 있게 해주는 보안 메커니즘이다.
- 기본적으로 브라우저는 같은 출처 정책(Same-Origin Policy)을 적용한다.  
  이 정책은 웹 페이지가 다른 출처의 리소스를 사용하는 것을 제한한다.
- CORS 는 이러한 제한을 안전하게 완화할 수 있는 방법을 제공한다.

### 1-1. Same-Origin Policy(동일 출처 정책)
- 동일 출처 정책은 보안상의 이유로, 웹 페이지가 서로 다른 출처의 리소스에 접근하는 것을 제한한다.
  (도메인, 프로토콜, 포트가 모두 일치해야 같은 출처로 간주)
- 예를 들어, example.com 에서 호스팅되는 웹 페이지는 anotehr.com 의 API 에 직접적으로 요청을 보낼 수 없다.

### 1-2. CORS 작동 원리
#### 1-2-1. Preflight Request
- 브라우저가 OPTIONS 메서드를 사용하여 서버에 사전 요청(Preflight Request)을 보낸다.
- 이 요청은 브라우저가 실제 요청을 보내기 전에 서버가 교차 출처 요청을 하용하는지 확이한다.
- Preflight 요청에는 Access-Control-Reuquest-Method 와 Access-Control-Request-Headers 헤더가 포함되어,  
  실제 요청에서 사용될 HTTP 메서드와 헤더를 서버에 알린다.
#### 1-2-2. Sever Response
- 서버는 Access-Control-Allow-Origin, Aceess-Control-Allow-Methods, Access-Control-Allow-Headers 등의
  헤더를 포함한 응답을 보낸다. 이 해더들은 브라우저에게 어떤 출처, 메서드, 헤더가 허용되는지 알려준다.
#### 1-2-3. Client Request
- Preflight 가 성공적으로 통과되면, 브라우저는 원래의 HTTP 요청을 보낸다.
#### 예시
- example.com 의 웹 페이지가 api.example.com 의 데이터를 요청하는 경우,  
  api.example.com 서버는 응답에 다음과 같은 헤더를 포함할 수 있다.

      Access-Control-Allow-Origin: http://example.com
- 이 헤더는 example.com 에서의 요청만 api.example.com 의 리ㅅ소스에 접근할 수 있음을 의미한다.
- 서버가 모든 출처에서의 접근을 허용하려면, * 와일드 카드를 사용할 수 있다.

      Access-Control-Allow-Origin: *
#### 중요한 CORS 헤더
- Access-Control-Allow-Origin: 특정 출처의 접근을 허용한다.
- Access-Control-Allow-Methods: 리소스에 대해 허용된 HTTP 메소드를 명시한다.
- Access-Control-Allow-Headers: 요청 중에 사용될 수 있는 HTTP 헤더를 명시한다.
- Access-Control-Allow-Credentials: 자격 증명(쿠키 등)을 사용한 요청을 허용할 지 여부를 명시한다.

<br>
  
## 2. 주의사항
### 2-1. 보안 문제
- CORS 를 너무 관대하게 설정하면 보안 위험이 증가할 수 있다.
- 가능한 한 필요한 도메인만 허용하는 것이 좋다.

### 2-2. 자격 증명
- 기본적으로 CORS 는 쿠키나 인증 정보를 포함한 요청을 허용하지 않는다.
- 이를 허용하려면 서버는 Access-Control-Allow-Credentials 헤더를 true 로 설정해야 하고,
  클라이언트 측에서는 withCredentials 을 true 로 설정해야 한다.
