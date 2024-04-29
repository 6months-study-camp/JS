객체의 프로퍼티는 두 종류로 나뉜다.

- 데이터 프로퍼티
- 접근자 프로퍼티

접근자 프로퍼티의 본질은 함수인데, 이 함수는 값을 획득(get)하고 설정(set)하는 역할을 담당한다.
객체 리터럴 안에서 getter와 setter 메서드는 get과 set으로 나타낼 수 있다.

```js
let soccer = {
  name: "lcfc",
  mark: "fox",

  get fullName() {
    return `${this.name}${this.mark}`;
  },

  set fullName(value) {
    [this.name, this.mark] = value.split(" ");
  },
};

soccer.fullName = "lcfc 0202";

console.log(soccer.fullName);
```

이렇게 getter와 setter 메서드를 구현하면 객체엔 fullName이라는 '가상’의 프로퍼티가 생긴다.
가상의 프로퍼티는 읽고 쓸 순 있지만 실제로는 존재하지 않는다.

접근자 프로퍼티엔 설명자 value와 writable가 없는 대신에 get과 set이라는 함수가 있다.

```js
function User(name, birthday) {
  this.name = name;
  this.birthday = birthday;

  // age는 현재 날짜와 생일을 기준으로 계산된다.
  Object.defineProperty(this, "age", {
    get() {
      let todayYear = new Date().getFullYear();
      return todayYear - this.birthday.getFullYear();
    },
  });
}

let john = new User("John", new Date(1992, 6, 1));

alert(john.birthday); // birthday를 사용할 수 있다.
alert(john.age);
```
