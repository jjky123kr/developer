---
layout: single
title: Bootstrap
category: CSS
---

### Bootstrap
부트스크립 다운
[getbootstrap](http://getbootstrap.com)  
부트스크립 참조 사이트 
[w3chools](http://www.w3schools.com)

### 사용법
1.다운로드 받은 Bootstrap 파일들을 불러와서 사용함

```

        <link href="../css/bootstrap.min.css" rel="stylesheet">       
 
        <script src="../js/bootstrap.min.js"></script>
````

2.Bootstrap CDN 방식

`````
 <!-- Latest compiled and minified CSS -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap.min.css" integrity="sha512-dTfge/zgoMYpP7QbHy4gWMEGsbsdZeCXz7irItjcC3sPUFtf0kuFbDz/ixG7ArTxmDjLXDmezHubeNikyKGVyQ==" crossorigin="anonymous">

	    <!-- Optional theme -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap-theme.min.css" integrity="sha384-aUGj/X2zp5rLCbBxumKTCw2Z50WgIr1vs/PFN4praOTvYXWlVyh2UtNUU0KAUhAX" crossorigin="anonymous">

	    <!-- Latest compiled and minified JavaScript -->
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/js/bootstrap.min.js" integrity="sha512-K1qjQ+NcF2TYO/eI3M6v8EiNYZfA95pQumfvcVrTHtwQVDG+aHRqLi/ETn2uB+1JqwYqVG3LIvdm9lj6imS/pQ==" crossorigin="anonymous"></script>

```````
###  부트스트립 활용법
 _accordino.html_
* 내용을 펼치때 : href="#collapseOne" 와
내용에 id="collapseOne" 적용

```html
<div class="card-header">
        <a class="card-link" data-toggle="collapse"
        href="#collapseOne">
          	자바
        </a>
      </div>      
      <div id="collapseOne" class="collapse show" data-parent="#accordion">
``````
* form_-group으로 묶어준다.
* input type="email"로 설정하면, email양식의 검사한다.
* form-contro 적용하면, 부드러운 모양의 양식이다.

id=email  
```html
<form action="/action_page.php">
    <div class="form-group">
      <label for="email">Email:</label> 
      <input type="email" class="form-control" id="email" placeholder="Enter email" name="email">   
    </div>
`````````
### Bootstrap 활용 하기
1. webpage.html 을 jsp 파일로  만들기 (webpage.html복사)
2. jsp파일을 생성 하여 nav 메뉴에 추가 한다. 
3. jsp 로 nav 메뉴 링크를 설정하기 <%include file="파일명"%>


