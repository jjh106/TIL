### modal - only css

```html
<p>메인 콘텐츠입니다. Lightbox를 표시하려면<a href="#open">여기</a>를 클릭하십시오.</p>
<div class="white_content" id="open">
  <div>
    <p>Lightbox 콘텐츠입니다. <a href="#close">닫기</a></p>
  </div>
</div>
```

```css
.white_content {
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    background: rgba(0, 0, 0, 0.8);
    opacity:0;
    -webkit-transition: opacity 400ms ease-in;
    -moz-transition: opacity 400ms ease-in;
    transition: opacity 400ms ease-in;
    pointer-events: none;
}
.white_content:target {
    opacity:1;
    pointer-events: auto;
}
.white_content > div {
	position: absolute;
	top: 25%;
	left: 25%;
	width: 50%;
	height: 50%;
	padding: 16px;
	border: 16px solid orange;
	background-color: white;
	overflow: auto;	
}
```

