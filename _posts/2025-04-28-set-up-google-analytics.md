---
layout: post
title: "Google Analytics 넣어보기"
description: "How to set up Google Analytics"
date: 2025-04-28
feature_image: images/analytics.jpg
tags: [google analytics, jekyll]
---

그게 무슨 일이든, 미래를 알고 있다면...<br />
행복할 거라 장담은 못 하지만 적어도 실패하진 않을 거라 말할 수 있겠지. 시험을 앞둔 수험생에게 출제될 시험 문제를 미리 알고 있다면. 다가올 위험을 미리 알고 있다면. 내일 주식이 어떻게 될지 알고 있다면. 이번 주 복권 결과를 알고 있다면. 그 삶이 행복하고 안 하고를 떠나, 결코 실패하진 않을 것이다. 하지만 도대체 누가 미래를 알 수 있겠는가?

## Although we don't have a crystal ball,

과거를 바탕으로 현재를 판단하여 미래를 **예측**하는 능력을 우리는 가지고 있다. (*Praise the Load* 🎉) 과거의 정보가 쌓여 있고 그것을 읽을 수 있다면 충분히 현재를 파악할 수도 있고 미래를 예측할 수도 있다. 물론 **얼마나 잘 읽는가**는 또 다른 얘기가 되겠지만. 어쨌든 데이터를 수집하고 그것을 분석하는 것은 매우!! 중요하다. Github Page는 결국 웹사이트다. 웹사이트를 위한 데이터 분석툴들은 여러 가지가 있겠지만, 내가 알고 있고 주로 사용하는 것이 **Google Analytics**니 이것을 붙여야겠다. 

마음을 먹고, _config.yml 파일을 보니 다음과 같은 부분이 눈에 들어온다.

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

#### 1. 계정 생성
The iPhone 6 and iPhone 6 Plus were unveiled on September 9, 2014 and released on September 19, 2014; pre-orders began on September 12, 2014, with the iPhone 6 starting at US$649 and the iPhone 6 Plus starting at US$749. In China, where the iPhone 5S and 5C were the first models in the iPhone series to be released in the country on the same day as their international launch, Apple notified local wireless carriers that it would be unable to release the iPhone 6 and iPhone 6 Plus in China on the 19th because there were "details which are not ready"; local media reported that the devices had not yet been approved by the Ministry of Industry and Information Technology, and earlier in the year, a news report by state broadcaster China Central Television alleged that iPhone devices were a threat to national security because iOS 7's "frequent locations" function could expose "state secrets."

On August 2015 Apple admitted that some iPhone 6 Plus may have faulty cameras that could be causing photos to look blurry and initiated a replacement program.

On September 9, 2015 the 128 GB version of both the iPhone 6 and iPhone 6 Plus was discontinued along with the gold version of both phones, the 16 GB and 64 GB versions of the iPhone 6 and iPhone 6 Plus in silver and space gray remain available for sale at a reduced price due to the release of the iPhone 6S and iPhone 6S Plus flagship devices.

## Specifications

The design of the iPhone 6 and iPhone 6 Plus are influenced by that of the iPad Air with a glass front that is curved around the edges of the display, and an aluminum rear that contains two plastic strips for the antenna. Both models come in gold, silver, and "space gray" finishes. The iPhone 6 has a thickness of 6.9 millimetres (0.27 in), while the iPhone 6 Plus is 7.1 mm (0.28 in) in thickness; both are thinner than the iPhone 5S and iPhone 5C, with the iPhone 6 being Apple's thinnest phone to date. The most significant changes to the iPhone 6 and iPhone 6 Plus are its displays; both branded as "Retina HD Display" and "ion-strengthened", the iPhone 6 display is 4.7 inches in size with a 16:9 resolution of 1334x750 (326 PPI, minus one row of pixels), while the iPhone 6 Plus includes a 5.5-inch 1920x1080 (1080p) display (401 PPI). The displays use a multiple-domain LCD panel, dubbed "dual-domain pixels"; the RGB pixels themselves are skewed in pattern, so that every pixel is seen from a different angle. This technique helps improve the viewing angles of the display.

To accommodate the larger physical size of the iPhone 6 and iPhone 6 Plus, the power button was moved to the side of the phone instead of the top to improve its accessibility. The iPhone 6 features a 6.91 Wh (1810 mAh) battery, while the iPhone 6 Plus features a 11.1 Wh (2915 mAh) battery. Unlike the previous model, the rear-facing camera is not flush with the rear of the device, and has a slight "bulge" around the lens. It has a dual-core 1.4 GHz Cyclone processor (ARM v8-based). [ [Source](https://en.wikipedia.org/wiki/IPhone_6) ]