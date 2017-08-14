### JSON Text => JSON Object

*JSON Text를 자바스크립트에서는 Object가 아닌 그냥 텍스트로 인식하기 때문에 이것을 Object로 바꾸어야*

*그 값을 불러 사용할 수 있다.*

---

**JSON.parse()**

* json 포멧의 string을 json객체로 변환시킨다.

* ```javascript
  // 문자열 타입을 Number 타입으로 변환
  var result = JSON.parse("123");
  console.log(result);  // 123
  console.log(typeof result);  // number

  // 문자열 "true"를 boolean 타입으로 변환
  // 대문자 x 
  console.log(JSON.parse("true")); // true
  console.log(typeof JSON.parse("true")); // boolean

  // 문자열 "[]" => 배열 오브젝트로 변환
  console.log(JSON.parse('[]')); // []
  console.log(Array.isArray(JSON.parse("[]"))); // true

  // "ABC" 처럼 값에 큰따옴표 사용 시 배열은 '[]'같이 작은따옴표 사용
  result = JSON.parse('["ABC", "가나다"]');
  for( var i=0; i<result.length; i++ ){
    console.log(result[i]); // abc 가나다
  }

  // Object 타입으로 변환하고 for ~ in
  var result = JSON.parse('{"sport": "soccer"}');
  for( var name in result ){
    console.log('name:' + name + ', value:' + result[name]);
  }
  ```


---

**JSON.stringify()**

* json객체를 json 포멧의 string로 변환시킨다.

* ```javascript
  var result = JSON.stringify(123);
  console.log(result); // 123
  console.log(typeof result); // string

  console.log(JSON.stringify([Infinity, NaN, null])); // [null, null, null]

  // true, false는 값은 변하지 않고 문자열로 변환
  console.log(JSON.stringify([true, false])); // [true, false]

  // 파라미터에 직접 undefined로 작성하면 문자열 "undefined"로 변환
  console.log(JSON.stringify(undefined));

  // 배열에 작성하면 문자열 "null"로 변환
  console.log(JSON.stringify([undefined]));

  // 프로퍼티 값으로 작성하면 프로퍼티(이름:값)를 제외시킴
  console.log({sport: undefined}); // {}

  // []는 문자열로 변환
  // [] 내부의 작은따옴표는 큰따옴표로 변환
  console.log(['ABC', '가나다']); // ["ABC", "가나다"]

  // 'soccer'에서 작은따옴표가 큰따옴표로 변환
  // 문자열 타입의 프로퍼티 이름과 값이 큰따옴표안에 작성
  // 프로퍼티 값이 숫자, true, false, null은 변환하지 않는다.
  console.log(JSON.stringify({sport: 'soccer', player: 11})); // {"sport": "soccer", "player": 11}
  ```

---

#### Example

```javascript
var data = {
  Name: "jjh",
  Age: 27,
  Job: "developer"
}

var jsonStr = JSON.stringify(data);

console.log(jsonStr);
// String으로 만들기
// { "Name": "jjh", "Age": 27, "job": "developer" }

var jsonObj = JSON.parse(jsonStr);
console.log(jsonObj);
// Object로 만들기
// { Name: "jjh", Age: 27, Job: "developer" }
```

