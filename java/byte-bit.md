## `byte` 
### `bit` vs `byte`
> [참고 자료](https://aitconomy.tistory.com/13)

- `bit`: 인터넷 속도 측정하는 최소 단위로 사용
- `byte`: bit 8개 / 바이트는 메모리 단위 >> ⭐ __데이터 크기__ 측정하는 최소 단위로 사용! 
  - `byte`가  bit 8개인 이유는? 텍스트의 단일 문자를 인코딩하려면 8비트가 필요!
  - 왜 데이터 크기 측정 단위가 `byte`인 이유? 데이터를 보관하는 하드디스크 등의 용량을 측정할 때 메모리 양으로 표현하는게 수월하기 때문

### 자바 인코딩 `ASCII` `EUC-KR` `UTF-8`
> [참고 자료](https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=pjok1122&logNo=221505713248)
- ✔ 인코딩 별 바이트 크기가 다 다르다!! 

#### 1. `ASCII` 코드
- 7bit 가지고 알파벳, 공백, 쉼표, 특수문자 등을 표현하는 문자체계
- 최상위 비트 0으로 고정 / 7bit 사용해 1byte로 구성
- 영어로 나타내는 문제가 없지만, 한글을 포함하여 다른 언어 나타낼 수 없다.

#### 2. `Extended ASCII` 코드
- 128~255 부분 해당하는 빈 공간을 이용하는 방법(최상위 비트=1)
- 최상위 비트 1로 설정 시 유럽에서 사용하는 특수한 형태의 문자 나타낼 수 있다.
- 한글도 같은 방법

#### 3. `Unicode` 
- 국제 표준화 기구(IOS) 표준화 작업 진행
- 전 세계 어디에서나 동일한 형시으로 인식 한다는 점에 초점
- 기존 ASCII 인코딩 기법 버리고 2Byte 기준으로 인코딩하는 유니코드 개발
- 각 나라별로 자신의 언어가 속하고 있는 고유한 공간 할당
- 이전 `Extended ASCII`의 인코딩 기법인 `EUC-KR`과 호환되지 않음 ㅠ,ㅠ

#### 4. `UTF-8`
- UTF-8 >> 가변 길이 지원
- 영문의 경우 1바이트 / 한글의 경우 3바이트

#### 5. 자바에서는 어디서 인코딩 적용?
- 바이트 데이터를 기준으로 문자를 만들어내는 모든 부분 적용

#### 6. `String`과 인코딩
- String 클래스에는 바이트 배열을 어떤 인코딩 기법으로 해석 >> 문자를 생성할 것인지 지정하는 생성자가 존재
- 반대로 String 객체에서 어떤 인코딩 기법을 이용해 바이트 배열로 분해할지 지정하는 `getBytes()` 메서드 존재

```java
String str = "기분 좋은 날씨인데, 집에만 틀어박혀있어야 한다니.. 뷁";
		
byte defaultBytes[] = str.getBytes();
byte eucBytes[] = str.getBytes("euc-kr");
byte ksc5601Bytes[] = str.getBytes("ksc5601");
byte ms949Bytes[] = str.getBytes("ms949");
byte unicodeBytes[] = str.getBytes("unicode");
byte utf8Bytes[] = str.getBytes("utf-8");
byte utf16Bytes[] = str.getBytes("utf-16");

System.out.println("기본 인코딩 : "+ new String(defaultBytes));
System.out.println("EUC-KR 인코딩 : "+ new String(eucBytes,"euc-kr"));
System.out.println("KSC5601 인코딩 : "+ new String(ksc5601Bytes,"ksc5601"));
System.out.println("MS949 인코딩 : "+ new String(ms949Bytes,"ms949"));
System.out.println("Unicode 인코딩 : "+ new String(unicodeBytes,"unicode"));
System.out.println("UTF-8 인코딩 : "+ new String(utf8Bytes,"utf-8"));
System.out.println("UTF-16 인코딩 : "+ new String(utf16Bytes,"utf-16"));

```

### 크기 차이 비교 실습 ⭐
```java
String name = "장현호";
byte[] encodedNameEucKr = name.getBytes("EUC_KR");
byte[] encodedNameUtf8 = name.getBytes("UTF-8");
System.out.println(encodedNameEucKr.length); //6
System.out.println(encodedNameUtf8.length); //9
```
