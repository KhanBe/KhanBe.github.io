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
last_modified_at: 2022-10-18T08:06:00-05:00

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
