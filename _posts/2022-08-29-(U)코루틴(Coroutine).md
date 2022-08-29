---
title:  "[Unity] - 코루틴 (Coroutine)"
excerpt: "코루틴 다루기"


categories:
  - Unity
tags:
  - c#
  - Coroutine
  - game
last_modified_at: 2022-08-29T08:06:00-05:00

---

### Update

Update() 함수는 게임오브젝트가 활성화된 상태에서 매 프레임 호출되어 수행된다.
그래서 대부분 Update() 함수에서 작동하도록 구현한다. Update() 함수는 프레임마다 동작하기 때문에   
일시적인 서브동작이나, 다른 동작을 기다리는 기능을 구현하기 어렵다.   
또한 Update() 함수에 되돌아가는 기능을 구현 하더라도 함수의 크기가 커져 유지보수에 매우 어렵다.

### Coroutine
위의 해결방안이 코루틴이다.
일시적인 서브동작이나, 다른 동작을 기다리는 기능을 구현하게 해준다.

```c#
IEnumerator Name(){
	yield return ;
}
```

반환 형식은 IEnumerator이고 일반적인 return과 다르게 앞에 yield가 붙어있다.
yield return을 마주하면 코드 동작을 중지하고 제어권을 유니티에 준다. 

#### 반환
- null : 한 프레임동안 기다린다.
- WaitForSeconds : 인자값으로 넣어준 시간만큼 기다린다.
- WaitForSecondsRealTime : WaitForSeconds 차이점은 타임 스케일의 영향을 받는가 이다.
- WaitForFixedUpdate : FixedUpdate 과정이 끝난 후 제어권을 돌려받는다.
- WaitForEndOfFrame : Update, 화면을 렌더링하는 과정 등, 한 프레임이 지나가는 과정 전체가 끝난 뒤 가장 마지막에 제어권을 돌려받는다.

#### TimeScale
유니티 엔진에는 타임 스케일이라는게 있는데 이것이 시간의 길이를 조절한다.
타임 스케일을 0.5로 하면 게임속 시간흐름이 절반으로 느려진다.

#### Example
```c#
void Update()
{
	StartCoroutine(CoroutineName());	
}

IEnumerator CoroutineName()
{
	//2초 기다린다.
	yield return new WaitForSeconds(2f);
}
```

코루틴 실행은 StartCoroutine 함수로 호출해야 한다.

### 주의점
1. 코루틴을 Start 함수가 호출된 이후에, 게임 오브젝트가 활성화된 상태에서 호출해야만 한다.
Start가 호출되기 이전인 Awake 함수에서 코루틴을 실행하거나 오브젝트가 비활성화된 상태에서 실행시 작동하지 않는다.

2. 코루틴을 서브 Update 함수처럼 쓰기 위해 코루틴 내에서 무한 루프를 돌릴 때, 반복문 바깥에 yield return을 쓰는 경우 종종 발생한다. (에러표시는 안남)   
이러면 유니티에디터나 빌드한 게임이 응답없음으로 멈춘다.
