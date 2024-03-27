# Clean Code

## 1. 깨끗한 코드

### 우리는 저자다 
- 새 코드를 짜면서 우리는 기존 코드를 끊임 없이 읽는다.
- 기존 코드를 읽어야 새 코드를 짜므로 읽기 쉽게 만들면 짜기도 쉬워진다.
- 비록 읽기 쉬운 코드를 짜기 어렵다고해도 결국은 이 방법이 더 빠르고 쉬운 방법이다.

### 보이스카우트 규칙
> "캠프장은 처음 왔을 때보다 더 깨끗하게 해놓고 떠나라."
- 체크아웃할 때보다 점 더 깨끗한 코드를 체크인 한다면 코드는 절대 나빠지지 않는다.  
- 한꺼번에 많은 시간과 노력을 투자해 코드를 정리하라는 것이 아니다.
   - 변수 이름하나 개선
   - 조금 긴 함수 하나 분할
   - 약간의 중복 제거
   - 복잡한 if 문 하나 정리
 
<br>

## 2. 의미 있는 이름

### 의도를 분명히 밝혀라
- 변수, 함수 그리고 클래스의 이름은 다음과 같은 질문에 답할 수 있어야 한다.
  - 존재 이유는 무엇인가?
  - 수행 기능은 무엇인가?
  - 사용 방법은 무엇인가?
- 만약 따로 주석이 필요하다면 의도를 분명히 드러내지 못했다는 말이다.

### 그릇된 정보를 피하라 
- 코드에 그릇된 단서를 남겨선 안된다. 널리 쓰이는 의미가 있는 단어를 다른 의미로 사용해도 안된다.
- 서로 흡사한 이름을 사용하지 않도록 주의 한다.
- 유사한 개념은 유사한 표기법을 사용해야 한다. 일관성이 떨어지는 표기법도 그릇된 정보다.

### 의미있게 구분하라
- 컴파일러나 인터프린터만 통과하려는 생각으로 코드를 구현하는 프로그래머는 스스로 문제를 일으킨다.
- 컴파일러를 통과할지라도 연속된 숫자를 덧붙이거나 noise word 를 추가하는 방식은 적잘하지 못하다.
- 불용어는 중복이다. 변수 이름에 variable, table, String 과 같은 noise word는 금물이다.

### 발음하기 쉬운 이름을 사용하라

### 검색하기 쉬운 이름을 사용하라 
- 변수 이름의 길이는 해당 변수가 사용되는 범위 크기에 비례해야 한다.
  (사용되는 영역이 넓을 수록 겹칠 위험도 높아지기 때문에 더 명확하게 표현해야 한다.)

### 인코딩을 피하라 

#### 헝가리안 표기법
- 요즘 나오는 프로그래밍 언어는 많은 타입을 지원한다. 또한 컴파일러가 타입을 기억하고 강제한다.
- 게다가 클래스와 함수는 점차 작아져 변수를 선언한 위치와 사용하는 위치가 멀지 않다.
- 따라서 오늘 날에는 헝가리안 표기법이나 기타 인코딩 방식이 오히려 방해가 될 뿐이다.

#### 멤버 변수 접두어
- 이제는 멤버 변수에 m_ 이라는 접두어를 붙일 필요도 없다.
- 클래스와 변수는 접두어가 필요없을 적ㅇ도로 작아야 마땅하다.
- 또한 멤버 변수를 다른 색상으로 표시하거나 눈에 띄게 보여주는 IDE 를 사용해야 마땅하다.

#### 인터페이스 클래스와 구현 클래스
- 때로는 인코딩이 필요한 경우도 있다. 인터페이스와 구현체를 구분할 때가 그렇다.
- 과거에는 인터페이스 앞에 I를 붙이지만 이보다는 구현체 앞에 인코딩하는 것이 더 낫다.
  (DroneControlService - ArduCopteDronerControlService)

### 자신의 기억력을 자랑하지 마라
- 일반적으로 문제 영역(domain)이나 해법 영역에서 사용하는 이름을 사용해야한다.
- 문자 하나만 사용하는 변수 이름은 적절하지 않다.
  (루프에서 반복 횟수를 세는 것은 하나만 써도 괜찮다. 그러나 l, 대문자 o는 안된다.)

### 클래스 이름
- 클래스 이름과 객체 이름은 명사나 명사구가 적합하다.
- Manager, Processor, Data, Info 등과 같은 단어는 피하고 동사는 사용하지 않는다.

### 메서드 이름
- 메서드 이름은 동사나 동사구가 적합하다.
   - 접근자(accessor)는 get 를 붙인다.
   - 변경자(mutator)는 set 를 붙인다.
   - 조건자(predicate)는 is 를 붙인다.
- 생성자를 오버로드할 때는 정적 팩터리 메서드를 사용한다.
   - 메서드는 인수를 설명하는 이름을 사용한다. (아래 예제)


   Complex fulcrumPoint = Complex.FromRealNumber(23.0);
######
   Complex fulcrumPoint = new Complex(23.0);
- 위에 코드가 아래 코드보다 더 좋은 코드이다.

### 기발함 이름은 피하라
- 재미있는 이름보다 명료한 이름을 사용해야 한다.
- 의도를 분명히 표현하고 솔직하게 표현해야 한다.

### 한 개념에 한 단어만 사용하라
- 추상적인 개념 하나에 단어 하나를 선택해 이를 고수한다.
   - 예를 들어 똑같은 메서드를 클래스마다 fetch, retrieve, get로 제각각 부르면 혼란스럽다.
   - 같은 맥락에서 Controller, Manager, Driver 를 섞어 쓰면 혼란 스럽다.

### 말장난을 하지마라 
- 한 단어를 가지고 두가지 목적으로 사용하지 말아야 한다.
- 다른 개념에 같은 단어를 사용하는 것은 말 장난이다.
   - 같은 맥락은 매개변수와 반환 값이 유사할 때 같은 개념이라고 한다.

### 해법 영역에서 가져온 이름을 사용하라
- 코드를 읽는 사람도 프로그래머이기 때문에 전산용어, 알고리즘 이름, 패턴 이름, 수학 용어를 사용해도 된다.
- 모든 이름을 문제 영역(domain)에서 가져오는 것은 좋지 않다. 동료들이 매번 고객에게 의미를 물어야하기 때문이다.

### 문제 영역에서 가져온 이름을 사용하라
- 적절한 '프로그래머 용어'가 없다면 문제 영역에서 이름을 가져온다.
- 그러면 코드를 보수하는 프로그래머가 문제 분야 전문가에게 의미를 물어 파악할 수 있다.
- 우수한 프로그래머라면 해법 영역과 문제 영역을 구분할 줄 알아야 한다.
- 문제 영역 개념과 관련이 깊은 코드라면 문제 영역에서 이름을 가져와야 한다.

### 의미 있는 맥락을 추가하라
- 클래스, 함수, 이름(?) 공간에 넣어 맥락을 부여한다. 
- 모든 방법이 실패하면 마지막 수단으로 접두어를 붙인다.
  - 예를 들어, firstName, lastName, street, houseNumber, city, state, zipcode를 보면  
    주소라는 사실을 금방 알 수 있다.
  - 하지만 어떤 메서드가 state 라는 변수 하나만 사용한다면? 변수 state가 주소의 일부라는 사실을 알기 어렵다.
  - addr라는 접두어를 추가해 addrFirstName, addrLastName, addrState 라고 쓰면 맥락이 분명해진다.
 
#### 맥락이 불분명한 변수
   private void printGuessStatistics(char candidate, int count) {
      String number;
      String verb;
      String pluralModifier;
      if (count == 0) {
         number = "no";
         verb = "are";
         pluralModifier = "s";
      } else if (count == 1) {
         number = "1";
         verb = "is";
         pluralModifier = ""
      } else {
         number = Integer.toString(cout);
         verb = "are";
         pluralModifer = "s"
      }
      String guessMessage = String.format(
         "There %s %s %s%s, verb, number, candidate, pluralModifier
      );
      print(guessMessage);
   }

#### 맥락이 분명한 변수
   public class GuessStatisticMessage {
      private String number;
      private String verb;
      private String pluraModifier;

      public String make(char candidiate, int count) {
         createpluralDependentMessageParts(count);
         return String.format(
            "There %s %s %s%s,
            verb, number, candidate, pluralModifier );
      }

      private void createPluranDependentMessageParts(int count) {
         if (count == 0) {
            tehreAreNoLetters();
         } else if (count == 1) {
            thereIsOneLetters();
         } else {
            thereAreManyLetters();
         }
      }

      private void thereAreManyLetters(int count) {
         number = Integer.toString(count);
         verb = "are";
         pluralModifier = "s";
      }

      private void thereIsOneLetter() {
         number = 1;
         verb = "is"
      }

      private void thereAreNoLetters() {
      
      }
   }

### 의미 없는 맥락을 제거하라 
