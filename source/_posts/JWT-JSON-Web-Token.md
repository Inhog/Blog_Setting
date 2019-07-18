---
title: JWT(JSON Web Token)
date: 2019-07-16 10:08:03
tags:
- JSON
- Token
- OAuth
- JWT
---


>JWT에 대해 알아보기전 토큰 기반 인증시스템의 기본적인 개념에 대해 알아보는 포스트를 먼저 보는것을 추천드린다.
[토큰(Token)기반 인증에 대한 소개](https://velopert.com/2350)


###JWT(JSON Web Token)이란?

JSON Web Token(JWT)은 웹표준(RFC 7519)구현체로서 JSON 객체를 사용하는 클레임 기반 토큰의 대표적인 예이다.

JWT는 헤더(header), 페이로드(payload), 서명(signature) 세 가지로 나눠져 있으며, 아래와 같은 형태로 구성되어 있다.


`xxxxx.yyyyy.zzzzz`

구분자 `.` 으로 구분된 세 부분으로 구성되어있다.

####참고

[JSON Web Token 소개 및 구조](https://velopert.com/2389)

[JWT공식페이지](https://jwt.io/introduction/)
