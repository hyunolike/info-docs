## SecurityContextHolder
> [참고자료](https://ohtaeg.tistory.com/8) / 인증된 사용자 정보 저장! 
- 인증된 사용자 정보 `Principle` > Authentication에서 관리
- `Autentication` > SecurityContext에서 관리
- `SecurityContext` > SecurityContextHolder에서 관리
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/f2b7e880-c15e-406c-8203-c1f3d9a5143a)
### 특징
- `ThreadLocal` 사용
    - 한 쓰레드 내에서 사용하는 공용 저장소
    - `Authenticaton` 한 쓰레드 내에서 공유 가능
    - 쓰레드 달라지면 > 인증 정보 공유 불가 ㅠ,ㅠ
- `SecurityContextHolder` > `Authentication` 담고 있는 Holder
