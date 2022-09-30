---
layout  : wiki
title   : 백엔드 로드맵
summary : 
date    : 2022-09-30 14:57:37 +0900
updated : 2022-09-30 16:40:20 +0900
tag     : 
toc     : true
public  : true
parent  : [[index]]
latex   : false
---
* TOC
{:toc}

[http://roadmap.sh/backend](http://roadmap.sh/backend)
![image]( /resource/wiki/write-markdown-practice/193042090-85247849-a75d-46a5-b4d0-9d22cf4df9a5.png )

## 인터넷

- [[how-does-the-internet-work]]
- HTTP
- 브라우저와 작동 원리
- DNS와 작동 원리
- 도메인 네임
- 호스팅

## 기초 프론트엔드 지식

- HTML
- CSS
- JavaScript

## 운영체제와 일반적 지식

- 터미널 사용
- 운영체제의 일반적 작동 원리
- 프로세스 관리
- 스레드와 동시성
- 터미널 기본 명령
- 메모리 관리
- 프로세스 간 통신
- 입출력 관리
- POSIX 기초
- 네트워크 기본 개념

## 언어 배우기

- 자바
- 자바스크립트

## 버전 관리 시스템과 저장소 호스팅 서비스

- Git 기본 사용법
- Github

## 관계형 데이터베이스

- PostgreSQL
- MySQL
- MariaDB

## 더 깊은 데이터베이스 지식

- ORM
- ACID
- 트랜잭션
- N+1 문제

### NoSQL 데이터베이스

- 데이터 레플리케이션
- 샤딩 전략
- CAP 이론

## API

- HATEOAS
- 오픈 API 명세와 스웨거
- 인증
  - 쿠키 기반
  - OAuth
  - Basic 인증
  - 토큰 인증
  - JWT
  - OpenID
  - SAML
- REST (Roy Fielding 논문)
- JSON APIs
- SOAP

## 캐시

- CDN
- 서버사이드
  - Redis
  - Memcached
- 클라이언트 사이드

## 웹 보안 지식

- 해시 알고리즘
  - MD5와 이를 사용하지 않는 이유
  - SHA 함수군
  - scrypt
  - bcrypt
- HTTPS
- 콘텐츠 보안 정책(SCP)
- CORS
- SSL/TLS
- OWASP 보안 취약점

## 테스트

- 통합 테스트
- 단위 테스트
- 기능 테스트

## 지속적 통합과 지속적 전달(배포)


## 개발 설계 원칙

- GoF 디자인 패턴
- 도메인 주도 설계
- 테스트 주도 개발
- SOLID
- KISS
- YAGNI
- DRY

### 아키텍쳐 패턴

- 모놀리식 애플리케이션
- 마이크로서비스
- SOA
- CQRS와 이벤트 소싱
- 서버리스

## 검색 엔진

- ElasticSearch
- Solr

## 메시지 브로커

- RabbitMQ
- Kafka

## 컨테이너화 대 가상화

- Docker
- rkt, lxc

## 그래프QL

- Apollo
- Relay Modern

### 그래프 데이터베이스

- Neo4j

## 웹소켓



## 웹 서버

- Nginx
- Apache
- Caddy
- MS IIS

## 확장성 있는 구축

- 완화(mitigation) 전략
  - Graceful Degradation
  - Throttling
  - Backpressure
  - Loadshiftiing
  - Circuit Breaker
- 차이 이해하기
  - Instrumentation
  - Monitoring
  - Telemetry
- 마이그레이션 전략
- 수평 확장 대 수직 확장
- 관측 가능성을 고려한 구축
  - 디버깅과 로그 등 관측 가능한 항목들

