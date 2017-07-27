# script태그의 비동기 실행

> 자바스크립트 태그를 html문서의 head 내에 위치 시키면 웹 브라우저가 외부의 자바스크립트 파일을 불러올 때 스크립트를 내려 받아 해석할 때까지 html의 파싱을 미뤄둔다. 그래서 해당 페이지의 로딩 속도가 지체되는 병목현상이 발생하게 된다. 이러한 문제를 해결하기 위해 등장한 것이 HTML5의 defer과 async 속성이다.



### 일반적인 과정

![일반적](../assets/script-async-defer-1.png)

---

 ### async 속성

HTML구문과 동시에 스크립트를 가져온 후 스크립트가 준비 될 때마다 즉시 실행한다.

실행의 순서가 다운로드 완료 시점에 의해 결정되므로 실행 순서가 중요한 스크립트들은 async 속성을 사용할 때 유의해야 한다.

```html
<script async src="./main.js"></script>
```

![async](../assets/script-async-defer-2.png)

---

### defer 속성

HTML 구문의 해석이 완전히 끝나면 스크립트가 실행되도록 브라우저에 지시한다.

비동기적으로 로드된 스크립트와 마찬가지로 HTML 구문이 해석되는 동안 파일을 다운로드 할 수 있다. 그러나 HTML 구문의 해석이 완료되기 전에 스크립트의 다운로드가 완료 되더라도 구문의 해석이 완료 될 때까지 스크립트는 실행되지 않는다. 

async와 다르게 호출된 순서대로 실행된다.  

```html
<script async src="./main.js"></script>
```

![defer](../assets/script-async-defer-3.png)

---

### 브라우저 지원

* IE는 defer를 부분적으로 지원하고 있으며 async 속성은 10 버전 이상부터 지원한다.
* Firefox는 3.6 버전부터 지원
* chrome은 8 버전부터 지원 