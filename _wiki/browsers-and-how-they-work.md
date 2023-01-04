---
layout  : wiki
title   : 브라우저와 작동 원리
summary : Browsers and how they work?
date    : 2022-10-11 15:40:13 +0900
updated : 2023-01-04 22:59:55 +0900
tag     : 
toc     : true
public  : true
parent  : [[Internet]]
latex   : false
---
* TOC
{:toc}

## 브라우저

- 웹사이트에 접근하기위한 응용 소프트웨어

## 주요 기능

- 사용자가 선택한 자원을 서버에 요청하고 브라우저에 표시한다.
- HTML과 CSS 명세에 따라 HTML 파일을 해석해서 표시한다.

## 기본 구조

![image]( /resource/wiki/browsers-and-how-they-work/208055021-5185996c-280b-4abd-8b34-5167e3b89371.png )

1. 사용자 인터페이스: 주소 표시줄, 이전/다음 버튼, 북마크 메뉴 등.
  요청한 페이지를 보여주는 창을 제외한 나머지 부분
2. 브라우저 엔진: 사용자 인터페이스와 렌더링 엔진 사이의 동작 제어한다.
3. 렌더링 엔진: 요청 컨텐츠 표시. HTML과 CSS를 파싱하여 화면에 표시한다.
4. 통신: HTTP 요청과 같은 네트워크 호출에 사용. 플랫폼 독립적인 인터페이스이며 각 플랫폼 하부에서 실행된다.
5. UI 백엔드: 콤보 박스와 창 같은 기본적인 장치를 그림. 플랫폼에서 명시하지 않은 일반적인 인터페이스로서 OS 사용자 인터페이스 체계를 사용한다.
6. 자바스크립트 해석기: 자바스크립트 코드를 해석하고 실행한다.
7. 자료 저장소: 자료를 저장하는 계층. 쿠키 저장과 같이 모든 종류의 자원을 하드 디스크에 저장할 필요가 있다. HTML5 명세에는 브라우저가 지원하는 '웹 데이터베이스'가 정의되어 있다.

## 렌더링 엔진의 역할

- 요청 받은 내용을 브라우저 화면에 표시한다. (Render)
- HTML 및 XML 문서와 이미지를 CSS로 표시한다. 플러그인이나 확장 프로그램을 이용해 PDF 등을 표시하는 것도 가능하다.

## 동작 과정

통신으로부터 요청받은 문서의 내용으로 시작하며 문서의 내용은 보통 8kB 단위의 chunk로 전송된다.

![image]( /resource/wiki/browsers-and-how-they-work/208065397-8947d2e6-c0ab-4ffa-9439-0b1a1bca2800.png )

HTML 문서를 [파싱](#파싱)하고 태그를 [DOM](#dom) 노드로 변환한다.

그 다음 외부 CSS 파일과 함께 포함된 스타일 요소도 파싱한다.

스타일 정보와 HTML 표시 규칙을 합쳐 [렌더 트리](#렌더-트리-dom--cssom)라는 또 다른 트리를 생성한다.

렌더 트리는 색상, 면적과 같은 시각적 요소를 포함한 사각형으로 이루어져 정해진 순서대로 화면에 표시된다.

렌더 트리의 생성이 끝나면 각 노드를 화면의 정확한 위치에 표시하기위한 [배치](#배치-layout)과정으로 넘어간다.

그 후 UI 백엔드에서 렌더 트리의 각 노드를 가로지르며 형상을 만들어내는 [그리기](#그리기-painting)단계로 넘어간다.

일련의 과정들이 점진적으로 진행된다는 것을 아는 것이 중요하다.
렌더링 엔진은 좀 더 나은 사용자 경험을 위해 가능하면 빠르게 내용을 표시하기 위해 모든 HTML을 파싱할 때까지 기다리지 않고 배치와 그리기 과정을 시작한다.
네트워크로부터 나머지 내용이 전송되기를 기다리는 동시에 받은 내용의 일부를 먼저 화면에 표시하는 것이다.

### 동작 과정 예시

#### Webkit

- 사파리와 크롬

![image]( /resource/wiki/browsers-and-how-they-work/208069728-d1b93ac6-d509-43f8-b149-970a4dc5eb31.png )

#### Gecko

- 파이어폭스

![image]( /resource/wiki/browsers-and-how-they-work/208069899-60e4759e-3221-4f67-bc73-a5667ed0876b.png )

## 파싱

문서 파싱은 브라우저가 코드를 이해하고 사용할 수 있는 구조로 변환하는 것을 의미한다.

html 파서가 문서에 존재하는 어휘와 구문을 분석하며 DOM tree를 구축한다.

css 파서가 css 정보를 분석하며 CSSOM tree를 구축한다.

## DOM

HTML 요소들의 구조화된 표현. Document Object Model

![image]( /resource/wiki/browsers-and-how-they-work/210568446-c4932a3b-6db6-42ff-ae74-cca90e8d4e24.png )

1. Conversion: 브라우저가 바이트코드를 읽어 UTF-8 같은 특정한 인코딩에 따라 문자로 변환한다.
2. Tokenizing: 변환된 문자들을 W3C HTML5 표준에 따라 <html>, <body>와 같은 문자열로 변환한다. 각 토큰은 특정한 규칙에 따르는 특정한 의미를 갖는다.
3. Lexing: 각 토큰을 속성과 규칙을 정의하는 객체로 변환한다.
4. DOM construction: 각기 다른 태그들을 트리 구조(부모-자식 관계)로 연결시킨다.

## CSSOM

요소들과 연관된 스타일 정보의 구조화된 표현. CSS Object Model

![image]( /resource/wiki/browsers-and-how-they-work/210568684-de0ccefd-b298-4778-a165-c93d2416d5a7.png )

![image]( /resource/wiki/browsers-and-how-they-work/210568734-4cc46804-e990-4713-b1ee-17ecfec50489.png )


## 렌더 트리 (DOM + CSSOM)

DOM과 CSSOM을 합쳐 렌더 트리가 된다.

![image]( /resource/wiki/browsers-and-how-they-work/210567080-b875fca2-6a94-480b-8d77-81026e615321.png )

브라우저 뷰포트에 보이는 것. 오직 스크린에 그려지는 것으로 구성되어 있다.

## 배치 (layout)

렌더러가 생성되어 트리에 추가될 때 크기와 위치 정보는 없는데 이런 값을 계산하는 것을 배치 또는 리플로라고 부른다.

## 그리기 (painting)

그리기 단계에서는 화면에 내용을 표시하기 위한 렌더 트리가 탐색되고 렌더러의 paint() 메서드가 호출된다. 그리기는 UI 기반의 구성 요소를 사용한다.

## 참고

- [https://web.dev/howbrowserswork/](https://web.dev/howbrowserswork/)
- [https://d2.naver.com/helloworld/59361](https://d2.naver.com/helloworld/59361)
- [https://developer.mozilla.org/en-US/docs/Web/Performance/How_browsers_work](https://developer.mozilla.org/en-US/docs/Web/Performance/How_browsers_work)
- [https://wit.nts-corp.com/2019/02/14/5522])(https://wit.nts-corp.com/2019/02/14/5522)
- [https://web.dev/critical-rendering-path-constructing-the-object-model/](https://web.dev/critical-rendering-path-constructing-the-object-model/)
