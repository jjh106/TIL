## DOM API

### 1. innerHTML

#### * innerHTML 특성

- 만약 <div>, <span>, 또는 <noembed> 노드가 (&), (<), (>) 문자를 포함하는 텍스트 노드를 가지고 있다면 innerHTML은 이러한 문자들을 &amp, &lt, &gt로 대체한다. 정확한 복사를 원한다면 Node.textContent 를 사용하면 된다.
- innerHTML은 Method가 아닌 property이다.

```
 element.innerHTML = content;

```

- element의 모든 자식들(하위노드, 즉HTML 코드들)을 제거한다. content의 문자열을 파싱하고, 생성 된 노드를 element의 자식으로 할당한다.
- innerHTML은 무겁고 비싼 대가를 치르는 HTML 해석기를 호출하므로 사용에 주의가 요구된다.
- Element.innerHTML 프로퍼티는 HTML구문의 하위 노드들을 가져오거나, 설정한다.

```
var content = element.innerHTML;

```

- content변수가 return 받는 값은, element의 모든 하위 노드를 설명하는 직렬화된 HTML 코드이다.

```javascript
//문서에서 .demo-innerHTML  대상 찾기
var demo = query('.demo-innerHTML');

//문서에 동적으로 생성할 HTML 코드 문자 유형 데이터
var add_html_string = '<header class="container-header"><h1 class="site-brand" lang="en">Using Dom Script</h1></header>';
//demo 참조 변수에 add_html_string 문자열을 InnerHTML  속성을 사용하여 문서 객체를 해석/생성 한다.
// demo.innerHTML = add_html_string;

//문서에서 .add-HTML-btn 버튼을 찾아 이벤트를 연결해보자.
query('.add-HTML-btn').onclick = function(){
  // demo.innerHTML = add_html_string;
  // 사용자가 입력한 데이터
  // 사용자가 <input> 필드에 입력한 데이터(model) 값을 가져와
  // 아래 변수에 할당하시요.

  var lang = query('#input-language').value || 'ko';
  var heading = query('#input-heading').value || '오늘은 눈인지 비인지..';

  //데이터를 조합할 HTML 템플릿
  var template = '<header class="container-header"><h1 class="site-brand" lang="'+lang+'">'+heading+'</h1></header>';


// template + model(Data) -> view 완성되어 화면에 실제 구현
demo.innerHTML = template;
};
```

#### 1-1. 한줄로 늘어진 markup을 보기가 힘들다면?

1. 변수안에 += 를 해서 한줄씩 마크업을 추가할 수 있음

```javascript
var comp = query('.component');

var comp_input_heading              = '섹션 제목';
var comp_input_heading_placeholder  = '아름다운 우리 강산';
var comp_input_language             = '작성된 언어(스크린리더가 사용할 음성엔진 언어)';
var comp_input_language_placeholder = 'ko';
var comp_button_contnet             = '문서객체 생성';

var comp_complete_html_str='';

comp_complete_html_str += '<div class="input-field" role="group" lang="en">';
comp_complete_html_str += '<div role="group">';
comp_complete_html_str += '<label for="input-heading">'+comp_input_heading+'</label>';
comp_complete_html_str += '<input type="text" id="input-heading" placeholder="'+comp_input_heading_placeholder+'">';
comp_complete_html_str += '</div>';
comp_complete_html_str += '<div role="group">';
comp_complete_html_str += '<label for="input-language">'+comp_input_language+'</label>';
comp_complete_html_str += '<input type="text" id="input-language" placeholder="'+comp_input_language_placeholder+'">';
comp_complete_html_str += '</div>';
comp_complete_html_str += '<button type="button" class="add-HTML-btn">'+comp_button_contnet+'</button>';
comp_complete_html_str += '</div>';

comp.innerHTML = comp_complete_html_str;
```

1. 변수 = [].join(''); 를 통해 멀티라인으로 한꺼번에 넣을 수 있음

- 한줄이 끝나는 부분에는 쉼표
- .join('');을 붙여주면 됨

```javascript
var comp_complete_html_str = [
   '<div class="input-field" role="group" lang="en">',
    '<div role="group">',
      '<label for="input-heading">'+comp_input_heading+'</label>',
      '<input type="text" id="input-heading" placeholder="'+comp_input_heading_placeholder+'">',
    '</div>',
    '<div role="group">',
      '<label for="input-language">'+comp_input_language+'</label>',
      '<input type="text" id="input-language" placeholder="'+comp_input_language_placeholder+'">',
    '</div>',
    '<button type="button" class="add-HTML-btn">'+comp_button_contnet+'</button>',
   '</div>'
].join('');
```

### 1-2. innerText

- css의 영향을 받는다.
- `display:none;`(화면에 보이지 않는) 상태인 텍스트는 가져올 수 없다.(확인필요)
- 안에 있는 텍스트는 가져올 수 없음
- 'textContent' property를 이용하면 모든 텍스트를 반환

### 2. matches

- 비교를 통해 해당조건과 같은지 아닌지 boolean(true/false) 형태로 반환
- IE9 이상 지원함 / IE나 Edge의 경우 msMatchSelector 사용해야함
- 크로스 브라우징을 위해서는 if문으로 브라우저에서 지원하는지 확인을 해야 하는데 for문 안에서 해당 if문을 사용할 경우 반복되는 동안 똑같은 질문을 계속 반복하게 되므로 비효율적임
- 추후 helper 함수등을 통해 문서 처음에 선언해주고 반복되지 않도록 하는 방법 배울 계획

```javascript
var demo_matches          = query('.demo-matches');
var demo_matches_children = demo_matches.children;

// 질문!! demo_matches-target  참조 변수의
// 문서 요소객체는 부모 demo_matches의 몇번째 자식일까요?

for (var m=0; m<demo_matches_children.length; m+=1) {
  var item = demo_matches_children.item(m);
  var matching = null;  //null과 undefined은 false 값
  if ( item.matches ) {
    matching = item.matches('.demo-matches-target');
  } else {
    // MS IE, Edge
    matching = item.msMatchSelector('.demo-matches-target');
  }
  if ( matching === true ) {
    item.setAttribute('style', 'font-weight: 900; letter-spacing: 0.34em;');
  }
}
```

### 3. insertAdjacentHTML()

> 마크업에서 target의 위치를 지정해 html마크업을 추가해줄 수 있다 `beforebegin`,`afterend`옵션은 노드가 문서 트리에 존재하고, 부모 요소노드를 가지 경우에만 동작한다.

- beforebegin : 이전 형제
- beforeend : 마지막 자식
- afterbegin : 첫 번째 자식
- afterend : 다음 형제

*이렇게 외우면 쉽다! begin은 시작 태그를 뜻하여 before는 태그의 앞에 있는 형제요소로 생각하고, after는 시작* *태그의 뒤에 있는 첫 번째 자식요소로 생각하면 된다. end는 마지막 태그로 생각하여 마찬가지로 적용!*

```javascript
var demo_insert_ad = query('.demo-insertAdjacentHTML');

//1. demo_insert_ad 요소노드의 인근에 HTML 코드 삽입
var prev_sibling = '<section class="before-demo-insertAdjacentHTML">이전 형제</section>';
var next_sibling = '<section class="after-demo-insertAdjacentHTML">다음 형제</section>';
var first_child = '<article class="first-child-demo-insertAdjacentHTML">첫번째 자식</article>';
var last_child = '<article class="last-child-demo-insertAdjacentHTML">마지막 자식</article>';

demo_insert_ad.insertAdjacentHTML('beforebegin',prev_sibling);
demo_insert_ad.insertAdjacentHTML('afterbegin',first_child);
demo_insert_ad.insertAdjacentHTML('beforeend',last_child);
demo_insert_ad.insertAdjacentHTML('afterend',next_sibling);
```

```javascript
HTML 결과
<section class="before-demo-insertAdjacentHTML">이전 형제</section>
<div class="demo-insertAdjacentHTML">
<article class="first-child-demo-insertAdjacentHTML">첫번째 자식</article>
  <h1>Insert Adjacent HTML</h1>
  <p>Lorem ipsum dolor sit amet</p>
  <article class="last-child-demo-insertAdjacentHTML">마지막 자식</article>
</div>
<section class="after-demo-insertAdjacentHTML">다음 형제</section>
```

### 3-1 insertAdjacentElement()

> 마크업에서 target의 위치를 지정해 요소(element)를 추가해줄 수 있다

```javascript
//insertAdjacentElement 예제()
var demo_element = query('.demo-insertAdjacentElement')
// <h1>Insert Adjacent HTML</h1>
var h1 = document.createElement('h1');
h1.innerText = 'Insert Adjacent Element';
// <p>Lorem ipsum dolor sit amet</p>
var p = document.createElement('p');
p.innerText = 'Lorem ipsum dolor sit amet.';


demo_element.insertAdjacentElement('beforebegin',document.createElement('figure'));
demo_element.insertAdjacentElement('afterbegin',h1);
demo_element.insertAdjacentElement('beforeend',p);
demo_element.insertAdjacentElement('afterend',document.createElement('span'));
HTML 결과
<figure></figure>
<div class="demo-insertAdjacentElement">
  <h1>Insert Adjacent Element</h1>
  <p>Lorem ipsum dolor sit amet</p>
</div>
<span></span>
```