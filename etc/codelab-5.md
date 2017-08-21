* **빌트인 Function 오브젝트**
  * Function.prototype.call(){}


* **function 오브젝트**
  * function book(){}


* **function 인스턴스**
  * new Book()
  * Book.prototype


* function 키워드를 만나면 빌트인이 book객체를 만든다.
* **빌트인**으로 **function오브젝트**를 만들고 그것으로 **인스턴스**를 생성한다.

---

#### Function 오브젝트

* 엔진이 function 키워드를 만나면 빌트인 Function 오브젝트의 prototype에 연결된 프로퍼티로 Function 오브젝트( var sports = function(){}; ) 생성

  얘도 인스턴스이다. but 구분안되니 걍 펑션오브젝트로..

* 생성한 오브젝트를 sports 변수에 할당

  * sports함수호출
  * Function오브젝트이므로 호출 가능.

---

#### 오브젝트 저장

호출하기 위해선 생성한 Function 오브젝트 저장 필요

오브젝트 저장 형태

* function 키워드로 생성한 Function 오브젝트를 { name: value } 형태로 저장
* { sports: Function오브젝트 }

함수 호출

* 함수 이름으로 저장된 오브젝트 검색
* value 값을 구하고 value가 Function 오브젝트이면 호출.

Function 오브젝트 생성순서, 방법

```javascript
sports: { 
  prototype: { constructor: sports },
              __proto__: { constructor: function Object(){},
                           hasOwnProperty: ,........ }
  __proto__: { apply, bind, call, constructor  }
}
```

1. Function 오브젝트 생성

   {코드} function sports(){}

   sports는 생성한 Function 오브젝트 이름

   오브젝트 타입이 "function"이며 빈 오브젝트

   지금부터 빈 오브젝트를 채운다.

2. sports 오브젝트에 prototype 오브젝트 첨부

3. prototype에 constructor 프로퍼티 첨부

4. prototype.constructor에서 sports 오브젝트 전체를 참조할 수 있도록 설정

5. prototype에 __ proto __오브젝트 첨부

6. 빌트인 Object 오브젝트의 prototype에 연결된 프로퍼티로 Object 인스턴스를 생성하여 prototype.__ proto __에 첨부

7. sports오브젝트에 __ proto __ 오브젝트를 첨부

8. 빌트인 Function 오브젝트의 prototype에 연결된 프로퍼티로 Function 인스턴스 생성

9. 생성한 Function 인스턴스를 sports.__ proto __에 첨부

10. sports 오브젝트 프로퍼티에 초기값 설정

---

#### 실행 환경(파라미터, 함수블록 내부의 코드) 인식

* 인식 필요성
  * 함수가 호출되었을 때 실행될 환경을 인식할 수 있어야 실행 환경에 맞추어 실행 가능.
* 실행 환경 설정 시점
  * Function 오브젝트를 생성하는 시점에 환경 설정
  * ex: 함수에 작성한 코드, 파라미터, 실행 영역 등
  * Function 오브젝트를 생성하고 바로 실행하는 것이 아니므로 함수가 호출되었을 때 사용할 수 있도록 환경 저장 필요
* 어디에 저장하는가?
  * 생성한 Function 오브젝트에 저장
  * {name: value} 형태
  * 인식한 환경을 Function 오브젝트의 내부 프로퍼티에 설정

---

#### 내부 프로퍼티

엔진이 내부처리에 사용하는 프로퍼티

[[]]형태, 예 : [[scope]]

---

프리컴파일 언어(컴파일한 후 실행)는 function키워드를 보고 function 내부로 들어가 컴파일하지만 자바스크립트는 

호출 시에 컴파일한다. 

프리컴파일언어는 사전에 오류를 감지하는 장점이 있지만 반복적인 컴파일을 한다는 단점이 있음.

---

#### 코드해석 단계

1. 함수 선언문 해석

2. 변수 초기화

   var sports;

   var member;

3. 자바스크립트 코드 실행

   var sports = function() {};

   var member = 123;

   ​

함수선언문을 먼저 해석하고 그 다음 함수표현식을 해석한다.

```javascript

	function sports(){
		debugger;
		var player = 11;

		function soccer(){
			return player;
		};
		var baseball = function(){};
		soccer();
	};
	sports();
```

1. player 변수 선언

   var player = 11;

2. 함수 선언문 작성

   function soccer(){ return player; }

3. 함수 표현식 작성

   var baseball = function(){};

4. soccer호출

   soccer();

##### 처리 순서

1. 마지막 줄에서 sports 함수를 호출하면 두 번째 줄의 debugger에서 실행 stop
2. player와 baseball 값은 undefined이고 soccer는 function soccer(){}이다.
3. 첫 번째 줄에서 멈추었는데 soccer에 Function 오브젝트가 설정된 것은 function soccer(){}문장을 해석한 것을 의미함.
4. 또한 player와 baseball에 설정된 undefined도 값이며 해석한 것을 의미함. 해석하지 않았다면 player와 baseball 자체가 표시되지 않는다.
5. baseball은 현재 변수만 선언된 상태이다.



함수선언문을 찾다 function soccer(){};를 발견하고 Function 오브젝트를 생성한다. 

더이상 함수선언문이 없으므로 함수의 처음으로 돌아간다.

변수 선언만 모두 하고 한 번 돌고 난 다음 다시 돌 때 변수 초기화 해주고 세 번째 돌 때 실행한다.

두 번째 돌 때 함수표현식은 Function 오브젝트가 생성된다(처음에 생성x)



**정리**

함수 선언문 먼저 찾음

변수 선언을 모두 한다 => 값은 undefined (이미 같은 이름으로 function오브젝트가 있다면 언디파인드 x 그냥 선언)

두 번째 돌 때 변수 선언만 해준다.

세 번째에 실행하면서 변수에 값 초기화.( 함수표현식은 이 때 Function 오브젝트 생성하여 이제 호출 가능)

##### 호이스팅

```javascript
function sports(){
  baseball();
  
  function baseball(){
    console.log("야구");
  };
}
sports();
```

1. baseball 함수 앞에서 baseball()을 호출하지만
2. 함수를 호출하기 전에 함수 선언문을 Function오브젝트로 생성했으므로 호출 가능.

---

#### 함수선언문 오버라이딩

함수 이름이 같을 때 함수 코드 대체

자바스크립트는 파라미터 수, 데이터 타입 체크하지 않음

{key: value}로 저장하기 때문에

```javascript
function sports(){
  function soccer(){
    console.log('축구1');
  };
  soccer();
  function soccer(){
    console.log('축구2');
  };
};
sports();
```

마지막 soccer이 대체된다. 축구2 출력

---

#### 함수 파라미터

**파라미터 값 처리**

* 호출한 함수에서 보낸 값을 호출받는 함수의 파라미터에 작성한 순서에 맞춰 매핑
* 호출된 함수의 파라미터 이름이 아닌 순서가 기준! 

**arguments**

호출한 함수의 파라미터 값 저장

호출한 함수의 파라미터에 작성한 순서로 저장

호출한 함수에 파라미터를 작성하지 않아도 생성

arguments 장단점

* 파라미터 수가 고정일 때
  * 파라미터 이름 사용
* 파라미터 수가 유동적일 때
  * arguments 사용
  * 함수 파라미터에 이름이 있으면 값 설정
  * 즉, 파라미터와 arguments에 모두 설정

```
var get = function(qty, price){
  var amount;
  if(qty !== undefined && price !== undefined) {
    
  }
}
```



**length 프로퍼티**

* 호출한 함수의 파라미터 수
  * get(1,2,3) : 3개
  * get([4,5], 6) : 2개
  * 콤마 기준으로 구분
  * 배열 전체가 파라미터 1개
* 사용형태
  * arguments.length
* Array-like



**arguments 값 반환**

* 호출한 함수의 파라미터 값 작성 형태
  * 문자열,숫자,배열,오브젝트 등
* arguments 매커니즘
  * 파라미터 순서를 0부터 인덱스를 부여하여 key로 사용
  * 파라미터로 받은 값을 value에 설정
  * {0: value, 1: value}
* 결론 : for문 사용
  * 파라미터가 배열일 때 for~in문 사용

---

#### 스코프!

함수가 실행되는 영역

함수가 실행될 때 영향을 받는 범위

split의 스코프

split는 String 오브젝트에 존재하므로 String오브젝트가 스코프이다.

Number 오브젝트에는 split()를 호출하면 에러 발생(없기 때문에)



**사용목적**

* 범위제한
  * 신속한 검색/접근
* 같은 프로퍼티 이름 사용 가능
  * String의 indexOf( )
  * Array의 indexOf( )



**스코프의 구조**

계층적 구조

* 스코프 설정 시점
  * Function 오브젝트를 생성할 때
  * 함수를 호출할 때 설정하지 않는다.
  * function 안의 코드에 대해서는 구조를 만들지 않음.
* 스코프 구조 형성 방법
  * 밖에서 안으로 들어가면서 스코프 구조 형성
  * 안에서 밖으로 나가면서 스코프 범위 검색

```javascript
function sales(){
  function get(){
    function discount(){};
    discount();
  };
  get();
};
sales();
```

1. 엔진이 첫 번째 줄의 sales를 만난다

2. sales Function 오브젝트를 생성하고 스코프를 설정

   Function 오브젝트 내부 프로퍼티인 [[scope]]에 스코프를 설정

3. sales 함수 안으로 들어가지 않고 아래로 내려간다.(중요한 js매커니즘)

   함수 코드를 Function 오브젝트의 [[code]]에 설정하며 함수 안의 코드를 해석하지 않음

4. 마지막 줄의 sales()를 만나 sales함수를 호출!

5. 엔진이 sales 함수 안으로 이동

6. sales 함수 안의 첫 번째 줄부터 해석하며 function get(){}을 만난다.

7. get Function 오브젝트를 생성하고 Funtion 오브젝트의 [[scope]]에 스코프 설정

8. get 함수 안으로 들어가지 않고 내려간다.

9. get()을 만나 get함수 호출

10. 엔진 제어가 get 함수 안으로 이동

11. get 함수 안의 첫 번째 줄부터 해석하게 되며 function discount 만난다.

12. discout Function 오브젝트 생성하고 스코프를 [[scope]]에 설정

13. discount 함수안으로 들어가지 않고 내려간다.

14. discount()를 만나 discount함수를 호출



**글로벌 오브젝트**

* 프로그램의 시작점
* 특성
  * 전체 프로그램을 통해 하나만 존재
  * 오브젝트 이름을 작성하지 않고 함수를 호출하면 글로벌 오브젝트로 간주
* 글로벌 오브젝트 생성
  * 첫 번째 <script>에서 한 번만 생성
  * 자바스크립트 실행 환경 설정
  * <script>의 프로그램 실행 전에 생성



**글로벌 스코프**

글로벌 오브젝트 = 글로벌 스코프

최종 검색 스코프

검색한 스코프가 없으면 undefined 반환

스코프 설정

* Function 오브젝트의 [[scope]]에 설정

 

**글로벌 함수**

* 함수 구분
  * 글로벌 함수: 전역함수
  * 로컬함수: 지역함수
* 글로벌 함수
  * 글로벌 오브젝트에 작성한 함수
* 지역함수
  * 함수 안에서 var 키워드를 사용한 함수와 함수 선언문
  * 함수 안에서 var 키워드를 사용하지 않으면 글로벌 함수
  * strict 모드일 때 var를 사용하지 않고 함수를 선언하면 에러
  * 글로벌 오브젝트에서 var 키워드를 사용하여 함수 선언 가능
* 권장
  * 글로벌, 지역에 관계없이 함수표현식 함수는 var 사용



**바인딩**

구조적으로 결속된 상태로 만드는 것

대상 : 오브젝트와 프로퍼티 이름

```javascript
var get = {
  qty: value,
  price: value
};
```

* 바인딩 목적
  * 스코프 결정
  * 스코프에서 이름 식별 => 식별자 해결이라고 함.
* 바인딩 시점 분류
  * 정적 바인딩(렉시컬 바인딩)
    * 초기화 단계에서 바인딩
    * 함수 선언문 이름 바인딩
    * 변수, 함수 표현식 이름 바인딩
    * 값은 바인딩 대상이 아님
    * 대부분 정적 바인딩
  * 동적 바인딩(다이나믹 바인딩)
    * 실행단계에서 바인딩
    * eval함수, with문



**스코프 체인**

근접한 스코프에서 프로퍼티(함수,변수) 검색

ES5에서 scope chain 개념 폐지

* 렉시컬 환경 개념 사용



**프로퍼티 검색 방법**

* [[scope]] 프로퍼티에서 검색
  * 함수를 실행할 때 [[scope]]에서 프로퍼티 이름으로 검색
* 프로퍼티 검색을 위한 추가 처리 필요하지 않음
  * Function 오브젝트 생성할 때 정적으로 바인딩 하였기 때문에
* 처리속도에 영향 x

---

#### 렉시컬 환경

**실행 컨텍스트**

* 함수의 실행 영역
* 함수 코드를 실행하고 실행 결과를 저장

