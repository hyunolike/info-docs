## `where 1=1` 
> [참고자료](https://ssd0908.tistory.com/entry/MYSQL-WHERE-11-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EC%9D%B4%EC%9C%A0-%EC%A3%BC%EC%9D%98%EC%82%AC%ED%95%AD%EC%9C%BC%EB%A1%9C%EB%8A%94)
- ✔ 참 의미!
- 쿼리의 조건을 동적으로 변경 / sql 작성 시 조건을 주석 처리하여 질의문을 변경할 수 있기에 사용

### 장점
- 쿼리 디버깅 시, 주석치리 편함
- 동적쿼리에서 특정상황마다 where절 다르게 작성해줘야 할 때 편리

### 위험성
- SELECT 쿼리에 좋음
- 🙄 갱신 OR 삭제 쿼리 주의!
