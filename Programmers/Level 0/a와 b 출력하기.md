# a와 b 출력하기 - 181951

### 문제 설명

 - 정수 a와 b가 주어집니다. 각 수를 입력받아 입출력 예와 같은 형식으로 출력하는 코드를 작성해 보세요.

<br/>

### 제한 사항

 - -100,000 ≤ a, b ≤ 100,000

<br/>

### 입출력 예

 - 입력
```
4 5
```
 - 출력
```
a = 4
b = 5
```

<br/>

### `소스 코드`

```Java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int a = sc.nextInt();
        int b = sc.nextInt();

        System.out.printf("a = %d\n", a);
        System.out.printf("b = %d", b);
    }
}
```
