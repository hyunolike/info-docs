## BufferedReader BufferedWriter
> [참고자료](https://jhnyang.tistory.com/92)
- 버퍼 이용해 읽고 쓰는 함수
- 입출력의 효율이 비교할 수 없을 만큼 좋아짐!!

### (참고) 버퍼 개념
- `Buffer`: 데이터를 한 곳에서 다른 한 곳으로 전송하는 동안 일시적으로 그 데이터 보관하는 임시 메모리 영역
  - 입출력 속도 향상 위해 버퍼 사용
- `buffer flush`: 버퍼에 남아 있는 데이터 출력(버퍼 비우는 동작)
- `BufferedReader`: 버퍼 이용한 **입력**
- `BufferedWriter`: 버퍼 이용한 **출력**

### 1. `BufferedReader`
- 데이터를 **라인 단위** 로 읽음
- `String` 으로 고정 ✔
