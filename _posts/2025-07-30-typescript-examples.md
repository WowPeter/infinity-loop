---
layout: post
title: "[나의 첫 타입스크립트 프로젝트] Chapter 5."
description: "TypeScript Examples"
date: 2025-07-30
feature_image: images/book-typescript-5.png
tags: [나의 첫 타입스크립트 프로젝트, typescript, book, review]
---

# Chapter 5. 타입스크립트 예제

타입스크립트에서 자주 사용되는 패턴과 고급 기능들을 배워보자.

<!--more-->

## 5.1 클래스와 인터페이스

[Chapter 4. 타입스크립트 스킬](https://wowpeter.github.io/infinity-loop/typescript-skills){:target="_blank"}의 마지막 부분에서도 작성했지만,
객체 지향에 대한 올바른 이해가 선행되어야 객체 지향 개념에 맞는 설계가 되고 그래야 유기적으로 동작하는 코드가 발생한다.
여기서 표현한 '유기적으로 동작하는 코드'는 '완벽한 코드'라는 의미가 아니다. 나는 완벽한 코드라는 것은 없다고 감히 말한다.
다만 그 코드를 작성할 때 주어진 환경에서 **최선을 다한 코드**가 존재할 뿐이다.

사람에 대한 클래스를 다음과 같이 만들었다고 하자.
```javascript
interface IPerson {
  greet(): void;
}

class Person implements IPerson {
  name: string;
  language: string;

  constructor(name: string, language: string) {
    this.name = name;
    this.language = language;
  }

  greet(): void {
    if (this.language === 'Korean') { 
      console.log(`안녕하세요, 제 이름은 ${this.name}이고 한국어를 합니다.`);
    } else if (this.language === 'Japanese') {
      console.log(`こんにちは、 ${this.name}です。日本語を話します。`);
    } else {
      console.log(`Hello, my name is ${this.name} and I speak ${this.language}.`);
    } 
  }
}
```
이름(name)과 언어(language) 속성만 가진 `Person` 클래스다.
이 클래스는 `IPerson`이라는 이름의 인터페이스를 사용하고 있고, 이 인터페이스는 greet()라는 메서드를 선언한다.

이 클래스를 가지고 예제 코드를 다음과 같이 만들 수 있다.
```javascript
const person1 = new Person('Alice', 'English');
const person2 = new Person('Bob', 'Korean');
const person3 = new Person('Charlie', 'Japanese');

person1.greet();    // Hello, my name is Alice and I speak English.
person2.greet();    // 안녕하세요, 제 이름은 Bob이고 한국어를 합니다.
person3.greet();    // こんにちは、 Charlieです。日本語を話します。
```

## 5.2 추상 클래스와 인터페이스

추상 클래스<sub>Abstract Class</sub>는 하나 이상의 추상 메서드를 포함하는 클래스로, 객체 지향 프로그래밍에서 중요한 개념이다.
추상 클래스는 직접 인스턴스화될 수 없으며, 다른 클래스들이 상속받아 사용해야 한다.
이를 통해 코드 재사용성을 높이고, 다형성<sub>Polymorphism</sub>을 구현하며, 시스템의 확장성을 향상시킬 수 있다. 

**추상 클래스<sub>Abstract Class</sub>와 인터페이스<sub>Interface</sub>는 언제 어떻게 사용해야 할까?**<br />
추상 클래스부터 살펴보자. 추상 클래스는 말 그대로 '클래스'다. 즉, 어떤 객체에 대한 설계도<sub>blueprint</sub>라는 것이다.
그렇다면 추상<sub>Abstract</sub>을 어떻게 이해해야 할까? 나는 **'상속받은 클래스들은 반드시 구현해야 하는 메서드를 가진 상위 클래스'**라고 정의한다.

## 5.3 타입 가드

**타입 가드<sub>type guard</sub>는 타입을 예측할 수 있도록 범위를 좁히는 것을 말한다**고 한다. 이게 무슨 말인가!?
`typeof` 또는 `instanceof`를 사용하면 해당 값(또는 변수)가 어떤 타입인지 판별할 수 있다.

## 5.4 최하위 타입 undefined

타입스크립트에는 `undefined`라는 타입이 있다. 전에도 말했지만, 참으로 고약한 타입이다. 이 타입은 `null`과 같은 의미이지만 null과 다르다. null이 아니다.
나처럼 스크립트 언어보다 다른 언어에 대한 친숙도가 더 높은 개발자라면, 항상 `undefined`가 존재하고 있음을 기억해야 할 것이다.
나도 노력은 하는데, 참~ 힘들다. 항상 까먹어!

## 5.5 타입 단언과 타입 캐스팅

**타입 단언<sub>type assertion</sub>은 개발자가 해당 타입에 대해 확신이 있을 때 사용하는 타입 지정 방식**이라고 한다. 이건 또 무슨 소린가!?
나는 이게 무엇인지 이해하려는 노력을 하지 않았다. 그저. `as`를 사용하여 **타입 캐스팅<sub>type casting</sub>**을 할 수 있다고만 이해하련다.

```javascript
const div = document.getElementById("my-div") as HTMLDivElement;
```
이 샘플 코드를 남겨 두는 것으로 넘어간다.

## 5.6 싱글턴 패턴

**싱글턴 패턴<sub>singleton pattern</sub>은 인스턴스를 단 하나만 생성할 수 있는 클래스를 활용하는 디자인 패턴**이다. 
다음은 싱글턴 패턴에 대한 예제 코드다.

```javascript
class Singleton {
  private static instance: Singleton;

  private constructor() {
    // Private constructor to prevent instantiation
  }

  public static getInstance(): Singleton {
    if (!Singleton.instance) {
      Singleton.instance = new Singleton();
    }
    return Singleton.instance;
  }

  public greet(): string {
    return "Hello, I am a singleton!";
  }
}

console.log(Singleton.getInstance().greet()); // Output: Hello, I am a singleton!
```

## 후기

이번 장은.. 아니.. 꼭 이번 장만은 아니지만, 타입스크립트의 객체 지향 특징에 신경을 많이 쓰는 느낌이었다.
이번 장에서 재미있는 부분을 고르라면, 타입스크립트로 싱글턴 패턴을 구현했다는 것이다. 어떤 언어를 쓰든 싱글턴 패턴은 종종 사용하게 된다.
싱글턴 패턴을 구현하는 코드는 거의 유사한 구조를 가지고 있어서 새로울 건 없었지만, 타입스크립트 코드로 봤다는 것이 재미있었다.
