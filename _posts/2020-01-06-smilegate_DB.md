---
layout: post
title: "개인프로젝트"
date: 2020-01-06
excerpt: "Web application Framework 별 특징"
smile: true
comments: true
tag: [스마일게이트,서버캠프,스마일게이트온라인서버캠프,SNS프로젝트]
---
# 개인프로젝트
스마일게이트 서버캠프에는 팀플만 있는 것이 아니라 개인별로 주어지는 과제가 따로 있다. 온라인은 사실 필수가 아니지만 우리조는 어차피 로그인 기능을 써야하기 때문에 개인별로 Node.js도 익힐겸 하도록 했다. 미션은 다음과 같다.


가입,로그인페이지, 유저관리페이지, 인증서버, Mysql 사용, 패스워드 암호화, 캐시, email 인증, 비밀번호 찾기.

다음과 같은 모든 기능을 구현하며 필요했던 것들을 하나하나 적도록하겠다.

특히 DB의 경우 많이 까먹어서 그 내용도 추가로 정리하겠다.

mysql을 설치하는 과정은 맥의 경우 homebrew를 통해서 설치하면 쉽기 때문에 넘어가기로 하고
    mysql.server start //실행하는 명령어
    mysql -uroot -p //myql로 접속하는 명령어

자세한 설명은 whitepeak.tistory.com/16
이분 블로그 가보면 매우 잘 설명 되어져 있다.

다만 중간에 패스워드를 설정하는 부분에서 보안이 강한 비밀번호만 설정 가능하게 하는 것을 yes로 하는 바람에 여러가지 문제가 생겨 다시 삭제하고 설치하였다.

특히 맥의 경우

    ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'yourpassword';

를 해주지 않을경우 DB를 불러오지 못한다.

SQL을 설치한 후 node.js와 mysql을 연동시켜본다.

    var mysql = require('mysql');
    var connection = mysql.createConnection({
        host 	: '127.0.0.1',
        user 	: 'userid',
        password: 'password',
        port	: 'portnum',
        database: 'dbname'	 
    });
    var express=require('express');
    var apt=express();


    connection.connect();

    connection.query('SELECT * From customer',function(err,rows,fields){
        if(!err)
            console.log("The solution is : ", rows);
        else
            console.log(err);
    });

    connection.end();

    apt.get('/',function(req,res){
        res.send("Hello");
    });

    apt.listen(3000,function(){
        console.log("connection");
    });

다음과 같이 진행을 하니 콘솔창에는 db의 내용이 잘 출력되며 localhost:3000 으로 접속 하였을때 hello가 잘뜨는것을 볼 수있다.