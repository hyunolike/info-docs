## fetch join - `N+1 문제`
> [참고자료](https://cobbybb.tistory.com/18)
### 요약
|`일반 Join`|`Fetch Join`|
|---|---|
|select 하는 entity >> jpql 조회하는 주체가 되는 `entity` 만 조회 및 영속화|조회 주체 entity 외에도 연관 entity도 함께 select 하여 영속화|
|![image](https://user-images.githubusercontent.com/61215550/228123557-915fc2a8-85ed-4043-9a75-6b221d890ec0.png)|![image](https://user-images.githubusercontent.com/61215550/228123585-40263bb3-cbcf-48cc-8bd7-a84d6719c0a0.png)|


- ✔ 일반 Join
  - join 조건을 제외하고 실제 질의하는 **대상 Entity에 대한 칼럼만 SELECT**
- ✔ Fetch Join
  - 실제 질의하는 대상 Entity와 **Fetch join 걸려있는 Entity 포함한 칼럼 함께 SELECT**

### 💡 일반 조인 쓰는 시점
- JPA >> `DB <--> 객체` 의 일관성 잘 고려해서 사용
- 로직에 꼭 필요한 Entity만을 영속성 컨텍스트에 담아놓고 사용
- ⭐ 검색 조건에만 연관 Entity 사용할 경우 >> 일반 조인 효율적!
