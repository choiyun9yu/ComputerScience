# Redis

## 1. What is redis?
### 1-1. redis란?
- redis는 Remote Dictionary Server의 약자로 오픈소스(BSD licensed) 데이터 구조 저장소이다.
- In-memory 데이터 저장소이며, Key-Value 기반의 NoSQL이다. 보통 DB, Cache, 메시지 브로커 등의 용도로 사용한다.
- Redis 는 다양한 데이터 구조를 지원하며, 이를 통해 문자열, 해시, 리스트, 세트, 정렬된 세트 등을 저장하고 조작할 수 있다.
- 주로 높은 성능과 scalability 를 목적으로 설계되어 있어, 데이터 조회 및 쓰기가 매우 빠르고 실시간 애플리케이션에서 많이 사용된다.
- 초당 10만 ~ 15만건의 명령을 수행할 수 있으며, 파이프링을 통해 리눅스 시스템에서 초당 100만건의 요청도 수행이 가능하다.

#### In-memory 저장
- 데이터를 메모리에 저장하므로 매우 빠른 읽기와 쓰기 속도를 제공한다. 따라서 데이터베이스나 캐시로 사용될 때 특히 유용하다.

#### 다양한 데이터 구조 지원
- Redis 는 다양한 데이터 구조를 지원하여 여러 용도로 활용될 수 있다.
    - 문자열: 일반적인 텍스트 데이터 저장
    - 해시: 필드와 값을 갖는 맵 형태의 데이터 저장
    - 리스트: 순서가 있는 데이터의 집합을 저장
    - 세트: 중복이 없는 데이터의 집합을 저장
    - 정렬된 세트: 값에 대해 정렬된 순서로 데이터를 저장.

#### 영속성
- Redis 는 옵션으로 디스크에 있는 데이터를 저장할 수 있는 영속성을 지원한다.
- 이를 통해 재시작 시 데이터 손실 없이 지속적으로 사용할 수 있다.

#### 고급 기능
- Redis 는 PUB/SUB 메시징 패턴을 지원하여 메시지 브로커로 사용될 수 있다.
- 또한 Lua 스크립트를 이용한 복잡한 연산도 지원하며, 트랜잭션과 같은 고급 기능도 제공한다.

> **?메시지브로커** - 메시지 브로커는 소프트웨어 서비스나 애플리케이션 간에 데이터를 안전하고 효율적으로 전달하는 중간 매개체이다.
> - 메시지 전달: 메시지 브로커는 프로듀서(데이터를 생성하고 전송하는 애플리케이션)와 컨슈머(데이터를 수신하고 처리하는 애플리케이션) 간에  
    >   메시지를 전달한다. 이 과정에서 메시지 브로커는 메시지를 저장하고, 전송 시 중간에 데잍 ㅓ변환 및 라우팅을 수행할 수 있다.
> - 프로토콜 지원: 다양한 프로토콜을 지원하여, 프로듀서와 컨슈머 간의 통신을 가능하게 한다. 대표적으로 AMQP, MQTT, Kafaka, Redis 등의   
    >   프로토콜이 사용된다.
> - 큐잉: 메시지 브로커는 메시지를 안전하게 큐에 저장하여, 컨슈머가 준비되었을 때 메시지를 전달할 수 있다.
    >   이는 비동기적으로 작업을 처리하거나, 과부하를 관리하는데 유용하다.
> - 토픽 기반 라우팅: 일부 메시지 브로커는 토픽 기반의 라루팅을 지원하여, 특정 주제에 관련된 메시지만 필터링하거나 전달할 수 있다.
> - 확장성과 고가용성: 대규모 애플리케이션에서는 메시지 브로커가 클러스터링을 지원하여 확장성과 고가용성을 제공할 수 있다.
> - 주로 메시지 브로커는 분산 시스템 내에서 데이터 통신과 이벤트 기반 아키텍처를 구현하는 데 사용된다.
    >   대규모 데이터 처리, 실시간 데이터 흐름 관리, IoT 시스템에서의 센서 데이터 처리 등 다양한 분야에서 중요한 역할을 한다.
## 2. Why those use redis?

## 3. What is problem of redis?

## 4. How to use redis?