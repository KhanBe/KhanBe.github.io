---
title:  "[42seoul] - get_next_line"
excerpt: "42seoul 본과정의 두 번째 프로젝트"


categories:
  - 42seoul
tags:
  - C
  - read
  - get_next_line
last_modified_at: 2022-01-24T08:06:00-05:00

---

# 파일의 문장을 읽어서 반환하기
## 파일 디스크립터로부터 읽고, 개행으로 끝나는 한 줄을 반환하는 함수를 코드화 하는 프로젝트

시작하기 전 read함수에 대해 알아야 한다.

## read 함수

```
size_t read(int fd, void *buf, size_t len)
```
fd(파일 디스크립터)가 참조하는 파일의 현재 offset에서 len바이트만큼 buf로 읽어들인다.   
읽어들이는 작업 성공시 buf에 쓴 바이트 숫자 반환, 읽어들이는 작업 실패시 -1을 반환한다.   
offset은 fd에서 읽은 바이트크기(len)만큼 앞으로 나아간다.(자동)   
