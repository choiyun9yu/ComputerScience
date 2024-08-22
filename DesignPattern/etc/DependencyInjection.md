# Dependency Injection, 의존성 주입

## 1. 의존성 주입 3가지 방법
### 1-1. 생성자 주입(Constructor Injection)
- 생성자 주입은 의존성을 객체의 생성자(constructor)를 통해 주입하는 방식이ㅣ다.
- 객체가 생성될 때 피룡한 의존성을 전달받아 이를 필드에 저장한다.
  
#### 특징
- **불변성 보장**: 의존성이 생성 시점에 전달되기 때문에, 객체가 생성된 이후에는 의존성을 변경할 수 없다.
  이를 통해 객체의 불변성을 보장할 수 있다.
- **필수적인 의존성 주입**: 생성자를 통해 의존성을 주입하기 때문에, 해당 의존성이 없이는 객체가 생성될 수 없다.
  따라서 의존성이 반드시 필요할 때 사용하기 적합하다.

#### 예시
    public class Service {
        private final Repository repository;
    
        public Service(Repository repository) {
            this.repository = repository;
        }
    
        public void performOperation() {
            repository.save();
        }
    }

### 1-2. 수정자 주입(Setter Injection)
- 세터 주입은 객체가 생성된 이후, 세터 메서드를 통해 의존성을 주입하는 방식이다.

#### 특징
- **유연성**: 의존성을 나중에 설정하거나 변경할 수 있다. 따라서 선택적 의존성이나 나중에 주입이 필요한 경우 유용하게 사용할 수 있다.
- **의존성 주입의 선택적 관리**: 의존성이 없더라도 객체를 생성할 수 있다가 후에 필요할 때 의존성을 주입할 수 있다.

#### 예시
    public class Service {
        private Repository repository;
    
        public void setRepository(Repository repository) {
            this.repository = repository;
        }
    
        public void performOperation() {
            repository.save()'
        }
    }

### 1-3. 필드 주입(Field Injection)
- 필드 주입은 객체의 필드에 직접 의존성을 주입하는 방식이다.
- 주로 프레임워크에서 의존성을 자동으로 주입할 때 사용된다.

#### 특징
- **간결성**: 코드가 간결해지며, 주로 로직이 숨겨져 있어 코드가 더 명확해 보일 수 있다.
- **테스트의 어려움**: 필드가 외부에서 접근이 불가능하기 때문에 테스트할 때 의존성을 주입하기가 어렵다.
- **불변성 확보 어려움**: 필드 주입은 런타임에 주입되므로, 객체가 생성될 때 필드가 초기화되지 않을 수 있다.
  이는 객체의 불변성을 해칠 수 있다.

#### 예시
    public class Service {
        @Autowired
        private Repository repository;
    
        public void performOperation() {
            repository.save();
        }
    }
- 위 코드에서 Service 클래스는 Repository 객체를 필드에 직접 주입받는다.

### 1-4. 비교와 선택 요령
- 생성자 주입: 의존성이 필수이며, 객체의 불변성을 유지하고자 할 때 사용한다. 대부분의 경우 권장되는 방식이다.
- 세터 주입: 선택적 의존성을 주입하거나, 객체 생성 이후에 의존성을 설정해야 할 때 사용한다.
- 피리드 주입: 코드가 간결해지지만 테스트와 유지 보수가 어려워질 수 있으므로,
  프레임워크가 필드 주입을 지원하는 경우에만 사용하고 일반적으로는 지양하는 것이 좋다.
