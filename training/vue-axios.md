## vue axios 실습 자료 :)
### 준비사항
- vue 2.x
- vue cli
- axios
- json-server

### json-server - `data.json`
```json
{
  "posts": [
    {
      "id": 1,
      "title": "리덕스 미들웨어를 배워봅시다",
      "body": "리덕스 미들웨어를 직접 만들어보면 이해하기 쉽죠."
    },
    {
      "id": 2,
      "title": "redux-thunk를 사용해봅시다",
      "body": "redux-thunk를 사용해서 비동기 작업을 처리해봅시다!"
    },
    {
      "id": 3,
      "title": "redux-saga도 사용해봅시다",
      "body": "나중엔 redux-saga를 사용해서 비동기 작업을 처리하는 방법도 배워볼 거예요."
    }
  ]
}
```

### vue - `App.vue`
```vue
<template>
  <div>
    테스트
    <div>
      <ul>
        <li>{{ id }}</li>
        <li>{{ title }}</li>
        <li>{{ body }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      id: null,
      title: null,
      body: null,
    };
  },
  created() {
    this.axiosTest();
  },
  methods: {
    axiosTest() {
      var url = 'http://localhost:4000/posts/1';

      this.res = axios
        .get(url)
        .then((res) => {
          this.id = res.data.id;
          this.title = res.data.title;
          this.body = res.data.body;
          console.log(res);
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>

<style></style>
```

### 실습 결과
- `npx json-server [해당 데이터 json 파일 상대 경로].json --port 4000`
- `npm run serve`
- ![image](https://user-images.githubusercontent.com/61215550/207749775-4c607923-967b-41b8-a08d-ef02bcec3c84.png) 
