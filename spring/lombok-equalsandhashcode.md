## `@EqualsAndHashCode` `@Data` - Lombok
> [참고자료](https://n1tjrgns.tistory.com/164)
- `@RequiredArgsConstructor`: **final** / **@NonNull** 인 필드 값만 파라미터로 받는 생성자 만들어줌!

### @EqualsAndHashCode
- `equals` `hashCode` 자동 생성
  - equals: 두 객체의 내용이 같은지 동등성 비교
  - hashCode: 두 객체가 같은 객체인지 동일성 비교

### @Data
- `@Getter` `@Setter` `@RequiredArgsConstructor` `@ToString` `@EqualsAndHashCode` 한번에 설정해주는 어노테이션
