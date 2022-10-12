---
layout  : wiki
title   : traceroute 명령어
summary : 네트워크 상태 진단 도구
date    : 2022-10-12 17:34:24 +0900
updated : 2022-10-12 18:08:03 +0900
tag     : 
toc     : true
public  : true
parent  : [[CLI]]
latex   : false
---
* TOC
{:toc}

## 사용

hop-by-hop으로 IP 네트워크 사이의 라우터 경로를 추적한다.

## Syntax

```zsh
traceroute [options] <hostname or IP> [packet length]
```

## Options

| 커맨드               | 설명                                              |
|----------------------|---------------------------------------------------|
| -I                   | ICMP 패킷을 보낸다. (default: UDP)                |
| -n                   | 결과에서 디바이스 이름을 숨긴다.                  |
| -q number of packets | 보낼 패킷 수를 지정한다. (default: 3)             |
| -w wait_time         | 각 응답의 최대 대기 시간을 명시한다. (default: 5) |
| ...                  | ...                                               |

## Examples

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

## Output Fields

| 필드                         | 설명                                                                          |
|------------------------------|-------------------------------------------------------------------------------|
| 1, 2, 3..                    | 홉 번호                                                                       |
| 192.168.30.1                 | IP Address 혹은 hostname                                                      |
| 64 hops max, 72 byte packets | 최대 TTL 값과 패킷 데이터 크기                                                |
| 11.796ms                     | 각 라우터, 호스트에 도달하고 다시 돌아온 총 시간. ICMP 데이터그램 메시지 응답 |

## 참고

- [https://www.hostinger.com/tutorials/traceroute-command](https://www.hostinger.com/tutorials/traceroute-command)
- [https://www.cisco.com/E-Learning/bulk/public/tac/cim/cib/using_cisco_ios_software/cmdrefs/traceroute.htm](https://www.cisco.com/E-Learning/bulk/public/tac/cim/cib/using_cisco_ios_software/cmdrefs/traceroute.htm)
