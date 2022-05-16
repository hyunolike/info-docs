## 예외 처리
- 크게 2가지 예외
  - 개발자가 의도한 오류 `custom exception`
  - 예상치 못한 오류 `system exception`
- ✔ api 오류 메시지에 대해 일관된 형식으로 응답하도록 설계!

### 개발 순서
> [참고 자료](https://leeys.tistory.com/30?category=704916)
1. 에러 응답 모델 생성
2. 에러 `Enum Class` 선언
3. `Custom` 에러 구현
