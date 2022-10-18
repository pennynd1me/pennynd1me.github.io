---
layout  : wiki
title   : 인터넷의 작동 원리
summary : How does the internet work?
date    : 2022-09-30 14:13:25 +0900
updated : 2022-10-12 22:04:55 +0900
tag     : Internet
toc     : true
public  : true
parent  : [[Internet]]
latex   : false
---
* TOC
{:toc}

## 인터넷이란

![image]( /resource/wiki/how-does-the-internet-work/193767971-e5d8cab6-52fc-4aba-982d-b8f9605a87e5.png )
이미지 출처: [https://www.submarinecablemap.com/](https://www.submarinecablemap.com/)

- 컴퓨터들이 상호작용 할수 있는 거대한 기술적 네트워크
- 전 세계에 깔린 광케이블, UTP 등으로 직접 연결되어있다.
- 어느 하나에 의존적이지 않고 분산된 네트워킹 시스템이다.
- 어플리케이션(Web, email, streaming 등) 서비스를 제공하는 인프라

## 네트워크

![image]( /resource/wiki/how-does-the-internet-work/194316474-99c8b996-fb1d-454e-816e-e652eae4e896.png )
이미지 출처: Computer Networking 1장. figure 1.1.

- 여러 대의 host(=end system, 네트워크에 연결된 device)가 통신망을 통해 상호작용 할 수 있게 그물처럼 연결된 체계
- hosts ↔ Link-layer switch(L2 switch) ↔ 라우터 ↔ (DSL, Cable, FTTH 모뎀) ↔ ISPs ↔ 인터넷

| Network Edge               | Access network             | Network Core     |
|----------------------------|----------------------------|------------------|
| hosts, switch, edge router | DSL, Cable, FTTH 등        | core router, ISP |

### LAN

- Local Area Network
- 집, 사무실 등 제한된 지역에서 여러 대의 host를 연결 하기 위해 구성하는 네트워크

### WAN

- Wide Area Network
- 멀리 떨어진 LAN을 서로 연결 하는 광역 네트워크
- 인터넷은 가장 큰 규모의 WAN이라고 볼 수 있다.

## IP 주소

- 각 host가 식별, 통신을 하기 위해 가지는 고유한 주소

### IPv4

- 32 bits(약 43억 개)의 값을 가질 수 있는 주소 체계
  - 8비트씩 끊어 10진수 숫자로 표기하고(0 to 255), 각 숫자를 점으로 구분한다.

### IPv6

- 128 bits의 값을 가질 수 있는 주소 체계
  - 16진수 숫자 32개로 표기하고, 4개마다 쌍점으로 구분한다. (16 bits * 8)
  - IPv4 주소의 고갈을 앞두고 고안 되었으며, 라우팅에 효과적으로 쓰게끔 만들었다고 한다.

## DNS

- 인터넷의 전화번호부의 역할을 해주는 시스템
- 외우기 어려운 숫자인 IP 주소 대신 우리가 읽고 쓰는 도메인 이름을 사용, IP 주소로 변환하여 보다 쉽게 통신할 수 있다.

## 패킷

- 네트워크를 통해 전송하기 쉽도록 자른 데이터의 전송 단위
- 송신하는 곳에서 분할해서 전송하고 수신하는 곳에서 재조립한다.

헤더: 패킷의 송수신 주소 등 주요 제어 정보들이 포함되어 있다.

페이로드: 실제 데이터가 담긴 영역

### 패킷 교환 방식

- Store-and-forward transmission: 온전한 패킷을 받아(Store) 헤더를 분석을 마치고 난 후 전달(Forward)해준다.
  - 네트워크 자원이 필요할 때만 사용할 수 있다.

## 프로토콜

- host간의 하드웨어와 소프트웨어가 다를 수 있기 때문에 표준화된 통신 규약으로서 상호작용 할 수 있게 함

- Ethernet: 동일 네트워크에서 패킷 전송
- IP: 네트워크간 패킷 전송
- TCP: 패킷이 순서대로 성공적으로 도착 보장
- HTTP: 웹사이트와 어플리케이션의 데이터 포맷과 통신

### TCP/IP

- TCP및 IP라고 불리우는 프로토콜을 중심으로 구성되는 일련의 프로토콜군(Protocol suite)의 통칭

## 라우터

- 서로 다른 네트워크 간에 중계 역할을 해주는 장치
- 최적의 경로(route)를 지정해 다음 장치로 전달
- WAN에서 서로 다른 네트워크를 연결해준다.

패킷의 헤더를 분석해 목적지 주소를 읽고 동일 네트워크 내에 있지 않다면 인접한 다른 라우터로 전송한다.

### 라우팅 테이블

- 경로 선택의 근거
- 목적지에 도달하기 위한 경로 정보를 기반으로 최적의 경로로 데이터를 전달한다.

## 스위치

- 네트워크 내에서 데이터 전송을 해주는 장치
- LAN에서 여러 대의 기기를 연결해준다.
- L2 스위치의 경우 ARP를 통해 MAC주소를 기반으로 하여 통신한다.

## 예시로 보는 작동 원리

인터넷의 수 많은 서비스 중에 지금 이 글을 작성하고 업로드 하는 이 웹사이트와 통신을 한다고 가정해보자.

이 웹사이트는 github pages를 통해 hosting 되어 인터넷을 통해 어딘가에 있는 서버에서 돌아가고있다.

[[/CLI/traceroute]]로 IP 패킷을 보내 경로를 추적할 수 있다.

```zsh
$ traceroute -I -q1 pennynd1me.github.io
traceroute: Warning: pennynd1me.github.io has multiple addresses; using 185.199.111.153
traceroute to pennynd1me.github.io (185.199.111.153), 64 hops max, 72 byte packets
 1  192.168.30.1 (192.168.30.1)  11.796 ms
 2  14.6.95.1 (14.6.95.1)  38.946 ms
 3  10.21.241.37 (10.21.241.37)  6.439 ms
 4  10.242.230.173 (10.242.230.173)  5.530 ms
 5  1.213.28.57 (1.213.28.57)  5.786 ms
 6  1.213.105.157 (1.213.105.157)  8.718 ms
 7  *
 8  *
 9  1.208.179.54 (1.208.179.54)  13.158 ms
10  1.208.150.113 (1.208.150.113)  8.432 ms
11  bundle-ether41.br05.tok01.pccwbtn.net (63.218.146.118)  36.694 ms
12  205-177-84-66.static.pccwglobal.net (205.177.84.66)  39.782 ms
13  cdn-185-199-111-153.github.com (185.199.111.153)  41.403 ms
```

통신을 하기 위해서는 IP 주소를 알거나, 도메인 이름을 알아야 한다고 했다.

도메인 이름인 pennynd1me.github.io를 알고 있어 입력하니 DNS 서버를 통해 185.199.111.153라는 IP주소로 변환해 패킷을 보낼 수 있게 되었다.

현재 내 IP주소는 `192.167.30.1` 이라는 사설 IP(Private IP)를 가지고 있으며, switch와 edge router에서 NAT(Network Address Translation)를 거쳐 공인 IP(Public) `14.6.95.1` 를 가져 인터넷에 연결될 것이다.

그 후 Core network에서 수 많은 라우터를 통해 패킷이 전해지고 일본을 거쳐 미국까지 넘어가 캘리포니아에 있는 server와 통신을 할 수 있게 되는 것이다.
![image]( /resource/wiki/how-does-the-internet-work/195280526-3dff0d33-4bcf-41e2-be71-32346749a627.png )
이미지 출처: traceroute-mapper

하지만 이건 단순히 인터넷이 실제로 연결되어 있다는 것만을 설명하고 있을 뿐이며, 더 자세하고 깊은 내용은 앞으로 더 공부하여 추가하도록 해야겠다.

## 참고

- [https://fcit.usf.edu/network/chap1/chap1.htm#WideAreaNetwork](https://fcit.usf.edu/network/chap1/chap1.htm#WideAreaNetwork)
- [https://www.cloudflare.com/learning/network-layer/how-does-the-internet-work/](https://www.cloudflare.com/learning/network-layer/how-does-the-internet-work/)
- [https://stefansundin.github.io/traceroute-mapper/](https://stefansundin.github.io/traceroute-mapper/)
- Computer Networking: A Top Down Approach / 제임스 쿠로세, 키쓰 로스 저 / 피어슨 / 2020년
