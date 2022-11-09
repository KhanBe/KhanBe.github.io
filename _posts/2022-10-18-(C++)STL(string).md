---
title:  "[STL] - string"
excerpt: "C++ 공부하기"


categories:
  - STL
tags:
  - C++
  - Library
  - 자료구조
  - string
last_modified_at: 2022-10-25T08:06:00-05:00

---

## string (문자열)

### 문자열안의 문자열 찾기

```cpp
#include <string>
#include <vector>

using namespace std;

//str1문자열에서 str2문자열을 찾는 함수
int solution(string str1, string str2) {
    int answer = 0;

    //string::npos : 찾는 문자열이 없는 경우에는 string::npos를 반환한다.
    if (str1.find(str2) != string::npos) answer = 1;
    //못찾으면
    else answer = 2;

    return answer;
}
```

- string 헤더 사용

---

### 문자열 치환 (replace)

```cpp
str.replace(시작 주소, 길이, 치환할 문자열)
```

### 문자열에서 string찾기

- ```str.find("zero")``` 해당 문자열이 있으면 처음 주소값 반환하고 없으면 **string::npos** 반환 > 아마 No position 주소값없다는 뜻

- 항상 예외처리하기
- **없는 문자열을 찾으면 에러 생기기 때문에 string::npos를 써준다.**
```cpp
if (numbers.find("zero") != string::npos) {
    numbers.replace(numbers.find("zero"), 4, "0");
}
```

- 전체치환 하는 방법 : while문 써주면된다.
```cpp
while (numbers.find("zero") != string::npos) { //"zero"를 "0"로 전체 치환
    numbers.replace(numbers.find("zero"), 4, "0");
}
```

- list나 vector등 컨테이너에서 원소찾는 find함수는 다르다.
```cpp
find(해당 배열begin(), 해당 배열 end(), 찾을 원소)
```

---

### 대소문자 변환

```cpp
#include <string>
#include <algorithm>

using namespace std;

string solution(string my_string)
{
    string answer = my_string;

    for (int i = 0; i < answer.length(); i++)
    {
        //toupper() : 대문자로
        answer[i] = tolower(answer[i]);
    }

    return answer;
}
```

---

### gcd / lcm

```cpp
#include <numeric>

using namespace std;

int g = gcd(num1, num2);
int l = lcm(num1, num2);
```

---

### vector 중복 원소 제거

```cpp
#include <algorithm>

using namespace std;

//정렬 후 unique 후 erase 뒷부분
sort(answer.begin(), answer.end());
answer.erase(unique(answer.begin(), answer.end()), answer.end())
```

---

### 문자열에서 특정 문자 지우는 방법

```cpp
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

string solution(string my_string)
{
	string answer = "";

	char aeiou[5] {'a', 'e', 'i', 'o', 'u'};//특정문자
	
	for (int i = 0; i < my_string.length(); i++)
	{
		if (my_string[i] == a) {
			my_string.erase(my_string.begin() + i);
			i--;//erase 하면 주소값 + 1된다.
		}
	}
}
```

---

### stringstream

- 문자열을 공백과 \n을 기준으로 파싱하는 용도 등   
- <sstream> 헤더 선언

```cpp
//1. 초기화 방법
stringstream ss(str);

//2. 초기화 방법
stringstream ss;
ss.str("abcde ew");

while (ss >> n) { // 입력받을 값이 없을 때 까지, 없으면 0 반환

}

str = "23 259 a 15";
stringstream ss(str)
int num;
//num값에 파싱된 값이 저장됨
while (ss >> num) { //여기서 자료형(int)에 맞지않는 값(a)이 들어오면 멈춤
	v.push_back(num);
}

```

---
