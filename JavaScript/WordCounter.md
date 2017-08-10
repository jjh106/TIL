## WordCounter

```javascript
// 웹페이지의 모든 텍스트를 찾는다.
var entireText = document.querySelector('body').innerText;

// 공백을 기준으로 짤라 단어로 만든다.
var splitText = entireText.split(' ');

// 단어의 사용 횟수 찾는다.
var countText = {};
for( var i=0; i<splitText.length; i++ ){
  var word = splitText[i].toLowerCase();
  if( countText[word] === undefined ){
    countText[word] = 1;
  } else {
    countText[word] = countText[word] + 1;
  }
}

// 정렬
var countTextArr = [];
for( name in countText ){
  countTextArr.push([name, countText[name]])
}
countTextArr.sort(function(a, b){
  return a[1] - b[1];
})

// 출력
for( var i=0; i<countTextArr.length; i++ ){
  console.log(countTextArr[i][0], countTextArr[i][1]);
}
```

