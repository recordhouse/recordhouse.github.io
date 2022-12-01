---
layout: post
title: 슬라이드 배너(slide banner)
date: 2019-04-10 08:24:06
modified: 2019-04-10 08:24:06
tag: [ui, vanillajs]
---

vanillaJS로 만들어본 기본 슬라이드 배너

# 조건
- 라이브러리 없이 자바스크립트만 활용
- 다음, 이전 버튼으로 슬라이드 조작 가능
- 인디게이터는 슬라이드 갯수에 맞게 자동으로 생성
- 자동재생, 일시정지 버튼으로 웹 접근성 준수

# 구현
<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="zQJWPr" data-user="recordboy" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/recordboy/pen/zQJWPr">
  [VanillaJs] 슬라이드 배너</a> by recordboy (<a href="https://codepen.io/recordboy">@recordboy</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

# html
```html
<div id="slide">
  <ul class="cnt">
    <li>1</li>
    <li>2</li>
    <li>3</li>
    <li>4</li>
  </ul>
  <div class="btn">
    <button type="button" class="prev">prev</button>
    <button type="button" class="next">next</button>
  </div>
  <div class="auto">
    <button type="button" class="stop">stop</button>
    <button type="button" class="play">play</button>
  </div>
</div>
```

# css
```css
#slide {
  position: relative;
  overflow: hidden;
  width: 300px;
  height: 300px;
}

#slide .cnt > li {
  position: absolute;
  top: 0;
  left: 300px;
  width: 300px;
  height: 300px;
  text-align: center;
  font-size: 30px;
  line-height: 300px;
  color: #fff;
}

#slide .cnt > li:nth-child(1) {
  background-color: red;
}

#slide .cnt > li:nth-child(2) {
  background-color: orange;
}

#slide .cnt > li:nth-child(3) {
  background-color: green;
}

#slide .cnt > li:nth-child(4) {
  background-color: blue;
}

#slide .btn > button {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  border: 0;
  padding: 5px;
  background-color: #fff;
}

#slide .btn .prev {
  left: 5px;
}

#slide .btn .next {
  right: 5px;
}

#slide .auto > button {
  display: none;
  position: absolute;
  bottom: 5px;
  right: 5px;
  border: 0;
  padding: 5px;
  background-color: #fff;
}

#slide .indi {
  position: absolute;
  bottom: 10px;
  left: 50%;
  transform: translateX(-50%);
}

#slide .indi:after {
  content: "";
  display: block;
  clear: both;
}

#slide .indi > li {
  float: left;
  margin-left: 5px;
  border-radius: 50%;
  width: 12px;
  height: 12px;
  cursor: pointer;
  opacity: 0.5;
  background-color: #fff;
}

#slide .indi > li.on {
  opacity: 1;
}

#slide .indi > li:first-child {
  margin-left: 0;
}
```

# javascript
```javascript
window.addEventListener("load", function () {
  var MOVEING_PX = 4,
    AUTO_TIME = 2000,
    slide = document.getElementById("slide"),
    indi = document.createElement("ul"),
    slideCnt = slide.getElementsByClassName("cnt"),
    slideCntItem = slideCnt[0].getElementsByTagName("li"),
    prevBtn = slide.getElementsByClassName("prev"),
    nextBtn = slide.getElementsByClassName("next"),
    playBtn = slide.getElementsByClassName("play"),
    stopBtn = slide.getElementsByClassName("stop"),
    playSet = null,
    before = 0,
    after = 0,
    moveIng = false;

  // init
  slideCntItem[0].style.left = 0;
  playBtn[0].style.display = "block";
  var indi = document.createElement("ul");
  for (var i = 0; i < slideCntItem.length; i++) {
    indi.innerHTML += "<li></li>";
  }
  indi.classList.add("indi");
  indi.children[0].classList.add("on");
  slide.append(indi);

  for (var j = 0; j < indi.children.length; j++) {
    indiClick(j);
  }

  // initEvnet
  nextBtn[0].addEventListener("click", function (e) {
    if (!moveIng) {
      after++;
      if (after >= slideCntItem.length) {
        after = 0;
      }
      move(after, before, "next");
      before = after;
    }
  });

  prevBtn[0].addEventListener("click", function (e) {
    if (!moveIng) {
      after--;
      if (after < 0) {
        after = slideCntItem.length - 1;
      }
      move(after, before);
      before = after;
    }
  });

  playBtn[0].addEventListener("click", function () {
    playBtn[0].style.display = "none";
    stopBtn[0].style.display = "block";
    playSet = setInterval(function () {
      if (!moveIng) {
        after++;
        if (after >= slideCntItem.length) {
          after = 0;
        }
        move(after, before, "next");
        before = after;
      }
    }, AUTO_TIME);
  });

  stopBtn[0].addEventListener("click", function () {
    playBtn[0].style.display = "block";
    stopBtn[0].style.display = "none";
    clearInterval(playSet);
  });

  function indiClick(target) {
    indi.children[target].addEventListener("click", function () {
      if (!moveIng) {
        after = target;
        if (after > before) {
          move(after, before, "next");
        } else if (after < before) {
          move(after, before);
        }
        before = after;
      }
    });
  }

  function move(after, before, type) {
    var nextX = type === "next" ? slide.offsetWidth : slide.offsetWidth * -1,
      prevX = 0,
      set = null;
    set = setInterval(function () {
      moveIng = true;
      if (type === "next") {
        nextX -= MOVEING_PX;
        slideCntItem[after].style.left = nextX + "px";
        if (nextX <= 0) {
          clearInterval(set);
          nextX = slide.offsetWidth;
          moveIng = false;
        }
        prevX -= MOVEING_PX;
      } else {
        nextX += MOVEING_PX;
        slideCntItem[after].style.left = nextX + "px";
        if (nextX >= 0) {
          clearInterval(set);
          nextX = slide.offsetWidth * -1;
          moveIng = false;
        }
        prevX += MOVEING_PX;
      }
      slideCntItem[before].style.left = prevX + "px";
    });
    indi.children[before].classList.remove("on");
    indi.children[after].classList.add("on");
  }
});
```
