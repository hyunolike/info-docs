## typescript 기초 강의
> [강의자료](https://www.youtube.com/watch?v=VJ8rvsw2j5w&list=PLJf6aFJoJtbUXW6T4lPUk7C66yEneX7MN&index=1)

- 타입스크립트 
  - 💡프로그래밍 언어인 동시에 컴파일러(해당 언어로 번역)
  - 타입스크립트 >> 자바스크립트
- vscode extention
  - prettier: 코드 보기좋게 만들어줌
  - eslint: 코드 품질 검사
  - path intellisense: 파일 빠르게 참조하게 해줘
  - bracket pair color: 짝이 맞는 ( ) 이거끼리 색상 맞춰줌
  - material icon theme
- 타입스크립트 설치
  - npm i -g typescript
  
  
### 💡TypeScript Compiler
- `tsc` 명령어 사용 >> 타입스크립트를 자바스크립트로 변환가능!

### 타입스크립트 동작
- 자바스크립트 기반 언어 >> 자바스크립트에서 유효한 코드는 타입스크립트에서도 유효!
#### 1. tsc app.ts
- ts 명령어로 js파일로 컴파일 해주는 명령어
- `app.js` 파일이 새로 생기게 되
- ![image](https://user-images.githubusercontent.com/61215550/206327265-fb1bf6eb-376f-4a98-b689-6faa7f8a823d.png)
#### 2. node app.js
- 해당 함수 결과가 보여지게되
- ![image](https://user-images.githubusercontent.com/61215550/206327283-cb792fa6-4b8c-4b3c-b4bf-f149e4cfba7a.png)
#### 3. vscode 에러 해결? 
- `tsc --init` 
- 아래와 같이 설정파일 생성
- ![image](https://user-images.githubusercontent.com/61215550/206327441-35d7251d-04de-4cdb-aecb-f0b5ce293bbd.png)
#### 4. 만약 app.ts 변경된 부분 자동으로 app.js 로 컴파일되게끔 할려면
- `tsc -w app.ts` 명령어 사용
- ![image](https://user-images.githubusercontent.com/61215550/206327638-578b5fae-2dd1-47cb-9dae-c4c5f83626a9.png)

### 타입스크립트 정적 타이핑⭐
#### 1. 타입 추론 `Type Inference`
- 말그대로 타입을 추론하는거야
- 타입 표기 없는 경우 >> 읽고 분석 >> 타입 유추하는 방식
- ![image](https://user-images.githubusercontent.com/61215550/206327881-71c0745b-c9e7-4509-a2c9-92675f804e2e.png)
#### 2. 타입 명시
- 변수 선언 시, 변수 값의 타입 명시 >> 변수 값의 데이터 타입 지정!
- ![image](https://user-images.githubusercontent.com/61215550/206328169-ba6a545b-ee0f-44c8-98d0-74166c3b2eb8.png)


```typescript
let studentId: string = "현호"

funciton getStudentDetails(studentId: string): void{ 💡 함수도 타입명시 가능!

}
```
### 타입으로 사용되는 인터페이스⭐
- 대문자로 시작!
- ✔ 인터페이스 타입으로 가지는 값은 인터페이스 구조를 그 값으로 가지도록 강제!


```typescript
interface Student {
  studentId: number;
  age: number;
  name?: string; // ⭐ 선택적 속성 기능!!!
}

function getStudentDetails(studentId: number): Student {
  return {
    studentId: 123,
    age: 12,
  };
}
```

#### 1. `Readonly` 속성
- ✔객체 생성시 할당된 프로퍼티의 값을 바꿀수 없음 ㅠ,ㅠ

### 열거형 & 리터럴 타입
#### 1. Enum 
- 연관된 아이템들을 함께 묶어서 표현할 수 있는 수단

##### 1-1. 숫자형
```typescript
enum GenderType { ⭐
  Male,
  Female,
}

interface Student {
  readonly studentId: number;
  age: GenderType;
}

function getStudentDetails(studentId: number): Student {
  return {
    studentId: 123,
    age: GenderType.Female, ⭐
  };
}
```
##### 1-2. 문자형
```typescript
enum GenderType {
  Male = 'male',
  Female = 'female',
}
```
