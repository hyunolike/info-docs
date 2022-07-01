## `sendbird` - User
- 표준 `HTTP` 프로토콜 사용
- API와 함께 사용 가능한 `Java libraray` 존재 - [바로 가기](https://github.com/sendbird/sendbird-platform-sdk-java)
### 1. 준비
- `applicaton_id` >> ✔ 샌드버드 API 사용시 필요

### 2. 사용자
- `user_id` ✔ : 사용자는 고유한 id로 식별
- 토큰 발행: `/users/{user_id}` 사용 ❌ >> `/users/{user_id}/token` 사용 ⭕
- 사용자는 모든 대화의 핵심
- Sendbird 애플리케이션 >> 개발형 채널, 그룹 채널 >> 이렇게 채팅하는 사용자가 구성
#### 2.1 사용자 생성
> 3가지 매개변수 필수
- `user_id`(고유 id) 
- `nickname`
- `profileurl` (프로필 이미지)


