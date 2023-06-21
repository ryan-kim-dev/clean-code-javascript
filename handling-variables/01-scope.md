# 1. `var` 키워드 사용 지양하기

## 함수 스코프 (`var` 키워드)

```javascript
// * 함수 스코프 vs 블록 스코프
var global = '전역변수';

if (global === '전역변수') {
	var global = '지역변수';
	console.log(global); // 지역변수
}

console.log(global); // 지역변수
```

`var` 키워드는 함수 스코프이므로 위 예제의 if문에서 선언한 `global` 변수는 if문의 블록을 벗어나서도 유효하다.

## 블록 스코프 (`let`, `const` 키워드)

`let, const` 키워드는 블록 스코프를 가진다. 따라서 if문, for문, 함수 내부 등 코드 블럭 내부에서 선언한 변수는 해당 블록을 벗어나면 유효하지 않다.
따라서 예측 불가능한 재할당과 재선언의 우려가 있는 `var` 키워드 대신 `let` 이나 `const` 키워드를 사용하여 변수를 선언하는 것이 좋다.

```javascript
// 1. if문
let global1 = '전역변수1';
if (global1 === '전역변수1') {
	let global1 = '지역변수1';
	console.log(global1); // 지역변수1
}
console.log(global1); // 전역변수1
```

```javascript
// 2. 코드블럭
const global2 = '전역변수2';
{
	const global2 = '지역변수2';
	console.log(global2); // 지역변수2
}
console.log(global2); // 전역변수2
```

```javascript
// 3. 함수
const global3 = '전역변수3';
function scope() {
	const global3 = '지역변수3';
	console.log(global3); // 지역변수3
}
scope();
console.log(global3); // 전역변수3
```

또한 가급적 `let` 대신 `const` 키워드를 사용하는 것이 권장되는데, 이는 `const` 키워드로 선언한 변수는 재할당이 불가능하기 때문이다.
따라서 `const` 키워드로 선언한 변수는 의도치 않은 재할당을 방지할 수 있고, 코드의 가독성을 높일 수 있다.
원시값이 아닌 참조타입을 `const` 키워드로 선언하면 재할당이 불가능하지만, 참조값은 얼마든지 변경이 가능하므로 사용에 지장이 없다.
그러므로 의도적으로 재할당이 필요한 경우에만 `let` 키워드를 사용하는 것이 좋다.
