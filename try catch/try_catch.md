### try catch
catch는 에러 종류와 관계없이 "JSON Error" 메시지를 보여준다.

이런 문제를 피하고자 다시 던지기 기술을 사용한다.

1. catch가 모든 에러를 받는다.
2. catch(err) {...} 블록 안에서 여러 객체 err를 분석한다.
3. 에러 처리 방법을 알지 못하면 throw err를 한다.

에러는 instanceof로 체크한다.

```js
try{
  user = {};
} catch(err){
  if(err instanceof RequestError){
    console.log('ReferenceError');
  }
}
```