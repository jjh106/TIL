### Rest Parameters

함수 정의 시 매개변수 값 앞에 ... 붙이는 경우

```
function sum(o, ...numbers) {
  return numbers.reduce((s,c) => s + c);
}

sum(2, 3, 5, 610, 21, -102); //537
```

---

### Spread Parameters

함수 실행 시 전달인자 앞에 ... 붙이는 경우

```javascript
function process(...steps) {
  console.log('steps[0]');
  console.log('steps[1]');
}

let lecture = ['css','html'];

process(...lecture);
```

