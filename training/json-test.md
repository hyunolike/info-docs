```javascript
var param = {
    "fruit": [
        {
            "이름": "장현호",
            "운영체제": [
                "macOS",
                "ios"
            ]
        },
        [1,2,3,4,5,6]
    ],
    "size": "Large"
}

console.log(param.fruit[0]);
console.log(param.fruit[0].이름);
console.log(param.fruit[0].운영체제);
console.log(param.fruit[0].운영체제[1])
console.log(param.fruit[1]);
console.log(param.fruit[1][1]);
console.log(param.size);
```

- ![image](https://user-images.githubusercontent.com/61215550/169740412-45aefc00-3f06-44b7-a915-de4c27b77dd9.png)
