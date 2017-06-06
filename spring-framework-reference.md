# 스프링 프레임워크 레퍼런스 문서 Ver. 4.3.8 RELEASE

이 문서의 복사본들은 개인이 사용하거나 타인에게 배포할 수 있다. 어떠한 비용 없이 제공되어지고, 각 복사본에는 인쇄물 혹은 전자 형식으로 카피라이트 통지가 있어야 한다.

- - -
# 목차

<!-- toc orderedList:0 depthFrom:1 depthTo:6 -->

* [스프링 프레임워크 레퍼런스 문서 Ver. 4.3.8 RELEASE](#스프링-프레임워크-레퍼런스-문서-ver-438-release)
* [목차](#목차)
* [I. 스프링 프레임워크 개요](#i-스프링-프레임워크-개요)
  * [1. 스프링 프레임워크와 시작하기](#1-스프링-프레임워크와-시작하기)
  * [2. 스프링 프레임워크 소개](#2-스프링-프레임워크-소개)
    * [2.1 의존성 주입과 제어의 역전](#21-의존성-주입과-제어의-역전)
    * [2.2 프레임워크 모듈](#22-프레임워크-모듈)
      * [코어 컨](#코어-컨)
      * [AOP와 수단](#aop와-수단)
      * [메시징](#메시징)
      * [데이터 접근/통합](#데이터-접근통합)
      * [웹](#웹)
      * [테스트](#테스트)
    * [2.3 사용 시나리오](#23-사용-시나리오)
      * [의존성 관리와 네이밍 규약](#의존성-관리와-네이밍-규약)
        * [스프링 의존성들과 스프링에서의 의존](#스프링-의존성들과-스프링에서의-의존)
        * [Maven 의존성 관리](#maven-의존성-관리)
        * [Maven "Bill Of Materials" 의존성](#maven-bill-of-materials-의존성)
        * [Gradle 의존성 관리](#gradle-의존성-관리)
        * [Ivy 의존성 관리](#ivy-의존성-관리)
        * [배포 Zip 파일](#배포-zip-파일)
      * [로깅](#로깅)
        * [Log4j 1.2, 2.x버전 사용](#log4j-12-2x버전-사용)
        * [Commons Logging 피하기](#commons-logging-피하기)
        * [Log4j, Logback으로 Slf4j 사용](#log4j-logback으로-slf4j-사용)
        * [JUL(java.util.logging) 사용](#juljavautillogging-사용)
        * [WebSphere에서의 Commons Logging](#websphere에서의-commons-logging)
* [II. 스프링 프레임워크 4.x버전에서 새로워진 것들](#ii-스프링-프레임워크-4x버전에서-새로워진-것들)
  * [3. 스프링 프레임워크 4.0버전에서 새로운 요소와 나아진 것들](#3-스프링-프레임워크-40버전에서-새로운-요소와-나아진-것들)
    * [3.1 Getting started에서 개선된 것들](#31-getting-started에서-개선된-것들)
    * [3.2 사용하지 않는 패키지와 메서드](#32-사용하지-않는-패키지와-메서드)
    * [3.3 Java 8 (6과 7 뿐만 아니라)](#33-java-8-6과-7-뿐만-아니라)
    * [3.4 Java EE 6과 7](#34-java-ee-6과-7)
    * [3.5 Groovy 빈 정의 DSL](#35-groovy-빈-정의-dsl)
    * [3.6 코어 컨테이너 개선점](#36-코어-컨테이너-개선점)
    * [3.7 일반적인 웹 개선점](#37-일반적인-웹-개선점)
    * [3.8 웹소켓, SockJS, STOMP 메시징](#38-웹소켓-sockjs-stomp-메시징)
    * [3.9 테스팅 개선점](#39-테스팅-개선점)
  * [4. 스프링 프레임워크 4.1버전에서 새로운 요소와 나아진 것들](#4-스프링-프레임워크-41버전에서-새로운-요소와-나아진-것들)
    * [4.1 JMS 개선점](#41-jms-개선점)
    * [4.2 캐싱 개선점](#42-캐싱-개선점)
    * [4.3 웹 개선점](#43-웹-개선점)
    * [4.4 웹소켓 메시징 개선점](#44-웹소켓-메시징-개선점)
    * [4.5 테스팅 개선점](#45-테스팅-개선점)
  * [5. 스프링 프레임워크 4.2버전에서 새로운 요소와 나아진 것들](#5-스프링-프레임워크-42버전에서-새로운-요소와-나아진-것들)
    * [5.1 코어 컨테이너 개선점](#51-코어-컨테이너-개선점)
    * [5.2 데이터 접근 개선점](#52-데이터-접근-개선점)
    * [5.3 JMS 개선점](#53-jms-개선점)
    * [5.4 웹 개선점](#54-웹-개선점)
    * [5.5 웹소켓 메시징 개선점](#55-웹소켓-메시징-개선점)
    * [5.6 테스팅 개선점](#56-테스팅-개선점)
  * [6. 스프링 프레임워크 4.3버전에서 새로운 요소와 나아진 것들](#6-스프링-프레임워크-43버전에서-새로운-요소와-나아진-것들)
    * [6.1 코어 컨테이너 개선점](#61-코어-컨테이너-개선점)
    * [6.2 데이터 접근 개선점](#62-데이터-접근-개선점)
    * [6.3 캐싱 개선점](#63-캐싱-개선점)
    * [6.4 JMS 개선점](#64-jms-개선점)
    * [6.5 웹 개선점](#65-웹-개선점)
    * [6.6 웹소켓 메시징 개선점](#66-웹소켓-메시징-개선점)
    * [6.7 테스팅 개선점](#67-테스팅-개선점)
    * [6.8 새로운 라이브러리 및 서버 세대 지원](#68-새로운-라이브러리-및-서버-세대-지원)
* [III. 코어 기술](#iii-코어-기술)
  * [7. IoC 컨테이너](#7-ioc-컨테이너)
    * [7.1 스프링 IoC 컨테이너와 빈에 대한 소개](#71-스프링-ioc-컨테이너와-빈에-대한-소개)
    * [7.2 컨테이너 개요](#72-컨테이너-개요)
      * [설정 메타데이터](#설정-메타데이터)
      * [컨테이너 인스턴스화하기](#컨테이너-인스턴스화하기)
        * [XML 기반 구성 메타데이터 작성](#xml-기반-구성-메타데이터-작성)
        * [Groovy 빈 정의 DSL](#groovy-빈-정의-dsl)
      * [컨테이너 사용하기](#컨테이너-사용하기)
    * [7.3 빈 개요](#73-빈-개요)
      * [빈 네이밍](#빈-네이밍)
        * [빈 정의 바깥에서 빈에 별칭 부여하기](#빈-정의-바깥에서-빈에-별칭-부여하기)
      * [빈 인스턴스화하기](#빈-인스턴스화하기)
        * [생성자로 인스턴스화하기](#생성자로-인스턴스화하기)
        * [정적 팩토리 메서드로 인스턴스화하기](#정적-팩토리-메서드로-인스턴스화하기)
        * [인스턴스 팩토리 메서드로 인스턴스화하기](#인스턴스-팩토리-메서드로-인스턴스화하기)
    * [7.4 의존성](#74-의존성)
      * [의존성 주입](#의존성-주입)
        * [생성자 기반 의존성 주입](#생성자-기반-의존성-주입)
        * [Setter 기반 의존성 주입](#setter-기반-의존성-주입)
        * [의존성 해결 프로세스](#의존성-해결-프로세스)
        * [의존성 주입 예시](#의존성-주입-예시)
      * [의존성과 상세 설정](#의존성과-상세-설정)
        * [프리미티브 타입, 문자열 등 값](#프리미티브-타입-문자열-등-값)
        * [다른 빈 참조 (공동 작업자)](#다른-빈-참조-공동-작업자)
        * [내부 빈](#내부-빈)
        * [컬렉션](#컬렉션)
        * [null과 빈 문자열 값](#null과-빈-문자열-값)
        * [p-namespace를 이용한 XML 바로가기](#p-namespace를-이용한-xml-바로가기)
        * [c-namespace를 이용한 XML 바로가기](#c-namespace를-이용한-xml-바로가기)
        * [복합 속성 이름](#복합-속성-이름)
      * [의존성 사용](#의존성-사용)
      * [늦게 초기화되는 빈](#늦게-초기화되는-빈)
      * [Autowiring 공동 작업자](#autowiring-공동-작업자)
        * [autowiring의 한계와 단점](#autowiring의-한계와-단점)
        * [autowiring으로부터 빈 제외](#autowiring으로부터-빈-제외)
      * [메서드 주입](#메서드-주입)
        * [Lookup 메서드 주입](#lookup-메서드-주입)
        * [임의의 메서드 대체](#임의의-메서드-대체)
    * [7.5 빈 스코프](#75-빈-스코프)
      * [싱글톤 스코프](#싱글톤-스코프)
      * [프로토타입 스코프](#프로토타입-스코프)
      * [싱글톤 빈과 프로토타입 빈 의존성](#싱글톤-빈과-프로토타입-빈-의존성)
      * [Request, session, global session, application 그리고 웹 소켓 스코프](#request-session-global-session-application-그리고-웹-소켓-스코프)
        * [초기 웹 설정](#초기-웹-설정)
        * [Request 스코프](#request-스코프)
        * [Session 스코프](#session-스코프)
        * [Global session 스코프](#global-session-스코프)
        * [Application 스코프](#application-스코프)
        * [의존성으로서의 스코프화된 빈](#의존성으로서의-스코프화된-빈)
      * [커스텀 스코프](#커스텀-스코프)
        * [커스텀 스코프 생성](#커스텀-스코프-생성)
        * [커스텀 스코프 사용](#커스텀-스코프-사용)
    * [7.6 빈의 성질 커스터마이징](#76-빈의-성질-커스터마이징)
      * [라이프사이클 콜백](#라이프사이클-콜백)
        * [초기화 콜백](#초기화-콜백)
        * [소멸 콜백](#소멸-콜백)
        * [기본 초기화와 소멸 메서드](#기본-초기화와-소멸-메서드)
        * [라이프사이클 매커니즘 결합](#라이프사이클-매커니즘-결합)
        * [시작과 종료 콜백](#시작과-종료-콜백)
        * [웹 어플리케이션이 아닌 환경에서 스프링 IoC 컨테이너 우아하게 종료하기](#웹-어플리케이션이-아닌-환경에서-스프링-ioc-컨테이너-우아하게-종료하기)
      * [ApplicationContextAware와 BeanNameAware](#applicationcontextaware와-beannameaware)
      * [그 밖에 Aware 인터페이스](#그-밖에-aware-인터페이스)
    * [7.7 빈 정의 상속](#77-빈-정의-상속)
    * [7.8 컨테이너 확대 포인트](#78-컨테이너-확대-포인트)
      * [BeanPostProcessor를 이용한 빈 커스터마이징](#beanpostprocessor를-이용한-빈-커스터마이징)
        * [예제 : Hello World, BeanPostProcessor-style](#예제-hello-world-beanpostprocessor-style)
        * [예제 : The RequiredAnnotationBeanPostProcessor](#예제-the-requiredannotationbeanpostprocessor)
      * [BeanFactoryPostProcessor와 설정 메타데이터 커스터마이징](#beanfactorypostprocessor와-설정-메타데이터-커스터마이징)
        * [예제 : 클래스네임 치환 PropertyPlaceholderConfigurer](#예제-클래스네임-치환-propertyplaceholderconfigurer)
        * [예제 : PropertyOverrideConfigurer](#예제-propertyoverrideconfigurer)
      * [FactoryBean을 이용한 인스턴스화 로직 커스터마이징](#factorybean을-이용한-인스턴스화-로직-커스터마이징)
    * [7.9 Annotation 기반 컨테이너 설정](#79-annotation-기반-컨테이너-설정)
      * [@Required](#required)
      * [@Autowired](#autowired)
      * [@Primary를 이용한 Annotation 기반 autowiring 미세 조정](#primary를-이용한-annotation-기반-autowiring-미세-조정)
      * [한정자를 이용한 Annotation 기반 autowiring 미세 조정](#한정자를-이용한-annotation-기반-autowiring-미세-조정)
      * [autowiring 한정자로서 제네릭 사용](#autowiring-한정자로서-제네릭-사용)
      * [CustomAutowireConfigurer](#customautowireconfigurer)
      * [@Resource](#resource)
      * [@PostConstruct와 @PreDestroy](#postconstruct와-predestroy)
    * [7.10 클래스패스 스캔과 컴포넌트 관리](#710-클래스패스-스캔과-컴포넌트-관리)
      * [@Component와 추가 스테레오타입 annotation](#component와-추가-스테레오타입-annotation)
      * [메타 annotation](#메타-annotation)
      * [자동으로 클래스 탐지와 빈 정의 등록하기](#자동으로-클래스-탐지와-빈-정의-등록하기)
      * [필터를 사용하여 scanning 커스터마이징하기](#필터를-사용하여-scanning-커스터마이징하기)
      * [컴포넌트 내에서 빈 메타데이터 정의](#컴포넌트-내에서-빈-메타데이터-정의)
      * [자동탐지 컴포넌트 네이밍](#자동탐지-컴포넌트-네이밍)
      * [자동탐지 컴포넌트를 위한 스코프 제공](#자동탐지-컴포넌트를-위한-스코프-제공)
      * [annotation을 이용하여 메타데이터 한정자 제공](#annotation을-이용하여-메타데이터-한정자-제공)
    * [7.11 JSR 330 표준 annotation 사용](#711-jsr-330-표준-annotation-사용)
      * [@Inject와 @Named를 이용한 의존성 주입](#inject와-named를-이용한-의존성-주입)
      * [@Named와 @ManagedBean: @Component에 표준 동급](#named와-managedbean-component에-표준-동급)
      * [JSR-330 표준 annotation의 한계](#jsr-330-표준-annotation의-한계)
    * [7.12 Java 기반 컨테이너 설정](#712-java-기반-컨테이너-설정)
      * [기본 컨셉: @Bean과 @Configuration](#기본-컨셉-bean과-configuration)
      * [AnnotationConfigApplicationContext를 이용한 스프링 컨테이너 인스턴스화](#annotationconfigapplicationcontext를-이용한-스프링-컨테이너-인스턴스화)
        * [간단한 구성](#간단한-구성)
        * [레지스터(Class<?>...)를 이용한 프로그래밍적인 컨테이너 빌드](#레지스터class를-이용한-프로그래밍적인-컨테이너-빌드)
        * [scan(String...)을 이용한 컴포넌트 scanning 사용가능하게 하기](#scanstring을-이용한-컴포넌트-scanning-사용가능하게-하기)
        * [웹 어플리케이션과 AnnotationConfigWebApplicationContext에 대한 지원](#웹-어플리케이션과-annotationconfigwebapplicationcontext에-대한-지원)
      * [@Bean annotation 사용하기](#bean-annotation-사용하기)
        * [빈 선언하기](#빈-선언하기)
        * [빈 의존성](#빈-의존성)
        * [라이프사이클 콜백 받기](#라이프사이클-콜백-받기)
        * [빈 스코프 명시하기](#빈-스코프-명시하기)
        * [빈 네이밍 커스터마이징](#빈-네이밍-커스터마이징)
        * [빈에 별칭 달기](#빈에-별칭-달기)
        * [빈 기술하기](#빈-기술하기)
      * [@Configuration annotation 사용하기](#configuration-annotation-사용하기)
        * [내부 빈 의존성 주입](#내부-빈-의존성-주입)
        * [Lookup 메서드 주입](#lookup-메서드-주입-1)
        * [Java 기반 설정이 내부적으로 어떻게 동작하는 지에 대한 자세한 정보](#java-기반-설정이-내부적으로-어떻게-동작하는-지에-대한-자세한-정보)
      * [Java 기반 설정 작성하기](#java-기반-설정-작성하기)
        * [@Import annotation 사용하기](#import-annotation-사용하기)
        * [조건부로 @Configuration 클래스나 @Bean 메서드 포함하기](#조건부로-configuration-클래스나-bean-메서드-포함하기)
        * [Java와 XML 설정 결합](#java와-xml-설정-결합)
    * [7.13 환경 추출](#713-환경-추출)
      * [빈 정의 프로파일](#빈-정의-프로파일)
        * [@Profile](#profile)
        * [XML 빈 정의 프로파일](#xml-빈-정의-프로파일)
        * [프로파일 활성화하기](#프로파일-활성화하기)
        * [기본 프로파일](#기본-프로파일)
      * [PropertySource 추출](#propertysource-추출)
      * [@PropertySource](#propertysource)
      * [문장 내 지시자로 해결](#문장-내-지시자로-해결)
    * [7.14 LoadTimeWeaver 등록](#714-loadtimeweaver-등록)
    * [7.15 ApplicationContext의 추가적인 기능](#715-applicationcontext의-추가적인-기능)
      * [MessageSource를 이용한 국제화](#messagesource를-이용한-국제화)
      * [표준, 그리고 커스텀 이벤트](#표준-그리고-커스텀-이벤트)
        * [annotation 기반 이벤트 리스너](#annotation-기반-이벤트-리스너)
        * [비동기 리스너](#비동기-리스너)
        * [주문 리스너](#주문-리스너)
        * [제네릭 이벤트](#제네릭-이벤트)
      * [로우 레벨 리소스에 대한 편리한 접근](#로우-레벨-리소스에-대한-편리한-접근)
      * [웹 어플리케이션에서 편리하게 ApplicationContext 인스턴스화하기](#웹-어플리케이션에서-편리하게-applicationcontext-인스턴스화하기)
      * [Java EE RAR 파일로 스프링 ApplicationContext 디플로이하기](#java-ee-rar-파일로-스프링-applicationcontext-디플로이하기)
    * [7.16 BeanFactory](#716-beanfactory)
      * [BeanFactory or ApplicationContext?](#beanfactory-or-applicationcontext)
      * [Glue code와 사악한 싱글톤](#glue-code와-사악한-싱글톤)
  * [8. 리소스](#8-리소스)
    * [8.1 소개](#81-소개)
    * [8.2 리소스 인터페이스](#82-리소스-인터페이스)
    * [8.3 내장 리소스 구현](#83-내장-리소스-구현)
      * [UrlResource](#urlresource)
      * [ClassPathResouce](#classpathresouce)
      * [FileSystemResource](#filesystemresource)
      * [ServletContextResource](#servletcontextresource)
      * [InputStreamResource](#inputstreamresource)
      * [ByteArrayResource](#bytearrayresource)
    * [8.4 ResourceLoader](#84-resourceloader)
    * [8.5 ResourceLoaderAware 인터페이스](#85-resourceloaderaware-인터페이스)
    * [8.6 의존성으로써의 리소스](#86-의존성으로써의-리소스)
    * [8.7 어플리케이션 컨텍스트와 리소스 패스](#87-어플리케이션-컨텍스트와-리소스-패스)
      * [어플리케이션 컨텍스트 만들기](#어플리케이션-컨텍스트-만들기)
        * [ClassPathXmlApplicationContext 인스턴스 만들기 - 단축키](#classpathxmlapplicationcontext-인스턴스-만들기-단축키)
      * [어플리케이션 컨텍스트 생성자 리소스 패스에서의 와일드카드](#어플리케이션-컨텍스트-생성자-리소스-패스에서의-와일드카드)
        * [Ant 스타일 패턴](#ant-스타일-패턴)
        * [Classpath*: 이식성 classpath*: 접두사](#classpath-이식성-classpath-접두사)
        * [그 밖에 와일드카드와 관련된 노트](#그-밖에-와일드카드와-관련된-노트)
      * [FileSystemResource 주의사항](#filesystemresource-주의사항)
  * [9. 유효성, 데이터 바인딩, 그리고 타입 컨벤션](#9-유효성-데이터-바인딩-그리고-타입-컨벤션)
    * [9.1 소개](#91-소개)
    * [9.2 스프링의 유효성 검사 인터페이스를 이용한 유효성 검사](#92-스프링의-유효성-검사-인터페이스를-이용한-유효성-검사)
    * [9.3 에러 메시지에 대한 해결 코드](#93-에러-메시지에-대한-해결-코드)
    * [9.4 빈 조작과 BeanWrapper](#94-빈-조작과-beanwrapper)
      * [기본 및 중첩된 속성 세팅과 가져오기](#기본-및-중첩된-속성-세팅과-가져오기)
      * [내장 PropertyEditor 구현](#내장-propertyeditor-구현)
        * [추가적인 커스텀 PropertyEditor 등록](#추가적인-커스텀-propertyeditor-등록)
    * [9.5 스프링 타입 컨벤션](#95-스프링-타입-컨벤션)
      * [Converter SPI](#converter-spi)
      * [ConverterFactory](#converterfactory)
      * [GenericConverter](#genericconverter)
        * [ConditionalGenericConverter](#conditionalgenericconverter)
      * [ConversionService API](#conversionservice-api)
      * [ConversionService 설정](#conversionservice-설정)
      * [ConversionService 프로그래밍적으로 사용하기](#conversionservice-프로그래밍적으로-사용하기)
    * [9.6 스프링 필드 포맷](#96-스프링-필드-포맷)
      * [Formatter SPI](#formatter-spi)
      * [Annotation 중심 포맷](#annotation-중심-포맷)
        * [Format Annotation API](#format-annotation-api)
      * [FormatterRegistry SPI](#formatterregistry-spi)
      * [FormatterRegister SPI](#formatterregister-spi)
      * [Spring MVC에서 포맷 설정](#spring-mvc에서-포맷-설정)
    * [9.7 글로벌 date & time 포맷 설정](#97-글로벌-date-time-포맷-설정)
    * [9.8 스프링 유효성 검사](#98-스프링-유효성-검사)
      * [JSR-303 빈 유효성 검사 API 개요](#jsr-303-빈-유효성-검사-api-개요)
      * [빈 유효성 검사 프로바이더 설정](#빈-유효성-검사-프로바이더-설정)
        * [Validator 주입](#validator-주입)
        * [커스텀 제약조건 설정](#커스텀-제약조건-설정)
        * [스프링 중심의 메서드 유효성 검사](#스프링-중심의-메서드-유효성-검사)
        * [추가적인 설정 옵션](#추가적인-설정-옵션)
      * [DataBinder 설정](#databinder-설정)
      * [Spring MVC 3 유효성 검사](#spring-mvc-3-유효성-검사)
  * [10. Spring Expression Language (SpEL)](#10-spring-expression-language-spel)
    * [10.1 소개](#101-소개)
    * [10.2 구성요소 개요](#102-구성요소-개요)
    * [10.3 스프링 Expressin 인터페이스를 이용한 표현식 평가](#103-스프링-expressin-인터페이스를-이용한-표현식-평가)
      * [EvaluationContext 인터페이스](#evaluationcontext-인터페이스)
        * [타입 컨벤션](#타입-컨벤션)
      * [파서 설정](#파서-설정)
      * [SpEL 컴파일](#spel-컴파일)
        * [컴파일러 설정](#컴파일러-설정)
        * [컴파일러 한계](#컴파일러-한계)
    * [10.4 빈 정의를 정의하기 위한 표현식 지원](#104-빈-정의를-정의하기-위한-표현식-지원)
      * [XML 기반 설정](#xml-기반-설정)
      * [Annotation 기반 설정](#annotation-기반-설정)
    * [10.5 언어 참조](#105-언어-참조)
      * [리터럴 표현식](#리터럴-표현식)
      * [프로퍼티, Array, List, Map, Indexer](#프로퍼티-array-list-map-indexer)
      * [인라인 List](#인라인-list)
      * [인라인 Map](#인라인-map)
      * [Array 구성](#array-구성)
      * [메서드](#메서드)
      * [연산자](#연산자)
        * [관계 연산자](#관계-연산자)
        * [논리 연산자](#논리-연산자)
        * [수학 연산자](#수학-연산자)
      * [할당](#할당)
      * [타입](#타입)
      * [생성자](#생성자)
      * [변수](#변수)
        * [#this와 #root 변수](#this와-root-변수)
      * [함수](#함수)
      * [빈 참조](#빈-참조)
      * [삼항 연산자](#삼항-연산자)
      * [Elvis 연산자](#elvis-연산자)
      * [Safe Navigation 연산자](#safe-navigation-연산자)
      * [컬렉션 셀렉션](#컬렉션-셀렉션)
      * [컬렉션 프로젝션](#컬렉션-프로젝션)
      * [표현식 템플릿](#표현식-템플릿)
    * [10.6 예제에 사용된 클래스](#106-예제에-사용된-클래스)
  * [11. 스프링에서의 관점 지향 프로그래밍](#11-스프링에서의-관점-지향-프로그래밍)
    * [11.1 소개](#111-소개)
      * [AOP 컨셉](#aop-컨셉)
      * [Spring AOP 기능 및 목표](#spring-aop-기능-및-목표)
      * [AOP 프록시](#aop-프록시)
    * [11.2 @AspectJ 지원](#112-aspectj-지원)
      * [@AspectJ 지원 가능하게 하기](#aspectj-지원-가능하게-하기)
        * [Java 설정으로 @AspectJ 지원 가능하게 하기](#java-설정으로-aspectj-지원-가능하게-하기)
        * [XML 설정으로 @AspectJ 지원 가능하게 하기](#xml-설정으로-aspectj-지원-가능하게-하기)
      * [aspect 선언](#aspect-선언)
      * [포인트컷 선언](#포인트컷-선언)
        * [지원하는 포인트컷 지정자](#지원하는-포인트컷-지정자)
        * [포인트컷 표현식 결합](#포인트컷-표현식-결합)
        * [공통 포인트컷 정의 공유](#공통-포인트컷-정의-공유)
        * [예제](#예제)
        * [좋은 포인트컷 작성](#좋은-포인트컷-작성)
      * [어드바이스 선언](#어드바이스-선언)
        * [Before 어드바이스](#before-어드바이스)
        * [After returning 어드바이스](#after-returning-어드바이스)
        * [After throwing 어드바이스](#after-throwing-어드바이스)
        * [After (finally) 어드바이스](#after-finally-어드바이스)
        * [Around 어드바이스](#around-어드바이스)
        * [어드바이스 파라미터](#어드바이스-파라미터)
        * [어드바이스 순서 부여](#어드바이스-순서-부여)
      * [소개](#소개)
      * [Aspect 인스턴스화 모델](#aspect-인스턴스화-모델)
      * [예제](#예제-1)
    * [11.3 스키마 기반 AOP 지원](#113-스키마-기반-aop-지원)
      * [aspect 선언](#aspect-선언-1)
      * [포인트컷 선언](#포인트컷-선언-1)
      * [어드바이스 선언](#어드바이스-선언-1)
        * [Before 어드바이스](#before-어드바이스-1)
        * [After returning 어드바이스](#after-returning-어드바이스-1)
        * [After throwing 어드바이스](#after-throwing-어드바이스-1)
        * [After (finally) 어드바이스](#after-finally-어드바이스-1)
        * [Around 어드바이스](#around-어드바이스-1)
        * [어드바이스 파라미터](#어드바이스-파라미터-1)
        * [어드바이스 순서 부여](#어드바이스-순서-부여-1)
      * [소개](#소개-1)
      * [Aspect 인스턴스화 모델](#aspect-인스턴스화-모델-1)
      * [어드바이저](#어드바이저)
      * [예제](#예제-2)
    * [11.4 사용할 AOP 선언 스타일 선택](#114-사용할-aop-선언-스타일-선택)
      * [Spring AOP or full AspectJ?](#spring-aop-or-full-aspectj)
      * [@AspectJ or XML for Spring AOP?](#aspectj-or-xml-for-spring-aop)
    * [11.5 aspect 타입 혼합](#115-aspect-타입-혼합)
    * [11.6 프록시 메카니즘](#116-프록시-메카니즘)
      * [AOP 프록시 이해](#aop-프록시-이해)
    * [11.7 프로그래밍적인 @AspectJ 프록시 생성](#117-프로그래밍적인-aspectj-프록시-생성)
    * [11.8 Spring 어플리케이션과 AspectJ 사용하기](#118-spring-어플리케이션과-aspectj-사용하기)
      * [AspectJ를 사용하여 스프링으로 도메인 객체를 의존성 삽입하기](#aspectj를-사용하여-스프링으로-도메인-객체를-의존성-삽입하기)
        * [@Configurable 객체 유닛 테스트하기](#configurable-객체-유닛-테스트하기)
        * [여러개의 어플리케이션 컨텍스트와 동작하기](#여러개의-어플리케이션-컨텍스트와-동작하기)
      * [AspectJ의 다른 스프링 aspect](#aspectj의-다른-스프링-aspect)
      * [Spring IoC를 이용하여 AspectJ aspect 설정](#spring-ioc를-이용하여-aspectj-aspect-설정)
      * [스프링 프레임워크에서 AspectJ로 로딩 시간 짜기](#스프링-프레임워크에서-aspectj로-로딩-시간-짜기)
        * [첫 번째 예제](#첫-번째-예제)
        * [Aspect](#aspect)
        * ['META-INF/aop.xml'](#meta-infaopxml)
        * [필요 라이브러리(JARS)](#필요-라이브러리jars)
        * [스프링 설정](#스프링-설정)
        * [구체적인 환경 설정](#구체적인-환경-설정)
    * [11.9 자세한 리소스](#119-자세한-리소스)
  * [12. Spring AOP APIs](#12-spring-aop-apis)
    * [12.1](#121)

<!-- tocstop -->


# I. 스프링 프레임워크 개요

## 1. 스프링 프레임워크와 시작하기

## 2. 스프링 프레임워크 소개

### 2.1 의존성 주입과 제어의 역전

### 2.2 프레임워크 모듈

#### 코어 컨

#### AOP와 수단

#### 메시징

#### 데이터 접근/통합

#### 웹

#### 테스트

### 2.3 사용 시나리오

#### 의존성 관리와 네이밍 규약

##### 스프링 의존성들과 스프링에서의 의존

##### Maven 의존성 관리

##### Maven "Bill Of Materials" 의존성

##### Gradle 의존성 관리

##### Ivy 의존성 관리

##### 배포 Zip 파일

#### 로깅

##### Log4j 1.2, 2.x버전 사용

##### Commons Logging 피하기

##### Log4j, Logback으로 Slf4j 사용

##### JUL(java.util.logging) 사용

##### WebSphere에서의 Commons Logging

# II. 스프링 프레임워크 4.x버전에서 새로워진 것들

## 3. 스프링 프레임워크 4.0버전에서 새로운 요소와 나아진 것들

### 3.1 Getting started에서 개선된 것들

### 3.2 사용하지 않는 패키지와 메서드

### 3.3 Java 8 (6과 7 뿐만 아니라)

### 3.4 Java EE 6과 7

### 3.5 Groovy 빈 정의 DSL

### 3.6 코어 컨테이너 개선점

### 3.7 일반적인 웹 개선점

### 3.8 웹소켓, SockJS, STOMP 메시징

### 3.9 테스팅 개선점

## 4. 스프링 프레임워크 4.1버전에서 새로운 요소와 나아진 것들

### 4.1 JMS 개선점

### 4.2 캐싱 개선점

### 4.3 웹 개선점

### 4.4 웹소켓 메시징 개선점

### 4.5 테스팅 개선점

## 5. 스프링 프레임워크 4.2버전에서 새로운 요소와 나아진 것들

### 5.1 코어 컨테이너 개선점

### 5.2 데이터 접근 개선점

### 5.3 JMS 개선점

### 5.4 웹 개선점

### 5.5 웹소켓 메시징 개선점

### 5.6 테스팅 개선점

## 6. 스프링 프레임워크 4.3버전에서 새로운 요소와 나아진 것들

### 6.1 코어 컨테이너 개선점

### 6.2 데이터 접근 개선점

### 6.3 캐싱 개선점

### 6.4 JMS 개선점

### 6.5 웹 개선점

### 6.6 웹소켓 메시징 개선점

### 6.7 테스팅 개선점

### 6.8 새로운 라이브러리 및 서버 세대 지원

# III. 코어 기술

## 7. IoC 컨테이너

### 7.1 스프링 IoC 컨테이너와 빈에 대한 소개

### 7.2 컨테이너 개요

#### 설정 메타데이터

#### 컨테이너 인스턴스화하기

##### XML 기반 구성 메타데이터 작성

##### Groovy 빈 정의 DSL

#### 컨테이너 사용하기

### 7.3 빈 개요

#### 빈 네이밍

##### 빈 정의 바깥에서 빈에 별칭 부여하기

#### 빈 인스턴스화하기

##### 생성자로 인스턴스화하기

##### 정적 팩토리 메서드로 인스턴스화하기

##### 인스턴스 팩토리 메서드로 인스턴스화하기

### 7.4 의존성

#### 의존성 주입

##### 생성자 기반 의존성 주입

##### Setter 기반 의존성 주입

##### 의존성 해결 프로세스

##### 의존성 주입 예시

#### 의존성과 상세 설정

##### 프리미티브 타입, 문자열 등 값

##### 다른 빈 참조 (공동 작업자)

##### 내부 빈

##### 컬렉션

##### null과 빈 문자열 값

##### p-namespace를 이용한 XML 바로가기

##### c-namespace를 이용한 XML 바로가기

##### 복합 속성 이름

#### 의존성 사용

#### 늦게 초기화되는 빈

#### Autowiring 공동 작업자

##### autowiring의 한계와 단점

##### autowiring으로부터 빈 제외

#### 메서드 주입

##### Lookup 메서드 주입

##### 임의의 메서드 대체

### 7.5 빈 스코프

#### 싱글톤 스코프

#### 프로토타입 스코프

#### 싱글톤 빈과 프로토타입 빈 의존성

#### Request, session, global session, application 그리고 웹 소켓 스코프

##### 초기 웹 설정

##### Request 스코프

##### Session 스코프

##### Global session 스코프

##### Application 스코프

##### 의존성으로서의 스코프화된 빈

#### 커스텀 스코프

##### 커스텀 스코프 생성

##### 커스텀 스코프 사용

### 7.6 빈의 성질 커스터마이징

#### 라이프사이클 콜백

##### 초기화 콜백

##### 소멸 콜백

##### 기본 초기화와 소멸 메서드

##### 라이프사이클 매커니즘 결합

##### 시작과 종료 콜백

##### 웹 어플리케이션이 아닌 환경에서 스프링 IoC 컨테이너 우아하게 종료하기

#### ApplicationContextAware와 BeanNameAware

#### 그 밖에 Aware 인터페이스

### 7.7 빈 정의 상속

### 7.8 컨테이너 확대 포인트

#### BeanPostProcessor를 이용한 빈 커스터마이징

##### 예제 : Hello World, BeanPostProcessor-style

##### 예제 : The RequiredAnnotationBeanPostProcessor

#### BeanFactoryPostProcessor와 설정 메타데이터 커스터마이징

##### 예제 : 클래스네임 치환 PropertyPlaceholderConfigurer

##### 예제 : PropertyOverrideConfigurer

#### FactoryBean을 이용한 인스턴스화 로직 커스터마이징

### 7.9 Annotation 기반 컨테이너 설정

#### @Required

#### @Autowired

#### @Primary를 이용한 Annotation 기반 autowiring 미세 조정

#### 한정자를 이용한 Annotation 기반 autowiring 미세 조정

#### autowiring 한정자로서 제네릭 사용

#### CustomAutowireConfigurer

#### @Resource

#### @PostConstruct와 @PreDestroy

### 7.10 클래스패스 스캔과 컴포넌트 관리

#### @Component와 추가 스테레오타입 annotation

#### 메타 annotation

#### 자동으로 클래스 탐지와 빈 정의 등록하기

#### 필터를 사용하여 scanning 커스터마이징하기

#### 컴포넌트 내에서 빈 메타데이터 정의

#### 자동탐지 컴포넌트 네이밍

#### 자동탐지 컴포넌트를 위한 스코프 제공

#### annotation을 이용하여 메타데이터 한정자 제공

### 7.11 JSR 330 표준 annotation 사용

#### @Inject와 @Named를 이용한 의존성 주입

#### @Named와 @ManagedBean: @Component에 표준 동급

#### JSR-330 표준 annotation의 한계

### 7.12 Java 기반 컨테이너 설정

#### 기본 컨셉: @Bean과 @Configuration

#### AnnotationConfigApplicationContext를 이용한 스프링 컨테이너 인스턴스화

##### 간단한 구성

##### 레지스터(Class<?>...)를 이용한 프로그래밍적인 컨테이너 빌드

##### scan(String...)을 이용한 컴포넌트 scanning 사용가능하게 하기

##### 웹 어플리케이션과 AnnotationConfigWebApplicationContext에 대한 지원

#### @Bean annotation 사용하기

##### 빈 선언하기

##### 빈 의존성

##### 라이프사이클 콜백 받기

##### 빈 스코프 명시하기

##### 빈 네이밍 커스터마이징

##### 빈에 별칭 달기

##### 빈 기술하기

#### @Configuration annotation 사용하기

##### 내부 빈 의존성 주입

##### Lookup 메서드 주입

##### Java 기반 설정이 내부적으로 어떻게 동작하는 지에 대한 자세한 정보

#### Java 기반 설정 작성하기

##### @Import annotation 사용하기

##### 조건부로 @Configuration 클래스나 @Bean 메서드 포함하기

##### Java와 XML 설정 결합

### 7.13 환경 추출

#### 빈 정의 프로파일

##### @Profile

##### XML 빈 정의 프로파일

##### 프로파일 활성화하기

##### 기본 프로파일

#### PropertySource 추출

#### @PropertySource

#### 문장 내 지시자로 해결

### 7.14 LoadTimeWeaver 등록

### 7.15 ApplicationContext의 추가적인 기능

#### MessageSource를 이용한 국제화

#### 표준, 그리고 커스텀 이벤트

##### annotation 기반 이벤트 리스너

##### 비동기 리스너

##### 주문 리스너

##### 제네릭 이벤트

#### 로우 레벨 리소스에 대한 편리한 접근

#### 웹 어플리케이션에서 편리하게 ApplicationContext 인스턴스화하기

#### Java EE RAR 파일로 스프링 ApplicationContext 디플로이하기

### 7.16 BeanFactory

####  BeanFactory or ApplicationContext?

#### Glue code와 사악한 싱글톤

## 8. 리소스

### 8.1 소개

### 8.2 리소스 인터페이스

### 8.3 내장 리소스 구현

#### UrlResource

#### ClassPathResouce

#### FileSystemResource

#### ServletContextResource

#### InputStreamResource

#### ByteArrayResource

### 8.4 ResourceLoader

### 8.5 ResourceLoaderAware 인터페이스

### 8.6 의존성으로써의 리소스

### 8.7 어플리케이션 컨텍스트와 리소스 패스

#### 어플리케이션 컨텍스트 만들기

##### ClassPathXmlApplicationContext 인스턴스 만들기 - 단축키

#### 어플리케이션 컨텍스트 생성자 리소스 패스에서의 와일드카드

##### Ant 스타일 패턴

##### Classpath*: 이식성 classpath*: 접두사

##### 그 밖에 와일드카드와 관련된 노트

#### FileSystemResource 주의사항

## 9. 유효성, 데이터 바인딩, 그리고 타입 컨벤션

### 9.1 소개

### 9.2 스프링의 유효성 검사 인터페이스를 이용한 유효성 검사

### 9.3 에러 메시지에 대한 해결 코드

### 9.4 빈 조작과 BeanWrapper

#### 기본 및 중첩된 속성 세팅과 가져오기

#### 내장 PropertyEditor 구현

##### 추가적인 커스텀 PropertyEditor 등록

### 9.5 스프링 타입 컨벤션

#### Converter SPI

#### ConverterFactory

#### GenericConverter

##### ConditionalGenericConverter

#### ConversionService API

#### ConversionService 설정

#### ConversionService 프로그래밍적으로 사용하기

### 9.6 스프링 필드 포맷

#### Formatter SPI

#### Annotation 중심 포맷

##### Format Annotation API

#### FormatterRegistry SPI

#### FormatterRegister SPI

#### Spring MVC에서 포맷 설정

### 9.7 글로벌 date & time 포맷 설정

### 9.8 스프링 유효성 검사

#### JSR-303 빈 유효성 검사 API 개요

#### 빈 유효성 검사 프로바이더 설정

##### Validator 주입

##### 커스텀 제약조건 설정

##### 스프링 중심의 메서드 유효성 검사

##### 추가적인 설정 옵션

#### DataBinder 설정

#### Spring MVC 3 유효성 검사

## 10. Spring Expression Language (SpEL)

### 10.1 소개

### 10.2 구성요소 개요

### 10.3 스프링 Expressin 인터페이스를 이용한 표현식 평가

#### EvaluationContext 인터페이스

##### 타입 컨벤션

#### 파서 설정

#### SpEL 컴파일

##### 컴파일러 설정

##### 컴파일러 한계

### 10.4 빈 정의를 정의하기 위한 표현식 지원

#### XML 기반 설정

#### Annotation 기반 설정

### 10.5 언어 참조

#### 리터럴 표현식

#### 프로퍼티, Array, List, Map, Indexer

#### 인라인 List

#### 인라인 Map

#### Array 구성

#### 메서드

#### 연산자

##### 관계 연산자

##### 논리 연산자

##### 수학 연산자

#### 할당

#### 타입

#### 생성자

#### 변수

##### #this와 #root 변수

#### 함수

#### 빈 참조

#### 삼항 연산자

#### Elvis 연산자

#### Safe Navigation 연산자

#### 컬렉션 셀렉션

#### 컬렉션 프로젝션

#### 표현식 템플릿

### 10.6 예제에 사용된 클래스

## 11. 스프링에서의 관점 지향 프로그래밍

### 11.1 소개

#### AOP 컨셉

#### Spring AOP 기능 및 목표

#### AOP 프록시

### 11.2 @AspectJ 지원

#### @AspectJ 지원 가능하게 하기

##### Java 설정으로 @AspectJ 지원 가능하게 하기

##### XML 설정으로 @AspectJ 지원 가능하게 하기

#### aspect 선언

#### 포인트컷 선언

##### 지원하는 포인트컷 지정자

##### 포인트컷 표현식 결합

##### 공통 포인트컷 정의 공유

##### 예제

##### 좋은 포인트컷 작성

#### 어드바이스 선언

##### Before 어드바이스

##### After returning 어드바이스

##### After throwing 어드바이스

##### After (finally) 어드바이스

##### Around 어드바이스

##### 어드바이스 파라미터

##### 어드바이스 순서 부여

#### 소개

#### Aspect 인스턴스화 모델

#### 예제

### 11.3 스키마 기반 AOP 지원

#### aspect 선언

#### 포인트컷 선언

#### 어드바이스 선언

##### Before 어드바이스

##### After returning 어드바이스

##### After throwing 어드바이스

##### After (finally) 어드바이스

##### Around 어드바이스

##### 어드바이스 파라미터

##### 어드바이스 순서 부여

#### 소개

#### Aspect 인스턴스화 모델

#### 어드바이저

#### 예제

### 11.4 사용할 AOP 선언 스타일 선택

#### Spring AOP or full AspectJ?

#### @AspectJ or XML for Spring AOP?

### 11.5 aspect 타입 혼합

### 11.6 프록시 메카니즘

#### AOP 프록시 이해

### 11.7 프로그래밍적인 @AspectJ 프록시 생성

### 11.8 Spring 어플리케이션과 AspectJ 사용하기

#### AspectJ를 사용하여 스프링으로 도메인 객체를 의존성 삽입하기

##### @Configurable 객체 유닛 테스트하기

##### 여러개의 어플리케이션 컨텍스트와 동작하기

#### AspectJ의 다른 스프링 aspect

#### Spring IoC를 이용하여 AspectJ aspect 설정

#### 스프링 프레임워크에서 AspectJ로 로딩 시간 짜기

##### 첫 번째 예제

##### Aspect

##### 'META-INF/aop.xml'

##### 필요 라이브러리(JARS)

##### 스프링 설정

##### 구체적인 환경 설정

### 11.9 자세한 리소스

## 12. Spring AOP APIs

### 12.1
