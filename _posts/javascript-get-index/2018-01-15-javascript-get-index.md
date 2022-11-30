---
layout: post
title: 바닐라 자바스크립트로 인덱스 구하기
date: 2018-01-15 21:28:59
modified: 2018-01-15 21:28:59
tag: [javascript, vanillajs]
---

제이쿼리의 `index()`를 바닐라 자바스크립트로 구현하는 방법이다.

## HTML
```html
<ul id="ul">
    <li>0</li>
    <li>1</li>
    <li>2</li>
    <li>3</li>
</ul>
```

## javascript
```javascript
var ul = document.getElementById('ul'),
    li = ul.getElementsByTagName('li');
for (var i = 0; i < li.length; i++) {
    (function(idx) {
        li[idx].onclick = function() {
            alert(idx);
        }
    })(i);
}
```

## 결과
아래 리스트 요소를 클릭하면 인덱스가 `alert`에 출력되는 것을 확인할 수 있다.

<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="VwdBNdV" data-user="recordboy" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/recordboy/pen/VwdBNdV">
  Untitled</a> by recordboy (<a href="https://codepen.io/recordboy">@recordboy</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

<!-- <style>
#ul {
    margin: 0;
    padding: 0;
    list-style: none;
}
#ul > li {
    border-radius: 5px;
    padding: 2px 10px;
    width: 50px;
    text-align: center;
    cursor: pointer;
    background-color: #ccc;
    color: #fff;
}
#ul > li:hover {
    background-color: #333;
}
</style>

<ul id="ul">
    <li>0</li>
    <li>1</li>
    <li>2</li>
    <li>3</li>
</ul>
<script>
var ul = document.getElementById('ul'),
    li = ul.getElementsByTagName('li');
for (var i = 0; i < li.length; i++) {
    (function(idx) {
        li[idx].onclick = function() {
            alert(idx);
        }
    })(i);
}
</script> -->
