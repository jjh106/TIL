### for ~ in & for ~ of

*forEach는 간단하지만 break를 이용해 루프를 중단하거나 return을 이용해 함수를 벗어날 수 없다.*

#### 예제1

```javascript
let userName = ['홍길동', '김삿갓', '변사또'];
```

##### for ~ in

```javascript
for( let value in userName ){
  console.log(value);
}
// 0
// 1
// 2
```

>0,1,2의 타입은 number가 아닌 string
>
>즉 for ~ in을 사용하여 반복하였을 경우 나오는 결과로 연산을 하면 올바른 결과가 나오지 않는다.

##### for ~ of

```javascript
for( let value of userName ){
  console.log(value);
}
// 홍길동
// 김삿갓
// 변사또
```

> for ~ of의 경우 userName의 값인 홍길동,김삿갓,변사또가 반환된다.

---

#### 예제2

```javascript
let userInfo = {
  'name': '홍길동',
  'age': 52,
  'gender': '남자'
};
```

##### for ~ in

```javascript
for( let value in userInfo ){
  console.log(value);
}
```

> key값이 출력

```javascript
for( let value in userInfo ){
  console.log(value[key]);
}
```

> value값에 접근하기 위해서는 value[key]처럼 쓴다. 

---

for ~ in의 단점

* 프로토타입 체인도 순회를 한다.
* 객체의 문자열 key를 순회하기 위한 문법으로 Array를 다루는 데는 유용하지 않음.

for ~ of

* break, continue, return과 함께 사용 가능.
* 배열의 요소들, 즉 data를 순회하기 위한 구문.

