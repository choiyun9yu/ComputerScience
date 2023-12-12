# Singleton Design Pattern

## 1. What is Singleton Pattern?

싱들톤 패턴은 객체의 인스턴스가 오직 1개만 생성되는 패턴을 말한다. 싱글톤 패턴은 생성자를 외부에서 호출하지 못하도록 접근 제한자를 private으로 설정한다.

    public class Sington {
        private static Singleton instance = new Singleton();

        private singleton() {
        }
    
        public static Singleton getInstance() {
            return instance;
        }

        public void say() {
            System.out.println("hi, there");
        }
    }

## 2. Why we use Singleton Pattern?

인스턴스를 1개만 생성할 수 있도록 하면 메모리 낭비를 방지할 수 있다. 최초 한번의 new 연산자를 통해 고정된 메모리 영역을 사용하기 때문에 추후 해당 객체에 접근할 때 메모리 낭비를 방지할 수 있다. 또한 이미 생성된 인스턴스를 활용하니 속도 측면에서 약간의 이점이 있다.

또한 싱글톤 패턴을 사용하면 다른 클래스 간에 데이터 공유도 더 쉽다. 싱글톤 인스턴스가 전역으로 상요되는 인스턴스이기 때문에 다른 클래스의 인스턴스들이 접근하여 사용하기 좋다. 하지만 여러 클래스의 인스턴스에서 싱글톤 인스턴스의 데이터에 동시에 접근하게 되면 '동시성 문제'가 발생할 수 있으니 유의해야한다.


## 3. What is problem of Singleton Pattern

싱글톤 패턴은 위와 같은 장점에도 불구하고 몇가지 문제점으로 인해 trade-off를 잘 고려해서 사용해야한다. 

먼저 싱글톤 패턴은 구현하는 코드가 많이 필요하다. 객체 생성을 확인하고 생성자를 호출하는 경우에 멀티 스레딩 환경에서 발생할 수 있는 동시성 문제를 해결하기 위해 syncronized 키워드를 사용해야한다. 

또한 싱글톤 패턴은 테스트하기가 어렵다. 싱글톤 인스턴스는 자원을 공유하고 있기 때문에 테스트가 결정적으로 격리된 환경에서 수행되려면 매번 인스턴스의 상태를 초기화해야 한다. 그렇지 않으면 어플리케이션 전역에서 상태를 공유하기 때문에 테스트가 온전하게 수행되지 못한다.

마지막으로 싱글톤 패턴은 의존 관계상 클라이언트가 구체 클래스에 존게하게 된다. new 키워드를 직접 사용하여 클래스 안에서 객체를 생성하고 있으므로, 이는 SOLID 원칙중 DIP를 위반하게되고 OCP원칙 도한 위반할 가능성이 높다.