---
title:  "[42seoul] - get_next_line"
excerpt: "42seoul 본과정의 두 번째 프로젝트"


categories:
  - 42seoul
tags:
  - C
  - read
  - get_next_line
last_modified_at: 2022-01-26T08:06:00-05:00

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
---

```
ulimit -n
```

ulimit 명령어의 -n옵션으로 **'한번에 오픈할 수 있는 파일의 최대 수'**를 확인한다.   
---

```
char	*read_join(int fd, char *buffer, char *buf_line)
```
- read_value : read함수의 리턴값 담을 변수
- buf_line : static변수로 프로그램이 끝나야 메모리가 지워진다.
- BUFFER_SIZE : 
while문으로  read를 반복한다.('\n', 개행을 찾을 때 까지)   
read함수로 인해 buffer에 문장들이 담긴다.   
read_value가 -1이면 에러니 0반환하고, 0이면 찾을게 없으니 break한다.   
temp를 buf_line의 임시변수로 설정해준다.   
```
buf_line = ft_strjoin(temp, buffer);
```
이 부분은 ```buf_line = buf_line + buffer;``` 로 해석하면 편하다.

buf_line은 결국 BUFFER_SIZE만큼 buffer에 읽어들이는 것을 반복하다가 개행을 발견하면 반환한다.   

```
char	*mod_next_line(char *res_line)
```
반환한 문장을 res_line으로 가지고 함수에 들어간다.   
개행이나 문장의 끝을 만날때 까지 index를 증가시킨다.   
```
temp = ft_substr(res_line, index + 1, ft_strlen(res_line) - index);
```
이 부분은 res_line의 index + 1 인덱스부터 끝까지 substring한다는 내용이다.

```
if (temp[0] == '\0')
```
이 부분은 결국 ```(res_line[index + 1] == '\0')``` 조건과 같다.   

temp를 반환해서 main의 buf_line이 된다.
