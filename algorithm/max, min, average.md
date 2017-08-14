### max, min, average

*양재동 코드랩 강의 중 자바스크립트 내장객체인 Math를 다루며 문제를 풀어 보았다.*

#### 진행 순서

1. 난수 10개를 발생시킨다.
2. 최대값과 최소값을 구한다.
3. 10개의 평균을 구한다.

---

#### 1. 난수 발생

```javascript
var arr = [];
for( var i=0; i<10; i++ ){
  var num = Math.random();
  arr.push(num);
}
```

> 1. 빈 배열을 만든다.
> 2. 반복문 내부에서 Math.random을 사용하여 10개의 난수를 만든다.
> 3. push메서드를 사용하여 배열에 하나씩 넣어준다.

#### 2. 최대값, 최소값 구하기

```javascript
var maxNum = Math.max.apply(null, arr);
```

```javascript
var minNum = Math.min.apply(null, arr);
```

> apply의 메서드 빌려쓰기를 이용해 최대값과 최소값을 구한다.

#### 3. 평균구하기

```javascript
var averageNum = arr.reduce( (a,b) => a + b/arr.length );
```

> array의 reduce를 사용하여 배열 내부의 수를 모두 더해주고 length만큼 나누어 평균을 구한다.