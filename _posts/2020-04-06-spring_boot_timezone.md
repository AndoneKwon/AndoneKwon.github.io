---
layout: post
title: "Spring boot DB설정 timezone 오류 해결"
date: 2020-01-04
excerpt: "Timezone 오류 해결"
spring_boot: true
comments: true
tag: [timezone에러]
---
# Spring boot 초기 설정중 발생한 에러
스프링부트를 공부하고 초기 설정을 하던 와중에
아래와 같은 에러가 발생하였다.

    com.mysql.cj.exceptions.InvalidConnectionAttributeException

구글링을 하던 와중에 timezone에 의해서 발생하는 오류인것을 발견하였다.

해결방법은 두가지가 있었는데 그중에 application.properties에서 DB를 설정해줄때

spring.datasource.hikari.jdbc-url=jdbc:mysql://localhost:3306/insight?useUnicode=true&characterEncoding=utf-8

이부분에

serverTimezone=UTC 을 추가하면 해결하는 것을 발견하였다.