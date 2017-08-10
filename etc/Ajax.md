## Ajax

```html
<body>
  <p>time : <span id="time"></span></p>
  <input type="button" id="execute" value="execute">
  <script>
    document.querySelector('input').addEventListener('click', function(e){
      var xhr = new XMLHttpRequest();
      xhr.open('GET', '경로');
      xhr.onreadystatechange = function(){
        if( xhr.readyState === 4 && xhr.status === 200 ){
          document.querySelector('#time').innerHTML = xhr.responseText;
        }
      }
      xhr.send();
    })
  
  </script>
</body>
```

> send() - 통신 시작.
>
> responseText - 서버에서 리턴해준 정보를 담고있는 프로퍼티.



##### xhr.setRequestHeader("content-Type", "application/x-www-form-urlencoded")

*전송한 정보가 마치 html의 form을 통해 전송한 정보인것 처럼 서버에서 인식한다.*



```html
<p id="timezones"></p>
<input type="button" id="execute" value="execute">
<script>
  document.querySelector('input').addEventListener('click', function(e){
    var xhr = new XMLHttpRequest();
    xhr.open('GET', '경로');
    xhr.onreadystatechange = function(){
      if( xhr.readyState === 4 && xhr.status === 200 ){
        var _tzs = xhr.responseText;
        var tzs = _tzs.split(',');
        var _str = '';
        for( var i=0; i<tzs.length; i++ ){
          _str += '<li>' + tzs[i] + '</li>'
        }
        _str = '<ul>' + _str + '</ul>';
        document.querySelector('#timezones').innerHTML = _str;
      }
    }
    xhr.send();
  })
</script>
```

---

#### Ajax + JSON

```html
<p id="timezones"></p>
<input type="button" id="execute" value="execute">
<script>
  document.querySelector('input').addEventListener('click', function(e){
    var xhr = new XMLHttpRequest();
    xhr.open('GET', '경로');
    xhr.onreadystatechange = function(){
      if( xhr.readyState === 4 && xhr.status === 200 ){
        var _tzs = xhr.responseText;
        var tzs = JSON.parse(_tzs);
        var _str = '';
        for( var i=0; i<tzs.length; i++ ){
          _str += '<li>' + tzs[i] + '</li>'
        }
        _str = '<ul>' + _str + '</ul>';
        document.querySelector('#timezones').innerHTML = _str;
      }
    }
    xhr.send();
  })
</script>
```

