---
layout: post
title: "[나의 첫 타입스크립트 프로젝트] Chapter 3."
description: "TypeScript Basics"
date: 2025-07-28
feature_image: images/book-typescript-3.png
tags: [나의 첫 타입스크립트 프로젝트, typescript, book, review]
---

# Chapter 3. 타입스크립트 문법

자바스크립트의 기본적인 문법과 기능을 이해하면 타입스크립트를 효과적으로 사용할 수 있다.
오래된 자바스크립트 표준 ES5와 현재 그리고 미래의 자바스크립트 표준인 ESNext를 이해하고, 타입스크립트의 문법과 내부 구조를 알아보자.  

<!--more-->

## 3.1 타입스크립트 기초 문법

3장을 진행하기 전, `tsconfig.json` 파일의 `strict`와 `noImplicitAny` 옵션을 다음과 같이 비활성화한다.
이 옵션들을 활성화하면 이번 장의 모든 코드에 **타입 주석<sub>type annotation</sub>**을 추가해야 한다.
```json
{
  "compilerOptions": {
    ...
    "strict": false,
    "noImplicitAny": false,
    ...
  }
}
```

### 3.1.1 주석

코드를 무효화시키거나 코드 외에 설명을 적어야 할 경우에 사용된다.
+ **//** - 한 줄 주석으로, 이후의 모든 문자를 무시한다.
+ **/* */** - 여러 줄 주석으로 포함된(감싸진) 모든 문자를 무시한다.
+ **/*\* */** - 여러 줄 주석과 동일하지만 줄을 바꿀 때마다 *를 추가해야 하며, 안의 내용은 js-doc(ts-doc)으로 사용된다.

### 3.1.2 변수의 선언

+ **const** : 상수<sub>constant</sub>를 선언할 때 사용하며, 값을 변경할 수 없다.
+ **let** : 변수<sub>variable</sub>를 선언할 때 사용하며, 값을 변경할 수 있다.

변수명은 **영문자**, **숫자**, **달러($)**, **언더스코어(_)**의 조합으로 만들 수 있지만, 숫자로 시작해서는 안된다. 

+ ✅ Example
+ ✅ hello_example
+ ❌ 9example
+ ❌ E#ample

변수명은 대소문자를 구분한다. 즉, 대문자와 소문자까지 완전히 일치하지 않는다면 서로 다른 변수라는 의미다. 예를 들어, Example, example, exAmple은 모두 다른 변수다.

변수명은 키워드<sub>keyword</sub>가 아니여야 한다. 타입스크립트에서의 키워드는 다음과 같다.

break, case, catch, class const, continue, debugger, default, delete, do else, enum, export, extends, false finally, for, function, if, import, in , instanceof, new, null, return, super, switch, this, throw, true, try, typeof, var, void, while, with

타입스크립트에서의 변수명 naming convention은 **camel case**다.

### 3.1.3 원시 타입 변수

노드<sub>node.js</sub>는 메모리를 효율적으로 사용하기 위해 **콜 스택<sub>call stack</sub>** 영역과 **힙<sub>heap</sub>** 영역으로 나누어 메모리에 저장한다.
콜 스택은 함수의 호출과 관련된 정보를 저장하는 영역이며, 처리 속도가 빠르고 구조가 단순하다. 힙은 동적으로 할당되는 데이터를 저장하는 영역이며 자유롭게 확장할 수 있는 구조여서 관리가 필요하다.
올바르게 관리되지 않는다면 메모리 누수<sub>memory leak</sub>가 발생할 수 있다.

콜 스택에 직접 저장되는 변수들을 **원시 타입 변수<sub>primitive type variable</sub>**라고 한다.

#### number

숫자를 저장하는 타입이다. 그런데, 이게 참! 고약한 게... 정수를 담으면 정수형이 되고 소수를 담으면 소수가 된다는 점이다.

```javascript
const num = 100; // 정수
const pi = 3.14; // 실수
```
이게 왜 고약하냐면! 실무에서 타입스크립트를 백엔드 코드로 사용하는 경우가 있는데, 임의의 API에 대한 response로 값을 반환할 때 해당 값이 정수와 실수로 마구 바뀌어 온다는 점이다.
물론, 프론트 쪽에서 강제로 형 변환(실수형으로)하면 되지만, 실력없는 백엔드 개발자들은 자기들이 무슨 값을 주는지도 모른다는 점. 🤬

어쨌든 `number`라는 타입은 고약한 일이 아닐 수 없다.

#### boolean

참과 거짓을 나타내는 값으로, `true`와 `false` 값만 있다. 숫자 `1`은 `true`이기도 하며, `0`은 `false`이기도 하다.
자세히 설명하면 길지만, 그냥 간단하게, 2진수인 비트<sub>bit</sub>를 생각하면 간단히 이해된다.

#### null

아무것도 할당되지 않은 값이다. 이것도 얘기하지면 길다. 어쨌든 0과 null은 다르다.  

#### undefined

이게 또 고약한 점이다. 사실 **null과 undefined는 같은 값이다.** 말로 풀어서 쓴다면 이렇다.

+ null은 개발자가 아무것도 할당하지 않았다고 표시한 것이고
+ undefined는 개발자가 아무것도 할당하지 않은 것이다.

말 장난같지만, 사실이다. 다음의 코드를 보자.  

```javascript
let myNull = null;
let value;
```
`myNull` 변수는 아직 아무것도 할당하지 않았다고 `null`로 표시했고 `value` 변수는 아무것도 할당하지 않았다. 즉, 같은 값이다. **비교문으로 서로 비교하면 값이 같다고 나온다.**

그런데 놀라운 것은 **`typeof` 연산자로 확인해보면 서로 다른 타입**이라는 것이다.

```javascript
console.log(typeof myNull); // object
console.log(typeof value);  // undefined
```

#### string

문자열을 나타내는 값이며 홑따옴표(') 또는 쌍따옴표(")를 사용한다. 문자열을 서로 합할 수 있다.

```javascript
const publisher = "jpub";
const book = "typescript";

console.log("Hello " + publisher + " " + book); // Hello jpub typescript
console.log(`Hello ${publisher} ${book} ${1 + 1}`); // Hello jpub typescript 2
```
백틱(`)을 활용하는 방법도 있다.

#### symbol

심벌<sub>symbol</sub>은 ES6부터 새롭게 추가된 원시 타입이기 때문에 타입스크립트에서 심벌을 사용하려면 **`tsconfig.json`의 `compilerOptions`에 있는 `lib`에 `ES2015`와 `DOM`을 추가**해야 한다.

```json
{
  "compilerOptions": {
    ...
    "lib": ["ES2015", "DOM"],
    ...
  }
}
```

심벌은 `Symbol(심벌형)` 형식으로 만든다. **심벌은 하나뿐인 고유한 값을 만들 때 사용**한다.

### 3.1.4 참조 타입 변수

실제 값을 힙<sub>heap</sub>에 저장하고 힙에 저장된 데이터를 참조하는 참조 주소는 콜 스택<sub>call stack</sub>에 저장하는 **참조 타입 변수<sub>reference type variable</sub>**을 알아보자.

#### 객체

타입스크립트에서의 객체는 키<sub>key</sub>와 값<sub>value</sub>으로 구성된 자료구조다. 파이썬의 딕셔너리 또는 자바의 맵과 비슷하다.

```javascript
const myObject = {
  name: "jpub",
};

console.log(myObject.name);     // jpub
console.log(myObject["name"]);  // jpub
console.log(myObject.hello);    // undefined
```
객체에 없는 프로퍼티에 접근할 경우, `undefined`가 반환된다.

#### 배열

배열<sub>array</sub>은 데이터가 나열된 자료구조다. 각 데이터를 요소<sub>element</sub>라고 하며 각 요소의 위치를 가리키는 숫자를 인덱스<sub>index</sub>라고 한다.
인덱스는 맨 처음 데이터를 0으로 하여 다음 값마다 1씩 증가한다. 또는 맨 마지막 데이터를 -1로 하여 그 이전 데이터마다 -1씩 감소한다.

```javascript
const myArray = ["A", "B", "C"];

myArray[2] = "Z";           // 인덱스 2의 데이터 변경

myArray.unshift = "START";  // 배열의 맨 앞에 데이터 추가
myArray.push = "END";       // 배열의 맨 끝에 데이터 추가

myArray.shift();            // 배열의 맨 앞의 데이터 삭제
myArray.pop();              // 배열의 맨 끝의 데이터 삭제
```

#### 함수

함수<sub>function</sub>는 `function` 키워드로 선언하고 함수 이름과 매개변수를 넣어 선언한다. 함수를 호출할 때는 함수명과 각 매개변수에 맞는 인수를 넣어 호출하면 실행된다.

```javascript
function functionName(parameter 1, parameter 2) {
  함수 코드
  
  return 반환값
}

// 함수 호출 시,
functionName(argument 1, argument 2);
```

함수형 프로그래밍을 접해봤다면 **익명 함수<sub>Anonymous function</sub>**가 낯설지 않을 것이다. 타입스크립트도 익명 함수를 지원한다. 말 그대로 '_함수 이름이 없는 함수_'라는 말인데, 사실 들여다보면 함수 이름이 필요없다 😅

다음의 코드를 보자.
```javascript
const minus = function(a, b) {
  return a - b;
};

console.log(minus(3, 1));   // 2
```
이런 걸 왜 하는냐!? 핵심은 **함수도 변수처럼 사용할 수 있다**라는 점이다. 거슬러 올라가서 의미를 폭 넓게 본다면... 뭐... 그거나 그거나~ 그런 느낌이지만...

### 3.1.5 얕은 복사, 깊은 복사

"얕은 복사<sub>shallow copy</sub>"라... 개인적으로 좋아하지 않는 개념이다. 좋아하고 좋아하지 않고를 떠나, 실무에서 얕은 복사를 사용하는 경우를 거의 못 봤다. 전혀 못 봤다고 말하고 싶지만, 나도 모르게 봤을 수도 있겠지.
이 개념은 '프로그램 언어학'에서나 나올 얘기다. 말도 안되는 쓸데없는 내용은 아니지만 실제로 이 개념을 사용하는 코드를 본 적이 없다. 왜냐? 이것은 코드를 짜는 본인뿐만 아니라 동료들에게도 혼란을 주는 코드가 될 수 있기 때문이라고 본다.

내용은 이렇다. 힙 메모리에 있는 실제 데이터(예를 들어 "REAL VALUE"라고 하자)을 참조하는 변수(예를 들어, 변수 명을 a라고 하자)가 콜 스택에 있는데, 콜 스택에 있는 변수에 담긴 값은 실제 데이터가 위치에 있는 힙 메모리의 주소값이다.
만약에 새로운 변수 b를 만들고 그 변수의 값으로 a를 할당하면, 변수 b에는 a의 값이 담길 것이며 변수 a에 담기 값은 실제 데이터인 "REAL VALUE"가 아닌 그 데이터를 가리키는 메모리 주소값이므로 변수 b에는 변수 a에 할당되어 있는 주소값이 할당된다.
즉, 변수 a와 변수 b는 "REAL VALUE"라는 데이터가 위치해 있는 주소값을 동일하게 가지게 된다.

자! 이제, 변수 b가 참조하고 있는 값(실제 데이터)를 변경하면 어떻게 될까? 당연히 실제 데이터가 변경되는 것이기 때문에 변수 a가 가리키는 값이 변경된 것과 같다. 이렇게 설명을 보면 이해 못할 개념은 아니다. 그런데, 실제 실무에서 이런 코딩을 한다면??
내가 모르는 다른 변수가 내가 가리키는 값을 변경한다는 의미가 되니, 얼마나 복잡해질지는 자명하다.

```javascript
const data1 = {name: "typescript"};

// shallow copy
const data2 = data1;

data2.name = "typescript2";

console.log(data1); // { name: 'typescript2' }
console.log(data2); // { name: 'typescript2' }
```

위의 예제처럼, 이렇게 된다.

이게 싫어서 "깊은 복사<sub>deep copy</sub>"라는 게 있다. 깊은 복사는 `...`라는 스프레드 연산자를 사용하면 된다. 위에서의 얕은 복사 예제를 깊은 복사로 바꿔서 테스트해보자.

```javascript
const data1 = {name: "typescript"};

// shallow copy
const data2 = {...data1};

data2.name = "typescript2";

console.log(data1); // { name: 'typescript' }
console.log(data2); // { name: 'typescript2' }
```
그런데, 여기에 또 문제가 있다. 하아~ 😰

스프레드 연산자로 깊은 복사를 한다고 해도 내부에 있는 객체(객체 안에 있는 객체)는 깊은 복사가 안된다!! 🤬 그래서(?) `lodash` 패키지를 설치하여 사용한다고 한다.

```bash
npm install lodash
```
```javascript
import { cloneDeep } from "lodash";

const obj = { a: 1, b: { c: 2 } };

const clonedObj = cloneDeep(obj);

clonedObj.b.c = 3;

console.log(obj);       // { a: 1, b: { c: 2 } }
console.log(clonedObj); // { a: 1, b: { c: 3 } }
```

### 3.1.6 조건문과 반복문

#### 연산자

| 비교 연산자 | 의미               |
|----------|------------------|
| ==     | 값이 동일하다          |
| !=     | 값이 다르다           |
| ===    | 값과 자료형이 같다       |
| !==    | 값 또는 자료형이 같지 않다  |
| a > b  | a가 b보다 크다        |
| a >= b | a가 b보다 크거나 같다    |
| a < b  | a가 b보다 작다        |
| a <= b | a가 b보다 작거나 같다    |

| 논리 연산자   | 의미                               |
|----------|----------------------------------|
| a && b   | a와 b 모두 true일 때, true            |
| a \|\| b | a 또는 b가 true일 때, true            |
| !a       | a가 false이면 true, a가 true이면 false |

| 기타 연산자     | 의미                 |
|------------|--------------------|
| typeof     | 해당 변수의 자료형을 반환     |
| instanceof | 해당 클래스의 인스턴스인지를 반환 |

#### 조건문

##### if

```javascript
if (조건 1) {
  // 조건 1을 만족할 때 실행되는 로직
} else if (조건 2) {
  // 조건 2을 만족할 때 실행되는 로직
} else if (조건 3) {
  // 조건 3을 만족할 때 실행되는 로직
} else {
  // 위의 어떤 조건에도 맞지 않을 경우 실행되는 로직
}
```

##### switch

```javascript
switch (표현식) {
  case 조건 1:
    // 조건 1에 만족할 때 실행되는 로직
    break;
  case 조건 2:
    // 조건 2에 만족할 때 실행되는 로직
    break;
  case 조건 3:
    // 조건 3에 만족할 때 실행되는 로직
    break;
  default:
    // 위의 어떤 조건에도 맞지 않을 경우 실행되는 로직
    break;
}
```

##### for

```javascript
for (시작값; 조건식; 증가식) {
  실행 로직
}
```
시작값이 조건식에 만족한다면 실행 로직을 수행하고 증가식에 의해 값이 증가된다. (반복)

##### while

```javascript
while (조건식) {
  실행 로직
}
```
조건식이 만족하는 동안 실행 로직이 한 번씩 수행된다. 언제까지? 조건식에 만족하지 않을 때까지.

## 3.2 ESNext 문법

타입스크립트는 자바스크립트의 슈퍼셋 언어이므로, 자바스크립트의 최신 문법인 ESNext를 사용할 수 있다. ESNext를 사용하면 효율적이고 안전한 코드를 작성할 수 있다.

### 3.2.1 템플릿 리터럴

템플릿 리터럴<sub>template literal</sub>은 문자열을 더 편하고 가독성 있게 작성할 수 있도록 한다.

```javascript
const myName = "Peter";
const hobby = "ice hockey";

console.log("Hello \"" + myName + "\", your hobby is \'" + hobby + "\'");
console.log(`Hello "${myName}", your hobby is '${hobby}'`);
```
위의 코드와 같이, 결합 연산자를 사용하여 문자열들을 연결할 수 있다. 또한 이스케이프 문자<sub>escape character</sub>를 사용하여 특수 문자를 표현할 수 있으며, 백틱(`)을 사용하여 조합할 수도 있다.

### 3.2.2 객체 리터럴

객체의 값의 접근할 때 `.`을 이용하여 속성에 접근할 수 있는데, ESNext에서는 `[]`를 사용하여 접근할 수도 있다.

```javascript
const Peter = {
  name: "Peter",
  hobby: "ice hockey",
};

console.log(Peter.name, Peter.hobby);       // Peter ice hockey
console.log(Peter["name"], Peter["hobby"]); // Peter ice hockey
```

### 3.2.3 화살표 함수

화살표 함수<sub>arrow function</sub>는 기존 `function` 키워드 대신 화살표(`=>`)로 함수를 선언한다.

```javascript
(매개변수 1, 매개변수 2) => {
  // 실행 로직
}
```
주의할 점은 화살표 함수는 해당 함수를 사용하는 코드보다 먼저 선언되어야 한다. `function`으로 선언된 함수는 상관없다.

### 3.2.4 클래스

그저 감사할 따름이다. 예전에 자바스크립트를 사용한 경험이 있다면 클래스가 도입되었다는 것은 거의 혁명이라고 말할 수 있다.
앞의 코드를 보면 알겠지만, '객체'라고 말하는 것들은 사실 관리가 어렵다.
프로젝트가 커지거나 코드 재사용을 요구하는 장면에서 '객체'는 복잡하고 하나하나 살펴봐야 할 또 다른 문서(?)같은 존재였다.
그러다보니 자바스크립트로 작성된 프로젝트는... 뭐랄까... 데이터 구조가 조각난 느낌이랄까? 그러했다. 필요한 화면마다 조각난(?) 객체를 다시 만들어서 가독성을 높였는데.
이제는 클래스를 사용할 수 있게 되었다니!! 놀라울 따름이다.

```javascript
class 클래스명 {
  // 필드
  name;
  
  // 생성자
  constructor(name: string) {
    this.name = name;
  }
  
  // 메서드
  메서드명(매개변수...) {
    // 실행 로직
  }
}
```

### 3.2.5 프로미스

비동기적으로 프로그램을 만들다보면, 어떤 이벤트에 대해 동작하는 콜백 함수<sub>callback function</sub>을 사용하게 된다.
그런데, 콜백 함수가 다시 콜백 함수를 호출하고 그게 다시 다른 콜백 함수를 부르다보니 **콜백 직옥**이라는 가독성 떨어지는 코드가 발생하곤 한다.

```javascript
함수호출()
  .then((res) => console.log("작업 성공: ", res)
  .catch((err) => console.log("작업 실패: ", err)
```
이런 코드는 http 통신과 같이 비동기 작업에 주로 사용된다.

### 3.2.6 구조 분해 할당

사실 클래스를 사용하면 이런 건 의미가 없지만(?), 그래도 있는 개념이니 눈으로 읽는다는 생각으로 보자.

```javascript
const array = [1, 2, 3, 4, 5];
console.log(array[0], array[1], array[2], array[3], array[4]); // 1 2 3 4 5
```
위의 코드와 같이 각 값들은 배열의 인덱스를 이용하여 접근할 수 있다.

이것을 다음과 같이 할 수도 있다.

```javascript
const [one, two, three, four, five] = [1, 2, 3, 4, 5];
console.log(one, two, three, four, five); // 1 2 3 4 5
```
이것을 구조 분해 할당<sub>Destructuring assignment</sub>라고 한다. 

## 후기

아~ 끝났다! 프로그래밍 언어를 처음 배운다면 끝없이 중요하고 공부해야 할 내용임에 틀림없다.
하지만, 나에겐 너무나도 지루한 내용이었다. 어쩔 수 없지. 나는 너무 많은 언어를 공부했었고 각 언어의 문법이 비슷하면서도 살짝살짝 달라서 실제 코딩할 때 헷갈릴 정도로 많은 언어를 접했다.
아마 이번 장을 시작하기도 전에 난 이 내용의 90% 이상을 이미 알고 있었으리라. 신기하고 재미있는 문법이 있음을 확인했음에 만족한다.