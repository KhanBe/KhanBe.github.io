---
title:  "[Programmers]-JadenCase 문자열 만들기"
excerpt: "대소문자 은근히 나온다."


categories:
  - programmers
tags:
  - java
  - algorithm
last_modified_at: 2021-06-20T08:06:00-05:00

---

## 문제

모든단어의 첫 문자가 대문자이고 나머지는 소문자로 만들면 된다.


### 코드

```java
import java.util.*;

class Solution {
    public String solution(String s) {
        String answer = "";
        s = s.toLowerCase();
        String[] arr = s.split(" ");
        
        for(String ss : arr){
            for(int i=0;i<ss.length();i++){
                if(i==0) 
                    answer += Character.toUpperCase(ss.charAt(i));
                else
                    answer += ss.charAt(i);
            }
            answer += " ";
        }
        if(s.charAt(s.length()-1) != ' ') return answer.trim(); 
        return answer;
    }
}
```

### 코드 설명

공백으로 나누어 String배열로 만들었다.

i==0이면 첫문자 이니 대문자로 만들었고

마지막 문자가 공백이면 trim()을 안하고 반환한다.

공백이 아니면 trim()하고 반환한다.

### 요약

- ```toUpperCase()```와 ```toLowerCase()```를 꼭 알자 자주 나오니까
- char형태는 ```Character.toUpperCase(문자)``` 이다.
- ``` 문자열.trim()```은 처음과 끝에 공백이 있으면 지워주는 함수이다.
