### nullish 병합 연산자

nullish 병합 연산자 ??를 사용하면 짧은 문법으로 여러 피연산자 중 그 값이 `확정되어있는` 변수를 찾을 수 있다.

`a ?? b`

- a가 null도 아니고 undefined도 아니면 a
- 그 외의 경우는 b

<비교 연산자와 논리 연산자만으로 nullish 병합 연산자와 같은 기능을 하는 코드>
`x = (a !== null && a !== undefined) ? a : b;`

```js
let height = 0;

alert(height || 100); // 100
alert(height ?? 100); // 0
```

height || 100은 height에 0을 할당했지만 0을 falsy 한 값으로 취급했기 때문에 null이나 undefined를 할당한 것과 동일하게 처리하여 100을 출력

반면 height ?? 100의 평가 결과는 height가 정확하게 null이나 undefined일 경우에만 100이 되기때문에 0을 출력

### 주의사항

안정성 관련 이슈 때문에 ??는 &&나 ||와 함께 사용하지 못한다.
`let x = 1 && 2 ?? 3;`

제약을 피하려면 괄호를 사용하면 된다.
`let x = (1 && 2) ?? 3;`

```js
// height가 null이나 undefined인 경우, 100을 할당
height = height ?? 100;
```
