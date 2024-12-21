# 기본 알고리즘

## 1. 시간 복잡도와 공간 복잡도

### 시간 복잡도

 - __시간 복잡도__
    - 시간 복잡도는 프로그램이 입력 크기에 대해 __얼마나 빠르게 실행되는지__ 를 나타낸다.
    - 시간 복잡도를 표기할 때는 빅오 표기법을 사용하여 표현한다.
 - __빅오 표기법(Big-O notation)__
    - 프로그램 동작 시간에 가장 큰 영향을 주는 값을 중심으로 시간 복잡도를 표기
    - 프로그램 동작 시간에 대한 대략적인 시간 복잡도를 표기
 - __시간 복잡도는 어떻게 쓰이는가?__
    - 시간 복잡도가 큰 풀이로 풀 경우 TLE(시간 초과)가 날 수 있음
    - 문제를 풀 때는 문제의 시간 제한을 만족하는 풀이를 작성해야 함
    - 1초 = 1억 번의 연산


### 공간 복잡도

 - __공간 복잡도__
    - 공간 복잡도는 프로그램이 __얼마나 많은 메모리를 사용하는지__ 를 나타낸다.
    - 공간 복잡도의 표기도 빅오 표기법으로 표현
 - __공간 복잡도는 어떻게 쓰이는가__
    - 공간 복잡도가 큰 풀이는 문제를 풀 경우 OOM(메모리 초과)이 날 수 있음
    - int 자료형 기준 1MB = 약 25만 개의 공간

## 2. 재귀함수 이해하기

 - __함수__: 일련의 작업을 수행하는 코드 블록으로 재사용이 가능하다.
 - __재귀함수__: 함수의 일종으로 재귀함수는 함수 내에서 자기 자신을 호출하는 함수를 의미한다.

```javascript
// 함수
function() {
    // ..
}

// 재귀 함수
recursion_function() {
    // ..
    recursion_function();
}
```

### 재귀함수의 구조

재귀 함수는 Base Case(기본 케이스)와 Recursive Case(재귀 케이스)를 가진다.
 - Base Case: 재귀 함수를 종료하는 부분
 - Recursive Case: 자기 자신을 호출하는 부분
```python
# 1부터 n까지 더하는 함수
def sum_func(n):
    if n == 1:
        return 1
    
    return sum_func(n-1) + n
```

### 재귀함수 이해하기 (백준 10870 문제)

 - n번쨰 피보나치 수를 구하는 문제
    - 피보나치 수열
        - 0 > 1 > 1 > 2 > 3 > 5 > 8 > 13
        - f(2) = f(1) + f(0)
        - f(3) = f(2) + f(1)
    - 재귀함수를 이용한 피보나치(메모이제이션)
        - 중복 계산을 방지하기 위해 전역 변수 arr로 배열 값을 관리하낟.
        - 값이 존재한다면 해당 값을 바로 리턴한다.
```python
##### 1. 반복문을 이용한 피보나치
n = int(input())

# n+2 개의 리스트를 생성하며, 모든 요소는 -1로 초기화
arr = [-1] * (n + 2)    
arr[0] = 0
arr[1] = 1

for i in range(2, n + 1):
	arr[i] = arr[i-1] + arr[i-2]

print(arr[n])

##### 2. 재귀함수를 이용한 피보나치
def fibo(x):
	if x == 0:
		return 0
	if x == 1:
		return 1
	return fibo(x - 1) + fibo(x - 2)


n = int(input())
print(fibo(n))

##### 3. 재귀함수를 이용한 피보나치(메모이제이션)
def fibo(x):
	global arr

	if arr[x] != -1:
		return arr[x]

	arr[x] = fibo(x - 1) + fibo(x - 2)
	return arr[x]


n = int(input())

arr = [-1] * (n + 2)
arr[0] = 0
arr[1] = 1

print(fibo(n))
```

### 재귀함수 이해하기 (백준 4779 문제)

 - `문제`
    - https://www.acmicpc.net/problem/4779
    - 문자열의 길이가 주어지면, 길이가 1이 될 때까지 -,  , - 형태로 바꾸는 문제
    - '-'가 3N개 있는 문자열에서 시작한다.
    - 문자열을 3등분 한 뒤, 가운데 문자열을 공백으로 바꾼다. 이렇게 하면, 선(문자열) 2개가 남는다.
    - 이제 각 선(문자열)을 3등분 하고, 가운데 문자열을 공백으로 바꾼다. 이 과정은 모든 선의 길이가 1일때 까지 계속 한다.
```python
##### 1. bottom-up 방식
# f(N) = F(N-1) + 공백이 3^(N-1) + F(N-1)
# ans[i] = ans[i-1] + 공백이 3^(i-1) + ans[i-1]
ans = ['' for _ in range(13)]
ans[0] = '-'

for i in range(1, 13):
	ans[i] = ans[i-1] + (' ' * (3 ** (i-1))) + ans[i-1]

while True:
	try:
		N = int(input())
		print(ans[N])
	except:
		break

##### 5. 재귀함수 이용
# func(k) = func(k-1) + 공백 3^(k-1)개 + func(k-1)
# k = 0을 base case
def func(k):
    # base case
    if k == 0:
        print('-', end="")
        return
    
    # recursive case
    func(k-1)
    print(' ' * (3 ** (k-1)))
    func(k-1)

while True:
    try:
        N = int(input())
        func(N)
        print()
    except:
        break
```

## 3. 조합과 순열

 - __순열__
    - n개의 원소 중에서 r개의 원소들을 나열하는 경우의 수
    - nPr = n * (n-1) .. (n-r+1)
        - 5개 중에서 3개를 고른다고 하면, 첫 번째로 고를 수 있는 숫자는 5가지, 두 번째로 고를 수 있는 숫자는 4가지, 세 번쨰로 고를 수 있는 숫자는 3가지로 5 * 4 * 3 = 60이다.
```python
# 순열 알고리즘
N = 4
R = 3
lst = [1, 2, 3, 4]
check = [False] * N # 원소 사용 여부를 체크
# check[k] 가 true 이면 인덱스가 k인 원소가 사용중임을 나타냄.
# check[k] 가 false 이면 인덱스가 k인 원소가 사용중이지 않음을 나타냄.
choose = [] # 나열한 원소를 보관

def permutation(level):
	if level == R:
		# 나열한 R 개의 원소를 출력
		print(choose)
		return

	# for문
	for i in range(0, N):
		if check[i] == True: # 인덱스가 i인 원소가 이미 사용중이라면 continue
			continue

		choose.append(lst[i]) # 인덱스가 i인 원소를 선택(추가) 
		check[i] = True # 인덱스가 i인 원소를 사용하고 있으므로 true로 초기화

		permutation(level+1) # 다음 for 문으로 들어가는 역할

		check[i] = False # 인덱스가 i인 원소의 사용이 끝났으므로 false로 초기화
		choose.pop() # (넣었던) 인덱스가 i인 원소를 제거


permutation(0)
```

 - __조합__
    - n개의 원소 중에서 r개의 원소들을 고르는 경우의 수
    - nCr = n * (n-1) .. (n-r+1) / r!
        - 조합은 {1,2,3}과 {2,1,3} 이 동일한 1개로 본다.
        - ABCDE 중에서 3개를 고른다고 할때, nPr / r! 공식이 된다.
        - r개를 골랐을 떄 순서를 바꿔도 동일하기 떄문에, 순열 값 / r! 로 구할 수 있다.
    - nCr = nCn-r
        - n개 중에서 r개를 고른다면, 남은 숫자는 n-r개가 된다.
        - 즉, nCr을 고를 경우와 nCn-r을 고른 경우가 동일하다.
```python
N = 4
R = 3
lst = [1, 2, 3, 4]
choose = [] # 선택한 원소를 보관

def combination(index, level):
	if level == R:
		# 선택한 R 개의 원소를 출력
		print(choose)
		return

	# for문
	for i in range(index, N): 
		choose.append(lst[i]) # 인덱스가 i인 원소를 선택(추가)
		combination(i+1, level+1) # 다음 for 문으로 들어가는 역할
		choose.pop() # (넣었던) 인덱스가 i인 원소를 제거

combination(0, 0)
```

### 조합 알고리즘 (개념)

 - 순열은 순서라는 개념이 존재하고, 조합은 순서라는 개념이 존재하지 않는다.

```python
# 11개 원소 중 1개 선택
for i in range(1, 12):
    print([i])

# 11개 원소 중 2개 선택
for i in range(1, 12):
    for j in range(i+1, 12):
        print([i, j])

# 11개 원소 중 3개 선택
for i in range(1, 12):
    for j in range(i+1, 12):
        for k in range(j+1, 12):
        	print([i, j, k])

# r개를 고르는 모든 경우를 살펴보는 코드를 짤 때  r개의 for문이 필요하다.
# 조합 알고리즘을 구현할 때 일반화를 위해 재귀함수를 이용한다.
N = 10
R = 5
lst = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
choose = [] # 선택한 원소를 보관

# level은 현재 선택한 원소의 개수
# index는 이전 원소의 인덱스+1
def combination(index, level):
    # base case
    if level == R:
        # 선택한 R 개의 원소를 출력
        print(choose)
        return

    # for문 (recursive case)
    for i in range(index, N):
        choose.append(lst[i]) # 인덱스가 i인 원소를 선택
        combination(i+1, level+1) # 다음 for문으로 들어가는 역할
        choose.pop() # 넣었던 인덱스가 i인 원소를 제거

combination(0, 0)
```

 - `백준 6603`
    - k개 수 중에서 6개를 뽑는 경우의 수 모두 출력
```python
def comb(index, level):
    global choose, arr, k

    # base case
    if level == 6:
        for u in choose:
            print(u, end=' ')
        print()
        return
    
    # recursive case
    for i in range(index, k):
        choose.append(arr[i])
        comb(i + 1, level + 1)
        choose.pop()


# 입력
while True:
    choose = []
    I = list(map(int, input().split()))

    k = I[0]
    arr = I[1:]
    if k == 0:
        break

    comb(0, 0)
    print()
```

### 순열 알고리즘

 - 순열은 n개의 원소 중에서 r개를 나열하는 모든 경우를 살펴보는 알고리즘이다.
 - for문을 이용하는 방법과 재귀함수를 이용하는 방법이 있다.
    - for문을 이용하면 for문을 r개 사용해야 하므로 확장성이 좋지않다.
    - 재귀함수를 이용하면 r을 인자로 받아 처리할 수 있어 확장성이 좋다.
```python
N = 10
R = 3
lst = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
check = [False] * N # 원소 사용 여부를 체크
choose = [] # 나열한 원소를 보관

def permutation(level):
    if level == R:
        print(choose)
        return
    
    for i in range(0, N):
        # 인덱스 i인 원소가 이미 사용중이라면 continue
        if check[i] == True:
            continue
        
        choose.append(lst[i]) # 인덱스가 i인 원소 선택
        check[i] = True # 인덱스가 i인 원소를 사용하고 있으므로 true로 초기화

        permutation(level + 1) # 다음 for문으로 들어가는 역할

        check[i] = False # 인덱스가 i인 원소의 사용이 끝났으므로 false로 초기화
        choose.pop() # 낳았던 인덱스가 i인 원소 제거


permutation(0)
```