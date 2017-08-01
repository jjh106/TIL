### 클로저

* 외부함수의 변수에 접근할 수 있는 내부함수를 일컫는다.(or 함수 내에서 또 다른 함수를 정의할 때)
* 외부함수의 변수뿐만 아니라 파라미터(매개변수)에도 접근할 수 있다.
* 단, 외부함수의 arguments객체를 호출할 수 없다.
* 외부함수에서 내부함수를 참조할 수 없다.
* 외부 함수가 종료된 이후에도 내부함수를 통해 접근할 수 있다.
* 클로저는 세 가지 스코프 체인을 가진다.
  * 클로저 자신에 대한 접근
  * 외부함수의 변수에 대한 접근
  * 전역변수에 대한 접근

---

```javascript
function movie(title) {
  return {
    get_title: function() {
      return title;
    },
    set_title: function(_title) {
      title = _title;
    }
  }
}

avengers = movie('토르');
avengers.get_title(); // 토르

dcComics = movie('슈퍼맨');
dcComics.get_title(); // 슈퍼맨
------------------------------------------
avengers.set_title('헐크');
avengers.get_title(); // 헐크

dcComics.set_title('배트맨');
dcComics.get_title(); // 배트맨
```

> * avengers와 dcComics는 같은 객체이지만, 그 객체가 가지고 있는 get_title 메소드가 접근하는 title이라 하는 이 외부함수의 매개변수가 서로 다르다.
> * title은 pirvate variable이다. movie함수가 어떤 값을 리턴했을 때 종료되어 그 지역변수인 title은 get_title과 set_title 메소드를 통해서만 접근이 가능한 변수가 된다.
> * 그렇다면 왜 private variable가 필요한가? why!!?
>   * 프로젝트가 커지다보면 많은 사람이 코드를 작성하게 되고 많은 데이터가 존재하는데 그럴 경우 데이터가 누구나 쉽게 수정 가능하게 된다. 그렇게 되면 프로젝트가 망가질 가능성이 크다. 때문에 private variable를 사용해 내부 메소드를 통해서만 접근이 가능하게 하면 안전하게 사용 가능하다. 클로저는 자바스크립트가 private variable를 사용할 수 있도록 도와주는 아주 좋은 매커니즘이다.

