---
date: 2025-11-03
layout: post
title: 웹 서버와 웹 어플리케이션 서비스
categories: [개발 공부]
tags: [SpringFrameWork]

---

# Web Server 와 WAS(Web Application Server)

## 1. Web Server 란?

 Web Server는 HTML, CSS, JavaScript, 이미지 등 정적인 컨텐츠를 제공하는 서버입니다. 복잡한 비즈니스 로직 수행 보다는 HTTP 응답 처리,
정적 리소스 호출, 로컬 캐싱, 로드 밸런싱 등 간단하고 가벼운 역할을 수행합니다. 가벼운 만큼 데이터 처리 속도가 빠르고, 정적 파일을 서빙
하는데 최적화가 되어 있습니다. 대표적으로 Ngnix, Apache HTTP Sever 등이 있습니다. 


## 2. WAS(Web Application Server) 란?

Was 는 동적인 웹 어플리케이션을 직접 실행하는 서버입니다. 서버에서 복잡한 비즈니스 로직을 처리하거나 데이터 베이스를 사용해야 할 때 사용합니다.
주요 역할로는 서블릿 실행, 외부 연동 웹 어플리케이션 실행, DB 연동 , 메인 비즈니스 로직 처리 등이 있습니다. 특징으로는 서버 안에서 프로그래밍
코드를 실행 할 수 있고 동적인 페이지를 구현 할 수 있습니다. 대표적인 WAS 서비스로는 TomCat, Jetty, JBoss 등이 있습니다.


## 3. Web Sever 와 Was 의 차이

Web Server와 Was 는 지양하는 방향이 다릅니다. Web Server는 단순한 정적 파일을 빠르게 호출하고 처리하는 역할에 초점을 맞춥니다. WAS는
서버에서 실행해야 할 프로그램 및 비즈니스 로직을 다루는 역할을 담당합니다. 속도 측면에서 Web Server가 훨씬 빠르고, 기능 확장성 및 구현 측면
에서 WAS 가 훨씬 다채롭습니다.


## 4. 사용 예시

클라이언트 → Nginx(Web Server) → Spring Boot 내장 Tomcat(WAS)

실제로는 WAS 와 Web Server 를 분리하여 사용하기 보다는 혼합해서 사용합니다. Web Server가 보안 및 HTTP 요청 처리를 담당하여 성능을 올립니다.
WAS는 Web Server의 요청을 받아 메인 서버로서 비즈니스 로직을 실행합니다. 서로 한 쪽만 사용해야 하는 관계가 아닌 상호 보완적 관계입니다.
