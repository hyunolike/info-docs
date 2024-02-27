## `JArray` `JObject`
> [참고자료](https://ryazum.tistory.com/33)
- `using Newtonsoft.Json.Linq;`

### 특징
- 2개의 Object 사용

```
JObject : JSON Object

JObject 자체가 name값을 가질 수는 없습니다.
(key, value) pair 들을 가질 수 있습니다.
key : string 값입니다.
value : JToken 타입이며 대부분의 premitive type들과 DateTime, TiemSpan, Uri 값을 직접대입 가능하며, 기타 Object도 입력이 가능합니다.

value에 다른 JObject나, JArray를 넣을 수 있습니다.




JArray : JSON Array

JObject와 특징이 거의 비슷하나 key 없이 value 들을 가지고 있습
```
