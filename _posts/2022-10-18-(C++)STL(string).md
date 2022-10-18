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
