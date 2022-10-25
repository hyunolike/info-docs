## Selenium session
- 세션 처리 필요 이유
  - 테스트 실행 중 항상 주어진 명령 실행하기 위해 브라우저와 상호 작용!
  - 실행시 현재 실행이 완료되기 전 다른 사람이 같은 컴퓨터에서 동일한 유형의 브라우저에서 다른 스크립트의 실행 시작 가능
  - ⭐2가지 다른 실행이 서로 겹쳐서는 안되는 메커니즘 필요해짐 >> Selenium의 `Session Handling` 사용해서 수행

### 세션 처리 방법 예시
```java
import org.openqa.selenium.WebDriver;
import org.testng.annotations.Test;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.remote.RemoteWebDriver;
import org.openqa.selenium.remote.SessionId;
public class TestNG10 {
   @Test
   public void myTest () {
      System.setProperty("webdriver.chrome.driver",
         "C:\Users\ghs6kor\Desktop\Java\chromedriver.exe");
      WebDriver driver = new ChromeDriver();
      //launch URL
      driver.get("https://www.tutorialspoint.com/index.htm");
      //get session ID
      SessionId s = ((RemoteWebDriver) driver).getSessionId();
      System.out.println("Session Id is for method1: " + s);
   }@Test
   public void myTest1 () {
      System.setProperty("webdriver.chrome.driver",
         "C:\Users\ghs6kor\Desktop\Java\chromedriver.exe");
      WebDriver driver = new ChromeDriver();
      //launch URL
      driver.get("https://www.google.com/");
      //get session ID
      SessionId s = ((RemoteWebDriver) driver).getSessionId();
      System.out.println("Session Id is for method1: " + s);
   }@Test
   public void myTest2 () {
      System.setProperty("webdriver.chrome.driver",
         "C:\Users\ghs6kor\Desktop\Java\chromedriver.exe");
      WebDriver driver = new ChromeDriver();
      //launch URL
      driver.get("https://www.tutorialspoint.com/about/about_careers.htm/");
      //get session ID
      SessionId s = ((RemoteWebDriver) driver).getSessionId();
      System.out.println("Session Id is for method1: " + s);
   }
}
```
