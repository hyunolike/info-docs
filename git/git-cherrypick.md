## git cherry-pick
> [참고자료](https://hbase.tistory.com/141)
- 다른 브랜치에 적용된 커밋을 가져와서 내 브랜치에 적용하고 싶은 경우


```shell
// 사용 방법
git cherry-pick <commit hash>

// 한번에 여러개
$ git cherry-pick 555f8b4 8f618a0 480b6bb

// 범위 지정
$ git cherry-pick 555f8b4..480b6bb
```


![image](https://user-images.githubusercontent.com/61215550/230539212-73e1634f-360f-483b-9e05-3dd0f7ddb3da.png)
