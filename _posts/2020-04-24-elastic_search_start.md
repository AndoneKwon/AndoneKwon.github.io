---
layout: post
title: "Elastic Search와 DB 연동"
date: 2020-04-06
excerpt: "ES와 DB연동"
spring_boot: true
comments: true
tag: [elastic_search,MYSQL]
---
# Elastic Search?
Elastic Search(이하 ES)는 루씬 기반의 검색 엔진이다. 루씬이란 아파치 재단에 의해서 관리되는 자바언어로 이루어진 정보 검색 라이브러리이다. ES는 Java 오픈소스 분산 검색 엔진이며 방대한 양의 데이터를 신속하게 거의 실시간으로 저장, 검색, 분석할 수 있다. 

일반적으로 ELK(Elasticsearch/Logstatsh/Kibana)스택으로 사용된다. Logstash는 다양한 소스의 로그 또는 트랜잭션 데이터를 수집, 집계, 파싱하여 Elasticsearch로 전달하게 된다. Kibana는 데이터를 시각화 하는 것이라고 보면 된다.

# MySQL to Elasticsearch
MySQL에 있는 데이터를 마이그레이션 할 때 방법은 여러가지가 있다.

1. 직접 손으로 넣는다
2. Logstash를 이용하여 넣는다.

당연히 손으로 많은 자원을 넣는 것은 불가능하고 보통 Logstash를 이용해 넣는다.

