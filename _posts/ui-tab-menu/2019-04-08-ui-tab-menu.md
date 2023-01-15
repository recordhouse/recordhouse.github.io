---
layout: post
title: "[UI] 탭메뉴(tab menu)"
date: 2019-04-08 08:36:59
modified: 2019-04-08 08:36:59
tag: [ui, javascript, vanillajs]
---

# 설명
vanillaJS로 제작된 기본 탭 메뉴

# 구현
<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="rgZdPe" data-user="recordboy" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/recordboy/pen/rgZdPe">
  [VanillaJs] 탭 메뉴</a> by recordboy (<a href="https://codepen.io/recordboy">@recordboy</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

# HTML
```html
<div id="tab">
    <div class="btn">
        <button type="button">01</button>
        <button type="button">02</button>
        <button type="button">03</button>
        <button type="button">04</button>
    </div>
    <div class="cnt">
        <div>content01 content01 content01 content01 content01 content01 content01 content01 content01 content01</div>
        <div>content02 content02 content02 content02 content02 content02 content02 content02 content02 content02</div>
        <div>content03 content03 content03 content03 content03 content03 content03 content03 content03 content03</div>
        <div>content04 content04 content04 content04 content04 content04 content04 content04 content04 content04</div>
    </div>
</div>
```

# CSS
```css
#tab {
    border: 1px solid #ccc;
    width: 300px;
}

#tab .btn:after {
    content: '';
    display: block;
    clear: both;
}

#tab .btn button {
    float: left;
    border: 0;
    width: 25%;
    height: 30px;
    cursor: pointer;
    outline: none;
    background-color: #ccc;
}

#tab .btn button:hover {
    background-color: #fff;
}

#tab .btn button.on {
    background-color: #fff;
}

#tab .cnt div {
    display: none;
}

#tab .cnt div.on {
    display: block;
}
```

# JavaScript
```javascript
window.addEventListener('load', function(){

    var tab = document.getElementById('tab'),
        btn = tab.getElementsByClassName('btn')[0],
        cnt = tab.getElementsByClassName('cnt')[0],
        index = 0;

    btn.children[0].classList.add('on');
    cnt.children[0].classList.add('on');

    for(var i = 0;i < btn.children.length;i++){
        (function(target){
            btn.children[target].addEventListener('click', function(){
                tabOn(target);
            });
        })(i);
    };

    function tabOn(target){
        for(var i = 0;i < btn.children.length;i++){
            btn.children[i].classList.remove('on');
            cnt.children[i].classList.remove('on');
        };
        btn.children[target].classList.add('on');
        cnt.children[target].classList.add('on');
    }

});
```
