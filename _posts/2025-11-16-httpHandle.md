---
date: 2025-11-16
layout: post
title: 클라이언트 요청 처리
categories: [개발 공부]
tags: [Rest]

---

# @RestController의 HTTP 요청 처리 과정

## 1. @RestController 란?

@RestController는 Spring boot에서 제공하는 어노테이션입니다.
Presentation layer를 담당하는 빈 객체를 생성합니다.
@Controller + @ResponseBody를 합쳤습니다. @RestController를 통해
기존 @controller 가 html을 반환한 것과 달리 json을 결과값으로 반환합니다.

## 2. HTTP 요청 처리 과정

| 순서 | 처리 주체 | 설명 |
|-----|-----------|------|
| 1 | 클라이언트 | HTTP 요청 전송 |
| 2 | DispatcherServlet | 요청을 가장 먼저 받는 프론트 컨트롤러 |
| 3 | HandlerMapping | 해당 URI의 컨트롤러 메서드 찾기 |
| 4 | HandlerAdapter | 컨트롤러 호출 준비(파라미터 바인딩) |
| 5 | HTTP 메시지 컨버터(요청) | JSON → Java 객체 변환 |
| 6 | Controller | 요청 처리 시작, Service 호출 |
| 7 | Service | 비즈니스 로직 수행 |
| 8 | Repository | DB 접근 |
| 9 | Database | 실제 데이터 처리 |
| 10 | Service → Controller | 결과 전달 |
| 11 | HTTP 메시지 컨버터(응답) | 객체 → JSON 변환 |
| 12 | DispatcherServlet | Response 조립 |
| 13 | 클라이언트 | 응답 수신 |


## 3. HTTP 메서지 converter 역할

HTTP 메세지 컨버터는 자바 객체와 JSON 사이에 직렬화 및 역직렬화를 해주는 역할을 합니다.
HTTP 요청에 json 데이터가 body에 담겨있으면 HTTP 메시지 컨버터는 json 데이터를 자바 객체로 역직렬화 합니다.
HTTP Response를 보낼 때 @ResponseBody 에 자바 객체가 있을 경우 HTTP 메시지 컨버터는 자바 객체를 json으로 직렬화
합니다.

## 4. @Controller vs @RestController

두가지 어노테이션은 동일하게 presentation layer를 담당합니다. @Controller는 html 페이지
렌더링 주요 목적입니다. @RestController는 httpmessageConverter을 사용해 json/xml 같은
데이터를 조회 및 반환하는 게 주요 목적입니다. 

