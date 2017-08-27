## prototype

#### 프로토타입 체인

자바스크립트는 Function() 인스턴스에 자동으로 prototype이라는 속성을 만든다.

prototype 속성은 new 키워드와 생성자 함수를 같이 사용해서 만든 객체에 연결된다.

인스턴스들은 생성자 함수의 prototype 속성을 통해 공통의 메소드와 속성을 공유하고 상속한다.

```javascript
var myArray = new Array('foo', 'bar');

console.log(myArray.join()); // 'foo, bar'
```

> join() 메서드는 myArray 객체 인스턴스에 정의되어 있지 않은 속성이다.
>
> Array() 생성자의 prototype 속성에 속성으로서 정의되어 있기 때문에 사용이 가능하다.
>
> 배열 객체 인스턴스에는 join() 메서드가 없기 때문에 자바스크립트는 프로토타입 체인에서 join()이라는 메서드가 있는지 검색한다. 즉, 배열 생성자 함수가 만드는 배열 인스턴스마다 동일한 메서드를 일일이 추가할 필요 없이 하나의 join() 함수를 모든 배열에서 가져다 쓰는 것이다.

