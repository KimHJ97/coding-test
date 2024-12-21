## Sublime Text 환경 설정

 - 다운로드 링크: https://www.sublimetext.com/3
 - Python 설치
   - **다운로드**
     - https://www.python.org/
   - **환경 변수 설정**
     - 윈도우 키 → 시스템 환경 변수 편집 검색 → 환경 변수(N)... → Path에 Python 경로 추가
     - C:\Program Files\Python\Python38, C:\Program Files\Python\Python38\Scripts
   - **Sublime Text에 빌드 시스템 추가**
     - Tools → Build System → New Build System... 클릭
```json
{
	"cmd": ["python3", "-u", "$file"],
	"file_regex": "^[ ]*File \"(...*?)\", line ([0-9]*)",
	"selector": "source.python",

	"env": {"PYTHONIOENCODING": "utf-8"},

	"variants":
	[
		{
			"name": "Run",
            "shell_cmd": "python -u \"${file}\" < input.txt",
		}
	]
}
```

## 백준 사이트

백준 온라인 저지는 컴퓨터 프로그래밍 알고리즘 문제 풀이 서비스를 제공해주는 웹 사이트이다.
 - https://www.acmicpc.net/
 - http://solved.ac/

### 문제 답안 제출

문제에 대한 답안은 코드 형태로 제출한다. 입력은 표준 입력(stdin), 결과는 표준 출력(stdout)을 이용한다.  
 - C++ 언어는 cin, cout 함수 이용
 - Python 언어는 input, print 함수 이용

### 백준 문제 난이도

 - 코딩테스트에 나오는 문제 난이도: 브론즈 2 ~ 골드 3
 - 구현을 잘 못하는 단계: 브론즈 1 ~ 브론즈 5
 - 구현을 어느정도 할 수 있고, 기본적인 알고리즘을 아는 단계: 브론즈 1 ~ 실버 2
 - 웬만한 풀이는 구현 할 수 있고 알고리즘 지식도 거의 아는 단계: 실버 3 ~ 골드3

### 백준 사이트 추천 문제

 - 단계별 풀어보기: https://www.acmicpc.net/step
 - 클래스별 문제 순차적 풀어보기: https://solved.ac/class
