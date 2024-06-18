# Generic Type
- 제네릭 타입은 클래스, 인터페이스, 메서드에서 사용할 데이터 타입을 미리 지정하지 않고,  
  사용할 때 지정할 수 있게 하는 기능이다.
- 제네릭을 사용하면 코드의 재사용성을 높이고, 타입 안정성을 강화하며, 코드의 가독성을 향상시킬 수 있다.

## 1. What is Generic
### 1-1. 제네릭 클래스 (클래스 사용(생성?) 시 타입 파라미터 -> 실제 타입 전환)
    // 제네릭 클래스 정의
    public class Box<T> {
        private T content;

        public void setContent(T content) {
            this.content = content;
        }

        public T getContent() {
            return content;
        }
    }
####
    // 여기서 'T' 는 타입 파라미터로, 클래스를 사용할 때 실제 타입으로 대체된다.
     Box<String> stringBox = new Box<>();
     stringBox.setContent("Hello");
     String content = stringBox.getContent();

     Box<Integer> integerBox = new Box<>();
     integerBox.setContent(123);
     Integer number = integerBox.getContent();
     

### 1-2. 제네릭 메서드(메서드 호출 시 타입 파라미터 -> 실제 타입 전환)
    // 제네릭 메서드 정의
    public class Utility {
        public static <T> void printArray(T[] array) {
            for (T element : array) {
                System.out.print(element + " ");
            }
            System.out.println();
        }
    }
####
    // 여기서 '<T>' 는 메서드의 타입 파라미터이다. 메서드를 호출할 때 실제 타입으로 대체된다.
        // 타입 파라미터: 제네릭 프로그래밍에서 사용되는 개념으로,
        // 사용할 데이터 타입을 나중에 지정할 수 있도록 하는 파라미터
    String[] stringArray = {"Hello", "World"};
    Integer[] intArray = {1, 2, 3};

    Utility.printArray(stringArray);
    Utility.printArray(intArray);
    

### 1-3. 제네릭 인터페이스 (인터페이스 사용 시 실제타입을 지정)
    //제네릭 인터페이스 정의
    public interface Pair<K, V> {
        public K getKey();
        public V getValue();
    }
####
    // 제네릭 인터페이스를 구현하는 클래스
    public class OrderedPair<K, V> implements Pair<K, V> {
        private K key;
        private V value;

        public OrderedPair(K key, V value) {
            this.key = key;
            this.value = value;
        }

        public K getKey() {
            return key;
        }

        public V getValue() {
            return value;
        }
    }
####
  // 인터페이스를 사용할 때 실제 타입 지정
  Pair<String, Integer> pair = new OrderedPair<>("One", 1);
  System.out.println("Key: " + pair.getKey() + ", Value: " + pair.getValue());


### 1-4. 제네릭 타입 제한(Bounded Type Parameters)
- 제네릭 타입 파라미터에 제한을 둘 수 있다.
- 예를 들어 타입 파라미터가 특정 클래스나 인터페이스를 상속해야 한다고 지정할 수 있다.
####
    // T 를 Number 또는 Number 를 상속하는 타입으로 제한
    public class NumberBox<T extends Number> {
        private T number;

        public void setNumber(T number) {
            this.number = number;
        }

        public T getNumber() {
          return number;
        }
    }
####
    NumberBox<Integer> intBox = new NumberBox<>();
    intBox.setNumber(10);
    Integer num = intBox.getNumber();

    NumberBox<Double> doubleBox = new NumberBox<>();
    doubleBox.setNumber(5.5);
    Double decimal = doubleBox.getNumber();
    

### 1-5. 와일드 카드 
- 제네릭 타입에서 와일드 카드는 '?' 를 사용하여 불특정한 타입을 나타낸다.
  - <?>: 어떤 타입이든지 가능
  - <? extends Type>: Type 또는 Type 의 서브 타입만 가능
  - <? super Type>: Type 또는 Type 의 슈퍼 타입만 가능
####
    public void printList(List<?> list) {
        for (Object elem : list) {
            System.out.println(elem);
        }
    }

## 2. Why we use Generic
- 타입 안정성: 컴파일 시 타입 체크를 통해 런타임 에러를 줄인다.
- 재사용성: 다양한 타입을 하나의 클래스나 메서드에서 사용할 수 있다.
- 가독성: 코드의 으도를 명확하게 표현할 수 있다.

> !요약 - 제네릭 타입은 코드의 재사용성과 타입 안정성을 높이는 강력한 기능이다. 제네릭 클래스를 사용하면 다양한 타입의 객체를 처리할 수 있으며, 제네릭 메서드를 통해 여러 타입에 대해 동일한 동작을 수행할 수 있다. 제네릭 인터페이스와 와일드 카드는 더 유연하고 타입 안전한 코드 작성을 도와준다. 이를 통해 자바 개발자는 보다 강력하고 유지보수하기 쉬운 코드를 작성할 수 있다.


## 3. What is problem of Generic
