### String()

```javascript
// new 키워드와 String() 생성자
var stringObject = new String('foo');
console.log(stringObject); // foo {0 = 'f', 1 = 'o', 2 = 'o'}
console.log(typeof stringObject) // 'object'

// new 키워드 없이 생성자만 사용해 리터럴 문자열을 만든다.
var stringObjectWithOutNewKeyword = String('foo');
console.log(stringObjectWithOutNewKeyword); // 'foo'
console.log(typeof stringObjectWithOutNewKeyword) // 'string'

// 리터럴 문자열
var stringLiteral = 'foo';
console.log(stringLiteral); // 'foo'
console.log(typeof stringLiteral); // 'string'
```



#### # String 객체 인스턴스의 속성과 메서드

##### 인스턴스 속성

* constructor
* length

##### 인스턴스 메서드

* charAt()
* charCodeAt()
* concat()
* indexOf()
* lastIndexOf()
* lacalCompare()
* match()
* quote()
* replace()
* search()
* slice()
* split()
* substr()
* substring()
* toLocaleLowerCase()
* toLocaleUpperCase()
* toLowerCase()
* toString()
* toUpperCase()
* valueOf()


