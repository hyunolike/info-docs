## `chart.js` - intersection
> [참고자료](https://minaminaworld.tistory.com/182) <br />
> [참고자료22](https://velog.io/@treejy/React%EC%97%90%EC%84%9C-Chart.js-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0-with-TypeScript)
### 개념
- `interaction`: 차트 데이터 각각의 지점 커서 올리면 뜨는 친구
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/c3828b47-2b42-435f-8f31-628633943ac4)


### 기본 사용
```js
options: {
	responsive: true,
	title: {
		display: true,
		text: 'Mode: ' + mode + ', intersect = ' + intersect
	},
	tooltips: {
        // 툴팁을 표현하는 방법
        // index, dataset, point, nearest(defalut), x, y
		mode: mode,
        // 툴팁을 표현할 때, 근처일때 표현할 것인가 아닌가
        // true(defalut), false
		intersect: intersect,
	},
	hover: {
		mode: mode,
		intersect: intersect
	},
}
```

