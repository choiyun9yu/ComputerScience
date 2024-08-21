# Overload 

## 1. 오버로드 응용
    public ExampleMethod (param) {
        // Part 1 ...
        UserType res = ...
        
        // Part 2 ...
    }
- 위와 같은 Method( )가 있다고 할 때 param 으로 int 가 들어올 수도 있고 string 이 들어올 수 있을때,  
  param 으로 들어오는 값에 따라 Part 1 의 부분이 달라지고 그 결과 값을 사용하는 Part 2 부분은 같다면
  오버로드를 사용하여 유연하게 대처할 수 있다.
#### Part 1 부분
    public ExampleMethod (int param) {
        UserType res = param...
        ExampleMethod(res);
    }

    public ExampleMethod (string param) {
        UserType res = param...
        ExampleMethod(res);
    }
#### Part 2 부분
    public ExampleMethod (UserType userType) {
        // Part 2...
    }
