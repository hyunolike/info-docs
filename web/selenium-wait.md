## Selenium wait()
- 웹페이지 완전히 로딩되지 않는 문제 발생 시 사용
  - 웹페이지가 다 열리지 않은 상태에서 특정 객체를 찾을 떄 해당 객체 없어서 찾을 수 없다는 에러 발생 시킴 ㅠ,ㅠ

### ✔ Selenium 2가지 `Wait` 방법
- `Implicitly wait`: **정해진 시간** 만틈 충분히 기달리기
- `Explicitly wait`:** 어떤 조건** 이 만족할 때까지 기다리기

### 1. `Implicitly wait`
```python
from selenium import webdriver

driver = webdriver.Chrome()
driver.implicitly_wait(10) # seconds
driver.get("https://chancoding.tistory.com/199")
myDynamicElement = driver.find_element_by_class_name("area_title")
```

### 2. `Explicitly wait 
> [다양한 조건 함수](https://selenium-python.readthedocs.io/api.html#module-selenium.webdriver.support.expected_conditions)
- `wait.until(조건)` ⭐
- 조건이 성립되지 않으면 timeout 설정된 시간만큼 최대한 기달림
```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

driver = webdriver.Chrome()
driver.get("https://chancoding.tistory.com/199")

# wait until someid is clickable
wait = WebDriverWait(driver, 10)
element = wait.until(EC.element_to_be_clickable((By.ID, 'someid')))
```

