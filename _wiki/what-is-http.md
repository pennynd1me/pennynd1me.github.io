---
layout  : wiki
title   : HTTP
summary : HTTP에 대해
date    : 2022-10-11 15:41:01 +0900
updated : 2022-10-18 23:13:23 +0900
tag     : Internet
toc     : true
public  : true
parent  : [[Internet]]
latex   : false
---
* TOC
{:toc}

## HTTP

- Hypertext Transfer Protocol
- 웹에서 브라우저와 서버 간 데이터를 주고 받기 위한 통신 프로토콜
- TCP/IP 기반으로 동작한다.
- `Stateless`: 상태를 저장하지 않는다. 독립적으로 관리된다.
  - HTTP 쿠키를 통해 상태를 유지하는 세션을 만든다.

## 클라이언트와 서버

![image]( /resource/wiki/what-is-http/195616822-1685d5a9-6fe2-4841-bdbe-64b5307d405b.png )
이미지 출처: HTTP definitive guide 1장

클라이언트는 서버로 요청(request)을 보내고, 서버는 요청에 따라 적절한 응답(response)을 클라이언트로 회신한다.

## 자원(Resource)

- 웹 서버가 제공하는 모든 종류의 웹 컨텐츠

### MIME type

- Multipurpose Internet Mail Extensions
- 수 많은 종류의 멀티미디어 컨텐츠들을 분류하고 설명한다.
- 응답 메시지 헤더 Content-type에 명시된다.

```
text/html, image/jpeg, video/webm, application/pdf 등
```

### URI

- Uniform Resource Identifier
- 인터넷 상의 자원을 고유하게 식별할 수 있다.
- URL과 URN이라는 두 가지 형태가 존재한다.

```
The following are two example URIs and their component parts:

url: foo://example.com:8042/over/there?name=ferret#nose
     \_/   \______________/\_________/ \_________/ \__/
      |           |            |            |        |
   scheme     authority       path        query   fragment
      |   _____________________|__
     / \ /                        \
     urn:example:animal:ferret:nose
```

#### URL

- Uniform Resource Locator
- 상세한 위치를 명시한다.

```
scheme://[userinfo@]host[:port][/port][/path][?query][#fragment]
```

URL은 크게 3개의 부분으로 나뉜다.

- scheme: 자원에 접근하기 위해 사용할 프로토콜을 명시한다. (http/https:, ftp:, mailto: 등)
- host: 서버의 주소
- resource: 초기 웹에서는 웹 서버의 물리적 파일 위치를 나타냈지만, 요즘은 웹 서버에 처리를 요청하는 것에 가깝다.

##### fragment

URL 마지막에 `#`과 함께 붙는다.
서버에 전달되지 않으며 브라우저가 서버로부터 리소스를 받은 이후 처리된다.


#### URN

- Uniform Resource Name
- 위치에 영향을 받지 않는 고유한 이름

```
urn:isbn:9780141036144
urn:ietf:rfc:7230
```

## HTTP 메시지

- 클라이언트와 서버간의 데이터 교환을 위한 메시지
- Request와 Response 두 가지로 나눠져 있으며 서로 비슷한 구조를 공유한다.

### 상태 줄(status line)

- 실행되어야 할 요청, 또는 요청 수행에 대한 성공 또는 실패가 기록되어 있으며 항상 한 줄로 끝난다.

### 헤더

- 대소문자를 구분하지 않는 문자열 다음 `:`이 오며, 값을 포함해 각 한 줄로 표시한다.

### Request

구조
```
<method> <request-url> <version>	; Status-Line
<headers>				; Headers
					; CRLF
<entity-body>				; Optional
```
https://www.rfc-editor.org/rfc/rfc9110.html의 요청 메시지
```
GET /rfc/rfc9110.html HTTP/1.1
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Accept-Encoding: gzip, deflate, br
Accept-Language: en-US,en;q=0.9
Cache-Control: max-age=0
Connection: keep-alive
Host: www.rfc-editor.org
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: none
Sec-Fetch-User: ?1
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/106.0.0.0 Safari/537.36
sec-ch-ua: "Chromium";v="106", "Google Chrome";v="106", "Not;A=Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "macOS"
```

### Response

구조
```
<version> <status> <reason-phrase>	; Status-Line
<headers>				; Headers
					; CRLF
<entity-body>				; Optional
```
https://www.rfc-editor.org/rfc/rfc9110.html의 응답 메시지
```
HTTP/1.1 200 OK
Date: Tue, 18 Oct 2022 12:03:38 GMT
Server: Apache
X-Powered-By: PHP/7.4.6
Vary: Accept-Encoding
Content-Encoding: gzip
Strict-Transport-Security: max-age=31536000; includeSubDomains
X-Frame-Options: SAMEORIGIN
X-Xss-Protection: 1; mode=block
X-Content-Type-Options: nosniff
Keep-Alive: timeout=1, max=10
Connection: Keep-Alive
Transfer-Encoding: chunked
Content-Type: text/html; charset=UTF-8

<!DOCTYPE html>
<html lang="en" class="RFC STD">
<head>
<meta charset="utf-8">
<meta content="Common,Latin" name="scripts">
<meta content="initial-scale=1.0" name="viewport">
<title>RFC 9110: HTTP Semantics</title>
<meta content="Roy T. Fielding" name="author">
<meta content="Mark Nottingham" name="author">
<meta content="Julian Reschke" name="author">
...
```

### 응답 상태 코드

- 서버가 클라이언트 HTTP 요청에 대한 응답 상태를 나타내는 3자리 코드

#### 1xx: 정보

- 100: Continue

#### 2xx: 성공

- 200: OK
- 201: Created
- 202: Accepted
- 204: No Content
- 205: Reset Content
- 206: Partial Content

#### 3xx: 리디렉션

- 300: Multiple Choices
- 301: Moved Permanently
- 302: Found
- 304: Not Modified

#### 4xx: 클라이언트 에러

- 400: Bad Request
- 401: Unauthorized
- 402: Payment Required
- 403: Forbidden
- 404: Not Found
- 405: Method Not Allowed
- 409: Conflict

#### 5xx: 서버 에러

- 500: Internal Server Error
- 501: Not Implemented
- 502: Bad Gateway
- 503: Service Unavailable
- 504: Gateway Time-out

## 참고

- HTTP: The Definitive Guide / 데이빗 고울리 저 / 오라일리 / 2002년
- [https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/Identifying_resources_on_the_Web](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/Identifying_resources_on_the_Web)
- [https://johngrib.github.io/wiki/URI/](https://johngrib.github.io/wiki/URI/)
- [https://johngrib.github.io/wiki/http](https://johngrib.github.io/wiki/http)
- [https://www.rfc-editor.org/rfc/rfc9110.html](https://www.rfc-editor.org/rfc/rfc9110.html)
