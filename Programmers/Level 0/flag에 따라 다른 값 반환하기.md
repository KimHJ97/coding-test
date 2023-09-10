# flag에 따라 다른 값 반환하기 - 181933

### 문제 설명

두 정수 a, b와 boolean 변수 flag가 매개변수로 주어질 때, flag가 true면 a + b를 false면 a - b를 return 하는 solution 함수를 작성해 주세요.  

<br/>

### 제한 사항

 - -1,000 ≤ a, b ≤ 1,000

<br/>

### 입출력 예

 - 입출력 예시1
    - 예제 1번에서 flag가 true이므로 a + b = (-4) + 7 = 3을 return 합니다.
```
# 입력
a: -4
b: 7
flag: true

# 출력
result: 3
```

 - 입출력 예시2
    - 예제 2번에서 flag가 false이므로 a - b = (-4) - 7 = -11을 return 합니다.
```
# 입력
a: -4
b: 7
flag: false

# 출력
result: -11
```

<br/>

### `소스 코드`

 - 삼항 연산자를 이용한다.
 - flag가 true면 a + b
 - flag가 false면 a - b
```Java
class Solution {
    public int solution(int a, int b, boolean flag) {
        return flag ? a + b : a - b;
    }
}
```
