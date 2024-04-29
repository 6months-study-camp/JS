### call

call 메서드는 모든 함수에 사용할 수 있으며, this를 특정 값으로 지정할 수 있다.

```js
const lsj = {
  name: "이상진",
};

const company = {
  name: "standbylab",
};

// const hiHello = () => {
//   console.log(this.name); // undefined
// };

function hiHello() {
  console.log(this.name); // 이상진
}

hiHello.call(lsj);
```

화살표 함수는 일반 함수와는 다르게 모든 인수에 접근할 수 있게 해주는 유사 배열 객체 arguments를 지원하지 않는다. (화살표 함수는 자신의 this를 바인딩하지 않는다.)
대신에 화살표 함수가 정의된 곳의 외부 컨텍스트의 this를 가져온다.

따라서 hiHello 함수에서 this.name을 호출하면 this는 hiHello 함수가 정의된 컨텍스트가 아니라 상위 컨텍스트를 가리키게 된다.

```js
const lsj = {
  name: "이상진",
};

const company = {
  name: "standbylab",
};

function update(year, occupation) {
  this.year = year;
  this.occupation = occupation;
}

update.call(company, 2024, "company");

console.log(company);

// { name: 'standbylab', year: 2024, occupation: 'company' }
```

### apply

apply는 함수 매개변수를 처리하는 방법을 제외하면 call과 완전히 같다.
apply는 매개변수를 배열로 받는다.

```js
const lsj = {
  name: "이상진",
};

const company = {
  name: "standbylab",
};

function update(year, occupation) {
  this.year = year;
  this.occupation = occupation;
}

update.apply(company, [2024, "company"]);

console.log(company);

// { name: 'standbylab', year: 2024, occupation: 'company' }
```

### bind

함수의 this 값을 영구히 바꿀 수 있다.

```js
const user = {
  name: "Mike",
  showName: function () {
    console.log(this.name);
  },
};

user.showName();

let fn = user.showName;

fn.call(user);
fn.apply(user);

let boundFn = fn.bind({ name: "John" });

boundFn();
fn.call(user);

// Mike
// Mike
// Mike
// John
// Mike
```

fn 함수 자체에만 적용되며 원본 user 객체에는 영향을 주지 않는다.
