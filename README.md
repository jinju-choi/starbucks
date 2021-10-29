# ☕Starbucks site clone

패스트캠퍼스 강의를 들으며, 예제 스타벅스 랜딩 페이지(홈페이지)를 제작하였습니다.

![starbucks-main](https://user-images.githubusercontent.com/89460582/139402361-b5cdd345-1c27-4112-932d-ee74704ccb41.PNG)

## 오픈그래프 & 트위터 카드

웹페이지가 소셜 미디어(페이스북 등)로 공유될 때 우선적으로 활용되는 정보를 지정합니다.
![starbucks-opengraph](https://user-images.githubusercontent.com/89460582/139412281-a86e518c-2b40-4bb5-b36e-3d1fc1afafe8.PNG)

- 오픈그래프
```html
<meta property="og:type" content="website" />
<meta property="og:site_name" content="Starbucks" />
<meta property="og:title" content="Starbucks Coffee Korea" />
<meta property="og:description" content="스타벅스는 세계에서 가장 큰 다국적 커피 전문점으로, 64개국에서 총 23,187개의 매점을 운영하고 있습니다." />
<meta property="og:image" content="./images/starbucks_seo.jpg" />
<meta property="og:url" content="https://starbucks.co.kr" />
```

- 트위터카드
```html
<meta property="twitter:card" content="summary" />
<meta property="twitter:site" content="Starbucks" />
<meta property="twitter:title" content="Starbucks Coffee Korea" />
<meta property="twitter:description" content="스타벅스는 세계에서 가장 큰 다국적 커피 전문점으로, 64개국에서 총 23,187개의 매점을 운영하고 있습니다." />
<meta property="twitter:image" content="./images/starbucks_seo.jpg" />
<meta property="twitter:url" content="https://starbucks.co.kr" />
```

## 프로모션 토글
프로모션 버튼 클릭시 프로모션 구간이 토글되는 기능을 구현 하였습니다.

![starbucks-preview05](https://user-images.githubusercontent.com/89460582/139412899-21a711a4-ad97-4abd-9993-e68fdcc1d8cc.gif)



## 벳지와 top버튼 제어
GSAP 라이브러리를 이용하여 벳지와 top버튼 스크롤시 show, hide 를 구현하였습니다.

[GSAP(The GreenSock Animation Platform)](https://greensock.com/gsap/)은 자바스크립트로 제어하는 타임라인 기반의 애니메이션 라이브러리입니다.
[ScrollToPlugin](https://greensock.com/scrolltoplugin/)은 스크롤 애니메이션을 지원하는 GSAP 플러그인입니다.

![starbucks-preview06](https://user-images.githubusercontent.com/89460582/139408498-c0aadd4e-a87a-477f-99dc-8dfdd1097f6b.gif)

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/gsap.min.js" integrity="sha512-IQLehpLoVS4fNzl7IfH8Iowfm5+RiMGtHykgZJl9AWMgqx0AmJ6cRWcB+GaGVtIsnC4voMfm8f2vwtY+6oPjpQ==" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/ScrollToPlugin.min.js" integrity="sha512-nTHzMQK7lwWt8nL4KF6DhwLHluv6dVq/hNnj2PBN0xMl2KaMm1PM02csx57mmToPAodHmPsipoERRNn4pG7f+Q==" crossorigin="anonymous"></script>
```

[.to() 사용법](https://greensock.com/docs/v3/GSAP/gsap.to())  
[GSAP Easing](https://greensock.com/docs/v2/Easing)

```js
gsap.to(요소, 시간, 옵션)
// 또는
TweenMax.to(요소, 시간, 옵션)
```

```js
toTopEl.addEventListener('click', function () {
  gsap.to(window, .7, {
    scrollTo: 0
  });
});
```
top버튼 클릭시 상단으로 이동.



## swiper API를 이용한 슬라이드 구현

[Swiper](https://swiperjs.com/)는 하드웨어 가속 전환과 여러 기본 동작을 갖춘 현대적인 슬라이드 라이브러리입니다.

[Getting Started With Swiper ](https://swiperjs.com/get-started)

![starbucks-preview02](https://user-images.githubusercontent.com/89460582/139402999-1e4c6001-ffcb-4236-b1ed-a555fefc3d4b.gif)

사용방법
```html
<!-- in HEAD -->
<link rel="stylesheet" href="https://unpkg.com/swiper@6.8.4/swiper-bundle.min.css" />
<script src="https://unpkg.com/swiper@6.8.4/swiper-bundle.min.js"></script>

<!-- in BODY -->
<div class="swiper-container">
  <div class="swiper-wrapper">
    <div class="swiper-slide">1</div>
    <div class="swiper-slide">2</div>
    <div class="swiper-slide">3</div>
  </div>
</div>
```
[Swiper API](https://swiperjs.com/swiper-api)(옵션)
```js
new Swiper(요소, 옵션);
```
```js
new Swiper('.swiper-container', {
  direction: 'vertical', // 수직 슬라이드
  autoplay: true, // 자동 재생 여부
  loop: true // 반복 재생 여부
});
```

## Youtube API
[IFrame Player API](https://developers.google.com/youtube/iframe_api_reference?hl=ko)를 통해 YouTube 동영상을 제어.

![starbucks-preview03](https://user-images.githubusercontent.com/89460582/139405193-515ac234-e8e7-421e-9b11-dffd45641a5f.gif)

```html
<!-- in HEAD -->
<script defer src="./js/youtube.js"></script>

<!-- in BODY -->
<div id="player"></div>
```
`onYouTubePlayerAPIReady` 함수 이름은 Youtube IFrame Player API에서 사용하는 이름이기 때문에 다르게 지정하면 동작하지 않는다.<br>
그리고 함수는 전역(Global) 등록해야 한다.

```js
// Youtube IFrame API를 비동기로 로드
const tag = document.createElement('script');

tag.src = "https://www.youtube.com/iframe_api";
var firstScriptTag = document.getElementsByTagName('script')[0];
firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);

function onYouTubeIframeAPIReady() {
  //player id속성 값을 찾아
  new YT.Player('player', {
    videoId: 'An6LvWQuj_8', //재생할 영상 id
    playerVars: {//재생하기 위한 변수들
      autoplay: true, //자동재생 유무
      loop: true, // 반복재생 유브
      playlist: 'An6LvWQuj_8' //반복 재생할 영상 id 
    }, 
    events: { //재생 되는 영상에 이벤트
      onReady: function (event) {//영상이 재생되면
        event.target.mute() //음소거
      }
    }
  });
}
```

## 요소 나타나는 효과 구현
스크롤과 요소의 상호 작용을 위한 자바스크립트 라이브러리인 [ScrollMagic](https://github.com/janpaepke/ScrollMagic)을 이용하였습니다.  
대표적으로 어떤 요소가 현재 화면에 보이는 상태인지를 확인할 때 사용합니다.

![starbucks-preview04](https://user-images.githubusercontent.com/89460582/139406445-e283ddf0-115e-4634-ad7a-a5c4f18fd1ce.gif)


[ScrollMagic API](http://scrollmagic.io/docs/)

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/ScrollMagic/2.0.8/ScrollMagic.min.js"></script>
```

```js
new ScrollMagic
  .Scene({ // 감시할 장면(Scene)을 추가
    triggerElement: spyEl, // 보여짐 여부를 감시할 요소를 지정
    triggerHook: .8 // 화면의 80% 지점에서 보여짐 여부 감시
  })
  .setClassToggle(spyEl, 'show') // 요소가 화면에 보이면 show 클래스 추가
  .addTo(new ScrollMagic.Controller()) // 컨트롤러에 장면을 할당(필수!)
```

