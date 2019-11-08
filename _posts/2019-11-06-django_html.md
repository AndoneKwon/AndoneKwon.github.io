---
layout: post
title: "Html 메서드"
date: 2019-11-08
excerpt: "html 패킷"
django: true
comments: true
tag: [django,project,tutorial,html]
---
## Get방식과 Post방식
혼자서 django 튜토리얼을 진행하던 중

	GET / HTTP/1.1" 200 16348

이라는 문장이 있어서 무엇인지 궁금하여 찾아봤다.

그래서 HTML 메서드 방식들을 정리 해보기로 하였다.

우선 클라이언트가 서버로 요청을 할때에 HTTP패킷을 보낸다.

HTTP 패킷의 구조는 크게 헤더와 바디로 나뉘어 지는데

HTTP 헤더에는 HTTP 메서드 방식중 어떤것을 사용했는지 클라이언트 정보, 브라우저 정보, 접속학 URL등과 같은 클라이언트의 정보를 담는다.

일반적으로 바디는 비어있으나 특정 데이터를 담아서 서버에게 요청을 보낼 수 있다.

여기서 Get메서드와 Post메서드 두가지 방식을 통해서 요청한다.

### GET 방식
클라이언트의 데이터를 URL뒤에 붙여서 보낸다. 

예를 들어보면 

	www.example.com?id=mommoo&pass=1234

이런식으로 보내는데 ?을 통해서 url의 끝을 알리고 데이터 표현의 시작점을 알린다.

데이터는 key와 value를 쌍으로 넣어야 하는데 여기서 Key는 pass고 value는 mommoo랑 1234 이다.

2개이상의 key또는 value를 보낼때에는 &마크로 구분해준다.

URL에 이런 값들을 붙이므로 헤더에 포함되어 서버에 요청하고 Body에는 특별히 넣을 내용이 없기 때문에 빈 상태로 보내지게 된다.

URL로 표현되다 보니 특정 페이지를 다른사람에게 접속 할 수 있게 한다.