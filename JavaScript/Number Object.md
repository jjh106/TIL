### Number Object

```javascript
var one = Number(123);
console.log(typeof one); // number

var two = new Number(123);
console.log(two); // object

console.log(Number('123')); // 123

console.log('123.456'); // 123.456

console.log(Number(new Number(123))); // 인스턴스를 지정해주면 primitive 값을 반환한다. => 123

Number(null); => null이라는 값을 할당. // 0 반환.

Number(undefined); => 선언만 하고 값을 할당하지 않음. // NaN 반환
```

> 추가
>
> * 문자열의 경우 null은 ""이고 숫자의 경우 0이 빈 값이다.
> * undefined는 자료형이 결정되지 않은 상태.



#### Number() vs parseInt(), parseFloat()

*string 타입의 숫자를 Number 타입으로 변환한다는 공통의 목적을 가진다.*

##### parseInt()

* 글로벌오브젝트에 존재.
  * Number 처리는 모든 오브젝트의 공통 처리가 아님.
  * ES6에서는 Number.parseInt / Number.parseFloat
* "123abc" => 123으로 변환, Number()는 NaN
* **언제 가장 많이 쓰이나?..**
  * DOM에서 width나 height 값을 불러올 때 단위(px)를 제거하기 위해 사용한다.