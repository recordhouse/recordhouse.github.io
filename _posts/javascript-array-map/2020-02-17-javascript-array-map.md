---
layout: post
title: "[JavaScript] ES5 Array.map"
date: 2020-02-17 18:49:45
modified: 2020-02-17 18:49:45
tag: [javascript, es5]
---

`Array.map` 메서드는 `Array.forEach`와 마찬가지로 배열의 각 요소를 순회하며 콜백 함수를 실행한다. 다만, 콜백에서 리턴되는 값을 배열로 만들어낸다. 원본 배열은 건들지 않고 그 요소들을 사용해서 혹은 약간 변형해서 새로운 배열을 만들어야 할 때 유용하다.

# Parameter
1. 현재 배열 요소의 값
2. 현재 배열 요소의 index
3. 현재 돌고 있는 배열 자체

# 예제
```javascript
var arr = ['a', 'b', 'c'];

//배열의 모든 요소에 NEW라는 문자열을 더하기
//메서드 수행 후 리턴값은 새로운 배열
var newArr = arr.map(function (item, index, array) {
    return item + 'NEW';
});

//메서드 수행 후 원본 배열
console.log(arr);
// ["a", "b", "c"]

//메서드 수행 후 생성된 배열
console.log(newArr);
// ["aNEW", "bNEW", "cNEW"]
```

## 실용적인 예제
<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="poZrEvw" data-user="recordboy" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/recordboy/pen/poZrEvw">
  데이터 가져오기</a> by recordboy (<a href="https://codepen.io/recordboy">@recordboy</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

# References
[[JavaScript] Array 객체에서 놓치기 쉬운 6개의 메서드](https://programmingsummaries.tistory.com/357)  
[자바스크립트 Array map](https://yuddomack.tistory.com/entry/자바스크립트-Array-map)
