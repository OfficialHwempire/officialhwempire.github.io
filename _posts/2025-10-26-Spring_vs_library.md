---
date: 2025-10-26
layout: post
title: Spring vs Library
categories: [개발 공부]
tags: [SpringFrameWork]

---

# JAVA Spring vs JAVA Library

![image](/assets/img/JavaSpringIcon.png)
## 1. JAVA Spring의 역할

Java Spring 은 JAVA 개발을 돕는 오픈 소스 어플리케이션 프레임워크입니다. JAVA Spring 은 이전에 JAVA 에서 주로 사용한 프레임 워크
EJB(Enterprise Java Bean) 의 기술 복잡도가 늘어나고 성능이 느린 문제를 해결하기 위해 개발되었습니다. POJO,DI,IOC 등 다양한 기능을
통해 JAVA 개발자가 오직 비즈니스 로직 구현에 집중할 수 있게 도와주는 개발 환경을 제공합니다.

## 2. JAVA Spring 이전 JAVA FrameWork EJB
EJB(Enterprise Java Bean) 은 대규모 기업 환경 시스템을 구측하기 위한 JAVA 서버 어플리케이션입니다. EJB는 구조가 복잡한
시스템의 DB,서버 클라이언트 등 다양한 객체 환경을 쉽게 구현하기 위해 개발되었습니다. 인스턴스 풀링, 트랜잭션 처리, 빈 메모리 사용 관리 등의
로우 레벨 기능을 자동 관리해주어 개발자가 로우 레벨에 신경 쓸 필요가 없게 하였습니다. 

# 3. EJB의 한계

1. 객체 직렬화 과정에서 어플리케이션 실행 속도 저하
2. JAVA의 객체 지향적인 특징과 장점을 포기한 EJB 비즈니스 오브젝트
3. 불필요하게 너무 많은 EJB 설정을 개발자가 해야함으로서 발생하는 낮은 개발 생산성

EJB는 시간이 흐르면 성능적으로 , 개발 친화 측면에서 많은 아쉬움을 보였습니다. 여러 EJB의 단점을 해결하기 위해 JAVA Spring이
개발되었습니다.

## 4. JAVA Spring의 장점

  1. POJO(Plain Old Java Object) 기반의 개발
  2. 필요한 모듈만 골라 사용해 프로그램의 경량화
  3. JPA, JDB 등 다양한 기술 스택을 사용 가능
  4. JUnit 을 사용한 단위 테스트 구현 용의

JAVA Spring은 기존의 EJB가 가지고 있는 너무 무겁다는 단점을 보완했습니다. 또한 POJO를 통해 JAVA 특징인 객체 지향 특성을 활용할 수 있고,
JAVA에 익숙한 개발자들이 쉽게 JAVA Spring을 사용할 수 있습니다. 다양한 기술 및 모듈과 연계해 개발자의 코드 생산성을 높혔습니다.

## 3. JAVA Spring과 JAVA Library의 차이점

그렇다면 JAVA Spring과 JAVA Library의 차이점은 무엇일까요? JAVA Library는 특정 코드의 기능을 재사용할 수 있도록 묶어 놓은 코드 집합입니다.
개발자가 직접 코드의 흐름을 제어할 때 라이브러리 함수를 호출해 사용합니다. 반면 JAVA Spring은 프로그램의 흐름을 대신 관리해주는 도구입니다.
프로그래머가 직접 전체 애플리케이션을 작성하지 않고 JAVA Spring이 전체 애플리케이션 흐름을 주도합니다.

## 4. 사용 예시

```java

@Primary
@Repository
@Profile("file")
public class FileChannelRepository implements ChannelRepository {


  private final String channelRepositoryDataPath = DATA_PATH + "channelRepository.ser";
  private File channelRepositoryFile = new File(channelRepositoryDataPath);
}

```

JAVA Spring을 이용해 간단히 짜본 Java 코드입니다. 어노테이션을 이용해 JAVA 객체를 빈으로 등록했습니다. 이제 개발자는
직접 객체를 관리하는 게 아니라 JAVA Spring이 빈을 통해 JAVA 객체를 관리합니다.

## 5. JAVA Spring에 관한 개인적 견해

JAVA를 사용해 백엔드 서비스를 개발하는 엔지니어라면 JAVA Spring은 필수라고 생각합니다. JAVA Spring은 굉장히 방대한 라이브러리
와 도구를 지니고 있습니다.  JAVA Spring을 통해 개발자는 개발 속도와 프로그램 관리를 효율적으로 할 수 있습니다.
