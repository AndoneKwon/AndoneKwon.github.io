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

	$pip install django ~= 2.0.0

위 명령어를 실행하면 설치가 완료된다.