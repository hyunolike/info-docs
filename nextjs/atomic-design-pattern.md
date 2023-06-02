## Atomic design pattern
> [참고자료](https://velog.io/@growingdeveloper/Next.js%EC%97%90%EC%84%9C-Atomic-Design-pattern-%EC%A0%81%EC%9A%A9%ED%95%98%EA%B8%B0)
- Atoms
  - 가장 기본적인 컴포넌트 블록
  - `label` `input` `button`
- Molecules
  - atoms들의 그룹
  - 자신만의 property 가질수 없음
- Organisms
  - molcule 들의 모음
  - 인터페이스가 어떠한 모양을 갖기 시작하는 단계
- Templates
  - organism들의 그룹
- Pages
  - template의 구체적인 구현체
  - 디자인 시스템의 효율성을 테스트해보는 단계
