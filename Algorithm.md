[Algorithm with C](https://github.com/choiyun9yu/C/tree/main/Algorithm.md)

# 검색 알고리즘

## 1. 선형 검색 알고리즘 
- 맨 앞 또는 맨 뒤부터 순서대로 살펴보면서 원하는 데이터를 찾는 방법
- 시간 복잡도: $O(n)$

## 2. 이진 검색 알고리즘
(선행 조건: 순서대로 정렬이 되어 있어야 한다.)
- 전체 데이터를 두 부류로 나눈 뒤 조건을 만족하는 데이터에서만 찾는 방법
- $1$ 이하의 데이터가 남을 때까지 절반으로 나누면서 탐색
- 시간 복잡도: $O(\log_2 n)$

#### $\log$ 
$\log n$ 은 밑을 몇번 곱하면 $n$이 되는지 나타낼 때 사용한다.  
(밑을 생략하면, 수학에선 보통 $\log_10$인데 컴퓨터 공학에서는 $\log_2$를 의미)  
$n$을 $2$로 $\log n$번 나누면 $1$이 된다. 

## 3. 해시 검색 알고리즘
- key값을 해시 함수에 넣어서 나온 해시 값을 인덱스로 사용해서 해시 테이블에 저장한다.  
*해시 테이블: 해시법에서 데이터를 보관하는 곳
- 검색할 때 key값을 넣으면 해시 함수가 해시값을 반환하고 해시 테이블에서 찾아서 값을 찾는다.
- 시간 복잡도: $O(1)$

#### 해시 충돌
해시 충돌은 서로 다른 key에서 해시 함수로 구한 해시 값이 같은 경우를 말한다.
- 오픈 주소법: 이미 해시 값 인덱스에 데이터가 들어가 있으면 이웃한 빈 공간에 데이터를 채워넣는다.   
  검색 시 이웃한 데이터도 같이 검색한다.
- 체인법: 이미 해시 값 인덱스에 데이터가 들어가 있으면 공간을 연결할 자리를 만든다.  
  검색 시 연결된 공간도 같이 검색한다.


<br>

# 정렬 알고리즘
정렬은 데이터값을 크기 순서로 배열하는 것이다. 배열이 이중 구조일 때는 안쪽 배열의 데이터를 1번째 데이터 부터 차례로 비교한다. 만약 1번째 데이터가 같다면 2번째 데이터를 비교한다.

정렬하고자 하는 순서와 반대로 정렬되어 있는 경우 가장 느리다.

## 1. 삽입 정렬($O(n^2)$)
삽입 정렬은 데이터를 앞에서 또는 뒤에서 하나씩 살펴본 뒤 적절한 위치에 삽입하고 정렬하는 방식이다. **정렬 대상인 데이터의 수가 적을 때 사용**한다. 

삽입 정렬은 앞이든 뒤든 한 축을 정렬 완료 축으로 잡고 하나씩 비교 하면서 정렬 완료의 범위에 하나씩 삽입해가며 정렬한다. 

### 1-1. 삽입 정렬 최선일 경우 
삽입 정렬의 경우 최선의 경우 데이터 이동 횟수가 0회이고, 데이터 비교 횟수는 $n - 1$회 이다. 최초 축이 되는 자신을 제외한 데이터와 1번씩만 비교하기 때문이다.

$$n - 1$$  

$$-> n$$ %%주요항만 남김%%  

$$-> O(n)$$   

### 1-2. 삽입 정렬 최악인 경우
최악일 경우 데이터 비교 횟수는 $O(n^2)$이다.

    $\frac{1}{2}n(n-1)$
    = $\frac{1}{2}n^2 - \frac{1}{2}n$
    -> $n^2 + n$    // 계수 생략
    -> $n^2$        // 주요 항만 남김
    -> $O(n^2)$

총 이동 횟수도 $O(n^2)$이다.

    $\frac{1}{2}(n+1)n - 1$
    = $\frac{1}{2}n^2 + \frac{1}{2}n - 1$
    -> $n^2 + n +1$  // 계수 생략
    -> $n^2$         // 주요 항만 남김
    -> $O(n^2)$

데이터 비교 횟수와 이동 횟수가 모두 $O(n^2)$이므로 최악의 경우 삽입 정렬의 데이터 복잡도는 $O(n^2)$이다. 

## 2. 선택 정렬
선택 정렬은 남아있는 데이터 가운데 가장 작은 값 또는 가장 큰 값처럼 가장 적합한 값을 찾아서 찾아서 남은 배열 끝으로 이동시키면서 정렬한다.

선택은 Selection인데 이 단어에는 '도태'라는 뜻도 담겨있다. 선택 정렬에서 가장 적당한 데이터를 꺼내는 방식은 마치 도태되는 과정과도 비슷하다.

그럼 가장 작은 값 혹은 가장 큰 값은 어떻게 구할까? 맨 앞에 있는 데이터를 복사해두고 차례대로 조사하면서 더 작거나 더 큰 값이 나오면 복사해둔 값을 갱신하는 식으로 찾는다.

### 2-1. 선택 정렬 최선인 경우


### 2-2. 선택 정렬 최악인 경우

## 3. 버블 정렬
이웃한 데이터와 교환하는 정렬이다.

### 3-1. 버블 정렬 최선인 경우

### 3-2. 버블 정렬 최악인 경우 

## 4. 퀵 정렬
기준 값으로 데이터를 분류해 정리하는 정렬이다.

### 4-1. 퀵 정렬 최선인 경우

### 4-2. 퀵 정렬 최악인 경우

## 5. 병합 정렬
데이터 열을 2개로 나누고 병합하는 정렬이다.

### 5-1. 병합 정렬 최선인 경우

### 5-2. 병합 정렬 최악인 경우

### 보초법(sentinel method)
보초법은 프로그램을 빠르게 만들어주는 방법 중 하나이다. 어떤 조건을 만족하는 데이터를 검색할 때 그 조건을 만족하는 것으로 보이는 데이터를 미리 배열 끝에 추가하면 배열 끝에 도달하는 과정을 생량할 수 있어서 프로그램의 처리 속도가 빨라진다.

보초법을 사용하지 않으면 검색하고 있는 데이터가 찾고자하는 데이터인지 확인하는 동시에 지금 검색하고 있는 데이터가 배열 밖인지도 확인해야한다. 찾고자하는 데이터가 배열 안에 없으면 배열 밖으로 나가기 때문이다. 그러나 검색을 시작하기 전에 배열의 끝에 찾고자하는 데이터를 넣어두면 반드시 데이터를 반드시 찾을 수 있으므로 배열 밖으로 나갔는지 나가지 않을지 확인하지 않아도 된다.

보초법은 삽입 정렬이나 퀵 정렬 같은 정렬 알고리즘에서 사용한다.

<br>

# 문제 해결 알고리즘 (PSS, Problem Solving Strategies_

## 1. 반복 전략(Loop Algorithm)
반복 전략은 루프(for, while등의 반복문) 속에서 조건이 충족될 때 까지 절차를 반복하는 것이다.

### 1-1. 중첩 루프와 멱집합
*멱집합; 어떤 집합의 원소로 만들 수 있는 모든 부분 집합을 의미

### 1-2. 재귀를 이용한 반복
재귀 알고리즘은 반복 알고리즘에 비해 간결하고 이해하기 쉽다는 장점이 있다. 그러나 재귀 알고리즘이 실행되면 수많은 자기 복제본이 만들어지고, 계산 비용이 별도로 발생한다. 완료되지 않은 재귀 호출과 중간 계산 과정을 계속 추적해야하기 때문이다. 

만약 성능을 취대한 높여야 하는 상황이라면 재귀 알고리즘을 순수한 반복형태로 수정해서 추가 비용이 발생하지 않도록 하는 것이 좋다. 

## 2. 완전 탐색(Brute Force)
완전 탐색은 답이 될 수 있는 후보를 전부 조사하여 문제를 해결하는 가장 무식하면서도 확실한 방법이다.

## 3. 역추적(Backtracking)
완전 탐색에서 정답이 될 수 없는 후보를 제거하여 불필요한 탐색을 줄여 효율성을 높인 문제 해결 방법이다.

## 4. 발견법(Heuristic)
직관에 의해 최고는 아니더라도 충분히 좋은 답을 찾는 방법이다. 완전 탐색이나 역추적 전략 사용시 시간이 너무 많이 걸릴 때 사용한다.

### 4-1. 탐욕법(Greedy Algorithm)
탑욕법은 이전의 선택으로 절대 돌아가지 않는다. 각 단계마다 최선의 선택을 추구하되, 일단 선택하고 나면 과거의 선택을 되돌아보지 않는 것이다.

완벽한 답을 구하는 전통적인 알고리즘 대신 발견법을 사용하면 답을 빨리 구할 수 는 있지만 정확성이 떨어지는 점을 감수해야한다. 그러나 작금의 선택이 미래에 영향을 끼치지 않는 경우에는 탐욕법과 완전탐색으로 얻은 답이 일치한다.

## 5. 분할 정복(Divide and Conquer)
이 전략은 최적 부분 구조로 구성된 문제를 해결하기에 적합하다. 최적 부분 구조로 구성된 문제란 비슷한 형태의 더 작은 부분 문제로 문제를 나눌 수 있는 문제를 말한다. 이렇게 나뉜 부문 문제 역시 같은 방식으로 계속 나눌 수 있다. 계속 나누다 보면 결국 쉽게 풀 수 있는 간단한 문제가 된다. 이 간단한 문제들의 답을 각각 구한 뒤 서로 결합하면 원래 문제의 답을 구할 수 있게 된다.

## 6. 동적 계획법(Dynamic Programming)
문제를 풀 때, 동일한 연산이 여러 차례 수행되는 경우가 있다. 동적 계획법을 활용하면 반복되는 부분 문제를 식별하여 이들을 한 번씩만 연산할 수 있다. 이를 위해 메모이즈라는 기법을 활용한다.


## 7. 분기 한정법
최적화 문제에서 구하려는 답이 '선택의 연속'일 때 자주 활용되는 전략이다. 나쁜 선택지를 빠르게 제거해서 시간을 절약할 수 있다. 

문제를 풀다보면 '차선의 답'을 쉽게 구할 수 있을 때가 많다. 이런 답은 최적해에 다가가는 범위를 설정한다. 차선의 답보다 안좋으면 버리고, 좋으면 범위를 좁혀나가는 방식으로 문제를 해결한다.


1) 문제를 여러 개의 부분 문제로 나눈다.
2) 각 부분 문제의 상한과 하한을 구한다
3) 각 부분문제에서 모든 분기의 상한, 하한 범위를 비교한다.
4) 가장 유망한 부분 문제를 선택하여 1단계로 돌아간다.