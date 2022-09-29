---
layout  : wiki
title   : 마크다운 작성 연습
summary : 
date    : 2022-09-29 21:07:11 +0900
updated : 2022-09-30 00:49:03 +0900
tag     : practice
toc     : true
public  : true
parent  : 
latex   : false
---
* TOC
{:toc}

# 마크다운 기본 문법

Jekyll에서는 기본적으로 kramdown을 지원한다.

## 헤더 (Header)

```markdown
header 1
======

header 2
------

# header 1
## header 2
### header 3
#### header 4
##### header 5
###### header 6
```
## 인용문 (Blockquote)

```markdown
> This is a blockquote.
>	 on multiple lines
that may be lazy.
>
> This is the second paragraph.
> > A nested blockquote.
>
> ### Headers work
>
> * lists too
>
> and all other block-level elements
```

> This is a blockquote.
>	 on multiple lines
that may be lazy.
>
> This is the second paragraph.
> > A nested blockquote.
>
> ### Headers work
>
> * lists too
>
> and all other block-level elements

## 코드 블럭 (Code block)

```markdown
~~~ 혹은 ```(첫 줄에 언어 지정 가능)
This is code block.
~~~ 혹은 ```
```

~~~
This is code block.
~~~

```
This is also code block.
```

## 인라인 코드 (Inline Code Block)

```markdown
`인라인 코드 블럭`
```

`인라인 코드 블럭`

## 강조 (Emphasis)

```markdown
*이탤릭* _이탤릭_

**볼드** __볼드__
```

*이탤릭* _이탤릭_

**볼드** __볼드__

## 리스트 (List)

```markdown
* kram
+ down
- now

1. kram
2. down
3. now
```

* kram
+ down
- now

1. kram
2. down
3. now

```markdown
* list 1 item 1
 * list 1 item 2 (indent 1 space)
  * list 1 item 3 (indent 2 spaces)
   * list 1 item 4  (indent 3 spaces)
    * lazy text belonging to above item 4
```

* list 1 item 1
 * list 1 item 2 (indent 1 space)
  * list 1 item 3 (indent 2 spaces)
   * list 1 item 4  (indent 3 spaces)
    * lazy text belonging to above item 4

```markdown
* list 1 item 1
  * nested list item 1
  * nested list item 2
* list 1 item 2
  * nested list item 1
```

* list 1 item 1
  * nested list item 1
  * nested list item 2
* list 1 item 2
  * nested list item 1

## 각주 (Footnote)

```markdown
각주[^fn]
[^fn]: 각주에 대한 설명
각주2[^footnote]
[^footnote]: 각주2에 대한 설명
```

각주[^fn]
[^fn]: 각주에 대한 설명
각주2[^footnote]
[^footnote]: 각주2에 대한 설명

# 표 입력

Vimwiki 단축키 \wt

```markdown
| 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|
| a | b | c | d | e |
| f | g | h | i | j |
```

| 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|
| a | b | c | d | e |
| f | g | h | i | j |

## [리스트를 테이블로 변환하는 기능](https://johngrib.github.io/wiki/blog/this/table-generate/)

```
<div id="table1"></div>
- th
    - Spring
    - javax.inject.*
    - javax.inject restrictions / comments
- tr
    - @Scope("singleton")
    - @Singleton
    - The JSR-330 default scope is like Spring’s prototype. However, in order to keep it consistent with Spring’s general defaults, a JSR-330 bean declared in the Spring container is a singleton by default. In order to use a scope other than singleton, you should use Spring’s @Scope annotation. javax.inject also provides a @Scope annotation. Nevertheless, this one is only intended to be used for creating your own annotations.
- tr
    - @Qualifier
    - @Qualifier / @Named
    - javax.inject.Qualifier is just a meta-annotation for building custom qualifiers. Concrete String qualifiers (like Spring’s @Qualifier with a value) can be associated through javax.inject.Named.
- tr
    - ObjectFactory
    - Provider
    - javax.inject.Provider is a direct alternative to Spring’s ObjectFactory, only with a shorter get() method name. It can also be used in combination with Spring’s @Autowired or with non-annotated constructors and setter methods.
{:class="table-generate" data-target-id="table1"}
```

<div id="table1"></div>
- th
    - Spring
    - javax.inject.*
    - javax.inject restrictions / comments
- tr
    - @Scope("singleton")
    - @Singleton
    - The JSR-330 default scope is like Spring’s prototype. However, in order to keep it consistent with Spring’s general defaults, a JSR-330 bean declared in the Spring container is a singleton by default. In order to use a scope other than singleton, you should use Spring’s @Scope annotation. javax.inject also provides a @Scope annotation. Nevertheless, this one is only intended to be used for creating your own annotations.
- tr
    - @Qualifier
    - @Qualifier / @Named
    - javax.inject.Qualifier is just a meta-annotation for building custom qualifiers. Concrete String qualifiers (like Spring’s @Qualifier with a value) can be associated through javax.inject.Named.
- tr
    - ObjectFactory
    - Provider
    - javax.inject.Provider is a direct alternative to Spring’s ObjectFactory, only with a shorter get() method name. It can also be used in combination with Spring’s @Autowired or with non-annotated constructors and setter methods.
{:class="table-generate" data-target-id="table1"}

# 이미지 입력

github 이슈 댓글에 이미지를 붙여넣으면 업로드 되며 다음과 같이 쓸 수 있다.

여기에 추가로 종립님이 만들어주신 pre-commit 훅으로 이미지를 자동으로 다운로드 하여 로컬에 자동으로 저장되며 문서에 포함된 링크 또한 다운로드한 파일을 바라본다. [참고](https://johngrib.github.io/wiki/my-wiki/#%EC%9D%B4%EB%AF%B8%EC%A7%80%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%9C%EB%8B%A4)

`![image]( /resource/wiki/write-markdown-practice/193042090-85247849-a75d-46a5-b4d0-9d22cf4df9a5.png )`
![image]( /resource/wiki/write-markdown-practice/193042090-85247849-a75d-46a5-b4d0-9d22cf4df9a5.png )

# 내부 링크와 외부 링크

## 내부 링크: [[/memo]]

```
[[/memo]]
```

## 외부 링크: [google](https://google.com)

```
[google](https://google.com)
```

# 추가로 볼 내용

 [외부 링크에 외부 링크 아이콘 추가](https://github.com/johngrib/johngrib.github.io/commit/214c7f3593557aff064d41b1b573881279b9d9e5)

# 참고 링크
- [이종립님의 블로그](https://johngrib.github.io/wiki/my-wiki/#%EC%8B%A4%EC%A0%9C%EB%A1%9C-%EC%96%B4%EB%96%BB%EA%B2%8C-%EC%82%AC%EC%9A%A9%ED%95%98%EB%82%98)
- [kramdown-syntax](https://kramdown.gettalong.org/syntax.html)

