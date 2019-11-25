---
layout: post
title: "node.js 웹페이지?"
date: 2019-11-25
excerpt: "node.js 웹페이지"
node: true
comments: true
tag: [node.js,project,tutorial]
---
# 웹페이지
자..이제 본격적으로 웹페이지를 간단하게 만들어보자.

그 전에 express framwork를 설치하고 설정하는 것은 튜토리얼을 잘 따라가 보도록 하자.

그렇게 처음으로 npm start를 실행하게 되면 보이는 화면은

![nodejs](./assets/img/post_img/nodejs_start)

이렇게 나오는데 안에 글씨를 한번 바꿔보자.

index.js 파일에 가면 router.get 이것을 고쳐서 경로를 정해줄 수 있다.

view 파일안에 보면 jade 파일이 있는데 index.jade 파일 구조는 이러하다.

    extends layout

    block content  
        h1= title
        p 환영합니다! #{title}

대충 알것 같지 않은가?

index.js 파일 구조를 보여주면

    var express = require('express');
    var router = express.Router();

    /* GET home page. */
    router.get('/', function(req, res, next) {
    res.render('index', { title: 'Node' });
    });

    module.exports = router;

이거 안에 title 부분을 바꾸면 홈페이지 안에 글씨가 바뀌게 된다.

따라서 view 안에 jade 파일을 생성하고 index.js 파일 안에 경로를 설정해 줄수 있다.

한번 스스로 해보도록 하자.

<hr>

## References
http://edu.goorm.io/learn/lecture/557/%EB%B0%94%EB%A1%9C-%EC%8B%A4%ED%96%89%ED%95%B4%EB%B3%B4%EB%A9%B4%EC%84%9C-%EB%B0%B0%EC%9A%B0%EB%8A%94-node-js/lesson/21938/%EB%85%B8%EB%93%9C%EC%9D%98-%EB%AA%A8%EB%93%88-%EA%B0%9C%EB%85%90