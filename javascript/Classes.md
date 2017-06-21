# 클래스의 기초

>함수를 기반으로하는 코딩은 코드가 구분없이 작성 되기 때문에 문제 발생 시 코드를 쉽게 찾을 수 없다.
>
>클래스를 이용하면 컴포넌트별로 코드를 작성할 수 있다.

---

#### # 사칙연산 예제

```javascript
function Calculator() {
  this.add = function(a,b) {
    console.log(a+b);
  }
  this.sub = function(a,b) {
    console.log(a-b);
  }
  this.mul = function(a,b) {
    console.log(a*b);
  }
  this.div = function(a,b) {
    console.log(a/b);
  }
}
```

* 사칙연산의 함수들이 Calculator라는 곳에 포장되어 있다.

---

#### # 인스턴스, 프로퍼티, 메서드

* 클래스를 사용하기 위해서는 인스턴스를 생성해야 한다.

```javascript
var class = new Class();
```

* 클래스 내부에서 만드는 변수를 프로퍼티or멤버변수라고 부른다.
* 클래스 내부에서 만드는 함수를 메서드or멤버함수라고 부른다.
* ​

#### # 클래스 내부에 있는 메서드를 호출하는 방법 

* 객체 외부에서 내부에 들어있는 프로퍼티와 메서드에 접근하는 방법은 접근 연산자인 점(.)을 사용해야 한다.
* EX) 인스턴스.프로퍼티 / 인스턴스.메서드( )

---

#### #위의 Calculator 예제에서 add 메서드를 호출해 보자.

##### step 1.

```javascript
var cal1 = new Calculator();
```

##### step 2.

```javascript
cal1.add(10,30);	
```

> 즉 인스턴스 생성 후 접근 연산자를 이용해 호출한다!

---

*클래스에 관한 더욱 자세한 내용은 추후에 학습한 후 작성한다.*

