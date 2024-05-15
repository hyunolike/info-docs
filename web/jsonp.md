## jquery + jsonp `크로스도메인` 간 통신 
> [참고자료](https://codejs.co.kr/jquery-jsonp/) <br/>
> [참고자료 - JSONP](https://blog.seotory.com/post/understand-jsonp)

### SOP
> Same-Origin policy

- <img width="893" alt="image" src="https://github.com/hyunolike/info-docs/assets/61215550/60d5bac0-89eb-4a46-9b3b-8c8b8e757129">
- <img width="707" alt="image" src="https://github.com/hyunolike/info-docs/assets/61215550/e664b09a-4b5f-434d-9851-83f03d2e3c5d">


### JSONP
- 크로스도메인간 통신
- `<script/>` 태그는 same-origin-policy 정책에 속하지 않는다는 근거로
- 서로 다른 도메인간의  javascript 호출 위해 jsonp (json with padding) 사용
- ⭐️서버단 jsonp 포맷 따라야함! >> 규칙!!
- <img width="829" alt="image" src="https://github.com/hyunolike/info-docs/assets/61215550/3a051ec4-abba-40b9-91b7-f5fcad769a0c">
