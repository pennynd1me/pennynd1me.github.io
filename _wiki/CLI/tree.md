---
layout  : wiki
title   : tree 명령어
summary : 디렉토리를 트리 구조로
date    : 2024-02-14 17:33:46 +0900
updated : 2024-02-14 21:02:42 +0900
tag     : 
toc     : true
public  : true
parent  : [[CLI]]
latex   : false
---
* TOC
{:toc}

## 설치

```zsh
brew install tree
```

## 사용

디렉토리를 트리 구조로 보여준다.

## Syntax

```zsh
tree [path] [options]
```


## Options


| 커맨드     | 설명                             |
|------------|----------------------------------|
| -a         | 숨김 파일과 디렉토리를 포함한다. |
| -d         | 하위 디렉토리만 본다.            |
| -I pattern | 주어진 경로를 무시한다.          |
| -L level   | depth를 지정한다.                |
| -P pattern | 일치하는 파일만 포함한다.        |
| ...        | ...                              |

## Examples

```zsh
tree . -d -I "_*|node_modules"
```

## Output Fields

```
├── css
├── data
│   ├── metadata
│   │   ├── CLI
│   │   └── memo
│   └── tag
├── js
├── post-img
│   ├── "_wiki
│   │   └── \354\236\221\354\204\261-\355\205\214\354\212\244\355\212\270.md"
│   ├── index
│   └── post-test
├── resource
│   ├── icon
│   ├── skeleton-post
│   └── wiki
│       ├── Blog
│       ├── CLI
│       │   └── traceroute
│       ├── Internet
│       ├── Memo
│       │   └── 2022
│       ├── backend-roadmap
│       ├── browsers-and-how-they-work
│       ├── dns-and-how-it-works
│       ├── how-does-the-internet-work
│       ├── index
│       ├── what-is-http
│       └── write-markdown-practice
└── tool
```

## 참고

- [https://oldmanprogrammer.net/source.php?dir=projects/tree](https://oldmanprogrammer.net/source.php?dir=projects/tree)
- [https://www.geeksforgeeks.org/tree-command-unixlinux/](https://www.geeksforgeeks.org/tree-command-unixlinux/)
