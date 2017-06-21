# CSS variables

JavaScript30을 진행하면서 생소한 것이 있어 찾아보았다.

CSS에서 변수를 사용한 것인데 문제는.. IE에서 당장 사용하기 힘들다는 단점이 있다.

### # 변수 설정

```css
:root {
	--spacing: 10px;
	--blur: 10px;
	--base: #ffc600;
}
```

> 커스텀 속성 정의는 이런식으로 대시 두 개(--)로 한다. 그리고 이 것은 케스케이딩 되기 때문에 :root에
>
> 정의 하는 것이 모든 요소에 변수를 사용하기에 더 용이하다.
>
> * :root란 가상클래스로서 문서의 최상위 루트요소를 나타낸다.(html요소)

---

### # 변수 사용

```css
img {
	padding: var(--spacing);
	filter: blur(var(--blur));
	background: var(--base);
}

.hl {
	color: var(--base);
}
```

> var 표기법을 이용해 변수를 사용한다.



### Refer

#### [CSS 변수 지원율](http://caniuse.com/#feat=css-variables)

