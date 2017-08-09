## addEventListener

```html
<input type="button" class="btn" value="eventBtn">

<script>
  var t = document.querySelector('.btn');
  t.addEventListener('click', function(e){
    alert('Hello world, ' + e.target.value);
  });
  // Hello world, eventBtn
</script>
```

> 첫 번째 인자로 event type을 받는다.
>
> 

#### # 하나의 이벤트 대상에 복수의 동일 이벤트 타입 리스너를 등록할 수 있다.

```html
<input type="button" class="btn" value="eventBtn">

<script>
  var t = document.querySelector('.btn');
  t.addEventListener('click', function(e){
    alert(1);
  });
  t.addEventListener('click', function(e){
    alert(2);
  });
</script>
```

---

#### # 복수의 엘리먼트에 하나의 리스너를 등록하여 재사용 가능.

```html
<input type="button" class="btn1" value="eventBtn1">
<input type="button" class="btn2" value="eventBtn2">

<script>
  var t1 = document.querySelector('.btn1');
  var t2 = document.querySelector('.btn2');
  
  function btnEvent(e) {
    switch(e.target.className) {
      case 'btn1':
        alert(e.target.value);
        break;
      case 'btn2':
        alert(e.target.value);
        break;
    }
  }
  
  t1.addEventListener('click', btnEvent);
  t2.addEventListener('click', btnEvent);
</script>
```

---

#### # Capturing과 Bubbling

```html
</html>
  <body>
    <fieldset>
      <input type="button" id="target" value="target">
    </fieldset>
  </body>
</html>
```

```javascript
function handler(e) {
  var phases = ['capturing', 'target', 'bubbling'];
  console.log(e.target.nodeName, this.nodeName, phases[e.eventPhase-1]);
}
document.querySelector('#target').addEventListener('click', handler, true);
document.querySelector('fieldset').addEventListener('click', handler, true);
document.querySelector('body').addEventListener('click', handler, true);
document.querySelector('html').addEventListener('click', handler, true);

/* INPUT HTML capturing
   INPUT BODY capturing
   INPUT FIELDSET capturing
   INPUT INPUT target */
```

> this.nodeName - 이벤트 핸들러가 호출된 엘리먼트.
>
> e.target.nodeName - 가장 깊은 곳에 있는 엘리먼트.
>
> html -> body -> fieldset -> input 순으로 부모로 부터 자식으로 이벤트가 호출되는 방식은 capturing.



```javascript
document.querySelector('#target').addEventListener('click', handler, false);
document.querySelector('fieldset').addEventListener('click', handler, false);
document.querySelector('body').addEventListener('click', handler, false);
document.querySelector('html').addEventListener('click', handler, false);

/* INPUT INPUT target
   INPUT FIELDSET bubbling
   INPUT BODY bubbling
   INPUT HTML bubbling */
```

>안에서 바깥쪽으로 이벤트가 전파된다.
>
>차이점은 true와 false!! addEventListener의 세 번째 인자로 인해 차이가 난다.
>
>세 번째 인자는 capturing이다. default는 false(즉, bubbling을 사용한다.)



```javascript
function stopHandler(e) {
  var phases = ['capturing', 'target', 'bubbling'];
  console.log(e.target.nodeName, this.nodeName, phases[e.eventPhase-1]);
  event.stopPropagation();
}
```

> 원하는 시점에 이벤트 버블링을 멈추고 싶을 때 stopPropagation(); 적용.

---

#### # Event Type

**form의 submit**

```javascript
var t = document.querySelector('#target'); // form요소를 찾는다.
t.addEventListener('submit', function(e){ // form요소에 이벤트 연결
  if( document.querySelector('#name').value.length === 0 ){ // input요소 찾아서 조건 적용
    alert('Name 필드의 값이 누락 되었습니다.');
    event.preventDefault();
  }
})
```

**change**

```html
<p id="result"></p>
<input id="target">

<script>
  var t = document.querySelector('#target');
  t.addEventListener('change', function(e){
    document.querySelector('#result').innerHTML = e.target.value;
  });
</script>
```

> 인풋 요소에 변화가 주어지고 포커스가 사라지면 적용된다.

*그 외 자주 쓰이는 마우스 이벤트타입*

* click, dbclick, mousedown, mouseup, mousemove, mouseover,mouseout

*키보드와 조합을 위해서는 event.altKey, event.ctrlKey, event.shiftKey를 사용한다.*

*마우스의 포지션을 알기 위해서는 event.clientX, event.clientY를 사용한다.*