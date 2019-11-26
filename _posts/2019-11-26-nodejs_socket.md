---
layout: post
title: "node.js socket.io"
date: 2019-11-25
excerpt: "node.js socket.io"
node: true
comments: true
tag: [node.js,project,tutorial]
---
# socket.io
말그대로 소켓 통신을 위한 모듈이다.

비동기 통신을 위한 라이브러리로 이벤트 기반의 처리에 의존하고 있다.

이제 예를들어
    var app = require('http').create.Server(handler);
    var io = require('socket.io').listen(app);
이런식으로 정의를 해놓으면 http 서버는 socket 통신을 지원하게 된다.

그리고 밑에

    io.on('connection',function(socket){
        ...
    });

이라고 정의 되어 있을때 io.on 의 connection은 socket.io의 기본 이베트로 웹사이트를 열면 자동으로 발생하는 이벤트이며 이벤트 안의 함수에는 접속한 사용자의 socket이 파라메터로 전달되게 되는데 접속한 각 클라이언트에 관한 이벤트를 작성하려면 connection 리스너의 함수 안에 socket을 사용하면된다.

<hr>

## References
http://edu.goorm.io/learn/lecture/557/%EB%B0%94%EB%A1%9C-%EC%8B%A4%ED%96%89%ED%95%B4%EB%B3%B4%EB%A9%B4%EC%84%9C-%EB%B0%B0%EC%9A%B0%EB%8A%94-node-js/lesson/21938/%EB%85%B8%EB%93%9C%EC%9D%98-%EB%AA%A8%EB%93%88-%EA%B0%9C%EB%85%90