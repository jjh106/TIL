# 자바스크립트 객체_1

*자바스크립트에서는 거의 모든 것들이 객체이거나 객체처럼 동작한다.*

### # 객체 만들기

#### 1. 리터럴

> 가장 일반적이고 간편한 방법.

```javascript
var people = {};
people.name = 'Lee';
people.gender = 'male';
people.age = 27;
```

```javascript
var people = {
  name: 'Lee',
  gender: 'male',
  age: 27
};
```

#### 2. Object()

```javascript
var people = new Object();
people.name = 'Lee';
people.gender = 'male';
people.age = 27;
```

#### 3. 생성자 함수

> 속성값이 다른 여러 개의 객체를 만들 때 간편함.
>
> 생성자 함수는 인식을 위해 대문자로 시작한다.

```javascript
function People(name, gender, age) {
  this.name = name;
  this.gender = gender;
  this.age = age;
}

var people_1 = new People('Lee', 'male', 20);
var people_2 = new People('Kim', 'female', 21);
```

---

### # 객체가 특정 생성자 함수의 인스턴스인지 확인하기

> instanceof 연산자를 사용하면 어떤 객체가 특정 생성자 함수의 인스턴스인지 확인 가능 (true or false 반환).

```javascript
// 객체 생성
var Obj_a = function() { this.foo = 'bar'; };

// Obj_a의 인스턴스 생성
var obj_b = new Obj_a();

// true 반환
console.log(obj_b instanceof Obj_a);
```

---

### # 객체의 속성에 접근하기

> 점 표기법 또는 각괄호 표기법을 사용하면 객체의 속성을 얻거나 설정하거나 갱신할 수 있다.

#### 1. 점 표기법

##### 1-1. jjh 객체 생성

```javascript
var jjh = new Object();
```

##### 1-2. 속성 설정 

```javascript
jjh.name = 'Jung';
jjh.age = 27;
jjh.gender = 'male';
```

##### 1-3. 속성의 값 가져오기

```javascript
console.log(
	jjh.name,
	jjh.age,
	jjh.gender
);
// 'Jung 27 male'
```

##### 1-4. 속성 갱신하기

```javascript
jjh.name = 'Lee';
jjh.age = 20;
jjh.gender = 'female';
```



#### 2. 각괄호 표기법

> 속성명이 유효한 자바스크립트 이름이 아니거나 예약어인 경우 각괄호 표기법을 사용한다.
>
> 각괄호 내에 들어가는 속성명은 반드시 문자열이어야 한다.

```javascript
var myObj = {'123':'zero', 'class':'foo'};
// class는 예약어이다.

console.log(myObj['123'], myObj['class']);
// 'zero foo'
```









####  