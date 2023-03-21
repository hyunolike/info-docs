## Rebase - 🙄한 브랜치에서 다른 브랜치 합치는 방법
> [참고자료](https://seosh817.tistory.com/240#%EB%--%B-%--%EC%-E%--%EC%--%--%--branch%EC%-D%--%--%EA%B-%--%EA%B-%--%--commit%EB%A-%--%EB%-B%A-%--conflict%EB%A-%BC%--%ED%--%B-%EA%B-%B-%ED%--%B-%EC%--%BC%--%ED%--%-C%EB%-B%A--) <br>
> [참고자료](https://velog.io/@kwonh/Git-Rebase%EB%9E%80)
- ✔ 한브랜치에서 다른 브랜치 합치는 방법
  - `Merge`
  - `Rebase`
- rebase >> base를 재설정(재배치)

### 😛 동작 설명
#### 상황
![image](https://user-images.githubusercontent.com/61215550/226495739-8313bfb9-dcae-4e6a-ba70-cce32afba29f.png)

#### `git rebase main`
![image](https://user-images.githubusercontent.com/61215550/226495771-631805a0-8e89-468e-9976-d21205633eca.png)

#### `git rebase bugFix`
- `bugFix` 의 부모쪽에 있었기에 더 앞쪽의 커밋을 가리키게 됨!

![image](https://user-images.githubusercontent.com/61215550/226495916-18dee4ea-fc64-4422-af22-e270e475dbc3.png)


### 장점
1. 공유 branch의 최신 변경사항을 즉각 반영
2. reabse는 커밋 이력 남지 않음 `commit history` 깔끔


|`merge`|`rebase`|
|---|---|
|![image](https://user-images.githubusercontent.com/61215550/226493847-2a29e17e-5804-4d89-a6ab-8f56eed51fad.png)|![image](https://user-images.githubusercontent.com/61215550/226493853-8a7f66b7-8c29-4e41-8813-f58a911b3712.png)|

### 단점 아닌 장점
- 내 작업 branch의 각각 commit 마다 conflict 해결

### 추가 설명
-![image](https://user-images.githubusercontent.com/61215550/226494164-2fef4095-482c-42db-9354-51590ad607f2.png)

---
### [학습 사이트](https://learngitbranching.js.org/?locale=ko)
- ![image](https://user-images.githubusercontent.com/61215550/226495554-5b5d7fa6-e929-42c5-9832-12f410fcc15a.png)

