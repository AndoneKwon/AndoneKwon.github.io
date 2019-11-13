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

간단한 데이터를 넣도록 설계했기 떄문에 데이터를 보내는 양의 한계가 있다.

### Post 방식
POST방식은 데이터 전송을 기반으로 한 요청 메서드이다.

GET방식과는 달리 BODY에 데이터를 넣어서 보낸다.

그래서 BODY를 설명하는 Content-Type라는 헤더 필드가 들어가고 어떤 데이터 타입인지 명시한다.

#### Content-Type
MIME(컨텐츠의 타입)과 문자열 인코딩(UTF-8 등등)을 명시할수 있다. <span style="font-weight: bold;">multipart/form-data</span>또는 <span style="font-weight: bold;">x-www-form-urlencoded</span>로 HTML form에서는 전성된다고 알려져 있다.

MIME같은 경우 개별타입으로 

* text/plain
* test/html
* image/jpeg
* audio/ogg
...
과 같이 나타낸다. 

multipart 타입 같은 경우에는 서로 붙어있는 여러 개의 메세지를 포함하여 하나의 복합 메세지로 보냄.

boundary는 메세지 파트를 구분하는 역할을 하며 메세지의 시작과 끝부분을 나타냄.

	1. application/x-www-form-urlencoded
	2. text/plain
	3. multipart/form-data

1번 같은 경우는 BODY에 GET방식과 동일하게 KEY와 VALUE를 쌍으로 넣으며 같은 구분자 &를 쓴다.

2번 같은 경우 BODY에 단순한 text를 넣는다.

3번 같은 경우는 파일 전송을 할 때 많이 사용 되는데 BODY의 데이터를 바이너리 데이터를 넣는다는 것을 알려준다.

자바와 같이 OOP 프로그래밍에서는 BODY데이터를 InputStream/OutputStream클래스를 통해서 읽고 쓰기를 한다.

### PUT
서버에게 resource를 업데이트 하거나 resource가 없다면 새로운 resource를 생성해 달라고 요청한다. 회원정보 수정 등에 사용된다.
PUT은 PATCH와 비교해서 전체 데이터를 교체하는 차이점이 있다. 예를들어 user가 data를 user.id user.name이라 하면 회원정보 수정시 put은 primary key인 id를 찾아 name만 업데이트 해도 모든 필드를 업데이트 한다.

### PATCH
서버에게 resource의 업데이트 요청을 한다. 주로 회원정보 수정등에 사용되는데 PUT과는 달리 부분 데이터만 업데이트 한다.