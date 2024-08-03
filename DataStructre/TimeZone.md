# Time Zone
- 세계는 다양한 타임존으로 나뉘어 있으며, 각 타임존 UTF(협정 세계시)로 부터의 시간 차이로 정의된다.
- 타임존 간의 시간 변환을 정확히 계산하는 것은 복잡하다. (DST, Dailylight Saving Time 등으로 인해)
- GMT(그리니치 평균시, Greenwich Mean Time): 태양이 그리니치 천문대를 통과할 때를 정오로 한다.
- UTC(협정 세계시 , Universal Time Coordinated) 는 세계 협정 시,  
  GMT 와 거의 비슷하지만 UTC 가 더 정밀해서 영국을 제외한 국가 대부분 UTC 를 쓴다.  
- 이러한 복잡성 때문에 대부분의 현대 개발 환경에서는 날짜와 시간을 처리하기 위해 잘 설계된 라이브러리를 사용해야한다.
* KST(Korea Standard Time): UTC + 9:00


## 1. Java
### 1-1. LocalDateTime
- 기본 날짜와 시간 정보를 가지고 있는 객체이다.
####    
    LocalDateTime localDateTime = LocalDateTime.now();

### 1-2. OffsetDateTime
- LocalDateTime 에 UTC 오프셋 정보인 ZoneOffset 이 합쳐진 것이다.
- Offset 정보간 가지고 있어서 일관 절약 시간 정보는 없다.
####
    OffestDateTime offsetDateTime = OffsetDateTime.now();
    
### 1-3. ZoneDateTime
- LocalDateTime 에 시간대 정보인 ZoneId 가 합쳐진 것이다.
- ZoneId 는 내부에 일광 절약 시간 정보, UTC 와의 오프셋 정보 등을 가지고 있다.
####
    ZoneDateTime zoneDateTime = ZoneDateTime.now();

#### ZoneDateTime vs OffsetDateTime
- ZoneDateTime 은 구체적인 지역 시간대를 다룰 때 사용 하며, 일광 절약 시간을 자동으로 처리할 수 있다.  
  사용자 지정 시간대에 따른 시간 계산이 필요할 때 적합하다.
- OffsetDateTime 은 UTC 와의 시간차이 만을 나타낼 때 사용하며, 지역 시간대의 복잡성을 고려하지 않는다.
  시간대 변환없이 로그를 기록하고, 데이터를 저장하고 처리할 때 적합하다.

### 1-4. Instant
- 기계 중심 시간으로 날짜와 시간을 1970년 1월 1일 0시 0분 0초 를 기준으로 경과한 시간을 나노초 정밀도로 표현한다.
- 쉽게 이야기해서 Instant 내부에는 초 정보만 들어있다. 따라서 날짜와 시간을 계산에 사용할 때는 적합하지 않다.
####
    Instant now = Instant.now();    // UTC 기준

<br>

## 2. dotNet
### 2-1. System.DateTime
- dotNet 의 DateTime 객체는 자체적으로 Time zone 정보를 가지고 있지 않다.
- 특정 시점을 나타내는 값 유형으로, 날짜와 시간 정보(년,월,일,시,분,초,밀리초) 정보만 가지고 있다.
####
    // 로컬 시간대
    DateTime localDateTime = DateTime.Now;

    // UTC 시간대
    DateTime utcDateTime = DateTime.UtcNow;

### 2-2. DateTimeOffset
- DateTimeOffset 구조체는 DateTime 값과 함께 UTC 로 부터의 오프셋을 저장한다.  
  이를 통해 특정 시간대의 시간을 명확히 나타낼 수 있다.

### 2-3. TimeZoneInfo
- TimeZoneInfo 클래스는 특정 시간대에 대한 정보를 제공한다.
- TimeZoneInfo 를 사용하여 DateTime 값을 다른 시간대로 변경하거나
  특정 시간대의 현재 시간을 가져올 수 있다.
