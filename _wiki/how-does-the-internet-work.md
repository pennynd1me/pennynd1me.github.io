---
layout  : wiki
title   : 인터넷의 작동 원리
summary : How does the internet work?
date    : 2022-09-30 14:13:25 +0900
updated : 2022-10-06 23:53:35 +0900
tag     : Internet
toc     : true
public  : true
parent  : [[Internet]]
latex   : false
---
* TOC
{:toc}

## 인터넷이란

- 컴퓨터들이 상호작용 할수 있는 거대한 기술적 네트워크 인프라
- 전 세계에 깔린 광케이블, UTP 등으로 직접 연결되어있다.
- 어느 하나에 의존적이지 않고 분산된 네트워킹 시스템이다.

![image]( /resource/wiki/how-does-the-internet-work/193767971-e5d8cab6-52fc-4aba-982d-b8f9605a87e5.png )

## 네트워크

- 여러 대의 host(=end system)가 통신망을 통해 상호작용 할 수 있게 그물처럼 연결된 체계

- 여러 대의 host ↔ (Link-layer switch) ↔ 라우터 ↔ (모뎀) ↔ ISP ↔ 인터넷

![image]( /resource/wiki/how-does-the-internet-work/194316474-99c8b996-fb1d-454e-816e-e652eae4e896.png )
이미지 출처: Computer Networking 1장. figure 1.1.

## 패킷

- 네트워크를 통해 전송하기 쉽도록 자른 데이터의 전송 단위
- 송신하는 곳에서 분할해서 전송하고 수신하는 곳에서 재조립한다.

헤더: 패킷의 송수신 주소 등 주요 제어 정보들이 포함되어 있다.

페이로드: 실제 데이터가 담긴 영역

트레일러: 패킷 에러 검출 등에 사용되지만 특정한 네트워크 프로토콜에서만 사용한다.

## 라우터

- 서로 다른 네트워크 간에 중계 역할을 해주는 장치

패킷의 헤더를 분석해 목적지 주소를 읽고 동일 네트워크 내에 있지 않다면 인접한 다른 라우터로 전송한다.

## 프로토콜

- 서로 다른 end system이 하드웨어와 소프트웨어가 다를 수 있기 때문에 표준화된 통신 규약으로서 상호작용 할 수 있게 함

- TCP/IP: TCP및 IP라고 불리우는 프로토콜을 중심으로 구성되는 일련의 프로토콜군(Protocol suite)의 통칭
  - TCP와 IP외에 TCP를 기반으로한 FTP나 HTTP등이나 UDP 등

## 참고

- [https://developer.mozilla.org/en-US/docs/Learn/Common_questions/How_does_the_Internet_work](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/How_does_the_Internet_work)
- [https://www.submarinecablemap.com/](https://www.submarinecablemap.com/)
- [https://www.cloudflare.com/learning/network-layer/how-does-the-internet-work/](https://www.cloudflare.com/learning/network-layer/how-does-the-internet-work/)
- [http://www.ktword.co.kr/test/view/view.php?m_temp1=205&id=861](http://www.ktword.co.kr/test/view/view.php?m_temp1=205&id=861)
- Computer Networking: A Top Down Approach / 제임스 쿠로세, 키쓰 로스 저 / 피어슨 / 2020년
