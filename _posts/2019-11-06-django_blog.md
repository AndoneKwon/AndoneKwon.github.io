---
layout: post
title: "장고 blog 예제"
date: 2019-11-06
excerpt: "장고 시작"
django: true
comments: true
tag: [django,project,tutorial]
---
#Blog 시작
	python manage.py startapp 어플리케이션명
우리는 blog를 시작할것 이므로 어플리케이션명 위치에 blog 써놓는다.

다음 Installed_app에 우리가 만든 blog를 추가해준다.

이제 다음 차례는 블로그 Model을 만들어 준다.

모든 Model객체는 blog/model.py 파일에 선언하여 모델을 만들어 준다.

다음과 같은 코드를 model 파일안에 추가해준다.

	from django.conf import settings
	from django.db import models
	from django.utils import timezone


	class Post(models.Model):
	    author = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
	    title = models.CharField(max_length=200)
	    text = models.TextField()
	    created_date = models.DateTimeField(
	            default=timezone.now)
	    published_date = models.DateTimeField(
	            blank=True, null=True)

	    def publish(self):
	        self.published_date = timezone.now()
	        self.save()

	    def __str__(self):
	        return self.title

각 코드 줄별로 살펴보면 앞부분은 간단하게 import 말그대로 넣어주는 코드이다.

class Post(models.Model)이 부분에서 클래스를 정의해 준다.

다음에는 각 요소에 필드를 정의해준다.

여기서 foreignkey는 다른 모델에 대한 링크를 의미한다. DB에서의 foreignkey와 같은 의미이다.

각 필드에 대한 정보는 https://docs.djangoproject.com/en/2.0/ref/models/fields/#field-types

이곳에서 참조하면 된다.

def는 파이썬에서 method를 정의하는 키워드이다. 

이제 다음에는 모델을 위해 테이블을 만들 차례이다.

##모델을 위한 테이블 생성
	이제 장고를 데이터베이스를 반영할 수 있도록 만들어 본다.
	(myvenv) ~/djangogirls$ python manage.py makemigrations blog

다음과 같이 하면 migration file 이라는 것이 만들어 지고 python manage.py migrate blog명령어를 통해 실제 데이터베이스에 메델 추가를 반연하자.




<hr>

## References
https://tutorial.djangogirls.org/

위 모든 글은 장고걸스의 튜토리얼을 따라했습니다.