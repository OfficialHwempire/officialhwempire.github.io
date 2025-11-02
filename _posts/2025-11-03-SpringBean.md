---
date: 2025-11-03
layout: post
title: Spring Boot Bean 등록
categories: [개발 공부]
tags: [SpringFrameWork]

---

# Spring Boot에서 Bean을 등록하는 다양한 방법

## 1. Bean 이란?

Spring Bean 은 Spring IOC 컨테이너가 직접 생성 및 관리를 담당하는 객체입니다. 개발자가 직접 객체를 생성하지 않고
Spring IOC 컨테이너가 Bean 이 필요한 곳에 객체를 주입합니다. Spring 에는 다양한 Bean 등록 방식이 있습니다.

## 2. @Component annotation

```java
@Component
public class MyService { }

```
대표적으로 @Component, @Sevice, @Repository 등 @Component annotation 을 사용해 빈을 등록하는 방식입니다. 이 경우 IOC 가 자체적으로
의존성이 필요한 곳에 빈을 주입합니다. 간편한 빈 등록 및 사용이 가능합니다. 그러나 동일한 역할을 가진 여러 빈이 존재할 경우 개발자가 일일히
어떤 빈을 주입할지 IOC 컨테이너에 알려주어야 합니다.

## 3. @Bean annotation


```java
@Configuration
public class AppConfig {
    @Bean
    public MyService myService() {
        return new MyService();
    }
}
```

직접 configuration 클래스 아래에 빈을 등록하는 방식입니다. Bean 생성 과정을 완전히 제어 할 수 있고, 외부 라이브러리 객체 역시 손쉽게 Bean 으로
등록할 수 있습니다. 하지만 개발자가 직접 설정을 관리하는 방식으로 생산성이 떨어집니다. 또한 별도의 설정 클래스를 관리해야 합니다. 이는 Spring
Boot 에서 관계의 역전성 장점을 위반해 추천드리지 않습니다.

## 4. FactoryBean 

```java
public class MyFactoryBean implements FactoryBean<MyService> {
    @Override
    public MyService getObject() {
        return new MyService("special");
    }

    @Override
    public Class<?> getObjectType() {
        return MyService.class;
    }
}
```

Bean 생성을 팩토리 패턴을 통해 제어하는 방식 입니다. 이는 객체 생성 로직을 캡슐화 하고 타입을 제네릭으로 받아 동적 객체를 생성하는 데 유용합니다.
개발자가 원하는 동적 객체 생성을 체계적으로 제어할 수 있습니다. 일반적으로 코드 가독성이 떨어지며, 구현 난이도가 높아 간단하고 단순한 역할을
하는 빈을 등록할 때 비효율 적입니다.

## 5. 어떤 Bean 등록 방식을 사용해야 할까요?

기본적으로 가장 관리가 쉽고 코드 가독성이 좋으면 구현 난이도가 낮은 @Component annotation을 활용하는 것을 권장합니다.
다만 동적 객체를 직접 생성하거나, 객체 구현 과정에서 직접 객체를 제어할 필요가 있을 때 FactoryBean 을 활용하는 것이 좋습니다.
