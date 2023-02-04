---
layout  : wiki
title   : DNS의 작동 원리
summary : DNS and how it works?
date    : 2022-10-11 15:37:28 +0900
updated : 2023-02-04 10:38:46 +0900
tag     : 
toc     : true
public  : true
parent  : [[Internet]]
latex   : false
---
* TOC
{:toc}

# 도메인 네임 시스템

호스트의 도메인 이름을 호스트의 네트워크 주소로 바꾸거나 그 반대의 변환을 수행할 수 있도록 하는 시스템

사람이 이해하기 쉬운 도메인 이름을 컴퓨터가 이해하는 IP 주소로 변환해준다.

TCP/IP suite에서 응용 계층에서 라우팅 정보를 제공하는 `계층 구조`를 가지는 `분산형 데이터베이스` 시스템이다.

# 구성 요소

## 도메인 네임 스페이스

- 트리 구조의 네임 스페이스를 비롯해 데이터에 대한 이름 관련 규칙을 정의
- 트리에 연결된 호스트는 자원 레코드로 표현
- DNS 서비스는 자원 레코드의 특정 유형 정보를 얻는 과정

![image]( /resource/wiki/dns-and-how-it-works/216229369-96d69951-0bc1-4aad-bcfe-30256f254ecb.png )

최상위에 루트가 존재하고 그 아래로 모든 호스트가 노드로 구성된 트리 구조로 이어져 있다.

점으로 구분한 레이블의 연속이다. 같은 레벨에서는 레이블이 유일해야 한다.

### Generic TLD(gTLD)

com, org, net, info, edu, gov, mil 등

### Country Code TLD(ccTLD)

kr, jp, io, .gg 등

### FQDN

```
aws.amazon.com.
\_/ \____/ \_/\/
 |    |     | root
 |   SLD   TLD
subdomain
```

실제 이름에 대하여 그에 상응하는 모든 상위 레벨의 도메인을 모두 포함시키는 전체 이름

### PQDN

전체 경로명이 아닌 하위 부분 경로명 만으로 식별가능한 이름

## 네임 서버

- 도메인 트리 구조와 트리에 보관된 자원 레코드를 관리하는 프로그램
- 여러 네임 서버가 구역을 분할해 전체 도메인을 관리한다.
- 분할한 구역을 담당하는 주 네임서버와 백업 용도의 부 네임서버가 있음
- 캐시에 다른 서버로부터 얻어온 정보 임시 보관

## 리졸버

- 클라이언트의 요청을 받아 DNS 메시지 형식의 질의를 생성하고 네임 서버로부터 정보를 얻어냄
- 하나 이상의 네임 서버와 접촉 가능
- 캐시에 얻어온 정보 임시 보관

# 동작 과정

![image]( /resource/wiki/dns-and-how-it-works/216228647-5a3f9395-c9f4-4c41-b67f-801abe594826.png )



참고:
- [https://devopedia.org/domain-name-system](https://devopedia.org/domain-name-system)
- [http://sunnykwak.tistory.com/99](http://sunnykwak.tistory.com/99)
- [https://copycode.tistory.com/124](https://copycode.tistory.com/124)
- [https://better-together.tistory.com/128](https://better-together.tistory.com/128)
