### 호이스팅(Hoisting)

*대부분의 프로그래밍 언어와는 달리 자바스크립트는 block-level scope를 가지지 않는다.*

*대신, 자바스크립트는 function-level scope를 가진다. 함수 내에 정의된 변수는 지역 범위를 가지며*

*해당 함수와 내부함수에서만 접근이 가능하다.*



*호이스팅은 변수의 정의가 그 범위에 따라 선언과 할당으로 분리되는 것을 의미한다.* 

*즉, 변수가 함수 내에서 정의 되었을 경우 선언이 함수의 최상위로, 함수 바깥에서 정의되었을 경우*

*전역 컨텍스트의 최상위로 끌어 올려진다.*



```javascript
function hoisting() {
	console.log(value); // undefined
	
   	var value = 10;
	
   	console.log(value); // 10
}

hoisting();
```

```javascript
function hoisting() {
	var value;
  
  	console.log(value); // undefined
  
  	value = 10;
  
  	console.log(value); // 10
}

hoisting();
```

> 변수 선언문이 함수범위의 최상단으로 끌어 올려지고 선언문이 있던 자리에서 초기화가 이루어진다.
>
> 첫 번째 호출에선 초기화가 되지 않았기 때문에 undefined가, 두 번째 호출에서는 초기화가 된 10이 나온다.



#### 호이스팅은 함수선언문에서만 나타난다.

```javascript
hoisting();

function hoisting() {
  var value = 10;
  console.log(value); // 10
}
```

```javascript
hoisting();

var hoisting = function() {
  var value = 10;
  console.log(value);
}
// Uncaught TypeError: hoisting is not a function
```

> 함수표현식을 통한 정의는 변수에 함수를 초기화 시키기 때문에 선언문이 호이스팅이 되어 올려진다 해도
>
> 함수가 아닌 변수로 인지하기 때문이다.