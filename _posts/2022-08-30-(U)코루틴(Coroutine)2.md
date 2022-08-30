---
title:  "[Unity] - 코루틴 (Coroutine) (2)"
excerpt: "코루틴 다루기"


categories:
  - Unity
tags:
  - c#
  - Coroutine
  - game
last_modified_at: 2022-08-29T08:06:00-05:00

---

### 정지

#### Example
```c#

IEnumerator enumerator;

void Start()
{
	enumerator = CoroutineName();
	StartCoroutine(enumerator);	
}

void Update()
{
	if(Input.GetKeyDown(KeyCode.Space))
	{
		StopCoroutine(enumerator);
	}
}

IEnumerator CoroutineName()
{
	int i = 0;
	while (true)
	{
		yield return null;
		Debug.Log("Coroutine : " + i++);
	}
}
```

위 코드는 Class 안에 있다고 가정한다.   
매 프레임마다 i를 증가시키며 출력하는 코드이고, 스페이스바를 누르면 중단하는 코드이다.   
이렇게 코루틴의 반환값 IEnumerator을 변수로 값을 넣어줘서 중단시켜야한다.   


#### 또한 코루틴함수 이름으로만 코루틴함수를 호출할 수 있다.   

```c#
StartCoroutine("CoroutineName");
StopCoroutine("CoroutineName");
```

```StopAllCoroutines()``` : 이 컴포넌트가 실행하고있는 모든 코루틴을 중단한다.   

---

코루틴 함수에 인자를 넣어 매개변수를 받는 방법도 있다.
```
void Start()
{
	StartCoroutine(CoroutineName(10));
}

IEnumerator CoroutineName(int count)
{
	int i = 0;
	while (i < count)
	{
		yield return null;
		Debug.Log("Coroutine : " + i++);
	}
}
```

```StartCoroutine("CoroutineName", 10);``` StartCoroutine(string methodName, object value) 형식으로도 가능하다.   
이름으로 호출할 때에는 인자를 하나밖에 못쓴다.

``StartCoroutine("CoroutineName", 10, 30);``` 이렇게 불가능 하다.   

#### object로 매개변수로 전달하는 방법의 약점

다른 타입의 변수를 object 타입으로 만드는 과정을 boxing이라고 하고   
object 타입의 변수를 되돌리는 과정을 unboxing이라고 부른다.   
이 과정에서 오버헤드를 일으킬 수 있어 최적화에 문제가 생길 수 있다.   

---
c#에서 오브젝트타입은 최상위 변수타입이다.   
오브젝트 타입으로 10을 받으면 내부적으로 int 타입으로 바꿔서 전달해준다.   

### yield break

```
IEnumerator CoroutineName()
{
	yield break;
}
```
코루틴 함수내에 yield break를 만나면 코루틴 함수를 중단시키는 방법도 있다.   
