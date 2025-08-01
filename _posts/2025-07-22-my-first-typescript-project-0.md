---
layout: post
title: "[나의 첫 타입스크립트 프로젝트] 들어가며"
description: "My first step for typescript."
date: 2025-07-22
feature_image: images/my-first-typescript-project.jpeg
tags: [나의 첫 타입스크립트 프로젝트, typescript, book, review]
---
**타입스크립트(Typescript)**라...

나에게 스크립트 언어는 '스낵'같은 존재다. 가끔씩 스낵을 먹으면 맛있긴 하지만 밥이 될 수 없듯이, 스크립트 언어는 전통적인(?) 언어와 다른 그런 느낌이다.
아주 오래 전, 내가 Java/JSP 웹 개발자로 일할 때 처음 접했던 스크립트 언어를 지금 다시 들여다 보려 한다.
이 책을 가지고 차분히 읽어가며 내용을 정리해 보련다. 책이 그리 두껍지 않고 (살짝 훑어보니) 쉽게 따라할 수 있는 구성인 듯 하다.
궁금한 점과 이해되지 않는 점 뿐만 아니라, 놀랍고 신기한 것들도 기록해두자. 타입스크립트로 만들 수 있는 토이 프로젝트도 만들어 봐야겠다. <br>
타입스크립트. 무엇을 어디까지 할 수 있는 것인지 무척 궁금하다.

<!--more-->

## Typescript?

[타입스크립트](https://ko.wikipedia.org/wiki/타입스크립트){:target="_blank"}가 무엇일까? 위키피디아의 내용을 요약하면 다음과 같다.
+ 자바스크립트의 슈퍼셋인 오픈소스 프로그래밍 언어<br>
+ 마이크로소프트에서 개발, 유지하고 있으며 엄격한 문법을 지원<br>
+ 모든 운영 체제, 모든 브라우저, 모든 호스트에서 사용 가능한 오픈 소스

타입스크립트로 만들 수 있는 것들은 무엇을까?

ChatGPT는 이렇게 말하고 있다.

1. 웹 프론트엔드 애플리케이션
+ **SPA (Single Page Application)**
  + React, Vue, Angular 등과 함께 사용 
  + 예: 블로그, 쇼핑몰, 대시보드, 포트폴리오 사이트 
+ **PWA (Progressive Web App)** 
  + 웹앱을 설치형 앱처럼 만들기 
  + 예: Todo 앱, 뉴스 리더, 오프라인 메모 앱

2. 백엔드 애플리케이션 (Node.js 기반)
+ **REST API 서버**
  + Express, Fastify, NestJS 등 사용 
  + 예: 사용자 인증 서버, 게시판 API, 쇼핑몰 백엔드
+ **GraphQL 서버**
  + Apollo Server, NestJS 등과 함께 사용
+ **실시간 서버**
  + Socket.io, WebSocket 기반 채팅/게임 서버
+ 서버리스 함수 (Serverless Functions)
  + Vercel, AWS Lambda, Cloudflare Workers

3. 데스크톱 애플리케이션
+ **Electron 기반 앱**
  + 웹 기술로 데스크톱 앱 개발 (Windows/Mac/Linux)
  + 예: 메모장, 코드 에디터, 뮤직 플레이어, 슬랙 클론

4. 모바일 애플리케이션
+ **React Native + TypeScript**
  + iOS/Android 앱 개발
  + 예: SNS 앱, 할일 앱, 피트니스 트래커
+ **Expo (React Native 플랫폼)**
  + 빠른 프로토타이핑 및 배포
 
5. 게임
+ **웹 게임**
  + HTML5 + TypeScript + Pixi.js / Phaser.js
  + 예: 캐주얼 게임, 2D 게임, 브라우저 기반 RPG
+ **Node.js 기반 멀티플레이어 서버**
  + 실시간 게임 로직 구현 (예: 온라인 보드게임 서버)

6. 도구/라이브러리/패키지
+ **NPM 라이브러리**
  + 유틸리티 함수, 날짜 라이브러리, 데이터 처리 등
+ **CLI 툴 (Command Line Interface)**
  + ts-node, oclif, yargs 등을 이용 
  + 예: 배포 도구, 로컬 파일 변환기
  
7. 테스트 및 자동화 도구
+ **테스트 스크립트**
  + Jest, Playwright, Cypress, Vitest 등과 함께 사용
+ **자동화 봇** 
  + Slack 봇, Discord 봇, Telegram 봇

8. AI/머신러닝 프론트엔드 UI
+ **OpenAI, Hugging Face API를 활용한 프론트엔드 UI**
+ 예: 챗봇, 이미지 생성기, 요약 도우미 등

## About this book

이 책은 [제이펍 출판사](https://www.jpub.kr){:target="_blank"}에서 2025년 6월 12일(1판 1쇄)에 발행된 책이다.
> **출판사** 제이펍 <br>
> **저작권사** 제이펍 <br>
> **도서명** LUVIT♥ 나의 첫 타입스크립트 프로젝트 <br> 
> **부제** 타입스크립트 + 리액트 + NestJS + 몽고DB로 나만의 블로그 만들기 <br> 
> **지은이** 조용수 <br>
> **시리즈** LUVIT(러빗) <br>
> **출판일** 2025. 06. 12 <br>
> **페이지** 268쪽 <br>
> **판 형** 46배판변형(188*245*13.9) <br>
> **제 본** 무선(soft cover) <br>
> **정 가** 26,000원 <br>
> **ISBN** 979-11-94587-28-6 (93000) <br>
> **키워드** 함수, 인터페이스, 데커레이터, 제네릭, undefined, react, UI, TailwindCSS, MongoDB, TypeScript <br> 
> **분 야** 프로그래밍 언어 / 타입스크립트 <br>
