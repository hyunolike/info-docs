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
Object와 특징이 거의 비슷하나 key 없이 value 들을 가지고 있습니다.

즉, JObject나 Jarray 자체는 name을 가질 수 없으나, 다른 JObject에 value로 소속될 경우에는 key값을 가져야 하며, 다른 JArray에 소속될 경우에는 key값 없이 입력됩니다.
```
