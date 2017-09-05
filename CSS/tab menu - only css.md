### tab menu - only css

```html
<section class="tab-area">    
  <span id="tab1"></span>
  <span id="tab2"></span>
  <a href="#tab1">tab1</a>
  <a href="#tab2">tab2</a>
  <article class="tab">tab1 content</article>
  <article class="tab">tab2 content</article>  
</section>
```

```css
.tab-area{
  position:relative;
  margin:30px
}
a{
  padding:5px;color:#333;
  text-decoration:none;
  text-transform: uppercase;
  background:#ccc
}
a:hover{
  background:#eee
}
.tab{
  position:absolute;
  left:0;top:26px;
  width:50%;
  padding:1%;
  min-height:100px;
  background:#ddd
}
.tab:nth-of-type(2){
  display:none
}
#tab1:target ~ a:nth-of-type(1),
#tab2:target ~ a:nth-of-type(2),
#tab2:not(:target) ~ a:nth-of-type(1){
  background:#ddd
}
#tab2:target ~ .tab:nth-of-type(2){
  display:block
}
```

