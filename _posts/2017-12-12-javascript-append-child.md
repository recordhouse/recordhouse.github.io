---
layout: post
title: "[JavaScript] 자바스크립트 노드 생성 및 추가"
date: 2017-12-12 20:44:40
modified: 2017-12-12 20:44:40
tag: [javascript]
---

# 노드 생성
```javascript
var input = document.createElement('input');
```

# 생성된 노드 속성 추가
```javascript
input.setAttribute('type', 'text');
```

# 텍스트 노드 추가
```javascript
var txt = document.createTextNode('hello');
```

# 부모 노드에 생성된 노드 추가
```javascript
부모노드.appendChild(input);
```

# 예제
위 노드 추가 방법으로 테이블을 추가하는 예제는 아래에서 확인할 수 있다.  
버튼을 계속 클릭하면 테이블이 추가된다.

<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="VwBzezZ" data-user="recordboy" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/recordboy/pen/VwBzezZ">
  노드 추가</a> by recordboy (<a href="https://codepen.io/recordboy">@recordboy</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

## References
[HTML DOM appendChild() Method](https://www.w3schools.com/jsref/met_node_appendchild.asp)
