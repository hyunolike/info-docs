## updated by 23.12.01 - `@Qualifier` 어노테이션
> [참고자료](https://lasbe.tistory.com/112#google_vignette)
- 빈 탐색 시 > 같은 타입의 클래스를 `@Autowised`로 부터 구별 가능하게 해줌


```java
@Component
public class SonyCamera implements Camera {
	@Override
	public void shooting() {
		System.out.println("소니 카메라로 사진을 찍었습니다.");
	}
}

/////////////////////////////////////////////////////////////////////////

@Component
public class CannonCamera implements Camera{
	@Override
	public void shooting() {
		System.out.println("캐논 카메라로 사진을 찍었습니다.");
	}
}
```
### @Qualifier 사용법
- `@Qualifier("[빈 이름]")`
- ⭐직접 지정해준게 아니면 > 클래스 이름의 첫 알파벳을 소문자로 변환
  - 예. HyunoJang.class >> @Qualifier("hyunhoJang")

## DI 빈 여러개 일떄
> [참고자료](https://velog.io/@neity16/Spring-%ED%95%B5%EC%8B%AC-%EC%9B%90%EB%A6%AC-%EA%B8%B0%EB%B3%B8%ED%8E%B8-8-Primary-Qualifier)

### 💡 `@Autowired`
- `Component Scan` + `@Component`로 객체 >> 스프링 빈 등록
- `@Autowired` 통해 등록된 빈에서 필요한 의존객체 설정
- ⭐ 우선적으로 `타입(Type)` 으로 해당 `빈(Bean)` 찾음

### `@Primary`
- 어노테이션 우선순위 지정하는 방식
- 실무에서 많이 사용하는 방식

### `@Qualifier`
- 스프링 컨테이너 여러개의 빈 찾을 때, 추가적으로 판단할 수 있는 정보 주는 원리
- ⭐ 선택되는 구현체들 / 사용 하는 코드에 작성!


### 예시
![image](https://user-images.githubusercontent.com/61215550/229389496-c10a31c2-c723-4289-bd81-a1a125c6ab5e.png)
