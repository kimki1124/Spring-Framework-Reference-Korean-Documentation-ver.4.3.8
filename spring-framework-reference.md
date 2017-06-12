# 스프링 프레임워크 레퍼런스 문서 Ver. 4.3.8 RELEASE

이 문서의 복사본들은 개인이 사용하거나 타인에게 배포할 수 있다. 어떠한 비용 없이 제공되어지고, 각 복사본에는 인쇄물 혹은 전자 형식으로 카피라이트 통지가 있어야 한다.

- - -
# 목차


<!-- toc orderedList:0 depthFrom:1 depthTo:6 -->

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
    * [12.1 소개](#121-소개)
    * [12.2 스프링에서의 포인트컷 API](#122-스프링에서의-포인트컷-api)
      * [컨셉](#컨셉)
      * [포인트컷 조작](#포인트컷-조작)
      * [AspectJ 표현식 포인트컷](#aspectj-표현식-포인트컷)
      * [편리한 포인트컷 구현](#편리한-포인트컷-구현)
        * [정적 포인트컷](#정적-포인트컷)
        * [동적 포인트컷](#동적-포인트컷)
      * [포인트컷 슈퍼클래스](#포인트컷-슈퍼클래스)
      * [커스텀 포인트컷](#커스텀-포인트컷)
    * [12.3 스프링에서의 어드바이스 API](#123-스프링에서의-어드바이스-api)
      * [어드바이스 라이프사이클](#어드바이스-라이프사이클)
      * [스프링에서의 어드바이스 타입](#스프링에서의-어드바이스-타입)
        * [Interception around 어드바이스](#interception-around-어드바이스)
        * [Before 어드바이스](#before-어드바이스-2)
        * [Throws 어드바이스](#throws-어드바이스)
        * [After Returning 어드바이스](#after-returning-어드바이스-2)
        * [Introduction 어드바이스](#introduction-어드바이스)
    * [12.4 스프링에서의 어드바이저 API](#124-스프링에서의-어드바이저-api)
    * [12.5 AOP 프록시를 만들기 위한 ProxyFactoryBean 사용](#125-aop-프록시를-만들기-위한-proxyfactorybean-사용)
      * [기본](#기본)
      * [JavaBean 프로퍼티](#javabean-프로퍼티)
      * [JDK와 CGLIB 기반 프록시](#jdk와-cglib-기반-프록시)
      * [프록시 인터페이스](#프록시-인터페이스)
      * [프록시 클래스](#프록시-클래스)
      * [글로벌 어드바이저 사용](#글로벌-어드바이저-사용)
    * [12.6 간결한 프록시 정의](#126-간결한-프록시-정의)
    * [12.7 ProxyFactory를 이용한 프로그래밍적으로 AOP 프록시 생성](#127-proxyfactory를-이용한-프로그래밍적으로-aop-프록시-생성)
    * [12.8 어드바이저 객체 조작](#128-어드바이저-객체-조작)
    * [12.9 auto-proxy 기능 사용](#129-auto-proxy-기능-사용)
      * [Autoproxy 빈 정의](#autoproxy-빈-정의)
        * [BeanNameAutoProxyCreator](#beannameautoproxycreator)
        * [DefaultAdvisorAutoProxyCreator](#defaultadvisorautoproxycreator)
        * [AbstractAdvisorAutoProxyCreator](#abstractadvisorautoproxycreator)
      * [메타데이터 중심의 auto-proxy 사용](#메타데이터-중심의-auto-proxy-사용)
    * [12.10 TargetSource 사용](#1210-targetsource-사용)
      * [핫 스왑가능한 타겟 소스](#핫-스왑가능한-타겟-소스)
      * [풀링 타겟 소스](#풀링-타겟-소스)
      * [프로토타입 타겟 소스](#프로토타입-타겟-소스)
      * [ThreadLocal 타겟 소스](#threadlocal-타겟-소스)
    * [12.11 새로운 어드바이스 타입 정의](#1211-새로운-어드바이스-타입-정의)
    * [12.12 자세한 리소스](#1212-자세한-리소스)
* [IV. 테스팅](#iv-테스팅)
  * [13. 스프링 테스팅 소개](#13-스프링-테스팅-소개)
  * [14. 유닛 테스팅](#14-유닛-테스팅)
    * [14.1 Mock 객체](#141-mock-객체)
      * [환경](#환경)
      * [JNDI](#jndi)
      * [Servlet API](#servlet-api)
      * [Portlet API](#portlet-api)
    * [14.2 유닛 테스팅 지원 클래스](#142-유닛-테스팅-지원-클래스)
      * [일반적인 테스팅 유틸리티](#일반적인-테스팅-유틸리티)
      * [Spring MVC](#spring-mvc)
  * [15. 통합 테스팅](#15-통합-테스팅)
    * [15.1 개요](#151-개요)
    * [15.2 통합 테스팅의 목적](#152-통합-테스팅의-목적)
      * [컨텍스트 관리 및 캐싱](#컨텍스트-관리-및-캐싱)
      * [테스트 픽스처의 의존성 주입](#테스트-픽스처의-의존성-주입)
      * [트랜잭션 관리](#트랜잭션-관리)
      * [통합 테스팅을 위한 지원 클래스](#통합-테스팅을-위한-지원-클래스)
    * [15.3 JDBC 테스팅 지원](#153-jdbc-테스팅-지원)
    * [15.4 Annotation](#154-annotation)
      * [스프링 테스팅 annotation](#스프링-테스팅-annotation)
        * [@BootstrapWith](#bootstrapwith)
        * [@ContextConfiguration](#contextconfiguration)
        * [@WebAppConfiguration](#webappconfiguration)
        * [@ContextHierarchy](#contexthierarchy)
        * [@ActiveProfiles](#activeprofiles)
        * [@TestPropertySource](#testpropertysource)
        * [@DirtiesContext](#dirtiescontext)
        * [@TestExecutionListeners](#testexecutionlisteners)
        * [@Commit](#commit)
        * [@Rollback](#rollback)
        * [@BeforeTransaction](#beforetransaction)
        * [@AfterTransaction](#aftertransaction)
        * [@Sql](#sql)
        * [@SqlConfig](#sqlconfig)
        * [@SqlGroup](#sqlgroup)
      * [표준 annotation 지원](#표준-annotation-지원)
      * [스프링 JUnit 4 테스팅 annotation](#스프링-junit-4-테스팅-annotation)
        * [@IfProfileValue](#ifprofilevalue)
        * [@ProfileValueSourceConfiguration](#profilevaluesourceconfiguration)
        * [@Timed](#timed)
        * [@Repeat](#repeat)
      * [테스팅을 위한 메타-annotation 지원](#테스팅을-위한-메타-annotation-지원)
    * [15.5 스프링 TestContext 프레임워크](#155-스프링-testcontext-프레임워크)
      * [주요 추상화](#주요-추상화)
        * [TestContext](#testcontext)
        * [TestContextManager](#testcontextmanager)
        * [TestExecutionListener](#testexecutionlistener)
        * [컨텍스트 로더](#컨텍스트-로더)
      * [TestContext 프레임워크 부트스트래핑하기](#testcontext-프레임워크-부트스트래핑하기)
      * [TestExecutionListener 설정](#testexecutionlistener-설정)
        * [커스텀 TestExecutionListener 등록](#커스텀-testexecutionlistener-등록)
        * [기본 TestExecutionListener의 자동 검색](#기본-testexecutionlistener의-자동-검색)
        * [TestExecutionListener 순서 지정](#testexecutionlistener-순서-지정)
        * [TestExecutionListener 병합](#testexecutionlistener-병합)
      * [컨텍스트 관리](#컨텍스트-관리)
        * [XML 리소스로 컨텍스트 설정](#xml-리소스로-컨텍스트-설정)
        * [Groovy 스크립트로 컨텍스트 설정](#groovy-스크립트로-컨텍스트-설정)
        * [annotated 클래스로 컨텍스트 설정](#annotated-클래스로-컨텍스트-설정)
        * [XML, Groovy 스크립트, annotated 클래스 같이 쓰기](#xml-groovy-스크립트-annotated-클래스-같이-쓰기)
        * [컨텍스트 이니셜라이저로 컨텍스트 설정](#컨텍스트-이니셜라이저로-컨텍스트-설정)
        * [컨텍스트 설정 계승](#컨텍스트-설정-계승)
        * [환경 프로파일로 컨텍스트 설정](#환경-프로파일로-컨텍스트-설정)
        * [테스트 프로퍼티 소스로 컨텍스트 설정](#테스트-프로퍼티-소스로-컨텍스트-설정)
        * [WebApplicationContext 로딩](#webapplicationcontext-로딩)
        * [컨텍스트 캐싱](#컨텍스트-캐싱)
        * [컨텍스트 계층화](#컨텍스트-계층화)
      * [테스트 픽스쳐의 의존성 주입](#테스트-픽스쳐의-의존성-주입)
      * [테스팅 request, session 스코프 빈](#테스팅-request-session-스코프-빈)
      * [트랜잭션 관리](#트랜잭션-관리-1)
        * [테스트 관리 트랜잭션](#테스트-관리-트랜잭션)
        * [트랜잭션 활성화와 비활성화](#트랜잭션-활성화와-비활성화)
        * [트랜잭션 롤백 및 동작](#트랜잭션-롤백-및-동작)
        * [프로그래밍 방식의 트랜잭션 관리](#프로그래밍-방식의-트랜잭션-관리)
        * [트랜잭션 외부의 코드 실행](#트랜잭션-외부의-코드-실행)
        * [트랜잭션 매니저 설정](#트랜잭션-매니저-설정)
        * [모든 트랜잭션과 관련된 annotation 시연](#모든-트랜잭션과-관련된-annotation-시연)
      * [SQL 스크립트 실행](#sql-스크립트-실행)
        * [프로그래밍 방식으로 SQL 스트립트 실행](#프로그래밍-방식으로-sql-스트립트-실행)
        * [@Sql을 사용하여 선언적으로 SQL 스크립트 실행](#sql을-사용하여-선언적으로-sql-스크립트-실행)
      * [TestContext 프레임워크가 지원하는 클래스](#testcontext-프레임워크가-지원하는-클래스)
        * [스프링 JUnit 4 Runner](#스프링-junit-4-runner)
        * [스프링 JUnit 4 Rules](#스프링-junit-4-rules)
        * [JUnit 4가 지원하는 클래스](#junit-4가-지원하는-클래스)
        * [TestNG가 지원하는 클래스](#testng가-지원하는-클래스)
    * [15.6 Spring MVC 테스트 프레임워크](#156-spring-mvc-테스트-프레임워크)
      * [서버 사이드 테스트](#서버-사이드-테스트)
        * [정적 임포트](#정적-임포트)
        * [설정 옵션](#설정-옵션)
        * [Request 수행하기](#request-수행하기)
        * [기대 정의](#기대-정의)
        * [필터 등록](#필터-등록)
        * [Out-of-Container와 End-to-End 통합 테스트의 차이점](#out-of-container와-end-to-end-통합-테스트의-차이점)
        * [자세한 서버 사이드 테스트 예제](#자세한-서버-사이드-테스트-예제)
      * [HtmlUnit 통하](#htmlunit-통하)
        * [왜 HtmlUnit 통합?](#왜-htmlunit-통합)
        * [MockMvc와 HtmlUnit](#mockmvc와-htmlunit)
        * [MockMvc와 WebDriver](#mockmvc와-webdriver)
        * [MockMvc와 Geb](#mockmvc와-geb)
      * [클라이언트 사이드 REST 테스트](#클라이언트-사이드-rest-테스트)
        * [정적 임포트](#정적-임포트-1)
        * [클라이언트 사이드 REST 테스트의 자세한 예제](#클라이언트-사이드-rest-테스트의-자세한-예제)
    * [15.7 PetClinic 예제](#157-petclinic-예제)
  * [16. 자세한 리소스](#16-자세한-리소스)
* [V. 데이터 접근](#v-데이터-접근)
  * [17. 트랜잭션 관리](#17-트랜잭션-관리)
    * [17.1 스프링 프레임워크 트랜잭션 관리에 대한 소개](#171-스프링-프레임워크-트랜잭션-관리에-대한-소개)
    * [17.2 스프링 프레임워크의 트랜잭션 지원 모델의 이점](#172-스프링-프레임워크의-트랜잭션-지원-모델의-이점)
      * [글로벌 트랜잭션](#글로벌-트랜잭션)
      * [로컬 트랜잭션](#로컬-트랜잭션)
      * [스프링 프레임워크의 일관된 프로그래밍 모델](#스프링-프레임워크의-일관된-프로그래밍-모델)
    * [17.3 스프링 프레임워크 트랜잭션 추출 이해](#173-스프링-프레임워크-트랜잭션-추출-이해)
    * [17.4 트랜잭션과 동기적 리소스](#174-트랜잭션과-동기적-리소스)
      * [높은 수준의 동기화 접근 방식](#높은-수준의-동기화-접근-방식)
      * [낮은 수준의 동기화 접근 방식](#낮은-수준의-동기화-접근-방식)
      * [TransactionAwareDataSourceProxy](#transactionawaredatasourceproxy)
    * [17.5 선언적인 트랜잭션 관리](#175-선언적인-트랜잭션-관리)
      * [스프링 프레임워크의 선언적인 트랜잭션 구현 이해](#스프링-프레임워크의-선언적인-트랜잭션-구현-이해)
      * [선언적인 트랜잭션 구현의 예제](#선언적인-트랜잭션-구현의-예제)
      * [선언적인 트랜잭션 롤백](#선언적인-트랜잭션-롤백)
      * [다른 빈에 대해 다른 트랜잭션 의미 설정](#다른-빈에-대해-다른-트랜잭션-의미-설정)
      * [<tx:advice /> 세팅](#txadvice-세팅)
      * [@Transactional 사용](#transactional-사용)
        * [@Transactional 세팅](#transactional-세팅)
        * [여러 개의 트랜잭션 매니저와 @Transactional](#여러-개의-트랜잭션-매니저와-transactional)
        * [커스텀 숏컷 annotation](#커스텀-숏컷-annotation)
      * [트랜잭션 전파](#트랜잭션-전파)
        * [Required](#required-1)
        * [RequiresNew](#requiresnew)
        * [Nested](#nested)
      * [트랜잭션 작업에 대한 조언](#트랜잭션-작업에-대한-조언)
      * [@Transactional과 AspectJ 사용하기](#transactional과-aspectj-사용하기)
    * [17.6 프로그래밍적인 트랜잭션 관리](#176-프로그래밍적인-트랜잭션-관리)
      * [트랜잭션 템플릿 사용](#트랜잭션-템플릿-사용)
        * [트랜젝션 세팅 지정](#트랜젝션-세팅-지정)
      * [PlatformTransactionManager 사용](#platformtransactionmanager-사용)
    * [17.7 프로그래밍 방식 및 선언적 트랜잭션 관리 중에서 선택하기](#177-프로그래밍-방식-및-선언적-트랜잭션-관리-중에서-선택하기)
    * [17.8 트랜잭션 바운드 이벤트](#178-트랜잭션-바운드-이벤트)
    * [17.9 어플리케이션 서버 지정 통합](#179-어플리케이션-서버-지정-통합)
      * [IBM WebSphere](#ibm-websphere)
      * [Oracle WebLogic Server](#oracle-weblogic-server)
    * [17.10 공통 문제의 해결책](#1710-공통-문제의-해결책)
      * [특정 DataSource에 대해 잘못된 트랜잭션 매니저 사용](#특정-datasource에-대해-잘못된-트랜잭션-매니저-사용)
    * [17.11 자세한 리소스](#1711-자세한-리소스)
  * [18. DAO 지원](#18-dao-지원)
    * [18.1 소개](#181-소개)
    * [18.2 일관된 예외 계층 구조](#182-일관된-예외-계층-구조)
    * [18.3 DAO 또는 Repository 클래스 구성에 사용되는 주석](#183-dao-또는-repository-클래스-구성에-사용되는-주석)
  * [19. JDBC를 이용한 데이터 접근](#19-jdbc를-이용한-데이터-접근)
    * [19.1 스프링 프레임워크 JDBC 소개](#191-스프링-프레임워크-jdbc-소개)
      * [JDBC 데이터베이스 액세스에 대한 접근 방식 선택](#jdbc-데이터베이스-액세스에-대한-접근-방식-선택)
      * [패키지 계층](#패키지-계층)
    * [19.2 JDBC 핵심 클래스를 사용하여 기본 JDBC 처리 및 오류 제어](#192-jdbc-핵심-클래스를-사용하여-기본-jdbc-처리-및-오류-제어)
      * [핸들링](#핸들링)
      * [JdbcTemplate](#jdbctemplate)
        * [JdbcTemplate 클래스 사용 예제](#jdbctemplate-클래스-사용-예제)
        * [JdbcTemplate 모범 사례](#jdbctemplate-모범-사례)
      * [NamedParameterJdbcTemplate](#namedparameterjdbctemplate)
      * [SQLExceptionTranslator](#sqlexceptiontranslator)
      * [Executing statements](#executing-statements)
      * [명령문 실행](#명령문-실행)
      * [쿼리문 실행](#쿼리문-실행)
      * [데이터베이스 업데이트](#데이터베이스-업데이트)
      * [자동 생성 키 가져오기](#자동-생성-키-가져오기)
    * [19.3 데이터베이스 커넥션 제어](#193-데이터베이스-커넥션-제어)
      * [DataSource](#datasource)
      * [DataSourceUtils](#datasourceutils)
      * [SmartDataSource](#smartdatasource)
      * [AbstractDataSource](#abstractdatasource)
      * [SingleConnectionDataSource](#singleconnectiondatasource)
      * [DriverManagerDataSource](#drivermanagerdatasource)
      * [TransactionAwareDataSourceProxy](#transactionawaredatasourceproxy-1)
      * [DataSourceTransactionManager](#datasourcetransactionmanager)
      * [NativeJdbcExtractor](#nativejdbcextractor)
    * [19.4 JDBC 배치 연산](#194-jdbc-배치-연산)
      * [JdbcTemplate 기본 배치 작업](#jdbctemplate-기본-배치-작업)
      * [객체 목록으로 배치 작업](#객체-목록으로-배치-작업)
      * [여러 배치로 배치 작업](#여러-배치로-배치-작업)
    * [19.5 SimpleJdbc 클래스를 사용하여 JDBC 작업 단순화](#195-simplejdbc-클래스를-사용하여-jdbc-작업-단순화)
      * [SimpleJdbcInsert를 이용하여 데이터 삽입](#simplejdbcinsert를-이용하여-데이터-삽입)
      * [SimpleJdbcInsert를 이용하여 자동 생성 키 가져오기](#simplejdbcinsert를-이용하여-자동-생성-키-가져오기)
      * [SimpleJdbcInsert의 컬럼 지정](#simplejdbcinsert의-컬럼-지정)
      * [SqlParameterSource를 사용하여 매개 변수 값 제공](#sqlparametersource를-사용하여-매개-변수-값-제공)
      * [SimpleJdbcCall을 사용하여 스토어드 프로시저 호출](#simplejdbccall을-사용하여-스토어드-프로시저-호출)
      * [SimpleJdbcCall에 사용할 매개 변수를 명시적으로 선언](#simplejdbccall에-사용할-매개-변수를-명시적으로-선언)
      * [SqlParameters 정의하는 방법](#sqlparameters-정의하는-방법)
      * [SimpleJdbcCall을 이용하여 저장되있는 함수 호출](#simplejdbccall을-이용하여-저장되있는-함수-호출)
      * [SimpleJdbcCall에서 ResultSet / REF 커서 리턴하기](#simplejdbccall에서-resultset-ref-커서-리턴하기)
    * [19.6 JDBC 작업을 Java 객체로 모델링](#196-jdbc-작업을-java-객체로-모델링)
      * [SqlQuery](#sqlquery)
      * [MappingSqlQuery](#mappingsqlquery)
      * [SqlUpdate](#sqlupdate)
      * [StoredProcedure](#storedprocedure)
    * [19.7 매개 변수 및 데이터 값 처리와 관련된 일반적인 문제](#197-매개-변수-및-데이터-값-처리와-관련된-일반적인-문제)
      * [파라미터의 SQL 타입 정보의 제공](#파라미터의-sql-타입-정보의-제공)
      * [BLOB, CLOB 객체 핸들링](#blob-clob-객체-핸들링)
      * [IN 절에 대한 값 목록 전달](#in-절에-대한-값-목록-전달)
      * [스토어드 프로시저 호출의 복잡한 유형 처리](#스토어드-프로시저-호출의-복잡한-유형-처리)
    * [19.8 임베디드 데이터베이스 지원](#198-임베디드-데이터베이스-지원)
      * [왜 임베디드 데이터베이스를 사용해야 하는가?](#왜-임베디드-데이터베이스를-사용해야-하는가)
      * [Spring XML을 이용한 임베디드 데이터베이스 생성](#spring-xml을-이용한-임베디드-데이터베이스-생성)
      * [프로그래밍적으로 임베디드 데이터베이스 생성](#프로그래밍적으로-임베디드-데이터베이스-생성)
      * [임베디드 데이터베이스 타입 선택](#임베디드-데이터베이스-타입-선택)
        * [HSQL 사용](#hsql-사용)
        * [H2 사용](#h2-사용)
        * [Derby 사용](#derby-사용)
      * [임베디드 데이터베이스로 데이터 접근 로직 테스트](#임베디드-데이터베이스로-데이터-접근-로직-테스트)
      * [임베디드 데이터베이스로 유니크 이름 생성](#임베디드-데이터베이스로-유니크-이름-생성)
      * [임베디드 데이터베이스 지원 확장](#임베디드-데이터베이스-지원-확장)
    * [19.9 DataSource 초기화](#199-datasource-초기화)
      * [Spring XML을 사용하여 데이터베이스 초기화](#spring-xml을-사용하여-데이터베이스-초기화)
        * [데이터베이스에 의존하는 다른 구성 요소의 초기화](#데이터베이스에-의존하는-다른-구성-요소의-초기화)
  * [20. 객체 관계 매핑 (ORM) 데이터 액세스](#20-객체-관계-매핑-orm-데이터-액세스)
    * [20.1 스프링과 ORM 소개](#201-스프링과-orm-소개)
    * [20.2 일반적인 ORM 통합 고려사항](#202-일반적인-orm-통합-고려사항)
      * [리소스와 트랜잭션 관리](#리소스와-트랜잭션-관리)
      * [예외 변환](#예외-변환)
    * [20.3 Hibernate](#203-hibernate)
      * [스프링 컨테이너에서 SessionFactory 설정](#스프링-컨테이너에서-sessionfactory-설정)
      * [기본 Hibernate API에 기반한 DAO 구현하기](#기본-hibernate-api에-기반한-dao-구현하기)
      * [선언적 트랜잭션 구분](#선언적-트랜잭션-구분)
      * [프로그래밍적인 트랜잭션 구분](#프로그래밍적인-트랜잭션-구분)
      * [트랜잭션 관리 전략](#트랜잭션-관리-전략)
      * [컨테이너 관리 및 로컬 정의 리소스 비교](#컨테이너-관리-및-로컬-정의-리소스-비교)
      * [Hibernate로 비논리적인 응용 프로그램 서버 경고](#hibernate로-비논리적인-응용-프로그램-서버-경고)
    * [20.4 JDO](#204-jdo)
      * [PersistenceManagerFactory 셋업](#persistencemanagerfactory-셋업)
      * [기본 JDO API에 기반한 DAO 구현하기](#기본-jdo-api에-기반한-dao-구현하기)
      * [트랜잭션 관리](#트랜잭션-관리-2)
      * [JdoDialect](#jdodialect)
    * [20.5 JPA](#205-jpa)
      * [스프링 환경에서 JPA 셋업을 위한 세 가지 옵션](#스프링-환경에서-jpa-셋업을-위한-세-가지-옵션)
        * [LocalEntityManagerFactoryBean](#localentitymanagerfactorybean)
        * [JNDI로부터 EntityManagerFactory 얻기](#jndi로부터-entitymanagerfactory-얻기)
        * [LocalContainerEntityManagerFactoryBean](#localcontainerentitymanagerfactorybean)
        * [다중 퍼시스턴스 유닛 다루기](#다중-퍼시스턴스-유닛-다루기)
      * [JPA에 기반한 DAO 구현 : EntityManagerFactory 및 EntityManager](#jpa에-기반한-dao-구현-entitymanagerfactory-및-entitymanager)
      * [스프링 중심의 JPA 트랜잭션](#스프링-중심의-jpa-트랜잭션)
      * [JpaDialect 및 JpaVendorAdapter](#jpadialect-및-jpavendoradapter)
      * [JTA 트랜잭션 관리로 JPA 세팅](#jta-트랜잭션-관리로-jpa-세팅)
  * [21. O/X 매퍼를 사용한 XML 마샬링](#21-ox-매퍼를-사용한-xml-마샬링)
    * [21.1 소개](#211-소개)
      * [쉬운 구성](#쉬운-구성)
      * [일관된 인터페이스](#일관된-인터페이스)
      * [일관된 예외 계층](#일관된-예외-계층)
    * [21.2 마샬러 및 언마샬러](#212-마샬러-및-언마샬러)
      * [마샬러](#마샬러)
      * [언마샬러](#언마샬러)
      * [XmlMappingException](#xmlmappingexception)
    * [21.3 마샬러 및 언마샬러 사용](#213-마샬러-및-언마샬러-사용)
    * [21.4 XML 스키마 기반 구성](#214-xml-스키마-기반-구성)
    * [21.5 JAXB](#215-jaxb)
      * [Jaxb2Marshaller](#jaxb2marshaller)
        * [XML 스키마 기반 구성](#xml-스키마-기반-구성)
    * [21.6 Castor](#216-castor)
      * [CastorMarshaller](#castormarshaller)
      * [Mapping](#mapping)
        * [XML 스키마 기반 구성](#xml-스키마-기반-구성-1)
    * [21.7 XMLBeans](#217-xmlbeans)
      * [XmlBeansMarshaller](#xmlbeansmarshaller)
        * [XML 스키마 기반 구성](#xml-스키마-기반-구성-2)
    * [21.8 JiBX](#218-jibx)
      * [JibxMarshaller](#jibxmarshaller)
        * [XML 스키마 기반 구성](#xml-스키마-기반-구성-3)
    * [21.9 XStream](#219-xstream)
      * [XStreamMarshaller](#xstreammarshaller)
* [VI. 웹](#vi-웹)
  * [22. 웹 MVC 프레임워크](#22-웹-mvc-프레임워크)
    * [22.1 스프링 웹 MVC 프레임워크 소개](#221-스프링-웹-mvc-프레임워크-소개)
      * [스프링 웹 MVC 특징](#스프링-웹-mvc-특징)
      * [다른 MVC 구현의 플러그 가능성](#다른-mvc-구현의-플러그-가능성)
    * [22.2 DispatcherServlet](#222-dispatcherservlet)
      * [WebApplicationContext에서 특별한 빈 타입](#webapplicationcontext에서-특별한-빈-타입)
      * [기본 DispatcherServlet 구성](#기본-dispatcherservlet-구성)
      * [DispatcherServlet 프로세싱 시퀀스](#dispatcherservlet-프로세싱-시퀀스)
    * [22.3 컨트롤러 구현](#223-컨트롤러-구현)
      * [@Controller로 컨트롤러 정의](#controller로-컨트롤러-정의)
      * [@RequestMapping로 Request 매핑](#requestmapping로-request-매핑)
        * [@RequestMapping 변형 구성](#requestmapping-변형-구성)
        * [@Controller 및 AOP 프록싱](#controller-및-aop-프록싱)
        * [스프링 MVC 3.1에서 @RequestMapping 메소드를 위한 새로운 지원 클래스](#스프링-mvc-31에서-requestmapping-메소드를-위한-새로운-지원-클래스)
        * [URI 템플릿 패턴](#uri-템플릿-패턴)
        * [정규식을 사용하는 URI 템플릿 패턴](#정규식을-사용하는-uri-템플릿-패턴)
        * [Path 패턴](#path-패턴)
        * [Path 패턴 비교](#path-패턴-비교)
        * [지시자가 있는 Path 패턴](#지시자가-있는-path-패턴)
        * [접미어 패턴 매칭](#접미어-패턴-매칭)
        * [접미어 패턴 매칭 및 RFD](#접미어-패턴-매칭-및-rfd)
        * [매트릭스 변수](#매트릭스-변수)
        * [소비 가능한 미디어 유형](#소비-가능한-미디어-유형)
        * [제작 가능한 미디어 유형](#제작-가능한-미디어-유형)
        * [Request 파라미터 및 헤더 값](#request-파라미터-및-헤더-값)
        * [HTTP HEAD 및 HTTP OPTIONS](#http-head-및-http-options)
      * [@RequestMapping 핸들러 메서드 정의](#requestmapping-핸들러-메서드-정의)
        * [지원되는 메서드 파라미터 타입](#지원되는-메서드-파라미터-타입)
        * [지원되는 메서드 리턴 타입](#지원되는-메서드-리턴-타입)
        * [@RequestParam을 사용하여 Request 매개 변수를 메서드 매개 변수에 바인딩](#requestparam을-사용하여-request-매개-변수를-메서드-매개-변수에-바인딩)
        * [Request body를 @RequestBody 어노테이션으로 매핑](#request-body를-requestbody-어노테이션으로-매핑)
        * [Response body를 @ResponseBody 어노테이션으로 매핑](#response-body를-responsebody-어노테이션으로-매핑)
        * [@RestController annotation으로 REST 컨트롤러 만들기](#restcontroller-annotation으로-rest-컨트롤러-만들기)
        * [HttpEntity 사용](#httpentity-사용)
        * [메서드에 @ModelAttribute 사용](#메서드에-modelattribute-사용)
        * [메서드 파라미터에 @ModelAttribute 사용](#메서드-파라미터에-modelattribute-사용)
        * [@SessionAttributes를 사용하여 HTTP 세션에 모델 애트리뷰트 저장](#sessionattributes를-사용하여-http-세션에-모델-애트리뷰트-저장)
        * [Request 사이](#request-사이)
        * [@SessionAttribute를 사용하여 기존 전역 세션 속성에 액세스](#sessionattribute를-사용하여-기존-전역-세션-속성에-액세스)
        * [@RequestAttribute를 사용하여 Request 속성에 액세스](#requestattribute를-사용하여-request-속성에-액세스)
        * ["application / x-www-form-urlencoded" 데이터 작업](#application-x-www-form-urlencoded-데이터-작업)
        * [쿠키 값을 @CookieValue annotation으로 매핑](#쿠키-값을-cookievalue-annotation으로-매핑)
        * [@RequestHeader annotation으로 Request 헤더 속성을 매핑](#requestheader-annotation으로-request-헤더-속성을-매핑)
        * [메서드 파라미터와 타입 변환](#메서드-파라미터와-타입-변환)
        * [WebDataBinder 초기화 커스터마이징](#webdatabinder-초기화-커스터마이징)
        * [@ControllerAdvice 및 @RestControllerAdvice가 있는 어드바이징 컨트롤러](#controlleradvice-및-restcontrolleradvice가-있는-어드바이징-컨트롤러)
        * [Jackson 직렬화 뷰 지원](#jackson-직렬화-뷰-지원)
        * [Jackson JSONP 지원](#jackson-jsonp-지원)
      * [비동기 Request 처리](#비동기-request-처리)
        * [비동기 Request를 위한 예외 핸들링](#비동기-request를-위한-예외-핸들링)
        * [비동기 Request 인터셉트](#비동기-request-인터셉트)
        * [HTTP 스트리밍](#http-스트리밍)
        * [Server-Sent 이벤트로 HTTP 스트리밍](#server-sent-이벤트로-http-스트리밍)
        * [OutputStream에 직접 HTTP 스트리밍](#outputstream에-직접-http-스트리밍)
        * [비동기 Request 처리 구성](#비동기-request-처리-구성)
      * [컨트롤러 테스트](#컨트롤러-테스트)
    * [22.4 핸들러 매핑](#224-핸들러-매핑)
      * [HandlerInterceptor로 Request 인터셉트](#handlerinterceptor로-request-인터셉트)
    * [22.5 리졸빙 뷰](#225-리졸빙-뷰)
      * [ViewResolver 인터페이스로 뷰 리졸빙](#viewresolver-인터페이스로-뷰-리졸빙)
      * [ViewResolver 체이닝](#viewresolver-체이닝)
      * [뷰 리다이렉트](#뷰-리다이렉트)
        * [RedirectView](#redirectview)
        * [redirect: 접두사](#redirect-접두사)
        * [forward: 접두사](#forward-접두사)
      * [ContentNegotiatingViewResolver](#contentnegotiatingviewresolver)
    * [22.6 플래시 속성 사용](#226-플래시-속성-사용)
    * [22.7 URI 작성](#227-uri-작성)
      * [URI와 컨트롤러 및 메소드 구현하기](#uri와-컨트롤러-및-메소드-구현하기)
      * [뷰로부터 URI와 컨트롤러 및 메소드 구현하기](#뷰로부터-uri와-컨트롤러-및-메소드-구현하기)
    * [22.8 locales 사용](#228-locales-사용)
      * [표준 시간대 정보 얻기](#표준-시간대-정보-얻기)
      * [AcceptHeaderLocaleResolver](#acceptheaderlocaleresolver)
      * [CookieLocaleResolver](#cookielocaleresolver)
      * [SessionLocaleResolver](#sessionlocaleresolver)
      * [LocaleChangeInterceptor](#localechangeinterceptor)
    * [22.9 테마 사용](#229-테마-사용)
      * [테마 개요](#테마-개요)
      * [테마 정의](#테마-정의)
      * [테마 리졸버](#테마-리졸버)
    * [22.10 스프링의 multipart(file upload) 지원](#2210-스프링의-multipartfile-upload-지원)
      * [소개](#소개-2)
      * [Commmons FileUpload로 MultipartResolver 사용](#commmons-fileupload로-multipartresolver-사용)
      * [Servlet 3.0으로 MultipartResolver 사용](#servlet-30으로-multipartresolver-사용)
      * [폼에서 파일업로드 핸들링](#폼에서-파일업로드-핸들링)
      * [프로그래밍 방식 클라이언트의 파일 업로드 요청 처리](#프로그래밍-방식-클라이언트의-파일-업로드-요청-처리)
    * [22.11 예외 핸들링](#2211-예외-핸들링)
      * [HandlerExceptionResolver](#handlerexceptionresolver)
      * [@ExceptionHandler](#exceptionhandler)
      * [표준 스프링 MVC 예외 핸들링](#표준-스프링-mvc-예외-핸들링)
      * [@ResponseStatus를 사용하여 비즈니스 예외에 annotation 추가](#responsestatus를-사용하여-비즈니스-예외에-annotation-추가)
      * [기본 서블릿 컨테이너 에러 페이지 커스터마이징](#기본-서블릿-컨테이너-에러-페이지-커스터마이징)
    * [22.12 웹 시큐리티](#2212-웹-시큐리티)
    * [22.13 설정 지원 컨벤션](#2213-설정-지원-컨벤션)
      * [컨트롤러 ControllerClassNameHandlerMapping](#컨트롤러-controllerclassnamehandlermapping)
      * [모델 ModelMap(ModelAndView)](#모델-modelmapmodelandview)
      * [뷰 RequestToViewNameTranslator](#뷰-requesttoviewnametranslator)
    * [22.14 HTTP 캐싱 지원](#2214-http-캐싱-지원)
      * [Cache-Control HTTP 헤더](#cache-control-http-헤더)
      * [정적 리소스에 대한 HTTP 캐싱 지원](#정적-리소스에-대한-http-캐싱-지원)
      * [컨트롤러에서 Cache-Control, ETag 및 Last-Modified Response 헤더 지원](#컨트롤러에서-cache-control-etag-및-last-modified-response-헤더-지원)
      * [얕은 ETag 지원](#얕은-etag-지원)
    * [22.15 코드 기반 서블릿 컨테이너 초기화](#2215-코드-기반-서블릿-컨테이너-초기화)
    * [22.16 스프링 MVC 설정](#2216-스프링-mvc-설정)
      * [MVC Java Config 또는 MVC XML 네임 스페이스 사용](#mvc-java-config-또는-mvc-xml-네임-스페이스-사용)
      * [제공된 구성 커스터마이징](#제공된-구성-커스터마이징)
      * [변환 및 서식 지정](#변환-및-서식-지정)
      * [유효성 검사](#유효성-검사)
      * [인터셉터](#인터셉터)
      * [컨텐츠 협상](#컨텐츠-협상)
      * [뷰 컨트롤러](#뷰-컨트롤러)
      * [뷰 리졸버](#뷰-리졸버)
      * [리소스 제공](#리소스-제공)
      * [리소스를 제공하기 위해 기본 서블릿에 떨어지는 것](#리소스를-제공하기-위해-기본-서블릿에-떨어지는-것)
      * [경로 매칭](#경로-매칭)
      * [메시지 컨버터](#메시지-컨버터)
      * [MVC Java Config를 사용한 고급 사용자 정의](#mvc-java-config를-사용한-고급-사용자-정의)
      * [MVC 네임 스페이스를 사용한 고급 사용자 정의](#mvc-네임-스페이스를-사용한-고급-사용자-정의)
  * [23. 뷰 기술](#23-뷰-기술)
    * [23.1 소개](#231-소개)
    * [23.2 Thymeleaf](#232-thymeleaf)
    * [23.3 Groovy 마크업 템플릿](#233-groovy-마크업-템플릿)
      * [구성](#구성)
      * [예제](#예제-3)
    * [23.4 Velocity & FreeMarker](#234-velocity-freemarker)
      * [의존성](#의존성)
      * [컨텍스트 설정](#컨텍스트-설정)
      * [템플릿 생성](#템플릿-생성)
      * [고급 설정](#고급-설정)
        * [velocity.properties](#velocityproperties)
        * [FreeMarker](#freemarker)
      * [바인드 지원 및 폼 핸들링](#바인드-지원-및-폼-핸들링)
        * [바인드 매크로](#바인드-매크로)
        * [간단한 바인딩](#간단한-바인딩)
        * [폼 입력 생성 매크로](#폼-입력-생성-매크로)
        * [HTML 이스케이프 및 XHTML 준수](#html-이스케이프-및-xhtml-준수)
    * [23.5 JSP & JSTL](#235-jsp-jstl)
      * [뷰 리졸버](#뷰-리졸버-1)
      * ['평범한' JSP와 JSTL](#평범한-jsp와-jstl)
      * [개발을 용이하게하는 추가 태그](#개발을-용이하게하는-추가-태그)
      * [스프링의 폼 태그 라이브러리 사용하기](#스프링의-폼-태그-라이브러리-사용하기)
        * [설정](#설정)
        * [form 태그](#form-태그)
        * [input 태그](#input-태그)
        * [checkbox 태그](#checkbox-태그)
        * [checkboxes 태그](#checkboxes-태그)
        * [radiobutton 태그](#radiobutton-태그)
        * [radiobuttons 태그](#radiobuttons-태그)
        * [password 태그](#password-태그)
        * [select 태그](#select-태그)
        * [option 태그](#option-태그)
        * [options 태그](#options-태그)
        * [textarea 태그](#textarea-태그)
        * [hidden 태그](#hidden-태그)
        * [errors 태그](#errors-태그)
        * [HTTP 메서드 변환](#http-메서드-변환)
        * [HTML5 태그](#html5-태그)
    * [23.6 스크립트 템플릿](#236-스크립트-템플릿)
      * [의존성](#의존성-1)
      * [스크립트 기반 템플릿 작성을 통합하는 방법](#스크립트-기반-템플릿-작성을-통합하는-방법)
    * [23.7 XML 마샬링 뷰](#237-xml-마샬링-뷰)
    * [23.8 타일즈](#238-타일즈)
      * [의존성](#의존성-2)
      * [타일즈를 통합하는 방법](#타일즈를-통합하는-방법)
        * [UrlBasedViewResolver](#urlbasedviewresolver)
        * [ResourceBundleViewResolver](#resourcebundleviewresolver)
        * [SimpleSpringPreparerFactory 및 SpringBeanPreparerFactory](#simplespringpreparerfactory-및-springbeanpreparerfactory)
    * [23.9 XSLT](#239-xslt)
      * [나의 첫 단어](#나의-첫-단어)
        * [빈 정의](#빈-정의)
        * [표준 MVC 컨트롤러 코드](#표준-mvc-컨트롤러-코드)
        * [문서 변환](#문서-변환)
    * [23.10 문서 뷰 (PDF/Excel)](#2310-문서-뷰-pdfexcel)
      * [소개](#소개-3)
      * [설정 및 셋업](#설정-및-셋업)
        * [문서 뷰 정의](#문서-뷰-정의)
        * [컨트롤러 코드](#컨트롤러-코드)
        * [Excel 뷰의 서브클래싱](#excel-뷰의-서브클래싱)
        * [PDF 뷰의 서브클래싱](#pdf-뷰의-서브클래싱)
    * [23.11 JasperReports](#2311-jasperreports)
      * [의존성](#의존성-3)
      * [설정](#설정-1)
        * [ViewResolver 설정](#viewresolver-설정)
        * [뷰 설정](#뷰-설정)
        * [리포트 파일에 대해](#리포트-파일에-대해)
        * [JasperReportsMultiFormatView 사용](#jasperreportsmultiformatview-사용)
      * [ModelAndView 채우기](#modelandview-채우기)
      * [하위 보고서 작업](#하위-보고서-작업)
        * [하위 보고서 파일 설정](#하위-보고서-파일-설정)
        * [하위 보고서 데이터 소스 설정](#하위-보고서-데이터-소스-설정)
      * [Exporter 파라미터 설정](#exporter-파라미터-설정)
    * [23.12 피드 뷰](#2312-피드-뷰)
    * [23.13 JSON 매핑 뷰](#2313-json-매핑-뷰)
    * [23.14 XML 매핑 뷰](#2314-xml-매핑-뷰)
  * [24. 다른 웹 프레임워크와 통합](#24-다른-웹-프레임워크와-통합)
    * [24.1 소개](#241-소개)
    * [24.2 공통 구성](#242-공통-구성)
    * [24.3 JavaServer Faces 1.2](#243-javaserver-faces-12)
      * [SpringBeanFacesELResolver (JSF 1.2+)](#springbeanfaceselresolver-jsf-12)
      * [FacesContextUtils](#facescontextutils)
    * [24.4 Apache Struts 2.x](#244-apache-struts-2x)
    * [24.5 Tapestry 5.x](#245-tapestry-5x)
    * [24.6 추가 리소스](#246-추가-리소스)
  * [25. Portlet MVC 프레임워크](#25-portlet-mvc-프레임워크)
    * [25.1 소개](#251-소개)
      * [컨트롤러 - C in MVC](#컨트롤러-c-in-mvc)
      * [뷰 - V in MVC](#뷰-v-in-mvc)
      * [웹 스코프 빈](#웹-스코프-빈)
    * [25.2 DispatcherServlet](#252-dispatcherservlet)
    * [25.3 ViewRendererServlet](#253-viewrendererservlet)
    * [25.4 컨트롤러](#254-컨트롤러)
      * [AbstractController 및 PortletContentGenerator](#abstractcontroller-및-portletcontentgenerator)
      * [그 밖의 간단한 컨트롤러](#그-밖의-간단한-컨트롤러)
      * [커맨드 컨트롤러](#커맨드-컨트롤러)
      * [PortletWrappingController](#portletwrappingcontroller)
    * [25.5 핸들러 매핑](#255-핸들러-매핑)
      * [PortletModeHandlerMapping](#portletmodehandlermapping)
      * [ParameterHandlerMapping](#parameterhandlermapping)
      * [PortletModeParameterHandlerMapping](#portletmodeparameterhandlermapping)
      * [HandlerInterceptors 추가](#handlerinterceptors-추가)
      * [HandlerInterceptorAdapter](#handlerinterceptoradapter)
      * [ParameterMappingInterceptor](#parametermappinginterceptor)
    * [25.6 뷰 및 해결](#256-뷰-및-해결)
    * [25.7 Multipart (file upload) 지원](#257-multipart-file-upload-지원)
      * [PortletMultipartResolver 사용](#portletmultipartresolver-사용)
      * [폼 안에 파일 업로드 다루기](#폼-안에-파일-업로드-다루기)
    * [25.8 예외 다루기](#258-예외-다루기)
    * [25.9 annotation 기반 컨트롤러 설정](#259-annotation-기반-컨트롤러-설정)
      * [annotation 지원을 위한 디스패처 설정](#annotation-지원을-위한-디스패처-설정)
      * [@Controller로 컨트롤러 정의](#controller로-컨트롤러-정의-1)
      * [@RequestMapping로 Request 매핑](#requestmapping로-request-매핑-1)
      * [지원되는 핸들러 메서드 파라미터](#지원되는-핸들러-메서드-파라미터)
      * [@RequestParam으로 메서드 파라미터에 Request 파라미터 바인딩](#requestparam으로-메서드-파라미터에-request-파라미터-바인딩)
      * [@ModelAttribute로 모델의 데이터에 대한 링크 제공](#modelattribute로-모델의-데이터에-대한-링크-제공)
      * [@SessionAttributes를 사용하여 세션에 저장할 특성 지정](#sessionattributes를-사용하여-세션에-저장할-특성-지정)
      * [WebDataBinder 초기화 커스터마이징](#webdatabinder-초기화-커스터마이징-1)
        * [@InitBinder를 사용하여 데이터 바인딩 커스터마이징](#initbinder를-사용하여-데이터-바인딩-커스터마이징)
        * [커스텀 WebBindingInitializer 구성](#커스텀-webbindinginitializer-구성)
    * [25.10 Portlet 어플리케이션 개발](#2510-portlet-어플리케이션-개발)
  * [26. 웹소켓 지원](#26-웹소켓-지원)
    * [26.1 소개](#261-소개)
      * [웹소켓 Fallback 옵션](#웹소켓-fallback-옵션)
      * [메시징 아키텍쳐](#메시징-아키텍쳐)
      * [웹소켓 하위 프로토콜 지원](#웹소켓-하위-프로토콜-지원)
      * [WebSocket을 사용해야합니까?](#websocket을-사용해야합니까)
    * [26.2 웹소켓 API](#262-웹소켓-api)
      * [WebSocketHandler 생성 및 구성](#websockethandler-생성-및-구성)
      * [웹소켓 핸드셰이크 커스터마이징](#웹소켓-핸드셰이크-커스터마이징)
      * [WebSocketHandler 꾸미기](#websockethandler-꾸미기)
      * [배포 시 고려사항](#배포-시-고려사항)
      * [웹소켓 엔진 설정](#웹소켓-엔진-설정)
      * [허용된 출처 구성](#허용된-출처-구성)
    * [26.3 SockJS Fallback 옵션](#263-sockjs-fallback-옵션)
      * [SockJS 개요](#sockjs-개요)
      * [SockJS 사용](#sockjs-사용)
      * [IE 8, 9의 HTTP 스트리밍 : Ajax / XHR 대 IFrame](#ie-8-9의-http-스트리밍-ajax-xhr-대-iframe)
      * [Heartbeat 메시지](#heartbeat-메시지)
      * [Servlet 3 비동기 Request](#servlet-3-비동기-request)
      * [SockJS 용 CORS 헤더](#sockjs-용-cors-헤더)
      * [SockJS 클라이언트](#sockjs-클라이언트)
    * [26.4 STOMP Over WebSocket 메시징 아키텍처](#264-stomp-over-websocket-메시징-아키텍처)
      * [STOMP 개요](#stomp-개요)
      * [WebSocket을 통한 STOMP 사용](#websocket을-통한-stomp-사용)
      * [메시지 흐름](#메시지-흐름)
      * [annotation 메시지 핸들링](#annotation-메시지-핸들링)
      * [메시지 전송](#메시지-전송)
      * [간단한 브로커](#간단한-브로커)
      * [완전한 기능의 브로커](#완전한-기능의-브로커)
      * [완전한 기능의 브로커에 연결](#완전한-기능의-브로커에-연결)
      * [@MessageMapping Destinations에서 구분 기호로 . 사용](#messagemapping-destinations에서-구분-기호로-사용)
      * [권한](#권한)
      * [토큰 기반 권한](#토큰-기반-권한)
      * [유저 목적지](#유저-목적지)
      * [ApplicationContext 이벤트 수신 및 메시지 수신](#applicationcontext-이벤트-수신-및-메시지-수신)
      * [STOMP 클라이언트](#stomp-클라이언트)
      * [웹소켓 스코프](#웹소켓-스코프)
      * [구성 및 성능](#구성-및-성능)
      * [런타임 모니터링](#런타임-모니터링)
      * [annotation이 달린 컨트롤러 메소드 테스트](#annotation이-달린-컨트롤러-메소드-테스트)
  * [27. CORS 지원](#27-cors-지원)
    * [27.1 소개](#271-소개)
    * [27.2 컨트롤러 메서드 CORS 설정](#272-컨트롤러-메서드-cors-설정)
    * [27.3 글로벌 CORS 설정](#273-글로벌-cors-설정)
      * [JavaConfig](#javaconfig)
      * [XML 네임스페이스](#xml-네임스페이스)
    * [27.4 고급 커스터마이징](#274-고급-커스터마이징)
    * [27.5 필터 기반 CORS 지원](#275-필터-기반-cors-지원)
* [VII. 통합](#vii-통합)
  * [28. 스프링을 사용한 원격 및 웹 서비스](#28-스프링을-사용한-원격-및-웹-서비스)
    * [28.1 소개](#281-소개)
    * [28.2 RMI를 사용하여 서비스 노출](#282-rmi를-사용하여-서비스-노출)
      * [RmiServiceExporter를 사용하여 서비스 노출](#rmiserviceexporter를-사용하여-서비스-노출)
      * [클라이언트에서 서비스 링크하기](#클라이언트에서-서비스-링크하기)
    * [28.3 Hessian 또는 Burlap을 사용하여 HTTP를 통해 원격으로 서비스 호출](#283-hessian-또는-burlap을-사용하여-http를-통해-원격으로-서비스-호출)
      * [Hessian과 co.을 위한 DispatcherServlet 연결하기.](#hessian과-co을-위한-dispatcherservlet-연결하기)
      * [HessianServiceExporter를 사용하여 빈 노출하기](#hessianserviceexporter를-사용하여-빈-노출하기)
      * [클라이언트에서 서비스 링크하기](#클라이언트에서-서비스-링크하기-1)
      * [Burlap 사용](#burlap-사용)
      * [Hessian 또는 Burlap을 통해 노출된 서비스에 HTTP 기본 인증 적용](#hessian-또는-burlap을-통해-노출된-서비스에-http-기본-인증-적용)
    * [28.4 HTTP 호출자를 사용하여 서비스 노출](#284-http-호출자를-사용하여-서비스-노출)
      * [서비스 객체 노출하기](#서비스-객체-노출하기)
      * [클라이언트에서 서비스 링크하기](#클라이언트에서-서비스-링크하기-2)
    * [28.5 웹 서비스](#285-웹-서비스)
      * [JAX-WS를 사용하여 서블릿 기반 웹 서비스 노출하기](#jax-ws를-사용하여-서블릿-기반-웹-서비스-노출하기)
      * [JAX-WS를 사용하여 독립형 웹 서비스 내보내기](#jax-ws를-사용하여-독립형-웹-서비스-내보내기)
      * [JAX-WS RI의 스프링 지원을 사용하여 웹 서비스 내보내기](#jax-ws-ri의-스프링-지원을-사용하여-웹-서비스-내보내기)
      * [JAX-WS를 사용하여 웹 서비스에 액세스하기](#jax-ws를-사용하여-웹-서비스에-액세스하기)
    * [28.6 JMS](#286-jms)
      * [서버사이드 설정](#서버사이드-설정)
      * [클라이언트사이드 설정](#클라이언트사이드-설정)
    * [28.7 AMQP](#287-amqp)
    * [28.8 원격 인터페이스에 대해 자동 감지가 구현되지 않았습니다.](#288-원격-인터페이스에-대해-자동-감지가-구현되지-않았습니다)
    * [28.9 기술 선택 시 고려사항](#289-기술-선택-시-고려사항)
    * [28.10 클라이언트에서 RESTful 서비스에 액세스하기](#2810-클라이언트에서-restful-서비스에-액세스하기)
      * [RestTemplate](#resttemplate)
        * [URI 작업하기](#uri-작업하기)
        * [Request 및 Response 헤더 다루기](#request-및-response-헤더-다루기)
        * [Jackson JSON 뷰 지원](#jackson-json-뷰-지원)
      * [HTTP 메시지 변환](#http-메시지-변환)
        * [StringHttpMessageConverter](#stringhttpmessageconverter)
        * [FormHttpMessageConverter](#formhttpmessageconverter)
        * [ByteArrayHttpMessageConverter](#bytearrayhttpmessageconverter)
        * [MarshallingHttpMessageConverter](#marshallinghttpmessageconverter)
        * [MappingJackson2HttpMessageConverter](#mappingjackson2httpmessageconverter)
        * [MappingJackson2XmlHttpMessageConverter](#mappingjackson2xmlhttpmessageconverter)
        * [SourceHttpMessageConverter](#sourcehttpmessageconverter)
        * [BufferedImageHttpMessageConverter](#bufferedimagehttpmessageconverter)
      * [비동기 RestTemplate](#비동기-resttemplate)
  * [29. Enterprise Java Beans (EJB) 통합](#29-enterprise-java-beans-ejb-통합)
    * [29.1 소개](#291-소개)
    * [29.2 EJBs 접근](#292-ejbs-접근)
      * [컨셉](#컨셉-1)
      * [로컬 SLSBs에 접근](#로컬-slsbs에-접근)
      * [원격 SLSBs에 접근](#원격-slsbs에-접근)
      * [EJB 2.x SLSB 대 EJB 3 SLSB 액세스](#ejb-2x-slsb-대-ejb-3-slsb-액세스)
    * [29.3 스프링의 EJB 구현 지원 클래스 사용하기](#293-스프링의-ejb-구현-지원-클래스-사용하기)
      * [EJB 3 주입 인터셉터](#ejb-3-주입-인터셉터)
  * [30. JMS (Java Message Service)](#30-jms-java-message-service)
    * [30.1 소개](#301-소개)
    * [30.2 스프링 JMS 사용하기](#302-스프링-jms-사용하기)
      * [JmsTemplate](#jmstemplate)
      * [커넥션](#커넥션)
        * [캐싱 메시지 리소스](#캐싱-메시지-리소스)
        * [SingleConnectionFactory](#singleconnectionfactory)
        * [CachingConnectionFactory](#cachingconnectionfactory)
      * [목적지 관리](#목적지-관리)
      * [메시지 리스너 컨테이너](#메시지-리스너-컨테이너)
        * [SimpleMessageListenerContainer](#simplemessagelistenercontainer)
        * [DefaultMessageListenerContainer](#defaultmessagelistenercontainer)
      * [트랜잭션 관리](#트랜잭션-관리-3)
    * [30.3 메시지 전송](#303-메시지-전송)
      * [메시지 컨버터 사용하기](#메시지-컨버터-사용하기)
      * [SessionCallback 및 ProducerCallback](#sessioncallback-및-producercallback)
    * [30.4 메시지 수신](#304-메시지-수신)
      * [동기식 수신](#동기식-수신)
      * [비동기식 수신 - 메시지 중심의 POJOs](#비동기식-수신-메시지-중심의-pojos)
      * [SessionAwareMessageListener 인터페이스](#sessionawaremessagelistener-인터페이스)
      * [MessageListenerAdapter](#messagelisteneradapter)
      * [트랜잭션 내에서 메시지 처리](#트랜잭션-내에서-메시지-처리)
    * [30.5 JCA 메시지 엔드포인트 지원](#305-jca-메시지-엔드포인트-지원)
    * [30.6 annotation 중심의 리스너 엔드포인트](#306-annotation-중심의-리스너-엔드포인트)
      * [리스너 엔드포인트 annotation 사용 가능](#리스너-엔드포인트-annotation-사용-가능)
      * [프로그래밍적인 엔드포인트 등록](#프로그래밍적인-엔드포인트-등록)
      * [annotation 엔드포인트 메서드 서명](#annotation-엔드포인트-메서드-서명)
      * [Response 관리](#response-관리)
    * [30.7 JMS 네임스페이스 지원](#307-jms-네임스페이스-지원)
  * [31. JMX](#31-jmx)
    * [31.1 소개](#311-소개)
    * [31.2 빈을 JMX로 내보내기](#312-빈을-jmx로-내보내기)
      * [MBeanServer 생성](#mbeanserver-생성)
      * [존재하는 MBeanServer 재사용](#존재하는-mbeanserver-재사용)
      * [지연 초기화 된 MBeans](#지연-초기화-된-mbeans)
      * [MBean의 자동 등록](#mbean의-자동-등록)
      * [등록 동작 제어](#등록-동작-제어)
    * [31.3 빈의 관리 인터페이스 제어](#313-빈의-관리-인터페이스-제어)
      * [MBeanInfoAssembler 인터페이스](#mbeaninfoassembler-인터페이스)
      * [소스레벨 메타데이터(자바 annotation) 사용](#소스레벨-메타데이터자바-annotation-사용)
      * [소스레벨 메타데이터 타입](#소스레벨-메타데이터-타입)
      * [AutodetectCapableMBeanInfoAssembler 인터페이스](#autodetectcapablembeaninfoassembler-인터페이스)
      * [Java 인터페이스를 사용하여 관리 인터페이스 정의](#java-인터페이스를-사용하여-관리-인터페이스-정의)
      * [MethodNameBasedMBeanInfoAssembler 사용](#methodnamebasedmbeaninfoassembler-사용)
    * [31.4 빈에 대한 ObjectNames 제어](#314-빈에-대한-objectnames-제어)
      * [프로퍼티로부터 오브젝트네임 읽기](#프로퍼티로부터-오브젝트네임-읽기)
      * [MetadataNamingStrategy 사용](#metadatanamingstrategy-사용)
      * [annotation 기반 MBean 내보내기 구성](#annotation-기반-mbean-내보내기-구성)
    * [31.5 JSR-160 커넥터](#315-jsr-160-커넥터)
      * [서버사이드 커넥터](#서버사이드-커넥터)
      * [클라이언트사이드 커넥터](#클라이언트사이드-커넥터)
      * [JMX over Burlap / Hessian / SOAP](#jmx-over-burlap-hessian-soap)
    * [31.6 프록시를 통한 MBean 접근](#316-프록시를-통한-mbean-접근)
    * [31.7 알림](#317-알림)
      * [알림을 위한 리스너 등록](#알림을-위한-리스너-등록)
      * [게시 알림](#게시-알림)
    * [31.8 추가 리소스](#318-추가-리소스)
  * [32. JCA CCI](#32-jca-cci)
    * [32.1 소개](#321-소개)
    * [32.2 CCI 설정](#322-cci-설정)
      * [커넥터 설정](#커넥터-설정)
      * [스프링에서 ConnectionFactory 설정](#스프링에서-connectionfactory-설정)
      * [CCI 커넥션 설정](#cci-커넥션-설정)
      * [싱글 CCI 커넥션 사용](#싱글-cci-커넥션-사용)
    * [32.3 스프링의 CCI 접근 지원 사용](#323-스프링의-cci-접근-지원-사용)
      * [레코드 변환](#레코드-변환)
      * [CciTemplate](#ccitemplate)
      * [DAO 지원](#dao-지원)
      * [자동 출력 레코드 생성](#자동-출력-레코드-생성)
      * [요약](#요약)
      * [CCI 연결 및 상호 작용 직접 사용](#cci-연결-및-상호-작용-직접-사용)
      * [CciTemplate 사용 예제](#ccitemplate-사용-예제)
    * [32.4 CCI 액세스를 운영 객체로 모델링](#324-cci-액세스를-운영-객체로-모델링)
      * [MappingRecordOperation](#mappingrecordoperation)
      * [MappingCommAreaOperation](#mappingcommareaoperation)
      * [자동 출력 레코드 생성](#자동-출력-레코드-생성-1)
      * [요약](#요약-1)
      * [MappingRecordOperation 사용 예제](#mappingrecordoperation-사용-예제)
      * [MappingCommAreaOperation 사용 예제](#mappingcommareaoperation-사용-예제)
    * [32.5 트랜잭션](#325-트랜잭션)
  * [33. 이메일](#33-이메일)
    * [33.1 소개](#331-소개)
    * [33.2 사용](#332-사용)
      * [기본 MailSender 및 SimpleMailMessage 사용법](#기본-mailsender-및-simplemailmessage-사용법)
      * [JavaMailSender 및 MimeMessagePreparator 사용](#javamailsender-및-mimemessagepreparator-사용)
    * [33.3 JavaMail MimeMessageHelper 사용하기](#333-javamail-mimemessagehelper-사용하기)
      * [첨부파일 및 인라인 리소스 보내기](#첨부파일-및-인라인-리소스-보내기)
        * [첨부파일](#첨부파일)
        * [인라인 리소스](#인라인-리소스)
      * [템플릿 라이브러리를 사용하여 이메일 콘텐츠 만들기](#템플릿-라이브러리를-사용하여-이메일-콘텐츠-만들기)
        * [벨로시티 기반 예제](#벨로시티-기반-예제)
  * [34. 작업 실행 및 스케줄링](#34-작업-실행-및-스케줄링)
    * [34.1 소개](#341-소개)
    * [34.2 스프링 TaskExecutor 추상화](#342-스프링-taskexecutor-추상화)
      * [TaskExecutor 타입](#taskexecutor-타입)
      * [TaskExecutor 사용](#taskexecutor-사용)
    * [34.3 스프링 TaskScheduler 추상화](#343-스프링-taskscheduler-추상화)
      * [트리거 인터페이스](#트리거-인터페이스)
      * [트리거 구현](#트리거-구현)
      * [TaskScheduler 구현](#taskscheduler-구현)
    * [34.4 스케줄링 및 비동기 실행을 위한 annotation 지원](#344-스케줄링-및-비동기-실행을-위한-annotation-지원)
      * [스케줄링 annotation 사용](#스케줄링-annotation-사용)
      * [@Scheduled annotation](#scheduled-annotation)
      * [@Async annotation](#async-annotation)
      * [@Async로 Executor 자격 부여](#async로-executor-자격-부여)
      * [@Async로 예외 관리](#async로-예외-관리)
    * [34.5 태스크 네임스페이스](#345-태스크-네임스페이스)
      * [scheduler 엘리먼트](#scheduler-엘리먼트)
      * [executor 엘리먼트](#executor-엘리먼트)
      * [scheduled-tasks 엘리먼트](#scheduled-tasks-엘리먼트)
    * [34.6 Quartz 스케줄러 사용](#346-quartz-스케줄러-사용)
      * [JobDetailFactoryBean 사용](#jobdetailfactorybean-사용)
      * [MethodInvokingJobDetailFactoryBean 사용](#methodinvokingjobdetailfactorybean-사용)
      * [트리거와 SchedulerFactoryBean을 사용하여 작업 연결](#트리거와-schedulerfactorybean을-사용하여-작업-연결)
  * [35. 동적 언어 지원](#35-동적-언어-지원)
    * [35.1 소개](#351-소개)
    * [35.2 첫 번째 예제](#352-첫-번째-예제)
    * [35.3 동적 언어로 지원되는 빈 정의](#353-동적-언어로-지원되는-빈-정의)
      * [일반적인 개념들](#일반적인-개념들)
        * [<lang:language/> 엘리먼트](#langlanguage-엘리먼트)
        * [새로고침 가능한 빈](#새로고침-가능한-빈)
        * [인라인 동적 언어 소스 파일](#인라인-동적-언어-소스-파일)
        * [동적 언어가 지원되는 빈의 컨텍스트에서 생성자 주입 이해](#동적-언어가-지원되는-빈의-컨텍스트에서-생성자-주입-이해)
      * [JRuby 빈](#jruby-빈)
      * [Groovy 빈](#groovy-빈)
        * [콜백을 통해 Groovy 객체 커스터마이징](#콜백을-통해-groovy-객체-커스터마이징)
      * [BeanShall 빈](#beanshall-빈)
    * [35.4 시나리오](#354-시나리오)
      * [스크립팅된 스프링 MVC 컨트롤러](#스크립팅된-스프링-mvc-컨트롤러)
      * [스크립팅된 벨리데이터](#스크립팅된-벨리데이터)
    * [35.5 잡동사니](#355-잡동사니)
      * [AOP - advising scripted bean](#aop-advising-scripted-bean)
      * [스코핑](#스코핑)
    * [35.6 추가 리소스](#356-추가-리소스)
  * [36. 캐시 추상화](#36-캐시-추상화)
    * [36.1 소개](#361-소개)
    * [36.2 캐시 추상화 이해](#362-캐시-추상화-이해)
    * [36.3 선언적인 annotation 기반 캐싱](#363-선언적인-annotation-기반-캐싱)
      * [@Cacheable annotation](#cacheable-annotation)
        * [기본 키 생성](#기본-키-생성)
        * [커스텀 키 생성 선언](#커스텀-키-생성-선언)
        * [기본 캐시 해결책](#기본-캐시-해결책)
        * [커스텀 캐시 해결책](#커스텀-캐시-해결책)
        * [동기적 캐싱](#동기적-캐싱)
        * [조건적 캐싱](#조건적-캐싱)
        * [사용 가능한 캐싱 SpEL 평가 컨텍스트](#사용-가능한-캐싱-spel-평가-컨텍스트)
      * [@CachePut annotation](#cacheput-annotation)
      * [@CacheEvict annotation](#cacheevict-annotation)
      * [@Caching annotation](#caching-annotation)
      * [@CacheConfig annotation](#cacheconfig-annotation)
      * [캐싱 annotation 사용](#캐싱-annotation-사용)
      * [커스텀 annotation 사용](#커스텀-annotation-사용)
    * [36.4 JCache(JSR-107) annotation](#364-jcachejsr-107-annotation)
      * [기능 요약](#기능-요약)
      * [JSR-107 지원 사용](#jsr-107-지원-사용)
    * [36.5 선언적인 XML 기반 캐싱](#365-선언적인-xml-기반-캐싱)
    * [36.6 캐시 스토리지 설정](#366-캐시-스토리지-설정)
      * [JDK ConcurrentMap 기반 캐시](#jdk-concurrentmap-기반-캐시)
      * [Ehcache 기반 캐시](#ehcache-기반-캐시)
      * [카페인 캐시](#카페인-캐시)
      * [Guava 캐시](#guava-캐시)
      * [GemFire 기반 캐시](#gemfire-기반-캐시)
      * [JSR-107 캐시](#jsr-107-캐시)
      * [백업 저장소가없는 캐시 처리](#백업-저장소가없는-캐시-처리)
    * [36.7 서로 다른 백엔드 캐시 연결](#367-서로-다른-백엔드-캐시-연결)
    * [36.8 TTL / TTI / Eviction policy / XXX 기능을 어떻게 설정할 수 있는가?](#368-ttl-tti-eviction-policy-xxx-기능을-어떻게-설정할-수-있는가)
* [VIII. 부록](#viii-부록)
  * [37. 스프링 프레임 워크 4.x 로의 마이그레이션](#37-스프링-프레임-워크-4x-로의-마이그레이션)
  * [38. 스프링 annotation 프로그래밍 모델](#38-스프링-annotation-프로그래밍-모델)
  * [39. 클래식 스프링 사용](#39-클래식-스프링-사용)
    * [39.1 클래식 ORM 사용](#391-클래식-orm-사용)
      * [Hibernate](#hibernate)
        * [HibernateTemplate](#hibernatetemplate)
        * [콜백 없이 스프링 기반 DAO 구현](#콜백-없이-스프링-기반-dao-구현)
    * [39.2 JMS 사용](#392-jms-사용)
      * [JmsTemplate](#jmstemplate-1)
      * [비동기식 메시지 수신](#비동기식-메시지-수신)
      * [커넥션](#커넥션-1)
      * [트랜잭션 관리](#트랜잭션-관리-4)
  * [40. 클래식 스프링 AOP 사용](#40-클래식-스프링-aop-사용)
    * [40.1 스프링에서의 포인트컷 API](#401-스프링에서의-포인트컷-api)
      * [컨셉](#컨셉-2)
      * [포인트컷에 대한 작업](#포인트컷에-대한-작업)
      * [AspectJ 표현식 포인트컷](#aspectj-표현식-포인트컷-1)
      * [편리한 pointcut 구현](#편리한-pointcut-구현)
        * [정적 포인트컷](#정적-포인트컷-1)
        * [동적 포인트컷](#동적-포인트컷-1)
      * [포인트컷 슈퍼클래스](#포인트컷-슈퍼클래스-1)
      * [커스텀 포인트컷](#커스텀-포인트컷-1)
    * [40.2 스프링에서의 어드바이스 API](#402-스프링에서의-어드바이스-api)
      * [어드바이스 라이프사이클](#어드바이스-라이프사이클-1)
      * [스프링에서의 어드바이스 타입](#스프링에서의-어드바이스-타입-1)
        * [인터셉터에 관한 어드바이스](#인터셉터에-관한-어드바이스)
        * [Before 어드바이스](#before-어드바이스-3)
        * [Throws 어드바이스](#throws-어드바이스-1)
        * [After Returning 어드바이스](#after-returning-어드바이스-3)
        * [Introduction 어드바이스](#introduction-어드바이스-1)
    * [40.3 스프링에서의 어드바이저 API](#403-스프링에서의-어드바이저-api)
    * [40.4 AOP 프록시 생성을 위한 ProxyFactoryBean 사용](#404-aop-프록시-생성을-위한-proxyfactorybean-사용)
      * [기초](#기초)
      * [JavaBean 프로퍼티](#javabean-프로퍼티-1)
      * [JDK 및 CGLIB 기반 프록시](#jdk-및-cglib-기반-프록시)
      * [프록싱 인터페이스](#프록싱-인터페이스)
      * [프록싱 클래스](#프록싱-클래스)
      * [글로벌 어드바이저 사용](#글로벌-어드바이저-사용-1)
    * [40.5 간결한 프록시 정의](#405-간결한-프록시-정의)
    * [40.6 ProxyFactory로 프로그래밍적으로 AOP 프록시 생성](#406-proxyfactory로-프로그래밍적으로-aop-프록시-생성)
    * [40.7 어드바이즈된 객체 조작](#407-어드바이즈된-객체-조작)
    * [40.8 "autoproxy"기능 사용](#408-autoproxy기능-사용)
      * [Autoproxy 빈 정의](#autoproxy-빈-정의-1)
        * [BeanNameAutoProxyCreator](#beannameautoproxycreator-1)
        * [DefaultAdvisorAutoProxyCreator](#defaultadvisorautoproxycreator-1)
        * [AbstractAdvisorAutoProxyCreator](#abstractadvisorautoproxycreator-1)
      * [메타데이터 중심의 오토 프록싱 사용](#메타데이터-중심의-오토-프록싱-사용)
    * [40.9 TargetSources 사용](#409-targetsources-사용)
      * [핫 스왑 가능한 타겟 소스](#핫-스왑-가능한-타겟-소스)
      * [풀링 타겟 소스](#풀링-타겟-소스-1)
      * [프로토타입 타겟 소스](#프로토타입-타겟-소스-1)
      * [ThreadLocal 타겟 소스](#threadlocal-타겟-소스-1)
    * [40.10 새로운 어드바이스 타입 정의](#4010-새로운-어드바이스-타입-정의)
    * [40.11 추가 리소스](#4011-추가-리소스)
  * [41. XML 스키마 기반 구성](#41-xml-스키마-기반-구성)
    * [41.1 소개](#411-소개)
    * [41.2 XML 스키마 기반 구성](#412-xml-스키마-기반-구성)
      * [스키마 참조](#스키마-참조)
      * [util 스키마](#util-스키마)
        * [<util:constant/>](#utilconstant)
        * [<util:property-path/>](#utilproperty-path)
        * [<util:properties/>](#utilproperties)
        * [<util:list/>](#utillist)
        * [<util:map/>](#utilmap)
        * [<util:set/>](#utilset)
      * [jee 스키마](#jee-스키마)
        * [<jee:jndi-lookup/> (simple)](#jeejndi-lookup-simple)
        * [<jee:jndi-lookup/> (싱글 JNDI 환경 세팅으로)](#jeejndi-lookup-싱글-jndi-환경-세팅으로)
        * [<jee:jndi-lookup/> (멀티 JNDI 환경 세팅으로)](#jeejndi-lookup-멀티-jndi-환경-세팅으로)
        * [<jee:jndi-lookup/> (복잡한)](#jeejndi-lookup-복잡한)
        * [<jee:local-slsb/> (기초)](#jeelocal-slsb-기초)
        * [<jee:local-slsb/> (복잡한)](#jeelocal-slsb-복잡한)
        * [<jee:remote-slsb/>](#jeeremote-slsb)
      * [lang 스키마](#lang-스키마)
      * [jms 스키마](#jms-스키마)
      * [tx(트랜잭션) 스키마](#tx트랜잭션-스키마)
      * [aop 스키마](#aop-스키마)
      * [context 스키마](#context-스키마)
        * [<property-placeholder/>](#property-placeholder)
        * [<annotation-config/>](#annotation-config)
        * [<component-scan/>](#component-scan)
        * [<load-time-weaver/>](#load-time-weaver)
        * [<spring-configured/>](#spring-configured)
        * [<mbean-export/>](#mbean-export)
      * [tool 스키마](#tool-스키마)
      * [jdbc 스키마](#jdbc-스키마)
      * [cache 스키마](#cache-스키마)
      * [beans 스키마](#beans-스키마)
  * [42. 확장 가능한 XML 작성](#42-확장-가능한-xml-작성)
    * [42.1 소개](#421-소개)
    * [42.2 스키마 작성](#422-스키마-작성)
    * [42.3 NamespaceHandler 코딩](#423-namespacehandler-코딩)
    * [42.4 BeanDefinitionParser](#424-beandefinitionparser)
    * [42.5 핸들러 및 스키마 등록](#425-핸들러-및-스키마-등록)
      * ['META-INF/spring.handlers'](#meta-infspringhandlers)
      * ['META-INF/spring.schemas'](#meta-infspringschemas)
    * [42.6 스프링 XML 설정에서 커스텀 확장 기능 사용하기](#426-스프링-xml-설정에서-커스텀-확장-기능-사용하기)
    * [42.7 Meatier 예제](#427-meatier-예제)
      * [커스텀 태그 내에서 커스텀 태그 중첩](#커스텀-태그-내에서-커스텀-태그-중첩)
      * ['normal'요소의 커스텀 속성](#normal요소의-커스텀-속성)
    * [42.8 추가 리소스](#428-추가-리소스)
  * [43. 스프링 JSP 태그 라이브러리](#43-스프링-jsp-태그-라이브러리)
    * [43.1 소개](#431-소개)
    * [43.2 argument 태그](#432-argument-태그)
    * [43.3 bind 태그](#433-bind-태그)
    * [43.4 escapeBody 태그](#434-escapebody-태그)
    * [43.5 eval 태그](#435-eval-태그)
    * [43.6 hasBindErrors 태그](#436-hasbinderrors-태그)
    * [43.7 htmlEscape 태그](#437-htmlescape-태그)
    * [43.8 message 태그](#438-message-태그)
    * [43.9 nestedPath 태그](#439-nestedpath-태그)
    * [43.10 param 태그](#4310-param-태그)
    * [43.11 theme 태그](#4311-theme-태그)
    * [43.12 transform 태그](#4312-transform-태그)
    * [43.13 url 태그](#4313-url-태그)
  * [44. 스프링 폼 JSP 태그 라이브러리](#44-스프링-폼-jsp-태그-라이브러리)
    * [소개](#소개-4)
    * [button 태그](#button-태그)
    * [checkbox 태그](#checkbox-태그-1)
    * [checkboxes 태그](#checkboxes-태그-1)
    * [errors 태그](#errors-태그-1)
    * [form 태그](#form-태그-1)
    * [hidden 태그](#hidden-태그-1)
    * [input 태그](#input-태그-1)
    * [label 태그](#label-태그)
    * [option 태그](#option-태그-1)
    * [options 태그](#options-태그-1)
    * [password 태그](#password-태그-1)
    * [radiobutton 태그](#radiobutton-태그-1)
    * [radiobuttons 태그](#radiobuttons-태그-1)
    * [select 태그](#select-태그-1)
    * [textarea 태그](#textarea-태그-1)

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

### 12.1 소개

### 12.2 스프링에서의 포인트컷 API

#### 컨셉

#### 포인트컷 조작

#### AspectJ 표현식 포인트컷

#### 편리한 포인트컷 구현

##### 정적 포인트컷

##### 동적 포인트컷

#### 포인트컷 슈퍼클래스

#### 커스텀 포인트컷

### 12.3 스프링에서의 어드바이스 API

#### 어드바이스 라이프사이클

#### 스프링에서의 어드바이스 타입

##### Interception around 어드바이스

##### Before 어드바이스

##### Throws 어드바이스

##### After Returning 어드바이스

##### Introduction 어드바이스

### 12.4 스프링에서의 어드바이저 API

### 12.5 AOP 프록시를 만들기 위한 ProxyFactoryBean 사용

#### 기본

#### JavaBean 프로퍼티

#### JDK와 CGLIB 기반 프록시

#### 프록시 인터페이스

#### 프록시 클래스

#### 글로벌 어드바이저 사용

### 12.6 간결한 프록시 정의

### 12.7 ProxyFactory를 이용한 프로그래밍적으로 AOP 프록시 생성

### 12.8 어드바이저 객체 조작

### 12.9 auto-proxy 기능 사용

#### Autoproxy 빈 정의

##### BeanNameAutoProxyCreator

##### DefaultAdvisorAutoProxyCreator

##### AbstractAdvisorAutoProxyCreator

#### 메타데이터 중심의 auto-proxy 사용

### 12.10 TargetSource 사용

#### 핫 스왑가능한 타겟 소스

#### 풀링 타겟 소스

#### 프로토타입 타겟 소스

#### ThreadLocal 타겟 소스

### 12.11 새로운 어드바이스 타입 정의

### 12.12 자세한 리소스

# IV. 테스팅

## 13. 스프링 테스팅 소개

## 14. 유닛 테스팅

### 14.1 Mock 객체

#### 환경

#### JNDI

#### Servlet API

#### Portlet API

### 14.2 유닛 테스팅 지원 클래스

#### 일반적인 테스팅 유틸리티

#### Spring MVC

## 15. 통합 테스팅

### 15.1 개요

### 15.2 통합 테스팅의 목적

#### 컨텍스트 관리 및 캐싱

#### 테스트 픽스처의 의존성 주입

#### 트랜잭션 관리

#### 통합 테스팅을 위한 지원 클래스

### 15.3 JDBC 테스팅 지원

### 15.4 Annotation

#### 스프링 테스팅 annotation

##### @BootstrapWith

##### @ContextConfiguration

##### @WebAppConfiguration

##### @ContextHierarchy

##### @ActiveProfiles

##### @TestPropertySource

##### @DirtiesContext

##### @TestExecutionListeners

##### @Commit

##### @Rollback

##### @BeforeTransaction

##### @AfterTransaction

##### @Sql

##### @SqlConfig

##### @SqlGroup

#### 표준 annotation 지원

#### 스프링 JUnit 4 테스팅 annotation

##### @IfProfileValue

##### @ProfileValueSourceConfiguration

##### @Timed

##### @Repeat

#### 테스팅을 위한 메타-annotation 지원

### 15.5 스프링 TestContext 프레임워크

#### 주요 추상화

##### TestContext

##### TestContextManager

##### TestExecutionListener

##### 컨텍스트 로더

#### TestContext 프레임워크 부트스트래핑하기

#### TestExecutionListener 설정

##### 커스텀 TestExecutionListener 등록

##### 기본 TestExecutionListener의 자동 검색

##### TestExecutionListener 순서 지정

##### TestExecutionListener 병합

#### 컨텍스트 관리

##### XML 리소스로 컨텍스트 설정

##### Groovy 스크립트로 컨텍스트 설정

##### annotated 클래스로 컨텍스트 설정

##### XML, Groovy 스크립트, annotated 클래스 같이 쓰기

##### 컨텍스트 이니셜라이저로 컨텍스트 설정

##### 컨텍스트 설정 계승

##### 환경 프로파일로 컨텍스트 설정

##### 테스트 프로퍼티 소스로 컨텍스트 설정

##### WebApplicationContext 로딩

##### 컨텍스트 캐싱

##### 컨텍스트 계층화

#### 테스트 픽스쳐의 의존성 주입

#### 테스팅 request, session 스코프 빈

#### 트랜잭션 관리

##### 테스트 관리 트랜잭션

##### 트랜잭션 활성화와 비활성화

##### 트랜잭션 롤백 및 동작

##### 프로그래밍 방식의 트랜잭션 관리

##### 트랜잭션 외부의 코드 실행

##### 트랜잭션 매니저 설정

##### 모든 트랜잭션과 관련된 annotation 시연

#### SQL 스크립트 실행

##### 프로그래밍 방식으로 SQL 스트립트 실행

##### @Sql을 사용하여 선언적으로 SQL 스크립트 실행

#### TestContext 프레임워크가 지원하는 클래스

##### 스프링 JUnit 4 Runner

##### 스프링 JUnit 4 Rules

##### JUnit 4가 지원하는 클래스

##### TestNG가 지원하는 클래스

### 15.6 Spring MVC 테스트 프레임워크

#### 서버 사이드 테스트

##### 정적 임포트

##### 설정 옵션

##### Request 수행하기

##### 기대 정의

##### 필터 등록

##### Out-of-Container와 End-to-End 통합 테스트의 차이점

##### 자세한 서버 사이드 테스트 예제

#### HtmlUnit 통하

##### 왜 HtmlUnit 통합?

##### MockMvc와 HtmlUnit

##### MockMvc와 WebDriver

##### MockMvc와 Geb

#### 클라이언트 사이드 REST 테스트

##### 정적 임포트

##### 클라이언트 사이드 REST 테스트의 자세한 예제

### 15.7 PetClinic 예제

## 16. 자세한 리소스

# V. 데이터 접근

## 17. 트랜잭션 관리

### 17.1 스프링 프레임워크 트랜잭션 관리에 대한 소개

### 17.2 스프링 프레임워크의 트랜잭션 지원 모델의 이점

#### 글로벌 트랜잭션

#### 로컬 트랜잭션

#### 스프링 프레임워크의 일관된 프로그래밍 모델

### 17.3 스프링 프레임워크 트랜잭션 추출 이해

### 17.4 트랜잭션과 동기적 리소스

#### 높은 수준의 동기화 접근 방식

#### 낮은 수준의 동기화 접근 방식

#### TransactionAwareDataSourceProxy

### 17.5 선언적인 트랜잭션 관리

#### 스프링 프레임워크의 선언적인 트랜잭션 구현 이해

#### 선언적인 트랜잭션 구현의 예제

#### 선언적인 트랜잭션 롤백

#### 다른 빈에 대해 다른 트랜잭션 의미 설정

#### <tx:advice /> 세팅

#### @Transactional 사용

##### @Transactional 세팅

##### 여러 개의 트랜잭션 매니저와 @Transactional

##### 커스텀 숏컷 annotation

#### 트랜잭션 전파

##### Required

##### RequiresNew

##### Nested

#### 트랜잭션 작업에 대한 조언

#### @Transactional과 AspectJ 사용하기

### 17.6 프로그래밍적인 트랜잭션 관리

#### 트랜잭션 템플릿 사용

##### 트랜젝션 세팅 지정

#### PlatformTransactionManager 사용

### 17.7 프로그래밍 방식 및 선언적 트랜잭션 관리 중에서 선택하기

### 17.8 트랜잭션 바운드 이벤트

### 17.9 어플리케이션 서버 지정 통합

#### IBM WebSphere

#### Oracle WebLogic Server

### 17.10 공통 문제의 해결책

#### 특정 DataSource에 대해 잘못된 트랜잭션 매니저 사용

### 17.11 자세한 리소스

## 18. DAO 지원

### 18.1 소개

### 18.2 일관된 예외 계층 구조

### 18.3 DAO 또는 Repository 클래스 구성에 사용되는 주석

## 19. JDBC를 이용한 데이터 접근

### 19.1 스프링 프레임워크 JDBC 소개

#### JDBC 데이터베이스 액세스에 대한 접근 방식 선택

#### 패키지 계층

### 19.2 JDBC 핵심 클래스를 사용하여 기본 JDBC 처리 및 오류 제어

#### 핸들링

#### JdbcTemplate

##### JdbcTemplate 클래스 사용 예제

##### JdbcTemplate 모범 사례

#### NamedParameterJdbcTemplate

#### SQLExceptionTranslator

#### Executing statements

#### 명령문 실행

#### 쿼리문 실행

#### 데이터베이스 업데이트

#### 자동 생성 키 가져오기

### 19.3 데이터베이스 커넥션 제어

#### DataSource

#### DataSourceUtils

#### SmartDataSource

#### AbstractDataSource

#### SingleConnectionDataSource

#### DriverManagerDataSource

#### TransactionAwareDataSourceProxy

#### DataSourceTransactionManager

#### NativeJdbcExtractor

### 19.4 JDBC 배치 연산

#### JdbcTemplate 기본 배치 작업

#### 객체 목록으로 배치 작업

#### 여러 배치로 배치 작업

### 19.5 SimpleJdbc 클래스를 사용하여 JDBC 작업 단순화

#### SimpleJdbcInsert를 이용하여 데이터 삽입

#### SimpleJdbcInsert를 이용하여 자동 생성 키 가져오기

#### SimpleJdbcInsert의 컬럼 지정

#### SqlParameterSource를 사용하여 매개 변수 값 제공

#### SimpleJdbcCall을 사용하여 스토어드 프로시저 호출

#### SimpleJdbcCall에 사용할 매개 변수를 명시적으로 선언

#### SqlParameters 정의하는 방법

#### SimpleJdbcCall을 이용하여 저장되있는 함수 호출

#### SimpleJdbcCall에서 ResultSet / REF 커서 리턴하기

### 19.6 JDBC 작업을 Java 객체로 모델링

#### SqlQuery

#### MappingSqlQuery

#### SqlUpdate

#### StoredProcedure

### 19.7 매개 변수 및 데이터 값 처리와 관련된 일반적인 문제

#### 파라미터의 SQL 타입 정보의 제공

#### BLOB, CLOB 객체 핸들링

#### IN 절에 대한 값 목록 전달

#### 스토어드 프로시저 호출의 복잡한 유형 처리

### 19.8 임베디드 데이터베이스 지원

#### 왜 임베디드 데이터베이스를 사용해야 하는가?

#### Spring XML을 이용한 임베디드 데이터베이스 생성

#### 프로그래밍적으로 임베디드 데이터베이스 생성

#### 임베디드 데이터베이스 타입 선택

##### HSQL 사용

##### H2 사용

##### Derby 사용

#### 임베디드 데이터베이스로 데이터 접근 로직 테스트

#### 임베디드 데이터베이스로 유니크 이름 생성

#### 임베디드 데이터베이스 지원 확장

### 19.9 DataSource 초기화

#### Spring XML을 사용하여 데이터베이스 초기화

##### 데이터베이스에 의존하는 다른 구성 요소의 초기화

## 20. 객체 관계 매핑 (ORM) 데이터 액세스

### 20.1 스프링과 ORM 소개

### 20.2 일반적인 ORM 통합 고려사항

#### 리소스와 트랜잭션 관리

#### 예외 변환

### 20.3 Hibernate

#### 스프링 컨테이너에서 SessionFactory 설정

#### 기본 Hibernate API에 기반한 DAO 구현하기

#### 선언적 트랜잭션 구분

#### 프로그래밍적인 트랜잭션 구분

#### 트랜잭션 관리 전략

#### 컨테이너 관리 및 로컬 정의 리소스 비교

#### Hibernate로 비논리적인 응용 프로그램 서버 경고

### 20.4 JDO

#### PersistenceManagerFactory 셋업

#### 기본 JDO API에 기반한 DAO 구현하기

#### 트랜잭션 관리

#### JdoDialect

### 20.5 JPA

#### 스프링 환경에서 JPA 셋업을 위한 세 가지 옵션

##### LocalEntityManagerFactoryBean

##### JNDI로부터 EntityManagerFactory 얻기

##### LocalContainerEntityManagerFactoryBean

##### 다중 퍼시스턴스 유닛 다루기

#### JPA에 기반한 DAO 구현 : EntityManagerFactory 및 EntityManager

#### 스프링 중심의 JPA 트랜잭션

#### JpaDialect 및 JpaVendorAdapter

#### JTA 트랜잭션 관리로 JPA 세팅

## 21. O/X 매퍼를 사용한 XML 마샬링

### 21.1 소개

#### 쉬운 구성

#### 일관된 인터페이스

#### 일관된 예외 계층

### 21.2 마샬러 및 언마샬러

#### 마샬러

#### 언마샬러

#### XmlMappingException

### 21.3 마샬러 및 언마샬러 사용

### 21.4 XML 스키마 기반 구성

### 21.5 JAXB

#### Jaxb2Marshaller

##### XML 스키마 기반 구성

### 21.6 Castor

#### CastorMarshaller

#### Mapping

##### XML 스키마 기반 구성

### 21.7 XMLBeans

#### XmlBeansMarshaller

##### XML 스키마 기반 구성

### 21.8 JiBX

#### JibxMarshaller

##### XML 스키마 기반 구성

### 21.9 XStream

#### XStreamMarshaller

# VI. 웹

## 22. 웹 MVC 프레임워크

### 22.1 스프링 웹 MVC 프레임워크 소개

#### 스프링 웹 MVC 특징

#### 다른 MVC 구현의 플러그 가능성

### 22.2 DispatcherServlet

#### WebApplicationContext에서 특별한 빈 타입

#### 기본 DispatcherServlet 구성

#### DispatcherServlet 프로세싱 시퀀스

### 22.3 컨트롤러 구현

#### @Controller로 컨트롤러 정의

#### @RequestMapping로 Request 매핑

##### @RequestMapping 변형 구성

##### @Controller 및 AOP 프록싱

##### 스프링 MVC 3.1에서 @RequestMapping 메소드를 위한 새로운 지원 클래스

##### URI 템플릿 패턴

##### 정규식을 사용하는 URI 템플릿 패턴

##### Path 패턴

##### Path 패턴 비교

##### 지시자가 있는 Path 패턴

##### 접미어 패턴 매칭

##### 접미어 패턴 매칭 및 RFD

##### 매트릭스 변수

##### 소비 가능한 미디어 유형

##### 제작 가능한 미디어 유형

##### Request 파라미터 및 헤더 값

##### HTTP HEAD 및 HTTP OPTIONS

#### @RequestMapping 핸들러 메서드 정의

##### 지원되는 메서드 파라미터 타입

##### 지원되는 메서드 리턴 타입

##### @RequestParam을 사용하여 Request 매개 변수를 메서드 매개 변수에 바인딩

##### Request body를 @RequestBody 어노테이션으로 매핑

##### Response body를 @ResponseBody 어노테이션으로 매핑

##### @RestController annotation으로 REST 컨트롤러 만들기

##### HttpEntity 사용

##### 메서드에 @ModelAttribute 사용

##### 메서드 파라미터에 @ModelAttribute 사용

##### @SessionAttributes를 사용하여 HTTP 세션에 모델 애트리뷰트 저장

##### Request 사이

##### @SessionAttribute를 사용하여 기존 전역 세션 속성에 액세스

##### @RequestAttribute를 사용하여 Request 속성에 액세스

##### "application / x-www-form-urlencoded" 데이터 작업

##### 쿠키 값을 @CookieValue annotation으로 매핑

##### @RequestHeader annotation으로 Request 헤더 속성을 매핑

##### 메서드 파라미터와 타입 변환

##### WebDataBinder 초기화 커스터마이징

##### @ControllerAdvice 및 @RestControllerAdvice가 있는 어드바이징 컨트롤러

##### Jackson 직렬화 뷰 지원

##### Jackson JSONP 지원

#### 비동기 Request 처리

##### 비동기 Request를 위한 예외 핸들링

##### 비동기 Request 인터셉트

##### HTTP 스트리밍

##### Server-Sent 이벤트로 HTTP 스트리밍

##### OutputStream에 직접 HTTP 스트리밍

##### 비동기 Request 처리 구성

#### 컨트롤러 테스트

### 22.4 핸들러 매핑

#### HandlerInterceptor로 Request 인터셉트

### 22.5 리졸빙 뷰

#### ViewResolver 인터페이스로 뷰 리졸빙

#### ViewResolver 체이닝

#### 뷰 리다이렉트

##### RedirectView

##### redirect: 접두사

##### forward: 접두사

#### ContentNegotiatingViewResolver

### 22.6 플래시 속성 사용

### 22.7 URI 작성

#### URI와 컨트롤러 및 메소드 구현하기

#### 뷰로부터 URI와 컨트롤러 및 메소드 구현하기

### 22.8 locales 사용

#### 표준 시간대 정보 얻기

#### AcceptHeaderLocaleResolver

#### CookieLocaleResolver

#### SessionLocaleResolver

#### LocaleChangeInterceptor

### 22.9 테마 사용

#### 테마 개요

#### 테마 정의

#### 테마 리졸버

### 22.10 스프링의 multipart(file upload) 지원

#### 소개

#### Commmons FileUpload로 MultipartResolver 사용

#### Servlet 3.0으로 MultipartResolver 사용

#### 폼에서 파일업로드 핸들링

#### 프로그래밍 방식 클라이언트의 파일 업로드 요청 처리

### 22.11 예외 핸들링

#### HandlerExceptionResolver

#### @ExceptionHandler

#### 표준 스프링 MVC 예외 핸들링

#### @ResponseStatus를 사용하여 비즈니스 예외에 annotation 추가

#### 기본 서블릿 컨테이너 에러 페이지 커스터마이징

### 22.12 웹 시큐리티

### 22.13 설정 지원 컨벤션

#### 컨트롤러 ControllerClassNameHandlerMapping

#### 모델 ModelMap(ModelAndView)

#### 뷰 RequestToViewNameTranslator

### 22.14 HTTP 캐싱 지원

#### Cache-Control HTTP 헤더

#### 정적 리소스에 대한 HTTP 캐싱 지원

#### 컨트롤러에서 Cache-Control, ETag 및 Last-Modified Response 헤더 지원

#### 얕은 ETag 지원

### 22.15 코드 기반 서블릿 컨테이너 초기화

### 22.16 스프링 MVC 설정

#### MVC Java Config 또는 MVC XML 네임 스페이스 사용

#### 제공된 구성 커스터마이징

#### 변환 및 서식 지정

#### 유효성 검사

#### 인터셉터

#### 컨텐츠 협상

#### 뷰 컨트롤러

#### 뷰 리졸버

#### 리소스 제공

#### 리소스를 제공하기 위해 기본 서블릿에 떨어지는 것

#### 경로 매칭

#### 메시지 컨버터

#### MVC Java Config를 사용한 고급 사용자 정의

#### MVC 네임 스페이스를 사용한 고급 사용자 정의

## 23. 뷰 기술

### 23.1 소개

### 23.2 Thymeleaf

### 23.3 Groovy 마크업 템플릿

#### 구성

#### 예제

### 23.4 Velocity & FreeMarker

#### 의존성

#### 컨텍스트 설정

#### 템플릿 생성

#### 고급 설정

##### velocity.properties

##### FreeMarker

#### 바인드 지원 및 폼 핸들링

##### 바인드 매크로

##### 간단한 바인딩

##### 폼 입력 생성 매크로

##### HTML 이스케이프 및 XHTML 준수

### 23.5 JSP & JSTL

#### 뷰 리졸버

#### '평범한' JSP와 JSTL

#### 개발을 용이하게하는 추가 태그

#### 스프링의 폼 태그 라이브러리 사용하기

##### 설정

##### form 태그

##### input 태그

##### checkbox 태그

##### checkboxes 태그

##### radiobutton 태그

##### radiobuttons 태그

##### password 태그

##### select 태그

##### option 태그

##### options 태그

##### textarea 태그

##### hidden 태그

##### errors 태그

##### HTTP 메서드 변환

##### HTML5 태그

### 23.6 스크립트 템플릿

#### 의존성

#### 스크립트 기반 템플릿 작성을 통합하는 방법

### 23.7 XML 마샬링 뷰

### 23.8 타일즈

#### 의존성

#### 타일즈를 통합하는 방법

##### UrlBasedViewResolver

##### ResourceBundleViewResolver

##### SimpleSpringPreparerFactory 및 SpringBeanPreparerFactory

### 23.9 XSLT

#### 나의 첫 단어

##### 빈 정의

##### 표준 MVC 컨트롤러 코드

##### 문서 변환

### 23.10 문서 뷰 (PDF/Excel)

#### 소개

#### 설정 및 셋업

##### 문서 뷰 정의

##### 컨트롤러 코드

##### Excel 뷰의 서브클래싱

##### PDF 뷰의 서브클래싱

### 23.11 JasperReports

#### 의존성

#### 설정

##### ViewResolver 설정

##### 뷰 설정

##### 리포트 파일에 대해

##### JasperReportsMultiFormatView 사용

#### ModelAndView 채우기

#### 하위 보고서 작업

##### 하위 보고서 파일 설정

##### 하위 보고서 데이터 소스 설정

#### Exporter 파라미터 설정

### 23.12 피드 뷰

### 23.13 JSON 매핑 뷰

### 23.14 XML 매핑 뷰

## 24. 다른 웹 프레임워크와 통합

### 24.1 소개

### 24.2 공통 구성

### 24.3 JavaServer Faces 1.2

#### SpringBeanFacesELResolver (JSF 1.2+)

#### FacesContextUtils

### 24.4 Apache Struts 2.x

### 24.5 Tapestry 5.x

### 24.6 추가 리소스

## 25. Portlet MVC 프레임워크

### 25.1 소개

#### 컨트롤러 - C in MVC

#### 뷰 - V in MVC

#### 웹 스코프 빈

### 25.2 DispatcherServlet

### 25.3 ViewRendererServlet

### 25.4 컨트롤러

#### AbstractController 및 PortletContentGenerator

#### 그 밖의 간단한 컨트롤러

#### 커맨드 컨트롤러

#### PortletWrappingController

### 25.5 핸들러 매핑

#### PortletModeHandlerMapping

#### ParameterHandlerMapping

#### PortletModeParameterHandlerMapping

#### HandlerInterceptors 추가

#### HandlerInterceptorAdapter

#### ParameterMappingInterceptor

### 25.6 뷰 및 해결

### 25.7 Multipart (file upload) 지원

#### PortletMultipartResolver 사용

#### 폼 안에 파일 업로드 다루기

### 25.8 예외 다루기

### 25.9 annotation 기반 컨트롤러 설정

#### annotation 지원을 위한 디스패처 설정

#### @Controller로 컨트롤러 정의

#### @RequestMapping로 Request 매핑

#### 지원되는 핸들러 메서드 파라미터

#### @RequestParam으로 메서드 파라미터에 Request 파라미터 바인딩

#### @ModelAttribute로 모델의 데이터에 대한 링크 제공

#### @SessionAttributes를 사용하여 세션에 저장할 특성 지정

#### WebDataBinder 초기화 커스터마이징

##### @InitBinder를 사용하여 데이터 바인딩 커스터마이징

##### 커스텀 WebBindingInitializer 구성

### 25.10 Portlet 어플리케이션 개발

## 26. 웹소켓 지원

### 26.1 소개

#### 웹소켓 Fallback 옵션

#### 메시징 아키텍쳐

#### 웹소켓 하위 프로토콜 지원

#### WebSocket을 사용해야합니까?

### 26.2 웹소켓 API

#### WebSocketHandler 생성 및 구성

#### 웹소켓 핸드셰이크 커스터마이징

#### WebSocketHandler 꾸미기

#### 배포 시 고려사항

#### 웹소켓 엔진 설정

#### 허용된 출처 구성

### 26.3 SockJS Fallback 옵션

#### SockJS 개요

#### SockJS 사용

#### IE 8, 9의 HTTP 스트리밍 : Ajax / XHR 대 IFrame

#### Heartbeat 메시지

#### Servlet 3 비동기 Request

#### SockJS 용 CORS 헤더

#### SockJS 클라이언트

### 26.4 STOMP Over WebSocket 메시징 아키텍처

#### STOMP 개요

#### WebSocket을 통한 STOMP 사용

#### 메시지 흐름

#### annotation 메시지 핸들링

#### 메시지 전송

#### 간단한 브로커

#### 완전한 기능의 브로커

#### 완전한 기능의 브로커에 연결

#### @MessageMapping Destinations에서 구분 기호로 . 사용

#### 권한

#### 토큰 기반 권한

#### 유저 목적지

#### ApplicationContext 이벤트 수신 및 메시지 수신

#### STOMP 클라이언트

#### 웹소켓 스코프

#### 구성 및 성능

#### 런타임 모니터링

#### annotation이 달린 컨트롤러 메소드 테스트

## 27. CORS 지원

### 27.1 소개

### 27.2 컨트롤러 메서드 CORS 설정

### 27.3 글로벌 CORS 설정

#### JavaConfig

#### XML 네임스페이스

### 27.4 고급 커스터마이징

### 27.5 필터 기반 CORS 지원

# VII. 통합

## 28. 스프링을 사용한 원격 및 웹 서비스

### 28.1 소개

### 28.2 RMI를 사용하여 서비스 노출

#### RmiServiceExporter를 사용하여 서비스 노출

#### 클라이언트에서 서비스 링크하기

### 28.3 Hessian 또는 Burlap을 사용하여 HTTP를 통해 원격으로 서비스 호출

#### Hessian과 co.을 위한 DispatcherServlet 연결하기.

#### HessianServiceExporter를 사용하여 빈 노출하기

#### 클라이언트에서 서비스 링크하기

#### Burlap 사용

#### Hessian 또는 Burlap을 통해 노출된 서비스에 HTTP 기본 인증 적용

### 28.4 HTTP 호출자를 사용하여 서비스 노출

#### 서비스 객체 노출하기

#### 클라이언트에서 서비스 링크하기

### 28.5 웹 서비스

#### JAX-WS를 사용하여 서블릿 기반 웹 서비스 노출하기

#### JAX-WS를 사용하여 독립형 웹 서비스 내보내기

#### JAX-WS RI의 스프링 지원을 사용하여 웹 서비스 내보내기

#### JAX-WS를 사용하여 웹 서비스에 액세스하기

### 28.6 JMS

#### 서버사이드 설정

#### 클라이언트사이드 설정

### 28.7 AMQP

### 28.8 원격 인터페이스에 대해 자동 감지가 구현되지 않았습니다.

### 28.9 기술 선택 시 고려사항

### 28.10 클라이언트에서 RESTful 서비스에 액세스하기

#### RestTemplate

##### URI 작업하기

##### Request 및 Response 헤더 다루기

##### Jackson JSON 뷰 지원

#### HTTP 메시지 변환

##### StringHttpMessageConverter

##### FormHttpMessageConverter

##### ByteArrayHttpMessageConverter

##### MarshallingHttpMessageConverter

##### MappingJackson2HttpMessageConverter

##### MappingJackson2XmlHttpMessageConverter

##### SourceHttpMessageConverter

##### BufferedImageHttpMessageConverter

#### 비동기 RestTemplate

## 29. Enterprise Java Beans (EJB) 통합

### 29.1 소개

### 29.2 EJBs 접근

#### 컨셉

#### 로컬 SLSBs에 접근

#### 원격 SLSBs에 접근

#### EJB 2.x SLSB 대 EJB 3 SLSB 액세스

### 29.3 스프링의 EJB 구현 지원 클래스 사용하기

#### EJB 3 주입 인터셉터

## 30. JMS (Java Message Service)

### 30.1 소개

### 30.2 스프링 JMS 사용하기

#### JmsTemplate

#### 커넥션

##### 캐싱 메시지 리소스

##### SingleConnectionFactory

##### CachingConnectionFactory

#### 목적지 관리

#### 메시지 리스너 컨테이너

##### SimpleMessageListenerContainer

##### DefaultMessageListenerContainer

#### 트랜잭션 관리

### 30.3 메시지 전송

#### 메시지 컨버터 사용하기

#### SessionCallback 및 ProducerCallback

### 30.4 메시지 수신

#### 동기식 수신

#### 비동기식 수신 - 메시지 중심의 POJOs

#### SessionAwareMessageListener 인터페이스

#### MessageListenerAdapter

#### 트랜잭션 내에서 메시지 처리

### 30.5 JCA 메시지 엔드포인트 지원

### 30.6 annotation 중심의 리스너 엔드포인트

#### 리스너 엔드포인트 annotation 사용 가능

#### 프로그래밍적인 엔드포인트 등록

#### annotation 엔드포인트 메서드 서명

#### Response 관리

### 30.7 JMS 네임스페이스 지원

## 31. JMX

### 31.1 소개

### 31.2 빈을 JMX로 내보내기

#### MBeanServer 생성

#### 존재하는 MBeanServer 재사용

#### 지연 초기화 된 MBeans

#### MBean의 자동 등록

#### 등록 동작 제어

### 31.3 빈의 관리 인터페이스 제어

#### MBeanInfoAssembler 인터페이스

#### 소스레벨 메타데이터(자바 annotation) 사용

#### 소스레벨 메타데이터 타입

#### AutodetectCapableMBeanInfoAssembler 인터페이스

#### Java 인터페이스를 사용하여 관리 인터페이스 정의

#### MethodNameBasedMBeanInfoAssembler 사용

### 31.4 빈에 대한 ObjectNames 제어

#### 프로퍼티로부터 오브젝트네임 읽기

#### MetadataNamingStrategy 사용

#### annotation 기반 MBean 내보내기 구성

### 31.5 JSR-160 커넥터

#### 서버사이드 커넥터

#### 클라이언트사이드 커넥터

#### JMX over Burlap / Hessian / SOAP

### 31.6 프록시를 통한 MBean 접근

### 31.7 알림

#### 알림을 위한 리스너 등록

#### 게시 알림

### 31.8 추가 리소스

## 32. JCA CCI

### 32.1 소개

### 32.2 CCI 설정

#### 커넥터 설정

#### 스프링에서 ConnectionFactory 설정

#### CCI 커넥션 설정

#### 싱글 CCI 커넥션 사용

### 32.3 스프링의 CCI 접근 지원 사용

#### 레코드 변환

#### CciTemplate

#### DAO 지원

#### 자동 출력 레코드 생성

#### 요약

#### CCI 연결 및 상호 작용 직접 사용

#### CciTemplate 사용 예제

### 32.4 CCI 액세스를 운영 객체로 모델링

#### MappingRecordOperation

#### MappingCommAreaOperation

#### 자동 출력 레코드 생성

#### 요약

#### MappingRecordOperation 사용 예제

#### MappingCommAreaOperation 사용 예제

### 32.5 트랜잭션

## 33. 이메일

### 33.1 소개

### 33.2 사용

#### 기본 MailSender 및 SimpleMailMessage 사용법

#### JavaMailSender 및 MimeMessagePreparator 사용

### 33.3 JavaMail MimeMessageHelper 사용하기

#### 첨부파일 및 인라인 리소스 보내기

##### 첨부파일

##### 인라인 리소스

#### 템플릿 라이브러리를 사용하여 이메일 콘텐츠 만들기

##### 벨로시티 기반 예제

## 34. 작업 실행 및 스케줄링

### 34.1 소개

### 34.2 스프링 TaskExecutor 추상화

#### TaskExecutor 타입

#### TaskExecutor 사용

### 34.3 스프링 TaskScheduler 추상화

#### 트리거 인터페이스

#### 트리거 구현

#### TaskScheduler 구현

### 34.4 스케줄링 및 비동기 실행을 위한 annotation 지원

#### 스케줄링 annotation 사용

#### @Scheduled annotation

#### @Async annotation

#### @Async로 Executor 자격 부여

#### @Async로 예외 관리

### 34.5 태스크 네임스페이스

#### scheduler 엘리먼트

#### executor 엘리먼트

#### scheduled-tasks 엘리먼트

### 34.6 Quartz 스케줄러 사용

#### JobDetailFactoryBean 사용

#### MethodInvokingJobDetailFactoryBean 사용

#### 트리거와 SchedulerFactoryBean을 사용하여 작업 연결

## 35. 동적 언어 지원

### 35.1 소개

### 35.2 첫 번째 예제

### 35.3 동적 언어로 지원되는 빈 정의

#### 일반적인 개념들

##### <lang:language/> 엘리먼트

##### 새로고침 가능한 빈

##### 인라인 동적 언어 소스 파일

##### 동적 언어가 지원되는 빈의 컨텍스트에서 생성자 주입 이해

#### JRuby 빈

#### Groovy 빈

##### 콜백을 통해 Groovy 객체 커스터마이징

#### BeanShall 빈

### 35.4 시나리오

#### 스크립팅된 스프링 MVC 컨트롤러

#### 스크립팅된 벨리데이터

### 35.5 잡동사니

#### AOP - advising scripted bean

#### 스코핑

### 35.6 추가 리소스

## 36. 캐시 추상화

### 36.1 소개

### 36.2 캐시 추상화 이해

### 36.3 선언적인 annotation 기반 캐싱

#### @Cacheable annotation

##### 기본 키 생성

##### 커스텀 키 생성 선언

##### 기본 캐시 해결책

##### 커스텀 캐시 해결책

##### 동기적 캐싱

##### 조건적 캐싱

##### 사용 가능한 캐싱 SpEL 평가 컨텍스트

#### @CachePut annotation

#### @CacheEvict annotation

#### @Caching annotation

#### @CacheConfig annotation

#### 캐싱 annotation 사용

#### 커스텀 annotation 사용

### 36.4 JCache(JSR-107) annotation

#### 기능 요약

#### JSR-107 지원 사용

### 36.5 선언적인 XML 기반 캐싱

### 36.6 캐시 스토리지 설정

#### JDK ConcurrentMap 기반 캐시

#### Ehcache 기반 캐시

#### 카페인 캐시

#### Guava 캐시

#### GemFire 기반 캐시

#### JSR-107 캐시

#### 백업 저장소가없는 캐시 처리

### 36.7 서로 다른 백엔드 캐시 연결

### 36.8 TTL / TTI / Eviction policy / XXX 기능을 어떻게 설정할 수 있는가?

# VIII. 부록

## 37. 스프링 프레임 워크 4.x 로의 마이그레이션

## 38. 스프링 annotation 프로그래밍 모델

## 39. 클래식 스프링 사용

### 39.1 클래식 ORM 사용

#### Hibernate

##### HibernateTemplate

##### 콜백 없이 스프링 기반 DAO 구현

### 39.2 JMS 사용

#### JmsTemplate

#### 비동기식 메시지 수신

#### 커넥션

#### 트랜잭션 관리

## 40. 클래식 스프링 AOP 사용

### 40.1 스프링에서의 포인트컷 API

#### 컨셉

#### 포인트컷에 대한 작업

#### AspectJ 표현식 포인트컷

#### 편리한 pointcut 구현

##### 정적 포인트컷

##### 동적 포인트컷

#### 포인트컷 슈퍼클래스

#### 커스텀 포인트컷

### 40.2 스프링에서의 어드바이스 API

#### 어드바이스 라이프사이클

#### 스프링에서의 어드바이스 타입

##### 인터셉터에 관한 어드바이스

##### Before 어드바이스

##### Throws 어드바이스

##### After Returning 어드바이스

##### Introduction 어드바이스

### 40.3 스프링에서의 어드바이저 API

### 40.4 AOP 프록시 생성을 위한 ProxyFactoryBean 사용

#### 기초

#### JavaBean 프로퍼티

#### JDK 및 CGLIB 기반 프록시

#### 프록싱 인터페이스

#### 프록싱 클래스

#### 글로벌 어드바이저 사용

### 40.5 간결한 프록시 정의

### 40.6 ProxyFactory로 프로그래밍적으로 AOP 프록시 생성

### 40.7 어드바이즈된 객체 조작

### 40.8 "autoproxy"기능 사용

#### Autoproxy 빈 정의

##### BeanNameAutoProxyCreator

##### DefaultAdvisorAutoProxyCreator

##### AbstractAdvisorAutoProxyCreator

#### 메타데이터 중심의 오토 프록싱 사용

### 40.9 TargetSources 사용

#### 핫 스왑 가능한 타겟 소스

#### 풀링 타겟 소스

#### 프로토타입 타겟 소스

#### ThreadLocal 타겟 소스

### 40.10 새로운 어드바이스 타입 정의

### 40.11 추가 리소스

## 41. XML 스키마 기반 구성

### 41.1 소개

### 41.2 XML 스키마 기반 구성

#### 스키마 참조

#### util 스키마

##### <util:constant/>

##### <util:property-path/>

##### <util:properties/>

##### <util:list/>

##### <util:map/>

##### <util:set/>

#### jee 스키마

##### <jee:jndi-lookup/> (simple)

##### <jee:jndi-lookup/> (싱글 JNDI 환경 세팅으로)

##### <jee:jndi-lookup/> (멀티 JNDI 환경 세팅으로)

##### <jee:jndi-lookup/> (복잡한)

##### <jee:local-slsb/> (기초)

##### <jee:local-slsb/> (복잡한)

##### <jee:remote-slsb/>

#### lang 스키마

#### jms 스키마

#### tx(트랜잭션) 스키마

#### aop 스키마

#### context 스키마

##### <property-placeholder/>

##### <annotation-config/>

##### <component-scan/>

##### <load-time-weaver/>

##### <spring-configured/>

##### <mbean-export/>

#### tool 스키마

#### jdbc 스키마

#### cache 스키마

#### beans 스키마

## 42. 확장 가능한 XML 작성

### 42.1 소개

### 42.2 스키마 작성

### 42.3 NamespaceHandler 코딩

### 42.4 BeanDefinitionParser

### 42.5 핸들러 및 스키마 등록

#### 'META-INF/spring.handlers'

#### 'META-INF/spring.schemas'

### 42.6 스프링 XML 설정에서 커스텀 확장 기능 사용하기

### 42.7 Meatier 예제

#### 커스텀 태그 내에서 커스텀 태그 중첩

#### 'normal'요소의 커스텀 속성

### 42.8 추가 리소스

## 43. 스프링 JSP 태그 라이브러리

### 43.1 소개

### 43.2 argument 태그

### 43.3 bind 태그

### 43.4 escapeBody 태그

### 43.5 eval 태그

### 43.6 hasBindErrors 태그

### 43.7 htmlEscape 태그

### 43.8 message 태그

### 43.9 nestedPath 태그

### 43.10 param 태그

### 43.11 theme 태그

### 43.12 transform 태그

### 43.13 url 태그

## 44. 스프링 폼 JSP 태그 라이브러리

### 소개

### button 태그

### checkbox 태그

### checkboxes 태그

### errors 태그

### form 태그

### hidden 태그

### input 태그

### label 태그

### option 태그

### options 태그

### password 태그

### radiobutton 태그

### radiobuttons 태그

### select 태그

### textarea 태그
