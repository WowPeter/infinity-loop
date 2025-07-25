---
layout: post
title: "[나의 첫 타입스크립트 프로젝트] Chapter 2."
description: "TypeScript Environment Setup"
date: 2025-07-24
feature_image: images/book-typescript-2.png
tags: [나의 첫 타입스크립트 프로젝트, typescript, book, review]
---

# Chapter 2. 타입스크립트 환경 설정

타입스크립트의 강력한 기능을 십분 활용하기 위해서는 먼저 타입스크립트 개발 환경을 제대로 구축해야 한다.
이번 장에서는 타입스크립트를 본격적으로 공부하기 전에 설치부터 시작하여 기본적인 개발 환경을 설정하고, 첫 프로젝트를 만들어 실행해본다.  

<!--more-->

## 2.1 타입스크립트 개발 환경

### 2.1.1 Node.js 설치

프로그래밍 언어는 컴파일 언어<sub>compiled languages</sub>와 인터프리트 언어<sub>interpreted languages</sub>로 나뉜다.
자바스크립트 언어는 인터프리트 언어로 런타입 환경<sub>runtime environment</sub> 위에서 동작한다. 즉, **자바스크립트는 런타임 환경을 반드시 설치해야 한다.**
이 책에서는 자바스크립트 런타임 환경인 노드<sub>Node.js</sub>를 설치한다.

그런데, 갑자기 왠 자바스크립트 타령이냐!<br>
그 이유는 타입스크립트를 서버 또는 컴퓨터에서 실행되도록 하기 위해 런타입 환경이 필요한데, 그것을 자바스크립트 런타입 환경인 노드로 한다는 것이다.
이렇게 되면 타입스크립트 파일을 자바스크립트 파일로 변환해야 하는데 그것을 트랜스파일<sub>transpile</sub>이라고 하며 타입스크립트가 그것을 가능하게 한다.

[Node.js 공식 사이트](https://nodejs.org)에서 **LTS**<sub>Long Term Support</sub> 버전을 다운로드하여 설치한다.
{% include image_caption.html imageurl="images/book-typescript-2-1.png" title="Node.js Download" caption="Node.js 다운로드" %}

### 2.1.2 IDE 설치

**통합 개발 환경**<sub>Integrated Development Environment, IDE</sub>를 설치한다.
노드 진영에서는 WebStorm과 VSCode가 자주 쓰이는데, 이 책에서는 VSCode를 사용한다.
[VSCode 공식 사이트](https://code.visualstudio.com)에서 설치 파일을 다운로드하여 설치한다.
{% include image_caption.html imageurl="images/book-typescript-2-2.png" title="VSCode Download" caption="VSCode 다운로드" %}

### 2.1.3 타입스크립트 설치

타입스크립트를 설치한다. [typescript 공식 사이트](https://www.typescriptlang.org)에서 안내하는 방법이 있지만, 책에서는 다음과 같이 설치하라고 한다.
```bash
npm i -g typescript
```
터미널에 나타난 결과는 다음과 같다.
```bash
npm error code EACCES
npm error syscall mkdir
npm error path /usr/local/lib/node_modules/typescript
npm error errno -13
npm error Error: EACCES: permission denied, mkdir '/usr/local/lib/node_modules/typescript'
npm error     at async mkdir (node:internal/fs/promises:852:10)
npm error     at async /usr/local/lib/node_modules/npm/node_modules/@npmcli/arborist/lib/arborist/reify.js:624:20
npm error     at async Promise.allSettled (index 0)
npm error     at async [reifyPackages] (/usr/local/lib/node_modules/npm/node_modules/@npmcli/arborist/lib/arborist/reify.js:325:11)
npm error     at async Arborist.reify (/usr/local/lib/node_modules/npm/node_modules/@npmcli/arborist/lib/arborist/reify.js:142:5)
npm error     at async Install.exec (/usr/local/lib/node_modules/npm/lib/commands/install.js:150:5)
npm error     at async Npm.exec (/usr/local/lib/node_modules/npm/lib/npm.js:207:9)
npm error     at async module.exports (/usr/local/lib/node_modules/npm/lib/cli/entry.js:74:5) {
npm error   errno: -13,
npm error   code: 'EACCES',
npm error   syscall: 'mkdir',
npm error   path: '/usr/local/lib/node_modules/typescript'
npm error }
npm error
npm error The operation was rejected by your operating system.
npm error It is likely you do not have the permissions to access this file as the current user
npm error
npm error If you believe this might be a permissions issue, please double-check the
npm error permissions of the file and its containing directories, or try running
npm error the command again as root/Administrator.
npm error A complete log of this run can be found in: /Users/peter/.npm/_logs/2025-07-25T05_33_01_810Z-debug-0.log
```
❌ 앗! permission! Mac은 항상(?) 이런 이슈가... 😅<br>
**sudo**로 다시 실행한다.
```bash
sudo npm i -g typescript
```
아무런 불평없이(?) 설치된 듯 하다. 그렇다면~ 통과!

## 2.2 타입스크립트 프로젝트 만들기

노드 프로젝트, 타입스크립트를 직접 구축해보고 직접 실행해보자.

### 2.2.1 Node.js 프로젝트

자바스크립트 런타임인 노드를 설치했기 때문에, 타입스크립트 코드를 자바스크립트 코드로 변환한 후 실행하게 된다.
따라서 타입스크립트 개발할 때는 타입스크립트 프로젝트와 노드(자바스크립트) 프로젝트 이렇게 2개의 프로젝트가 생성된다.
먼저, 노드 프로젝트를 만들어보자.

1. 프로젝트를 담아 둘 폴더를 영문명으로 만든다.
2. 터미널<sub>Terminal</sub>을 열고, 1번에서 만든 폴더로 이동한다.
3. 다음의 명령을 입력한다.
```bash
npm init -y
```

`npm init` 명령을 입력하면 `package.json` 파일이 다음과 같이 생성된다.
```json
{
  "name": "typescript",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "description": ""
}
```

`package.json` 파일은 노드 프로젝트 패키지를 관리하고 스크립트 명령어를 등록할 때 쓰이는 중요한 파일이다.
이제, 첫 자바스크립트 파일을 만들고 실행해보자. 여기서부터는 VSCode를 사용함.
VSCode를 실행하고, 앞에서 만든 폴더를 연다. 터미널에서 생성한 package.json 파일이 있을 것이다.
같은 폴더에 `index.js` 파일을 만들고 다음과 같이 입력한다.
```javascript
console.log("Hello, World");
```
터미널<sub>Terminal</sub>에서 다음과 같이 입력하여 실행한다.
```bash
node index.js
```

`index.js` 코드를 다음과 같이 변경하고 실행해본다.
```javascript
console.log("Hello World", "jPub", "typescript");
```
`console.log`는 인수의 모든 값을 출력하는 함수다.

### 2.2.2 타입스크립트 프로젝트
노드 프로젝트를 만들었으니, 이번에는 타입스크립트 프로젝트를 만든다.
터미널을 열고 앞에서 생성한 폴더로 이동한 후, 다음의 명령어를 입력한다.
```bash
tsc --init
```
이 명령을 실행하면 `tsconfig.json` 파일이 생성된다.

+ `tsconfig.json` 파일은 타입스크립트 프로젝트를 설정하고 어떻게 자바스크립트 파일로 변환할지 설정하는 파일이다.
  + 이 파일에 대해 자세한 설명은 [공식 문서](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)를 참고한다.

`index.ts` 이름의 새로운 파일을 만들고, 다음의 코드를 입력한다. 
```typescript
console.log("Hello typescript");
```

터미널에서 다음의 명령을 실행한다.
```bash
tsc index.ts
```
**이 명령은 타입스크립트 파일을 자바스크립트 파일로 변환한다.**
기존에 있던 `index.js` 파일을 보면, 이전 코드가 없어지고 `index.ts` 파일의 코드가 들어간 것을 확인할 수 있다. (😱 놀라움!!)
```bash
node index.js
```
터미널에서 이렇게 실행하여 확인한다.

## 2.3 타입스크립트 실행

타입스크립트 파일이 많아지면 트랜스파일<sub>transpile</sub> 시간이 오래 걸린다. 빠르게 실행 결과를 확인하기 위해서 `ts-node 패키지`를 전역 설치한다.
터미널에서 다음의 명령을 실행하여 설치한다.
```bash
sudo npm install -g ts-node
```

테스트를 위하여, `index.ts` 파일의 코드를 살짝 수정한다.
```typescript
console.log("Hello typescript with ts-node");
```

이제는 다음과 같이 ts-node 명령어를 실행하면 결과를 바로 볼 수 있다.
```bash
ts-node index.ts
```

자바스크립트 런타임인 노드가 타입스크립트 런타임으로 바뀌는 것은 아니고, 내부적으로 자바스크립트 변환 과정을 거치지만 우리에게는 바로 실행되는 것처럼 보인다.
실제로, `index.js` 파일의 코드를 보면 `index.ts` 파일의 코드를 변경하기 전 상태로 되어 있다.
다시말해서 `ts-node` 명령을 이용하여 실행한다고 해도 트랜스파일<sub>transpile</sub>이 되지 않는다는 것을 알 수 있다.

마지막으로, 실무에서 가장 많이 쓰이는 방법으로 `package.json` 파일을 이용하는 방법을 살펴보자.<br>
`package.json` 파일의 `script` 필드를 활용하여 명령을 단축하는 방법이다. 다음과 같이 `package.json` 파일의 `script` 필드에 **`"dev": "tsc index.ts && node index.js"`** 코드를 추가한다. 콤마(,) 주의!

```json
{
  "name": "typescript",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "dev": "tsc index.ts && node index.js"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "description": ""
}
```
이와 같이, `script` 필드에 `<등록할 스크립트 명령어 이름>: <실행할 명령어>`를 적으면 스크립트 명령어가 등록되며 등록된 스크립트로 터미널에서 다음과 같이 사용할 수 있다.  
```bash
npm run dev
```

## 후기
타입스크립트! 나름 흥미롭다! 지금까지 이해한 바로는...<br>
결국은 자바스크립트로 애플리케이션을 실행하게 되는데, 타입스크립트를 사용하면 자동으로 알맞게(?) 변환해 준다는 장점이 있는 것이구나!
타입스크립트로 코딩을 하면 변환 과정에서 코드 오류도 체크한다는 게, 이런 과정이 있어서 가능하다는 말이었나 보다.
타입스크립트 문법 및 코드 컨벤션<sub>Code Convention</sub>을 배우고 익숙해진다면 결과물인 애플리케이션은 큰 어려움없이 만들어지겠구나~ 싶은 생각이 든다.

자! 다음 장으로 넘어가 보자꾸나!