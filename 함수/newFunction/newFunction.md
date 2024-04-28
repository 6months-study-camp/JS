함수 표현식과 함수 선언문 이외에 함수를 만들 수도 있는 방법이 하나 더 있다.

```js
let func = new Function([arg1, arg2, ...argN], functionBody);

let sum = new Function("a", "b", "return a + b");

alert(sum(1, 2)); // 3
```

new Function을 이용해 함수를 만들면 함수의 [[Environment] 프로퍼티가 현재 렉시컬 환경이 아닌 전역 렉시컬 환경을 참조한다.
new Function을 이용해 만든 함수는 외부 변수에 접근할 수 없고, 오직 전역 변수에만 접근할 수 있다.

```js
function getFunc() {
  let value = "test";

  let func = new Function("alert(value)");

  return func;
}

getFunc()(); // ReferenceError: value is not defined
```
