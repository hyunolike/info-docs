## mongoose
> [참고자료](https://kasterra.github.io/mongoose-basics/)
- mongoose >> mongodb + nodejs 연결시켜주는 드라이버 ✔
  - mongdb 자체적 지원하는 드라이버도 존재(참고)
 
 ### 1. db 연결
```javascript
import mongoose from "mongoose"; //mongoose 불러오기
mongoose.connect("mongodb://localhost:27017/myapp"); //DB 연결!
```

### 2. 스키마, 모델 생성
```javascript
import mongoose from "mongoose";

const videoSchema = new mongoose.Schema({
  title: { type: String, required: true, trim: true, maxLength: 80 },
  description: { type: String, required: true, trim: true, minLength: 20 },
  createdAt: { type: Date, required: true, default: Date.now },
  hashtags: [{ type: String, trim: true }],
  meta: {
    views: { type: Number, default: 0, required: true },
    rating: { type: Number, default: 0, required: true },
  },
  owner: {
    type: mongoose.Schema.Types.ObjectId, //_id에 대한 이해가 필요함
    required: true,
    ref: "User", //.populate 설명에서 더욱 자세히 다룰 것
  },
});
```
...
