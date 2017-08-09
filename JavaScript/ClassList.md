## ClassList

- 기존에 javascript에서 class를 추가하거나 제거하기 위해 string을 제어했어야 하나 classList로 제어 가능
- 장점 : 기존 JQuery의 주요기능을 기본기능으로 제공하여 가볍고 빠르다.
- 단점 : IE 10+

```javascript
1) add() : 추가
2) remove() : 삭제
3) toggle() : on, off
4) contains() : 목록안에 문자열의 확인 (Boolean value)
  - true - 엘리먼트가 지정된 클레스 명에 포함되어있을경우
  - false - 엘리먼트가  지정된 클래스명이 포함되지 않은경우
```

---

#### 1) add()

```javascript
var element = document.getElementById( 'element' );

element.classList.add( 'someclass' );
element.classList.add( 'someclass1', 'someclass2' );
```

- Helper

```javascript
function addClass(el_node, class_name) {
  // 전달인자 검증(Arguments Validation)
  if ( el_node.nodeType !== 1 ) {
    // 문제가 발생하면, 오류 발생
    throw new Error('첫번째 전달 인자의 유형은 요소노드여야 합니다.');
  }
  if ( typeof class_name !== 'string' ) {
    throw new Error('두번째 전달 인자의 유형은 문자형 이어야 합니다.');
  }
  // HTML DOM 방식
  if ( !hasClass(el_node, class_name) ) {
    el_node.className += ' ' + class_name;
    //el_node.setAttribute('class', class_name);
    //core DOM 방식
    var old_class = el_node.getAttribute('class')
  }
}
```

#### 2) remove

```javascript
var element = document.getElementById( 'element' );

element.classList.remove( 'someclass' );
element.classList.remove( 'someclass1', 'someclass2' );  
```

- Helper

```javascript
function removeClass(el_node, class_name) {
  // [옵션] class_name 값을 사용자가 전달하지 않았을 경우
  if ( !class_name) {
    // el_node.removeAttribute('class');
    el_node.setAttribute('class', '');
  }
  // 해당 클래스 속성 이름이 존재하면 제거
  if ( hasClass(el_node, class_name) ) {
    var old_classes = el_node.getAttribute('class').split(' ');
    for ( var i=0; i<old_classes.length; i++ ) {
      var class_item = old_classes[i];
      if ( class_item === class_name ) {
        old_classes.splice(i, 1);
      }
    }
    el_node.setAttribute('class', old_classes.join(' '));
  }
}
```

#### 3) toggle

- toggle은 인자를 두개를 받을 수 있는데, 처음 인자는 토글링할 class 이름이고 다음 인자는 선택인자로 boolean 타입을 받는다. 이 인자를 true를 설정하면 강제로 class를 추가히고 false로 설정하면 강제로 class를 삭제한다.

```javascript
var element = document.getElementById( 'element' );
element.classList.toggle( 'someclass' );

element.classList.toggle( 'someclass', true );
element.classList.toggle( 'someclass', false );
```

- Helper

```javascript
demo_button.classList.add('demo-button');

demo_button.onclick = function () {
 if ( this.classList.contains('on') ) {
   this.classList.remove('on');
 } else {
   this.classList.add('on');
 }
 // VS
 this.classList.toggle('on');
};
```

#### 4) contains()

```javascript
// classList API 활용
demo_button.classList.add('demo-button');
demo_button.onclick = function() {
  if (this.classList.contains('on')) {
    this.classList.remove('on');
  }
  else {
    this.classList.add('on');
  }
};

var div = document.createElement('div');
var wrapper = document.createElement('div');
wrapper.classList.add('wrapper');

prepend(wrapper, div);
prepend(document.body, wrapper);

wrapper.style.cssText = [
  'position: absolute',
  'top: 200px',
  'left: 200px',
  'width: 500px',
  'height: 500px',
  'padding: 1rem',
  'border: 4px solid lightgray'
].join(';');

div.style.position = 'absolute';
div.style.top = '10px';
div.style.left = '20px';
div.style.width = '300px';
div.style.height = '300px';
div.style.background = '#333';
div.style.boxSizing = 'border-box';

console.log('width: ', window.parseInt(div.style.width, 10));
console.log('height: ', window.parseInt(div.style.height, 10));

div.style.padding = '10px';
div.style.border = '5px solid #32d2ff';

console.log('width | content-box + padding-box:', div.clientWidth);
console.log('height | content-box + padding-box:', div.clientHeight);

console.log('width | content-box + padding-box + border-box:', div.offsetWidth);
console.log('height | content-box + padding-box + border-box:', div.offsetHeight);
```

