# Computer Science

## Programming Language

### 프로그래밍 언어의 필요성
컴퓨터는 0과 1로 이루어진 이진 코드로 이루어진 기계어를 사용한다. 따라서 컴퓨터와 사람이 소통하기 위해서는 사람의 언어와 기계어의 다리 역할을 하는 프로그래밍 언어가 필요하다.

### 프로그래밍 언어의 종류
#### 고급 언어
컴퓨터와 대화할 수 있도록 만들어진 언어 중 사람이 쉽게 이해할 수 있는 언어이다. 고급 언어로 작성된 파일은 컴퓨터가 바로 이해할 수 없기 때문에 컴파일 과정을 거쳐 기계어로 변환이 필요하다.  
__ex) Java, C, C++, C#, Python__

#### 저급 언어
기계어에 가까운 언어, 대표적으로는 어셈블리어가 있다. 어셈블리어 : 기계어를 직접 작성하는 것 보다는 사람이 이해하기 쉬운 기호로 작성한 언어로, 특정 컴퓨터 아키텍처에 사용되는 CPU명령어 집합을 가지고 있다. 어셈블리어는 컴퓨터 아키텍처가 다른 컴퓨터 간에는 호환되지 않아 이식성이 낮다.

#### 정적 언어
컴파일 시 변수의 타입이 결정되는 언어이다. 따라서 프로그래머가 변수에 들어갈 값의 형태에 따라 직접 변수의 타입을 명시해줘야 한다. 타입 에러로 인한 문제점을 초기에 발견할 수 있어 타입의 안정성이 높다는 장점이 있지만 매번 코드 작성시 변수형을 결정해줘야하는 번거로움도 있다.

#### 동적 언어
런타임 시 변수의 타입이 결정되는 언어이다. 런타임까지 타입에 대한 결정을 끌고갈 수 있기 때문에 유연성이 높다는 장점이 있지만, 실행 도중에 변수에 예상치 못한 타입이 들어와 타입에러가 발생할 수 있다는 단점도 있다.

### 프로그래밍 언어 번역기
번역기는 프로그래밍 언어를 실행가능한 기계어로 변환해주는 프로그램을 뜻한다.

#### 컴파일러
소스코드 전체를 분석한 후 기계어 코드로 변환하는 방식으로 번역을 수행한다. 이때 생성된 기계어 코드는 실행 파일 형태로 저장되어 나중에 필요할 때마다 실행된다.컴파일러를 거치는 언어를 **컴파일 언어**라고하며 대표적으로 C, Java등이 있다.  
컴파일 언어는 한 번만 번역하면 되기 때문에 실행 속도는 빠르지만 소스 코드에 수정이 가해진 경우 다시 컴파일 해야하는 번거로움과 컴파일 시간이 올래 걸리는 경우도 있어서 개발 속도는 느린 편이다.

#### 인터프린터
반면 인터프린터는 소스 코드를 한 줄씩 읽어들여서 바로 실행하는 방식으로 번역을 수행한다. 이때 생성된 기계어 코드는 일시적으로 메모리에 저장되며, 프로그램 실행 중에 필요할 때마다 실행된다. 인터프린터를 거치는 언어를 **스크립트 언어**라고하며 대표적으로 Python, JavaScript등이 있다. 스크립트 언어는 실행할 때마다 번역을 해야해서 실행 속도는 한 번에 번역하는 컴파일 언어보다 느리지만 개발 속도는 컴파일 언어보다 빠르다.
