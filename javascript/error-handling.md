## 에러 핸들링
> [참고자료](https://ko.javascript.info/error-handling)
### 목차
- `try..catch` & 에러 핸들링
- 커스텀 에러와 에러 확장

### 1. `try..catch`
- ✔ 스크립트 죽는거 방지 및 에러 잡아서(catch) 더 합당한 무언가를 할 수 있게 해줌
#### 1-1 특징
1. 오직 `런타임 에러` 에만 동작 >> 유효한 코드에서 발생하는 에러만 처리
2. 동기적으로 동작 `setTimeout`과 같은 스케줄 된 코드에서 발생한 에러는 잡아낼 수 없음 ㅠ,ㅠ
  - 해당 에러를 잡기위해서는 해당 스케줄 코드를 함수로 만들어 안에다가 `try..catch` 작성

#### 1-2 에러 객체
- ✔ 에러 발생 시, 에러 상세내용 담긴 객체 생성!
- 주요 프로퍼티
  - `name`: 에러 이름, 정의되지 않은 변수 >> `ReferenceError` 이름 ! 
  - `message`: 에러 상세 내용 담고 있는 문자 메시지
  - `stack`: 현재 호출 스택, 에러를 유발한 중첩 호출들의 순서 정보를 가진 문자열로 __디버깅 목적__
#### 1-3 ⭐선택적 `catch` 바인딩
> 스펙 추가 얼마 안된 문법


```javascript
try {
  // ...
} catch { // <-- (err) 없이 쓸 수 있음
  // ...
}
```


#### 1-4 `throw` 연산자
- 에러 생성 담당

#### 1-5 다시 던지기
- 에러 종류와 관계없이 동일한 방식으로 에러 처리하는 것은 디버깅 어렵게 만듬
- catch 알고있는 에러만 처리하고 나머지는 **다시 던지기**


```javascript
try {
  user = { /*...*/ };
} catch(err) {
  if (err instanceof ReferenceError) {
    alert('ReferenceError'); //  정의되지 않은 변수에 접근하여 'ReferenceError' 발생
  }
}
```

#### 1-6 try..catch..finally`
- ✔ 해당 구문안에 사용되는 변수 >> **지역 변수**

#### 1-7 전역 catch
```javascript
<script>
  window.onerror = function(message, url, line, col, error) {
    alert(`${message}\n At ${line}:${col} of ${url}`);
  };

  function readData() {
    badFunc(); // 에러가 발생한 장소
  }

  readData();
</script>
```

### 2. 커스텀 에러와 에러 확장
> [참고자료](https://ko.javascript.info/custom-errors)

