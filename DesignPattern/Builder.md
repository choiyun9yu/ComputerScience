# Builder Design Pattern

# 1. What is Builder Pattern
- 객체 생성의 복잡성을 줄이고, 가독성을 높이며, 유연성을 제공하는 디자인 패턴
- 빌더 패턴은 특히 객체 생성 시 많은 매개 변수가 필요하거나, 생성자 오버로딩이 복잡해지는 경우에 유용

## 1-1. 빌더 패턴을 사용하지 않고 생성자를 사용하여 객체를 생성하는 경우

    public class User {
        private String firstName;
        private String lastName;
        private int age;
        private String email;

        public User(String firstName, String lastName, int age, String email) {
            this.firstName = firstName;
            this.lastName = lastName;
            this.age = age;
            this.email = email;
        }

        // Getters and Setters
    }
####
    // 객체 생성
    User user = new User("John", "Doe", 30, "john.doe@example.com");
- 많은 매개변수를 가진 생성자는 코드 가독성을 떨어뜨리고, 매개변수의 순서를 기억해야하므로 사용하기 불편할 수 있음
  (요즘은 IDEA 설정을 통해 볼 수 있긴하지만 여전히 가독성이 떨어짐)

## 1-2. 빌더 패턴을 사용하여 객체를 생성하는 경우

    public class User {
        private String firstName;
        private String lastName;
        private int age;
        private String email;

        private User(UserBuilder builder) {
            this.firstName = builder.firstName;
            this.lastName = builder.lastName;
            this.age = builder.age;
            this.email = builder.email;
        }

        public static class UserBuilder {
            private String firstName;
            private String lastname;
            private int age;
            private String email;

            public UserBuilder setFirstName(String firstName) {
                this.firstName = firstName;
                return this;
            }

            public UserBuilder setLastName(String lastName) {
                this.lastName = lastName;
                return this;
            }

            public UserBUilder setAge(int age) {
                this.age = age;
                return this;
            }

            public UserBuilder setEmail(String email) {
                this.email = email;
                return this;
            }

            public User build() {
                return new User(this)
            }
        }
        
        // Getters
    }
####
    // 객체 생성
    User user = new User.UserBuilder()
            .setFirstName("John")
            .setLastName("Doe")
            .setAge(30)
            .setEmail("john.doe@example.com")
            .build();

## 1-3. Lombok 을 사용한 빌더 패턴
- Lombok 라이브러리를 사용하면 빌더 패턴을 더 간단하게 구현할 수 있다.
####
    @Getter
    @Setter
    @Builder
    public class User {
        private String firstName;
        private STring lastName;
        private int age;
        private String email;
    }
####
    // 객체 생성
    User user = new User.UserBuilder()
            .setFirstName("John")
            .setLastName("Doe")
            .setAge(30)
            .setEmail("john.doe@example.com")
            .build();


# 2. Why we use Builder Pattern
- 단계적 객체 생성
- 가독성 향상: 메서드 체이닝을 통한 가독성 향상
- 불변객체 생성: 필요한 모든 값을 설정한 후 객체를 생성하므로, 불변객체를 쉽게 생성
- 필수 및 선택적 매개변수 구분: 생성자와 달리, 필수 매개변수와 선택적 매개변수 쉽게 구분


# 3. What is problem of Builder Pattern
