---
date: 2025-11-10
layout: post
title: Controller VS RestController
categories: [개발 공부]
tags: [SpringFrameWork]

---

# Spring MVC 가 도데체 뭘까

## 1. Spring MVC 란?

스프링 MVC는 스프링 프레임워크에서 제공하는 웹 어플리케이션 구조로 Model,View Controller 패턴을
기반으로 HTML 또는 JSON 요청 및 응답을 처리하는 방식입니다. Controller에서 요청을 받고, Model에서
비즈니스 로직을 처리 후 View를 통해 화면 GUI로 응답합니다.

## 2. Spring MVC 요청 처리 과정

 1. 클라이언트 요청
 2. DispatcherServlet ( Front Controller)
 3. HandlerMapping  ( 어떤 컨트롤러 실행할지 결정)
 4. HandlerAdapter  ( 특정 컨트롤러 실행)
 5. Controller (컨트롤러 또는 메서드 실행)
 6. Model
 7. ViewResolver (화면 출력 혹은 JSON)
 8. Response (클라이언트 응답)

## 3. @Controller 요청 처리

Spring Controller 전통적인 방식인 @Controller는 viewResolver 단계에서 직접 HTML을 반환합니다.
따로 데이터를 변환하는 것이 아닌, 직접 HTML을 통해 화면을 출력합니다. 전통적인 MVC 모델에 View를 
표현합니다.

## 4. @RestController 요청 처리

@RestController는 @Controller와 달리 ViewResolver 단계에서 JSON을 반환합니다.
HTML을 통해 화면을 출력하지 않고 Client에 JSON을 반환합니다. MVC 모델보다 레이어드 아키텍쳐에서 다른
서버에 JSON을 전달할 때 사용합니다.

## 5. @Controller vs @RestController 개인적 생각

@Controller는 한 서버에서 비즈니스 로직 수행 및 화면 GUI 출력까지 전부 담당할 때
유효한 방식입니다. 하지만 최근에는 백엔드 서버와 프론트 서버가 분리되며 레이어드 아키텍쳐를 주로 사용합니다.
백엔드 단계에서 View 를 구현할 필요가 없습니다. 그러므로 @RestController를 이용해 JSON을
반환하는 방식을 더욱 많이 채용한다고 생각합니다.




