CSS

/* 주석  cmd + /    */  
div {
  color: red; 
  margin: 20px;
}


선언방식

내장방식
<style>
div {
  color: red; 
  margin: 20px;
}
</style>

인라인 방식
<div style=”color: red; margin: 20px;”></div>

링크방식(병렬방식)
<link rel=”stylesheet” href=”./main.css”>

import 방식(직렬방식)
@import url(“./box.css”);

div {
  color: red;
}


선택자

** 기본선택자

1. 전체 선택자
모든 요소를 선택

* {
  color: red; 
  margin: 20px;
}


2. 태그 선택자
태그 이름이 선택자

div {
  color: red; 
  margin: 20px;
}

3. 클래스 선택자

.red {
  color: red; 
  margin: 20px;
}

4. id 선택자

#red {
  color: red; 
  margin: 20px;
}

** 복합선택자

1. 일치 선택자
span.orange {
    color: red;
}

<span class="orange">오렌지</span>

2. 자식 선택자
선택자 ABC의 자식 요소 XYZ 선택
ABC > XYZ 

<!-- <li class="orange">오렌지</li> 가 선택됨 -->
ul > .orange {
    color: red;
}

<div>
    <ul>
        <li></li>
        <li></li>
        <li class="orange">오렌지</li>
    </ul>
    <span class="orange">오렌지</span>
<div>

3. 하위(후손) 선택자
선택자 ABC의 하위 요소 XYZ 선택
ABC XYZ 

<!-- 둘다 선택됨  -->
div .orange {
    color: red;
}

<div>
    <ul>
        <li></li>
        <li></li>
        <li class="orange">오렌지</li>
    </ul>
    <span class="orange">오렌지</span>
<div>

4. 인접 형제 선택자
선택자 ABC의 다음 형제 요소 XYZ 하나를 선택
ABC + XYZ

<!-- 망고가 선택됨 -->
.orange + li {
    color: red;
}

    <ul>
        <li></li>
        <li>사과</li>
        <li class="orange">오렌지</li>
        <li>망고</li>
        <li>감자</li>
    </ul>

5. 일반 형제 선택자
선택자 ABC의 다음 형제 요소 XYZ 모두를 선택
ABC ~ XYZ

<!-- 망고, 감자가 선택됨 -->
.orange ~ li {
    color: red;
}

    <ul>
        <li></li>
        <li>사과</li>
        <li class="orange">오렌지</li>
        <li>망고</li>
        <li>감자</li>
    </ul>


** 가상 클래스 선택자

1. hover
선택자 ABC요소에 마우스 커서가 올라가 있는 동안 선택
ABC:hover 

2. active
선택자 ABC요소에 마우스를 클릭하고 있는 동안 선택
ABC:hover 

3. focus
선택자 ABC요소에 포커스가 되면 선택
입력가능한 요소에서만 동작한다
ABC:focus

div등 입력이 불가능한 요소에서 포커스를 가지게 하려면 tabindex=-1 을 지정한다.
<div class="box" tabindex="-1"></div>

4. first child
선택자 ABC가 형제 요소 중 첫째라면 선택
ABC:first-child

<!-- 딸기 선택 -->
.fruits span:first-child {
    color: red;
}
    
<div class="fruits">
    <span>딸기</span>
    <span>수박</span>
    <div>오렌지</div>
    <p>망고</p>
    <h3>사과</h3>
</div>

5. last child
선택자 ABC가 형제 요소 중 막내라면 선택
ABC:last-child

<!-- 사과 선택 -->
.fruits h3:last-child {
    color: red;
}
    
<div class="fruits">
    <span>딸기</span>
    <span>수박</span>
    <div>오렌지</div>
    <p>망고</p>
    <h3>사과</h3>
</div>

6. nth child
선택자 ABC가 형제 요소 중 (n)째라면 선택
ABC:nth-child(n)

<!-- 수박 -->
.fruits *:nth-child(2) {
    color: red;
}
    
<div class="fruits">
    <span>딸기</span>
    <span>수박</span>
    <div>오렌지</div>
    <p>망고</p>
    <h3>사과</h3>
</div>

<!-- 수박, 망고.. 짝수번째 선택 -->
.fruits *:nth-child(2n) {
    color: red;
}
    
<div class="fruits">
    <span>딸기</span>
    <span>수박</span>
    <div>오렌지</div>
    <p>망고</p>
    <h3>사과</h3>
</div>

<!-- 홀수번째 선택 -->
.fruits *:nth-child(2n+1) {
    color: red;
}
    
<div class="fruits">
    <span>딸기</span>
    <span>수박</span>
    <div>오렌지</div>
    <p>망고</p>
    <h3>사과</h3>
</div>

<!-- 두번째 이후 모두 선택 -->
.fruits *:nth-child(n+2) {
    color: red;
}
    
<div class="fruits">
    <span>딸기</span>
    <span>수박</span>
    <div>오렌지</div>
    <p>망고</p>
    <h3>사과</h3>
</div>

7. 부정 선택자 not
선택자 ABC가 아닌 ABC 요소 선택
ABC:not(XYZ)

<!-- 오렌지, 망고, 사과 선택 -->
.fruits *:not(span) {
    color: red;
}
    
<div class="fruits">
    <span>딸기</span>
    <span>수박</span>
    <div>오렌지</div>
    <p>망고</p>
    <h3>사과</h3>
</div>

** 가상 요소 선택자
1. before (인라인(글자) 요소)
선택자 ABC 요소의 내부 앞에 내용(Content)을 삽입.
ABC::before

<!-- 앞! Content    가 표시됨 -->
.box::before {
  content: "앞!";
}

<div class="box">
  Content!
</div>

2. after (인라인(글자) 요소)
선택자 ABC 요소의 내부 뒤에 내용(Content)을 삽입.
ABC::after

<!-- Content 뒤!    가 표시됨 -->
.box::after {
  content: "뒤!";
}

<div class="box">
  Content!
</div>

3. 사용 예제
  <style>
    .box {
        width: 100px;
        height: 100px;
        background-color: orange;

    }

    /* before, after는 인라인요소이기때문에 width, height가 적용되지 않음 */
    /* 인라인 요소를 블럭 요소로 바꾸려면 display: block; 을 사용한다 */
    .box::before {
        content: "";
        display: block;
        width: 30px;
        height: 30px;
        background-color: royalblue;
    }
  </style>
</head>
<body>
  <div class="box">HEROPY</div>
</body>

** 속성 선택자

1. ATTR
속성 ABC를 포함한 요소 선택
[ABC]

<!-- 마지막 INPUT이 선택됨 -->
[disabled] {
    color: red;
}

<!-- 3개 input이 다 선택됨 -->
[type] {
    color: red;
}

<!-- 두번째 input 선택 -->
[type="password"]{
    color: red;
}

<input type="text" value="HEROPY"> 
<input type="password" value="1234"> 
<input type="text" value="abcd" disabled> 

** 스타일 상속
부모요소에 적용된 css들은 자식요소에 상속됨
상속되는 css 속성들은 모두 글자/문자에 관련된 속성들

font-style, font-weight, font-size, line-height, font-family, color, text-align 등

1. 강제 상속
상속 안되는 속성들을 강제로 상속 

.parent {
    width: 300px;
    height: 200px
}

<!-- 부모를 상속 받아 height 200px -->
.child {
    width: 100px;
    height: inherit
}

** 선택자 우선순위

//결과는 빨간색
<style>
    div {color red !important;}     //!important 9999999999999점
    #color_yellow {color: yellow;}  //id 선택자 100점
    .color_green {color: green;}    //class 선택자 10점
    div {color: blue;}              //태그 선택자 1점
    * {color: darkblue;}            //전체 선택자 0점
    body {color: violet;}           //상속되는 경우는 계산하지 않음 
</style>

<body>
    <div
        id="color_yellow"
        class="color_green"
        style="color: orange">      //인라인 선언 1000점
        Hello World!!
    </div>
</body>

** 속성
HTML에서는 attribute
CSS에서는 properties
JS에서는 properties
