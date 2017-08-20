### 문제

numPY함수는 대문자와 소문자가 섞여있는 문자열 s를 매개변수로 입력받습니다.
s에 'p'의 개수와 'y'의 개수를 비교해 같으면 True, 다르면 False를 리턴하도록 함수를 완성하세요. 'p', 'y' 모두 하나도 없는 경우는 항상 True를 리턴합니다.
예를들어 s가 "pPoooyY"면 True를 리턴하고 "Pyy"라면 False를 리턴합니다.

### 풀이

```javascript
function numPY(s){
  let pLength = s.match(new RegExp("p", "ig")).length,
      yLength = s.match(new RegExp("y", "ig")).length;
  
  if( pLength === yLength ){
	return true;
  } else {
    return false;
  }
}

console.log( numPY("pPoooyY") )
```

### 다른 풀이

```javascript
function numPY(s) {
  return s.match(/p/ig).length == s.match(/y/ig).length;
}
```

> 두 조건이 동일하다고 하고 나머지는 모두 false로 리턴되게 하는 한 줄 코드.



length가 0인 경우를 고려하지 않았다.. 만약 p나 y가 없다면 오류가 날듯....