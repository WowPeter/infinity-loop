---
layout: post
title: "Google Analytics 넣어보기"
description: "How to set up Google Analytics"
date: 2025-04-26
feature_image: images/analytics.jpg
tags: [google analytics, jekyll]
---

그게 무슨 일이든, 미래를 알고 있다면...<br />
행복할 거라 장담은 못 하지만 적어도 실패하진 않을 거라 말할 수 있겠지. 시험을 앞둔 수험생에게 출제될 시험 문제를 미리 알고 있다면. 다가올 위험을 미리 알고 있다면. 내일 주식이 어떻게 될지 알고 있다면. 이번 주 복권 결과를 알고 있다면. 그 삶이 행복하고 안 하고를 떠나, 결코 실패하진 않을 것이다. 하지만 도대체 누가 미래를 알 수 있겠는가?

## Although we don't have a crystal ball,

과거를 바탕으로 현재를 판단하여 미래를 **예측**하는 능력을 우리는 가지고 있다. (*Praise the Load* 🎉) 과거의 정보가 쌓여 있고 그것을 읽을 수 있다면 충분히 현재를 파악할 수도 있고 미래를 예측할 수도 있다. 물론 **얼마나 잘 읽는가**는 또 다른 얘기가 되겠지만. 어쨌든 데이터를 수집하고 그것을 분석하는 것은 매우!! 중요하다. Github Page는 결국 웹사이트다. 웹사이트를 위한 데이터 분석툴들은 여러 가지가 있겠지만, 내가 알고 있고 주로 사용하는 것이 **Google Analytics**니 이것을 붙여야겠다. 

마음을 먹고, **_config.yml** 파일을 보니 다음과 같은 부분이 눈에 들어온다.

```yml
# Google Analytics id, e.g. "UA-NNNNNNNN-N"
google_analytics: ""
```
 
오호! 이미 준비되어 있는 겐가? 왠지, 생각보다 쉽게 될 수도 있겠다는 기대감이 상승한다.

<!--more-->

## Google Analytics

위키피디아에서는 구글 애널리틱스를 뭐라고 설명하고 있을까? [Wikipedia](https://ko.wikipedia.org/wiki/구글_애널리틱스 "위키피디아에서 구글 애널리틱스에 대한 설명")를 보면 다음과 같이 나와 있다.

> 구글 애널리틱스(Google Analytics)는 현재 구글 마케팅 플랫폼 브랜드 내의 플랫폼으로서, 웹사이트 트래픽을 추적하고 보고하는 구글이 제공하는 웹 애널리틱스 서비스이다. 구글은 2005년 11월 Urchin을 인수한 이후 이 서비스를 런칭했다.
> 
> 2019년 기준으로 구글 애널리틱스는 웹에서 가장 널리 사용되는 웹 애널리틱스 서비스이다. 구글 애널리틱스는 구글 애널리틱스 포 모바일 앱스(Google Analytics for Mobile Apps)라는 이름의 iOS, 안드로이드 앱을 제공한다. 구글 애널리틱스는 브라우저, 브라우저 확장 기능, 방화벽, 그리고 기타 수단을 통해 차단이 가능하다.
> 
> 구글 애널리틱스는 고안 당시부터 수많은 버전을 거쳐왔다. 현재는 GA4 단계에 있다. 현재 기본 구글 애널리틱스 설치본인 GA4는 구글이 베타 형태로 2019년 출시한 앱+웹 프로퍼티에서 이름이 변경된 버전이다. GA4는 현재 UA, 즉 유니버설 애널리틱스(Universal Analytics)를 대체한다. GA4의 한 가지 특별한 기능으로, 한때 엔터프라이즈 GA 360과만 호환되었던 기능인 구글의 빅쿼리와의 자연스러운 연동이 있다. 이러한 움직임은 GA와 무료 사용자들이 더 넓은 클라우드 제공 기능과 연동할 수 있게 하려는 구글의 노력을 의미한다.

이제 슬슬 Google Analytics를 붙여 볼까나!

### Google account needed

당연히 구글 제품이니 구글 계정이 필요하다. 그리고 난 이미 구글 계정이 있다. 심지어 여러 개. 구글 계정이 없는 사람이 있을까? 싶을 정도로 내 주변에는 모두 가지고 있다. 난 내가 가지고 있는 여러 구글 계정들 중 하나를 골라서 로그인했다.

### Creating an Analytics account

{% include image_caption.html imageurl="images/analytics-1.png" title="Google Analytics menu" caption="좌측 하단에 있는 [관리] 메뉴" %}

너무 오랜만에 접속한 걸까? 내 블로그를 위한 계정을 만들어야 하는데, 도대체 어디서 만들어야 하는지 보이지 않았다. 뭔가 바로 '똮' 하고 보일 거 같았는데 그러지 않았다. 이거 저거 눌러보다가 겨우겨우 저걸 찾았다. 저 **관리** 메뉴를 눌렀더니 다음 스샷처럼 계정을 만들 수 있는 메뉴가 보였다. 

{% include image_caption.html imageurl="images/analytics-2.png" title="Account menu" caption="좌측 상단에 있는 [만들기] - [계정] 메뉴" %}

**[만들기] - [계정] 메뉴**를 클릭하면 다음과 같이 5 단계의 가입 절차가 보인다.

{% include image_caption.html imageurl="images/analytics-3.png" title="5 steps" caption="계정을 만드는 5 단계" %}

#### 1. 계정 생성

여기서는 **계정 이름**을 요구한다. 내 블로그의 이름이 **Infinity Loop**이니 그대로 입력하고, 아래에 있는 체크박스는 모두 체크했다.

#### 2. 속성 만들기

속성? 그게 무슨 말이지? 무슨 속성을 말하는 걸까? 무엇을 의미하는지도 모르겠는데 이름을 입력하라니! 도대체 어쩌란 말인가? 난감하네. 어떻게 해야 하는지 몰라서 그냥 단순하게 생각했다. 내 블로그에 대한 것이니, **속성 이름**으로는 **blog**라고 썼다. **시간대**는 **대한민국**으로, **통화**는 **달러**로 했다.

#### 3. 비지니스 세부정보

**업종 카테고리**는 블로그를 만들었으니 **온라인 커뮤니티**가 맞는 거 같다. **비지니스 규모**라.. 이게 비지니스인가 싶었지만, 뭐라 부르든 어떠하리! 그래서 젤 작은 걸로 선택했다.

#### 4. 비지니스 목표

으음.. 난 비지니스를 하는 게 아닌데, 자꾸 비지니스에 맞춰서 물어보네. 보기들 중에 2개까지 고를 수 있다고 하니, 나에게 가장 그럴 듯한 것을 골랐다. **웹 또는 앱 트래픽 파악** 그리고 **사용자 참여 발생 시간 및 유지율 보기**

#### 5. 데이터 수집

약관 동의하고 데이터 수집할 플랫폼 선택하고 데이터 스트림 설정까지 다 끝내니, 갑자기(?) 다음과 같은 화면이 나왔다.

{% include image_caption.html imageurl="images/analytics-11.png" title="구글 태그 설정" caption="구글 태그 설정" %}

이게 뭐지? 그냥 가볍게 넘겼다. 하지만, 이후 삽질 1 시간 만에 이게 중요했다는 것을 알게 되었다. 그 삽질에 대한 내용은 아래에 계속...

#### 웹 스트림 세부정보

{% include image_caption.html imageurl="images/analytics-12.png" title="웹 스트림 세부정보" caption="웹 스트림 세부정보" %}

다른 건 몰라도, 감각적으로 **G-XXXXXXXXXX**이라고 표시된 값이 중요하다는 것을 알았다. 이런 건 일단 복사하고 봐야한다. 물론 나중에 잘 찾으면 언제든 볼 수 있는 것 일테지만. 경험상 이런 값은 한 번 설정만 잘 하면 두 번 다시 볼 일이 없는 값이다. 자! 이제 이 값을 써 먹어 볼까?

#### 다시, _config.yml

**_config.yml** 파일에서 봤던 다음과 같은 부분을 찾아서 **google_analytics**에 값을 넣는다.

```yml
# Google Analytics id, e.g. "UA-NNNNNNNN-N"
google_analytics: "G-XXXXXXXXXX"
```

그런데, 알 수 없는 싸늘한 느낌이 온다. 무언가 잘못된 느낌이 든다. 그 불길한 느낌을 준 것은 바로 주석의 내용이었다. "UA-NNNNNNNN-N" 이렇게 생긴 것을 넣으라는 것인데, 내가 복사한 값은 "G-XXXXXXXXXX"다. '_기분 탓 일거야_'라며 애써 외면하고 구글 애널리틱스를 켜 놓고 블로그를 새로고침 해본다. 실시간 Peak가 올라오지 않는다. 아마 내가 조급한 거겠지. 다시 블로그를 새로고침한다. 아직 실시간 Peak가 올라오지 않는다. 이건 뭔가 잘못된 거다.

아까의 '불길함'부터 실마리를 풀어 본다.

그래! 돌이켜보니 저 "UA-"로 시작하는 주석이 마음에 걸렸다. '_왜 구글 애널리틱스에서 내가 복사한 값은 "G-"로 시작하는 걸까?_' UA와 G가 무엇을 의미하는지 살펴보면 명확해진다. UA는 **Universal Analytics**를 의미하며 G는 **Google Analytics 4**를 의미한다. 이 둘의 차이점을 자세히 쓰진 않겠다. 그냥 Universal Analytics는 옛날(나쁘다는 뜻이 아닌 시간적으로 이전)에 쓰던 것이고 Google Analytics 4는 그 이후에 나온 것이다. 

정리하자면, 지금 내가 사용하는 Jekyll theme은 예전에 만들어진 것이며 그 때 당시 사용되던 Universal Analytics를 지원하게 되어 있다는 것이다.

으음.. 그래서.. 이를 어쩐다!!

#### google_analytics.html

망연자실한 상태로 시간이 꽤 흘렀다. 구글링도 해보고 이것저것 바꿔보고 다 실패하였다. github page의 단점인가? 싶은 생각도 들었다. 분명히 내가 무언가를 이해하지 못하고 있는데, 그게 무엇인지 모르는 그런 상태. 답답하다. 답답한 마음에 theme에 있는 파일들을 하나씩 살펴보았다. 그러다 발견한 파일. **google_analytics.html**은 다음과 같은 모습이었다.

{% include image_caption.html imageurl="images/analytics-12-1.png" title="google_analytics.html (previous)" caption="기존의 google_analytics.html 코드" %}

html 파일? 아까 html 코드 같은 걸 어디서 봤는데? 그렇다. Google Analytics 계정 만들 때 나왔던 코드(**위에 있는 "구글 태그 설정" 스샷의 코드**)가 있었다. 그래서 부랴부랴 그 코드를 다시 찾아 복사하고 형식에 맞게 수정하였다.

{% include image_caption.html imageurl="images/analytics-12-2.png" title="google_analytics.html (new)" caption="새롭게 수정된 google_analytics.html 코드" %}

기대하는 마음으로 수정된 파일을 반영하고 애널리틱스를 바라 보았다.

{% include image_caption.html imageurl="images/analytics-13.png" title="Google Analytics realtime" caption="구글 애널리틱스 실시간 개요" %}

ㅋㅑ~~~<br />
드디어 peak가 나타났다! 드디어 성공! 🎉