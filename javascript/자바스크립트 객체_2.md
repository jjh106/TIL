# 자바스크립트 객체_2

### # 객체 속성 삭제하기

> delete 연산자를 사용하여 객체에서 특정 속성을 제거할 수 있다.

```javascript
var obj = {name: 'jjh'};
delete obj.name;
```

---

### # 객체가 특정 속성을 가지고 있는지 확인하기

> in 연산자 사용하여 객체의 속성을 확인할 때 프로토타입 체인에서 상속받은 속성까지 포함하지만,
>
> hasOwnProperty 메서드를 사용하면 객체의 속성이 해당 객체 자체의 고유한 것인지 확인할 수 있다.

```javascript
var myObject = {name: 'jjh'};

console.log(myObject.hasOwnProperty('name'))
// true

// 프로토타입 체인에서 상속받은 속성과 비교
console.log(myObject.hasOwnProperty('toString'));
// false
```

---

### # in연산자를 사용해 객체가 주어진 속성을 포함하는지 확인하기

```javascript
var myObject = {name: 'jjh'};

console.log('name' in myObject); 
// true

console.log('toString' in myObject);
// true
```

> in 연산자는 참조한 객체에 포함된 속성은 물론 해당 객체가 프로토타입 체인을 통해서 상속받은 속성까지 확인한다.

---

### # for in 루프를 통해 객체의 모든 속성을 탐색하기

```javascript
var jjh = {
  age: 27,
  gender: 'male',
  living: true
};

for(var key in jjh) {
  console.log(key + ': ' + jjh[key]);
}
/* 
age: 27
gender: male
living: true
*/
```

