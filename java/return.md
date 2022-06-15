## `return` 문 
- 모든 메서드는 1개의 return 존재해야됨
  - 반환타입 `void`인 경우: return문 없어도 됨 >> 컴파일러가 `return;` 자동적으로 추가
### 1. 반환값
- 간단한 메서드 아래와 같이 수정
```java
// if문
int abs(int x){
  if(x>=0){
    return x;
  }else{
    return -x;
  }
}

//삼항 연산자 사용 ✔
int abs(int x){
  return x>=0 ? x : -x;
}
```

## 2. 매개변수 유효성 검사 ✔
- 메서드 구현시 가장 중요한 부분 >> 매개변수의 값 적절한 것 인지 확인
