# apple 제품 카드

## 과제 내용
- 과제 관련 에셋은 파일을 다운로드 받아 압축을 푼 뒤 `homework` 폴더로 복사한다.
- 구조(HTML)는 `apple.html` 파일에 스타일(CSS)은 `nstyles/apple.css` 파일에 과제에 대한 설명은 `apple.md` 파일에 작성한다. (**`반드시` 제공 된 파일에 작성할 것.**)
- 과제 수행에 대한 설명을 `apple.md` 파일에 작성하고 `homework` 폴더에 있는 `README.md` 파일에 링크로 연결한다.

- **`CSS Grid`** 를 사용하여 **반응형 레이아웃**을 구현한다.

- 중단점(breakpoint)은 **`1024px`** 로 지정한다.

  (Small Screen - 1024px 이하 / Large Screen - 1024px 이상)

## 구현 결과 (gif 로딩 중...)
![구현 결과](https://github.com/happyhye/homework/assets/167636384/bf5cd737-e909-401b-baf3-2ca45b64c9f1)
- 이미지 용량이 커서 줄이다 보니 UI가 움직이는 것처럼 나왔는데 실제로는 정상적으로 동작합니다.

  (나중에 이미지만 수정하도록 하겠습니다.)

## 개요
- 사용 언어: HTML, CSS
- apple 디렉터리 구조

  ![image](https://github.com/happyhye/homework/assets/167636384/e8f51ca4-b4c9-481f-9163-275be2a6a11e)


## 마크업 설계
![apple2](https://github.com/happyhye/homework/assets/167636384/0f72eea2-b670-4a8a-bc3d-73e86febca9f)

- 모바일: 1열
- 데스크탑: 2열

<br />

- `<article>`: 각각의 카드 컴포넌트를 구분하기 위해 article로 마크업
- `<h2>`: 최상단에 있는 상품명 (제목)
- `<p>`: 상품에 대한 설명, '출시일 추후 공개'라는 부가 설명을 p로 마크업
- `<ul>`, `<li>`, `<a>`: 버튼을 누르면 다른 링크로 이동함 → `<button>`이 아닌 `<a>` (링크) 태그 사용

<br />

`if ~`
- '출시일 추후 공개'라는 텍스트가 없는 컴포넌트는 `<div>`로 그룹 짓지 않음

## HTML 코드 설명
``` HTML
<section>

  <h1 class="sr-only">Apple</h1>

  <div class="card-grid">
    <article class="card-container cols-2">
      <h2 class="card-title" aria-describedby="iPadProDesc">iPad Pro</h2>
      <div class="card-text-group">
        <p class="card-description" id="iPadProDesc">놀라우리만치 얇다. <br /> 엄청나게 강력하다.</p>
        <p class="card-n-text">출시일 추후 공개</p>
        </div>
      <ul class="card-link-group">
        <li><a href="https://www.apple.com/kr/ipad-pro/" class="link-item more-item" target="_self">더 알아보기</a></li>
        <li><a href="https://www.apple.com/kr/shop/buy-ipad/ipad-pro/" class="link-item price-item" target="_self">가격 보기</a></li>
      </ul>
    </article>

    <article class="card-container cols-2">
      <h2 class="card-title" aria-describedby="iPhone15ProDesc">iPhone 15 Pro</h2>
      <p class="card-description" id="iPhone15ProDesc">티타늄. 초강력. 초경량. 초프로.</p>
      <ul class="card-link-group">
        <li><a href="https://www.apple.com/kr/iphone-15-pro/" class="link-item more-item" target="_self">더 알아보기</a></li>
        <li><a href="https://www.apple.com/kr/shop/buy-iphone/iphone-15-pro/" class="link-item price-item" target="_self">가격 보기</a></li>
      </ul>
    </article>


    ... 코드 중략 ...
</section>
```

- `<section>`: main으로 마크업 할지 section으로 마크업 할지 고민하다가 카드 컴포넌트만 있는 영역이라고 생각하여 section으로 마크업하였습니다.
- `<h1 class="sr-only">Apple</h1>`: 페이지 제목을 화면엔 보이지 않지만, 스크린리더로는 접근할 수 있도록 sr-only 클래스를 추가하였습니다.
- `<div class="card-grid">`: 그리드 레이아웃을 만들기 위해, 단순히 묶기 위한 용도로 div을 사용하였습니다.
- `<article>`: 카드 컴포넌트를 하나를 article로 마크업하였습니다.
  - `<h2>`: 상품명 제목
    - `aria-describedby="iPadProDesc"`: 상품에 대한 설명을 제공하는 속성을 사용하였습니다. (접근성 측면)
  - `<div class="card-text-group">`: 단순히 스타일링을 위해, `<p>` 태그를 묶기 위한 용도로 작성하여 class만 추가하였습니다.
  - `<ul>`, `<li>`: 버튼 2개를 li로 마크업하였습니다.
    - `<a target="_self">`: 현재 윈도우창에서 링크된 웹페이지를 오픈할 수 있게 하였습니다.

## CSS 코드 설명
``` CSS
/* 카드 레이아웃 */
.card-grid {
  display: grid;
  grid-template-columns: 1fr;
  grid-auto-rows: auto;
  gap: var(--small-spacing);
}
```
- 그리드 레이아웃을 만들기 위한 스타일링 코드입니다.
- 모바일 퍼스트로 작성하였습니다.
- 열 크기는 1fr, 행 크기는 auto.
- gap으로 각각의 카드 컴포넌트 사이에 여백을 주었습니다.

``` CSS
/* 카드 컴포넌트 */
.card-container {
  display: flex;
  flex-flow: column nowrap;
  height: var(--size); /* 500px - 카드 높이 고정 값 */
  padding-top: var(--large-spacing); /* 40px - Small Screen 상단 여백 */
  align-items: center;

  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;

  gap: var(--small-spacing); /* 12px - 카드 제목, 부제목, 버튼(링크)간 여백(gap) */

  .card-title {
    font-size: var(--large-text); /* 32px - Small Screen 제목 글자 크기 */
    font-weight: 800;
  }

  .card-text-group, .card-description {
    text-align: center;
  }

  .card-description {
    font-size: var(--base-text); /* 19px - Small Screen 부제목 글자 크기 */
    line-height: var(--line-normal); /* 부제목 줄간격 */
    margin-bottom: var(--x-small-spacing); /* 부제목 하단 여백 */
    font-weight: 600;
  }

  .card-n-text {
    color: var(--gray);
    font-size: var(--small-text); /* 17px - 출시일 추후 공개 글자 크기 (공통) */
  }

  .card-link-group {
    display: flex;
    flex-flow: row nowrap;
    gap: var(--base-spacing); /* 16px - 2개의 버튼(링크) 사이 여백 (공통) */
    
    .link-item {
      display: block;
      font-size: var(--xx-small-text); /* 12px - Small Screen 버튼(링크) 글자 크기 */
      padding: var(--x-small-spacing) var(--small-spacing);
      /* 8px - 버튼(링크) 상,하단 안쪽 여백 */
      /* 12px - 버튼(링크) 좌,우 안쪽 여백 */
      border-radius: 50px;
    }
  }
}
```
- 카드 컴포넌트에 대한 공통 스타일링 코드입니다.
- `display: flex`로 유연하게 반응할 수 있게 하였습니다.
- background position은 `center`,
  
  background size는 `cover`로 설정하여 가로&세로 모두 덮도록,

  이미지가 반복되지 않게 `no-repeat`으로 스타일링하였습니다.
- `theme.css` 파일에 있는 스타일링 조건을 모두 작성하였습니다.

``` CSS
/* 홀수 컴포넌트 */
.card-container:nth-of-type(odd) {
  background-color: var(--black);
  color: var(--white);

  ...공통 스타일링..중략..
}

/* 짝수 컴포넌트 */
.card-container:nth-of-type(even) {
  background-color: var(--white);
  color: var(--black);

  ...공통 스타일링..중략..
}
```
- 홀수 컴포넌트는 다크모드, 짝수 컴포넌트는 라이트모드라는 규칙성을 보았습니다.
- 홀수 컴포넌트`:nth-of-type(odd)`와 짝수 컴포넌트`:nth-of-type(even)`의 공통 스타일링 코드를 작성하였습니다.
- background 이미지가 로드되지 않을 경우를 고려하여 background color와 텍스트 color를 작성하였습니다.

``` CSS
/* 카드 배경 이미지 설정 */
.card-container:nth-of-type(1) {
  background-image: image-set(
    url(/products/ipad_pro.jpeg) 1x,
    url(/products/ipad_pro_2x.jpeg) 2x
  );
}
.card-container:nth-of-type(2) {
  background-image: image-set(
    url(/products/ipad_air.jpeg) 1x,
    url(/products/ipad_air_2x.jpeg) 2x
  );
}
... 중략
```
- `:nth-of-type`을 사용하여 각각의 카드 컴포넌트에 들어갈 배경 이미지를 추가하였습니다.

``` CSS
/* 미디어쿼리 */
@media (min-width: 1024px) {

  .cols-1 {
    grid-column: span 1;
  }

  .cols-2 {
    grid-column: span 2;
  }
  
  /* 가로 1024px 이상: grid 레이아웃 변경 */
  .card-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  /* 가로 1024px 이상: 셀 병합한 곳에 wide한 이미지로 변경 */
  .card-container:nth-of-type(1) {
    background-image: image-set(
    url(/products/ipad_pro_wide.jpeg) 1x,
    url(/products/ipad_pro_wide_2x.jpeg) 2x
  );
  }
  

  ... 중략


  .card-container {
    ... 중략

    .card-description br {
      display: none;

      ... 중략
    }
  }
}
```
- 미디어쿼리를 사용하여 뷰포트가 1024px 이상, 데스크탑일 때 보여지는 화면을 재정의하였습니다.
- 그리드 레이아웃과 background 이미지, 폰트 크기 등을 재정의하였습니다.
- `.card-description br { display: none; }`: 부제목이 모바일 버전에서 줄바꿈되는데, 데스크탑에선 한 줄로 보여질 수 있도록 br 태그를 `none`으로 지정하였습니다.

## 느낀 점

처음에 흰 화면만 보던 저였는데 슬비쌤 덕분에 성장하게 되었습니다.

이번 apple 과제할 때 아..! 그래도 내가 성장했구나!! 하는 생각이 문득 들었습니다.

마지막이라는 단어 때문인지 시원섭섭한 마음이 듭니다. 마지막 과제라니!!ㅠㅠ

과제할 땐 머리 터지더라도 내가 무엇을 몰랐고, 무엇을 이해 못했는지 다시 공부할 수 있어서 즐겁게 했습니다. 슬비쌤 피드백 덕분에 더 성장할 수 있었어요!!

HTML, CSS를 처음 하는데 슬비쌤께 배울 수 있어서 너무 좋았습니다. 감사합니다♥♥
