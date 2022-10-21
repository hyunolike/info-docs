## CharSequence vs String
> [참고자료](https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=elder815&logNo=220442548728)
### String
- Java >> String 객체내 보관하는 문자열은 유니코드로 변형하여 보관 
  - ✔ html과 같은 마크업 문자 입력, 출력 시 문제 발생 ㅠ,ㅠ
- ⭐마크업 문자를 입력하여 사용할 수 없는 문자열 >> **변경금지 문자**

### CharSequence
- ⭐마크업 문자를 사용하여 변형과 가공이 가능한 문자열 >> **스타일 문자 / 연속되는 문자**
