# HTTP, Hyper Text Transfer Protocol

## 1. HTTP
HTTP는 텍스트 기반의 통신 규악으로 인터넷에서 데이터를 주고받을 수 있는 프로토콜이다.  
TCP/IP 5계층에서 Application Layer에 속하는 프로토콜이다.  

#### HTTP의 동작
클라이언트 측에서 브라우저를 통해 어떤 서비스를 요청(request)하면, 서버측에서 해당 요청사항에 맞는 결과물을 사용자에게 응답(response)하는 형태로 동작한다. 

#### HTTP의 특징
HTTP는 연결 상태를 유지하지 않는 비연결성 프로토콜이다. 때문에 요청/응답 방식으로 동작한다. 또한 HTTP 통신을 하는 서버는 클라이언트의 요청에 대한 정보를 유지하지 않는다.

#### HTTP 요청의 종류(Requset Method)
- GET: 자료의 조회를 요청하는 메소드
- POST: 자료의 생성을 요청하는 메소드
- PUT: 자료의 수정을 요청하는 메소드
- DELETE: 자료의 상제를 요청하는 메소드

#### RTT
RTT는 작은 packet이 클라이언트에서 서버로 이동했다가 다시 돌아오는 왕복 시간을 의미한다.

### 1-1. HTTP 연결의 두가지 방식

#### non-persistent HTTP
non-persistent HTTP 방식에서는 TCP 연결 한번에 최대 하나의 객체를 전송할 수 있다. 두 개 이상의 객체를 전송하기 위해서는 두 번 이상의 연결이 필요하다.

#### persistent HTTP

## HTTP 1.1

## HTTP 2.0
