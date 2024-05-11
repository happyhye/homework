## 과제 내용
<details>
<summary>다음 조건을 만족할 수 있도록 마크업과 스타일링을 완성하자.</summary>
<div><br/>
  
  1. 아바타 이미지는 배경 방식이 아닌 콘텐츠 이미지(&lt;img&gt;요소)로 마크업한다.
  
2. 아바타의 상태 정보를 알 수 있도록 정보를 제공한다.
   
3. 아바타 이미지의 크기 - 64px X 64px
   
4. 아바타 이미지 간의 간격 - 20px
   
5. 회색 원 배경색 - #DBDBDB
   
6. 초록색 원 배경색- #4CFE88
    
7. `float`을 사용하여 다음의 레이아웃을 구현해 본다.
![ex1](https://github.com/happyhye/homework/assets/167636384/aa5094c4-7c09-4dd4-8d8c-cc751e7aedfe)

8. `flex`를 지원하는 환경에서는 다음과 같이 배치되도록 레이아웃을 구현해 본다.
![ex2](https://github.com/happyhye/homework/assets/167636384/ab4ee09a-6819-4e08-a5e7-08fdc02b4836)

아바타 과제 수행에 대한 설명을 `avatars.md` 파일에 작성하고 `homework` 폴더에 있는 `README.md`에 링크로 연결한다.

과제는 `5월 4일 오후 11시 59분`까지 Github 저장소에 Push 한다.
</div>
</details>

## 구현 결과
### Chrome에서 실행했을 때 (flex를 지원하는 브라우저)
- Firefox, 네이버 웨일, Microsoft Edge 👌
![0  실행결과](https://github.com/happyhye/homework/assets/167636384/d882cfb1-9f94-4195-9927-9f696c8c5175)
![0  실행결과](https://github.com/happyhye/homework/assets/167636384/d03d6fe3-66a9-4a1b-9d73-6e7f8f86cdbc)
### Internet Explorer에서 실행했을 때
![0  익스플로러 실행결과](https://github.com/happyhye/homework/assets/167636384/81612062-a809-4a57-8449-a4e01588187a)


## 개요
- 사용 언어: HTML, CSS
- avatars 디렉터리 구조

  ![image](https://github.com/happyhye/homework/assets/167636384/61a8c6f2-d6f0-49b5-b11e-29fd3a9dd2ec)

## HTML 코드 설명
- ```<div class="title">```: Abatars 타이틀
- ```<section class="group">```: 아바타들을 group으로 묶음
  - ```<div class="avatar">```: 이미지와 상태를 가진 아바타 하나
    - ```<img>```: 아바타 이미지
    - ```<div class="state">```: 상태 확인 (온라인 or 오프라인)
- 접근성을 고려하여 `title`,`group`,`state`에 `aria-label`을 추가하였습니다.
- 이미지 대체 텍스트(`alt` 속성)를 지정하였습니다.


## CSS 코드 설명
- ```* { box-sizing: border-box; }```: 요소의 크기를 width 값과 동일하게 설정
- `.avatar`
  - `position: relative;`: 자기 자신을 기준으로 배치
  - `float: left;`: 아바타 이미지와 상태를 나란히 배치하기 위해 float 속성 지정
- `.state`
  - `position: absolute;`: 부모(조상) 요소를 기준으로 배치
- `@supports`: 해당 CSS를 제공하는 브라우저에 따라 맞춤형으로 적용할 수 있음

## 문제 해결 및 궁금증
<details>
<summary>1. Internet Explorer에서 지원하지 않는 태그 사용</summary>
<div><br/>
  
![error](https://github.com/happyhye/homework/assets/167636384/3793664e-805e-4849-98b5-f4486860ee77)

과제를 보여줘야 하는 부분을 본문이라고 생각하여 &lt;main&gt;으로 마크업 했는데 Internet Explorer에서 보이는 결과가 이상했다.

위 사진 속 형광펜칠되어있는 부분이 border 속성을 지정한 부분인데 박스가 제대로 그려지지 않았다.

처음엔 &lt;main&gt; 문제라고 생각하지 못하고 열심히 삽질하다가 설마..? 하고 찾아봤는데

![cap](https://github.com/happyhye/homework/assets/167636384/0eca4dcd-c196-4023-af12-46fe372b025b)

Internet Explorer에서 &lt;main&gt;을 지원하지 않아 박스가 그려지지 않았던 것이다.

👉 <b>[캔아이유즈](https://caniuse.com/)에서 해당 요소를 지원하는지 안 하는지 꼭 확인하자.</b>
</div>
</details>

<details>
<summary>2. &lt;img&gt; 요소 사이즈가 지정한 대로 나오지 않았다.</summary>
<div><br/>

![Untitled](https://github.com/happyhye/homework/assets/167636384/be070df2-2c7b-4049-b10c-bcd53af36706)

CSS 파일에서 img 사이즈를 64px X 64px로 지정했는데 개발자 도구를 보니 64px X 68px로 나오는 것이다..!

사진 보면 알 수 있듯 이미지 밑에 약간의 여백이 있다.

**&lt;img&gt;가 인라인 요소라서 보이지 않는 가상의 기준선 때문에 여백이 생긴 것**이다.

![Untitled (1)](https://github.com/happyhye/homework/assets/167636384/54071c31-3dfe-4787-ade6-7511eb3c3c91)

👉 <b>``` img { display: block; } ``` 코드를 추가하면 간단하게 해결할 수 있다.</b> img를 블록 요소로 처리해주는 것.
</div>
</details>

<details>
<summary>궁금증. flex를 사용하여 아바타들 배치할 때</summary>
<div><br/>

과제 사진을 보면 윗줄에 아바타 4개, 아랫줄에 아바타 4개 배치되어 있는데 flex를 사용하니 이게 한 줄로 주르륵 배치되었다.

그래서 ``` @supports (display: flex) { .group { padding: 190px; } } ```

padding 값을 190px 주니까 내가 원하는 화면으로(윗줄 아바타 4개, 아랫줄 아바타 4개) 렌더링 되었는데

padding 값을 이렇게 설정해도 괜찮은 걸까?.. 더 찾아봐야겠다.

</div>
</details>


## 느낀 점
<details>
<summary>펼치기</summary>
<div><br/>
선생님께서 사진 있는 부분만 구현해도 된다고 하셨는데 이왕 과제하는 거 예제와 똑같이 만들어보고 싶었다.

HTML과 CSS를 프론트엔드 스쿨 와서 처음 하는지라 이 과제 하나 하는데도 정말 한세월 걸렸다. (ㅠㅠ)

수업 때 제대로 이해 못한 부분이 `float`과 `flex`였는데 아바타 과제하면서 많이 배웠다. 선생님께서 괜히 과제 내주신 게 아니구나..!

갈 길이 멀지만 하나하나 클리어할 때마다 뿌듯함이 더 커서 즐겁다.

이번 과제로 다시 한번 느낀 부분은 다른 예제를 많이 만들어서 익숙해져야겠다는 것. 그리고 이해했다고 그냥 넘긴 부분도 실습으로 다시 공부해야겠다.

TODO: 수업 시간에 box model을 계산해서 콘텐츠 배치해 줬던 게 생각나 과제에 적용했다.

가로 800px 세로 500px인 박스 안에 아바타들을 배치하였는데 크롬같이 flex를 지원해 주는 브라우저에선 반응형으로 동작하지만 Internet Explorer에선 반응형으로 동작하지 않는다. 나중에 반응형으로 만들어보기!
</div>
</details>
