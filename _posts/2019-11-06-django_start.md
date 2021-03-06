---
layout: post
title: "장고 설치, 예제 프로젝트"
date: 2019-11-06
excerpt: "장고 시작"
django: true
comments: true
tag: [django,project,tutorial]
---
<h1>장고 설치 방법</h1>
우선 파이썬을 설치해준다. 3.6버전 이후로 설치해야한다.

파이썬을 설치 한후에 디렉토리를 만들어준다.
	
	$mkdir django
	$cd django

위 명령어를 실행하면 되는데 사실 디렉토리 만드는건 그냥 폴더안에서 만들어 줘도 된다.

경로를 cd 명령어를 통해 만든 디렉토리로 이동을 하고 가상환경을 만든다.

	$python -m venv myvenv

가상환경에 장고를 설치해준다.

가상환경을 생성하는 이유는 가상환경을 분리해줘야 라이브러리의 버전을 분리해줄수 있기 때문이다.

파이썬을 하다보면 버전이 맞지않아 고생하는 경우가 매우 많이 발생하는데

만약 라이브러리 하나의 버전이 업데이트되게 되면 관련 소스를 바로 모두 수정해줘야 하는 경우가 생길수 있다.

	$pip install django ~= 2.0.0

위 명령어를 실행하면 설치가 완료된다.

&nbsp
&nbsp

이제 프로젝트를 생성해보자.

이 과정은 장고의 기본적인 골격을 만들어 주는 과정이라 이야기 할수 있다.

여기서 주의할점은 이때 생성한 파일들은 말그대로 골격이므로 파일 이름을 바꾼다거나 위치를 변경해서는 안된다.

아래 명령어를 실행하면 된다.

	django-admin.py startproject mysite .

웹서버를 이제 실행해보도록 하자.

우선 장고를 설치한 가상환경을 열기 위해선

	myvenv\Scripts\activate

위 명령어를 실행해야 한다.

다음으로는 기본적인 설정을 변경하자.

mysite\setting.py 에 있는 정보를 적당하게 변경해준다.

모든 세팅을 마친뒤 서버를 실행시켜보자.

manage.py 파일이 있는 폴더로가 다음과 같은 명령어를 시켜준다.

	python manage.py runserver

그럼 서버가 실행된다. 127.0.0.1:8000 으로 가보자

![장고 이미지](/assets/img/post_img/django_start.JPG)

다음과 같은 화면이 보이며 첫번째 미션은 끝이 난다.

<hr>

## References
https://tutorial.djangogirls.org/

위 모든 글은 장고걸스의 튜토리얼을 따라했습니다.