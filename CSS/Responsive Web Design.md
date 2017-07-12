# Responsive Web Design

반응형을 만들 때마다 야무샘 PDF를 보는 것도 귀찮아졌다.. 왜 계속 까먹지 ㅠㅠ 

손에 익혀서 눈 감고도 만들 수 있을 때까지 빠르게 보기 위해 작성해 놓자!!

### # 반응형 제작 시 고려사항

* 콘텐츠 전략
  * 각 뷰에 그려질 콘텐츠 구조를 사전에 분석한다.
  * 우선적으로 보여져야 할 콘텐츠가 무엇인지 고민한다.
* 유연한 그리드 레이아웃
  * 고정 그리드를 기반으로 상대적인 수치를 도출한다.
  * 픽셀이 아닌 상대 단위를 사용한다.
    * Target : context = results

---

### # 레이아웃 구현

* flexible box
  * 컨테이너 사이즈에 따라 유연하게 대응하는 flex를 이용한 레이아웃.
  * IE환경에서 완벽히 호환되지 않기 때문에 사용에 주의
* grid layout
  * 화면을 구성하는 컨텐츠를 일정한 비율로 배치하여 레이아웃을 구성하는 방법.
  * 그리드 레이아웃 제너레이터 [http://gridinator.com/](http://gridinator.com/)

---

### # 유연한 이미지

이미지를 포함하는 컨테이너 요소의 폭에 맞춰 크기가 변경되는 이미지.

**content image**

```css
.img {
  width: 100%;
  height: auto;
}
```

**background image**

```css
.img {
  width: 100%;
  padding-bottom: 66.66667%;
  background-image: url(img/image-1440x960.jpg);
  background-size: cover;
}
```

> padding-bottom은 image의 세로/가로 * 100으로 계산.

---

### # 재단 이미지

이미지를 포함하는 컨테이너 요소의 폭에 맞춰 크기가 동적으로 잘려지는 이미지.

**background image**

```css
.img {
  width: 100%;
  height: 960px;
  background-image: url(img/image-1440x960.jpg);
  background-position: center top;
  background-size: cover;
}
```

```css
.img-container {
  position: relative;
  height: 120px;
}

.img-content {
  position: absolute;
  left: 50%;
  width: 100%;
  height: auto;
  transform: translateX(-50%);
}
```

---

### # 유연한 아이프레임

```css
.container {
  position: relative;
  padding-bottom: 56.25%;
  height: 0;
  overflow: hidden;
  max-width: 100%;
}

.container iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
```

> 4:3 = 75% , 16:9 = 56.25% , 21:9 = 42.857142857%  

---

### # 미디어쿼리

```css
@media only all and (조건문) {실행문}
```

> break point를 설정하여 조건문에 삽입하여 사용한다.