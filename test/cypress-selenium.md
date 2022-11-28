## Selenium vs Cypress
> [참고자료](https://velog.io/@junbee/Selenium-%EA%B3%BC-Cypress)
### Selenium 📌
- 웹 드라이버를 통해 웹 브라우저 자동화 >> 웹 애플리케이션 테스트 도와주는 프레임워크
- 원하는 프레임워크 언어로 테스트 가능 / 개발 언어 다양
- 유연함 >> language bindings 지원
- Selenium 테스트 용도 외 크롤링 사용
#### 장점
- OS 호환성
- QA가 원하는 프로그래밍 언어로 테스트 가능
- Safari, Chrome .. 최신 브라우저 지원
- 간단한 api 제공
#### 한계
- 테스트 케이스 제작 오래 걸려
- 내장 커멘드 없음
- 페이지 로드나 요소 로드 어려움
- 테스트 이미지 지원 한계
- Cypress에 비해 테스트 환경 조성 어려움
### Cypress 📌
- 순수 자바스크립트 테스트 위한 테스팅 툴 
  - Unit Test
  - Integration Test
  - E2E Test
#### 장점
- 테스트 캡쳐 가능 >> Command Log 위로 마우스 올려서 특정 커멘드 확인 가능
- Explict 이나 Implict wait Commands 사용할 필요 없이 자동 처리
- Commands 실시간 반영
#### 한계
- 동시에 2개 이상의 브라우저 테스트 불가
- 멀티탭 미지원
- 자바스크립트를 테스트 제작용도로만 지원
- Safari, IE 미지원
- iFrames 사용 어려움 ㅠ,ㅠ
