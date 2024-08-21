# Self Reference Pattern, 자기 참조 패턴

## 1. What is Self Reference Pattern?
- 자기 참조 패턴은 객체 지향 프로그래밍에서 클래스 또는 객체가 자신의 인스턴스를 다른 객체에게 제공하는 패턴이다.
- 이 패턴은 객체가 자신의 참조를 다른 객체에게 제공함으로써 그 객체가 자기 자신을 사용하도록 할 수 있다.

## 2. Why we use Self Reference Pattern?
- 예를 들어, 이벤트 핸들러나 콜백 메서드를 다루는 경우 이 패턴이 종종 사용된다.
  - 이벤트 핸들러나 콜백 메서드는 특정 이벤트가 발생하면 호출되는 메서드 인데   
    이 메서드를 호출하는 객체는 자신의 참조를 이벤트 핸들러나 콜백 메서드에 제공함으로써   
    이 메서드가 호출하는 객체의 상태에 접근하거나 변경할 수 있다. 

        class MyClass {
            private MyListener listener;
        
            public MyClass() {
                listener = new MyListener(this)
            }
        
            public void notifiyEvent() {
                // some code
            }
        }
        
        class MyListener {
            private MyClass myClass;
        
            public MyListener (MyClass myClass) {
                this.myClass = myClass;
            }
        
            public void onEvent() {
                myClass.notifiyEvent();
            }
        }
      
    - 위 코드에서 MyLinstener 클래스의 생성자는 MyClass 인스턴스를 인자로 받고 있으며,
      이를 통해 MyListener 인스턴스가 MyClass 인스턴스의 메서드를 호출할 수 있게 된다.

## 3. What is problem Self Reference Pattern?
- 이 처럼 자기 참조 패턴은 객체 간의 상호작용을 구현하는데 유용하지만,
  잘못 사용하면 복잡성을 증가시키고 코드를 이해하기 어렵게 만들 수 있어 주의하여 사용하여야 한다.
- 또한 순환 참조 문제가 발생할 수 있으므로 메모리 관리에 주의하여야 한다. 

### 
- 자기 참조 패턴은 객체가 생성될 때 자신의 인스턴스를 다른 객체에 전달하는 방식이다.
- 이 패턴은 이벤트 핸들링, 콜백 메서드, Ovserver 패턴 등에서 자주 상요된다.
- 물론 이런 방식은 순환 참조를 조심해야 하며, 메모리 누스를 방지하기 위해 적절한 해제 처리를 해주어야 한다.

#### 순환 참조( Circular Dependency)
- 두 개 이상의 객체가 서로를 참조하고 있어서 참조의 사실이 끊어지지 않는 현상이다.
- 이는 메모리 관점에서 문제가 될 수 있다. 특히 가비지 컬렉션이 있는 언어에서는
  객체가 더 이상 필요 없을 때 그 참조를 제거하여 메모리를 회수 하는데,
  순환 참조가 발생하면 가비지 컬렉터가 이를 판단하기 어려워져서 메모리 누수가 발생할 수 있다.

> **!참고** - C# 내에서 생성자 호출 순서
> C# 에서 객체 생성은 생성자 호출을 통해 이루어진다.
> 생성자 내에서 다른 객체를 생성할 때, 해당 객체의 생성자가 완전히 실행된 후에야
> 현재 객체의 생성자 실행이 계속된다.
> 따라서 현재 객체에서 this 키워드를 사용하여 다른 객체를 생성하면
> 현재 객체가 완전히 생성되기 전에 다른 객체를 생성하게되는 문제가 발생할 수 있다.
