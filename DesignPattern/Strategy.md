# Strategy Pattern,전략 패턴 

## 1. What is Strategy Pattern?
- 전략 패턴은 객체지향 프로그래밍에서 행동 디자인 패턴 중 하나이다.
- 알고리즘을 캡슐화하여 동적으로 교체할 수 있도록 하는 패턴이다.
- 이 패턴은 알고리즘을 사용하는 클라이언트와 알고리즘 자체를 분리하여,
  클라이언트 코드의 변경 없이 알고리즘을 쉽게 교체할 수 있도록 한다.

### 1-1. 전략 패턴의 구성 요소
- 전략 인터페이스()
- 구체적인 전략()
- 컨텍스트()

### 1-2. 전략 패턴의 장점
- 유연성: 알고리즘을 쉽게 교체할 수 있어, 다양한 요구 사항에 대응할 수 있다.
- 유지보수성: 알고리즘이 분리되어 있어, 특정 알고리즘을 수정하더라도 다른 부분에 영향을 미치지 않는다.
- 확장성: 새로운 알고리즘을 추가할 때 기존 코드를 수정할 필요 없이 새로운 전략 클래스를 추가하면 된다.

### 1-3. 전략 패턴의 단점
- 복잡성 증가: 전략 패턴을 사용하면 클래스의 수가 증가하여 코드가 복잡해질 수 잇다.
- 클라이언트의 알고리즘 선택 책임: 클라이언트가 적절한 전략을 선택해야 하므로,
  클라이언트 코드가 알고리즘에 대한 지식을 가져야할 수 있다.

## 2. 예제 코드(Java)
#### 전략 인터페이스
    interface Strategy {
      void execute();
    }

#### 구체적인 전략 A
    class ConcreteStrategyA implements Strategy {
        public void execute() {
            System.out.println("Strategy A 실행");
        }
    }

#### 구체적인 전략 B
    class ConcreteStrategyB implements Strategy {
        public void execute() {
            System.out.println("Strategy B 실행");
        }
    }

#### 컨텍스트
    class Context {
        private Strategt strategy;
    
        public Context(Strategy strategy) {
            this.strategy = strategy;
        }
    
        public void setStrategy(Strategy strategy) {
            this.strategy = strategy;
        }
    
        public void executeStragegy() {
            strategy.execute();
        }
    }

#### 사용 예
    public class StrategyPatternExample {
        public static void main(String[] args) {
            Context context = new Context(new ConcreteStrategyA());
            context.executeStrategy();  // "Strategy A 실행"
    
            context.setStrategy(new ConcreteStrategyB());
            context.executeStrategy();  // "Strategy B 실행"
        }
    }
- 이 예제에서는 Strategy 인터페이스를 통해 다양한 알고리즘을 정의하고, Context 클래스가 이를 사용하여 실행한다.
- 클라이언트는 Context 객체에 원하는 전략을 설정하여 알고리즘을 실행할 수 있다.
- 전략패턴은 다양한 상황에서 유용하게 사용될 수 있으며, 특히 알고리즘이 자주 변경되거나 다양한 변형이 필요한 경우에 적합하다.
