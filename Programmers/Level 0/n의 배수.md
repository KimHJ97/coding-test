# 두 수의 연산값 비교하기 - 181937

### 문제 설명

정수 num과 n이 매개 변수로 주어질 때, num이 n의 배수이면 1을 return n의 배수가 아니라면 0을 return하도록 solution 함수를 완성해주세요.  

<br/>

### 제한 사항

 - 2 ≤ num ≤ 100
 - 2 ≤ n ≤ 9

<br/>

### 입출력 예

 - 입출력 예시1
    - 98은 2의 배수이므로 1을 return합니다.
```
# 입력
num: 98
n: 2

# 출력
result: 1
```

 - 입출력 예시2
    - 32는 3의 배수가 아니므로 0을 return합니다.
```
# 입력
num: 34
n: 3

# 출력
result: 0
```

<br/>

### `소스 코드`

 - num이 n으로 나누어떨어지면 1을 반환하고, 그 외에는 0을 반환한다.
```Java
class Solution {
    public int solution(int num, int n) {
        return num % n == 0 ? 1 : 0;
    }
}
```
