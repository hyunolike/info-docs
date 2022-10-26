## Selenium Architecture
- 셀레니움: 브라우저의 자동화 프레임워크 중 하나
  - 브라우저와 통신 / 테스트 자동화
- `Selenium WebDriver` 핵심 구성 요소

### workflow 
- ![image](https://user-images.githubusercontent.com/61215550/197912193-6a89fea2-fdf9-4241-b853-ff4a55f6d34a.png)

1. 자동화 실행 >> 자동화 코드 `JSON` 변환
2. 생성된 `JSON` >> HTTP 통해 JSON Wire Protocol 통해 브라우저 드라이버 전송
3. 브라우저 드라이버 >> HTTP 통해 각 브라우저에서 명령 실행
4. 브라우저 드라이버는 브라우저에서 응답 받고 사용자에게 다시 전송

### 셀레니움 주요 도구 모음
- Selenium IDE
- Selenium RC - ❌ 공식적으로 사용 안함
- Selenium WebDriver - 명령 수락 및 브라우저로 보내는 브라우저 자동화 프레임워크 ✔
- Selenium Grid
