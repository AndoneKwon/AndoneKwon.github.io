---
layout: post
title: "장고 url설정"
date: 2019-11-18
excerpt: "url설정"
django: true
comments: true
tag: [django,project,tutorial]
---
#장고 url
이제부터 장고의 url설정을 해보자.

이전에 만들어 놓은

mysite/urls.py 파일을 보자

안쪽에 보면 

	from django.contrib import admin
	from django.urls import path

	urlpatterns = [
	    path('admin/', admin.site.urls),
	]

위와 같은 내용이 보인다. 

이전에 우리가 관리자 페이지를 보여줬던 admin이 보인다. 

이제 blog에 있는 url을 가져오도록 하자.

include라는 함수를 사용한다.

그리고 blog폴더 안에 있는 url을 가져와야 하기 때문에 다음과 같이 변경한다.

	from django.contrib import admin
	from django.urls import path

	urlpatterns = [
	    path('admin/', admin.site.urls),
	    path('',include('blog.urls')),
	]

자.. 이제 블로그 폴더 안에도 urls을 만들어 주자.

	from django.urls import path
	from . import views

	urlpatterns = [
		path('',views.post_list,name='post_list'),
	]

이제 view파일을 만들어 주자.

blog파일안에 view를 만들어 준다.

	from django.shortcuts import render

	def post_list(request):
		return render(request,'blog/post_list.html',{})

그리고 templete 파일을 만들어 줘야한다. templetes 폴더를 만들어 주고 그 안에 blog를 만들어 주고 그 안에 post_list.html 을 만들고 그 파일 안에 HTML로 코드를 작성해주면 그 문서 내용이 뜨게 된다.
<hr>

## References
https://tutorial.djangogirls.org/

위 모든 글은 장고걸스의 튜토리얼을 따라했습니다.