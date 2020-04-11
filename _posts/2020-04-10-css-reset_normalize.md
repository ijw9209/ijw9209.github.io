---
title: "CSS normalize vs reset "
excerpt: "normalize vs reset "
toc: true
toc_sticky: true

categories:
  - css
tags:
  - css
last_modified_at: 2020-04-10T08:06:00-05:00
---

# normalize vs reset 

브라우저마다 기본적으로 제공하는 element의 style을 통일 시키기 위해 사용하는 두 css에대해 알아본다.

## reset.css

`reset.css`는 기본적으로 제공되는 브라우저 스타일 전부를 제거하기위해 사용된다. `reset.css`가 적용되면 `<h1>~<h6>` , `<p>` , `<strong>` , `<em>` 등과 같은 표준 요소는 완전히 똑같아 보이며 브라우저가 제공하는 기본적인 styling이 전혀 없다.


## normalize.css 

`normalize.css`는 브라우저 간 일관된 스타일링을 목표로 한다. `<h1>~<h6>`와 같은 요소는 브라우저간에 일관된 방식으로 굵게 표시된다. 추가적인 디자인에 필요한 style만 CSS로 작성해주면된다.

즉 `normalize.css`는 모든 것을 "해제" 하기 보다는 유용한 기본값을 보존하는 것이다. 
예를들어 sup sub와 같은 요소는 `nomalize.css`가 적용된 후 바로 기대하는 스타일을 보여준다, 반면 `reset.css`를 포함하면 시각적으로 일반 텍스트와 구별 할 수 없다. 또한 `normalize.css` 는 `reset.css`보다 넓은 범위를 가지고 있으며 HTML5 요소의 표시 설정, 양식 요소의 글꼴 상속 부족 , pre-font 크기 렌더링 수정, IE9의 SVG오버플로 및 IOS의 버튼 스타일링 버그에대한 이슈를 줄여준다
