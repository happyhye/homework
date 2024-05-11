## 과제 내용
네이버 로고 이미지는 아래 SVG 코드를 활용하거나 svg 형식 및 png 형식의 이미지로 저장하여 사용한다. 이때 로고 이미지 에셋의 저장 위치는 homework/naver/로 설정한다.

과제는 다음과 같은 조건을 만족할 수 있도록 구현한다.

`마크업`

- 로고 이미지는 배경이 아닌 \<img\> 요소로 마크업

  (svg를 지원하는 웹브라우저는 svg 형식으로 그렇지 않은 웹브라우저는 png 형식으로 보여지도록 구현)
    
- 웹접근성을 고려한 로그인 폼 서식 마크업

  (레이블 제공의 경우 WAI-ARIA가 아닌 HTML 네이티브 방식으로 구현)
    
- 아이디와 비밀번호는 필수 입력 서식임을 알 수 있도록 구현
- IP 보안 텍스트 클릭 시 미리 제공 된 ip_secruity.html 파일이 새창에 보이도록 구현
- 로그인 상태유지와 IP 보안 ON/OFF는 스위치는 키보드로도 조작 가능하도록 구현

`스타일링`
- 반응형으로 구현 (768px 미만 모바일 / 768px 이상 데스크탑)
- 모바일 퍼스트 (공통 스타일과 모바일 스타일을 먼저 구현한 후 데스크탑 스타일을 재정의 할 것)
- 글자 크기 및 여백(margin 및 padding)은 모두 rem 단위로 설정할 것)

- 기본 글자 크기 및 색상

  16px, #181818

- 로고

  가로 230px, 가운데 배치

- 포커스 스타일 커스텀 (색상 #24388d)
- 모바일 로그인 폼 로그인 폼의 가로 크기는 100%(좌/우 여백 각 20px 포함)
- 모바일 환경에서 IP 보안 ON/OFF 스위치는 사용자에게 제공되지 않도록 구현
- 데스크탑 로그인 폼의 가로 크기는 500px(좌/우 여백 각 20px 포함)
- 입력 서식 글자크기 및 세로 크기, 테두리 선 색상, 배경 색상

  기본 상태 : 14px, 45px, #dadada, #fff

  포커스 상태 : #03cf5d, #e9f0fd
    
- 로그인 버튼 글자 크기, 세로 크기, 글자 색상, 배경색상, 위쪽 여백

  16px, 45px, #fff, #03cf5d, 20px
    
- 로그인 상태유지 및 IP 보안 ON/OFF 영역 위쪽 여백 10px
- 로그인 상태유지 체크박스 배경 이미지 및 크기와 여백
    
    선택안함 : unchecked.svg
    
    선택함 : checked.svg
    
    가로 * 세로 : 24px * 24px
    
    배경 이미지 오른쪽 여백 : 5px
    
- IP 보안 스위치의 글자 크기 16px, 글자 색상 #181818

## 구현 결과
### 반응형
![0-반응형](https://github.com/happyhye/homework/assets/167636384/a5090a0f-d811-45e0-9c83-6ab3ade7879f)

### 마우스로 접근했을 때
![1-마우스](https://github.com/happyhye/homework/assets/167636384/62eff629-d67e-4bd0-8cb7-d6ee2f8a4f26)

### 키보드로 접근했을 때
![2-키보드](https://github.com/happyhye/homework/assets/167636384/e9a7d4e0-992b-403a-b03d-4ebf627bbae8)

## 개요
- 사용 언어: HTML, CSS
- naver 디렉터리 구조
  
  ![image](https://github.com/happyhye/homework/assets/167636384/79111058-7b9c-4432-be50-b54bf967367f)

## HTML 코드 설명
![layout](https://github.com/happyhye/homework/assets/167636384/83342ea6-cf86-4695-82ef-0d7673a44321)

전체적인 레이아웃은 위 이미지와 같습니다.

```
    <h1 class="logo">
      <picture>
        <source srcset="logo.svg" type="image/svg+xml">
        <img src="logo.png" alt="네이버">
      </picture>
    </h1>
```

- section 태그로 묶고자 하여 제목인 \<h1\> 태그를 작성하였습니다.
- logo.svg 파일을 지원하지 않는 브라우저라면 logo.png를 불러옵니다.

```
    <label for="userId" class="sr-only">사용자 아이디</label>
    <input type="email" id="userId" placeholder="아이디(이메일)" name="userId" required />

    <label for="userPassword" class="sr-only">사용자 비밀번호</label>
    <input type="password" id="userPassword" placeholder="비밀번호" name="userPassword" required />
```

- label 태그는 sr-only 클래스로 작성하여 화면엔 보이지 않지만, 스크린리더로 읽을 수 있게 하였습니다.
- input 태그에 required 속성을 추가하여 입력값을 필수로 작성할 수 있게 하였습니다.

```
<a href="/ip_security.html" target="_blank" rel="noopener noreferrer">IP보안</a>
```
- `target="_blank"`: 새창으로 열릴 수 있게 하였습니다.
- `rel="noopener noreferrer"`: `target="_blank"`의 문제(보안 취약, 성능 문제) 해결을 위해 추가하였습니다.

## CSS 코드 설명
```
:root {
  --font-size: 1rem;  /* 16px */
  --px-10: 0.625rem;  /* 10px */
  --px-14: 0.875rem;  /* 14px */
  --px-20: 1.25rem;   /* 20px */
  --px-45: 2.8125rem; /* 45px */
  --color-black: #181818; /* 기본 컬러 색상 */
  --color-green: #03cf5d;
}
```
- 유지보수 용이를 위해 변수를 작성하였습니다.

```
  &:focus{
    outline: 0;
  }

  &:focus-visible{
    outline: 2px solid #24388d;
  }
```
- 마우스로 접근할 땐 outline이 보이지 않고, 키보드로 접근할 땐 outline이 보입니다.

```
.login-check-group {
  display: flex;
  justify-content: right;
....
}
```
- 모바일일 땐 '로그인 상태유지'가 오른쪽에 위치하도록 right를 부여하였습니다.

```
@media (min-width: 768px) { .... }
```
- 미디어쿼리를 사용하여 데스크탑일 때 보여지는 화면을 재정의하였습니다.

```
    input:checked + .security-on-off::before {
      content: 'ON';
      color: var(--color-green);
    }
  
    input + .security-on-off::before {
      content: 'OFF';
    }
```
- 가상요소를 사용하여 ON / OFF 글자를 바꾸었습니다.

## 문제점
![image](https://github.com/happyhye/homework/assets/167636384/b34e1231-6156-459f-b65e-d8baa3adfe23)
- 키보드로 ON / OFF에 접근했을 때 텍스트 가로 크기만큼 포커스 잡히는 게 아니라 고정된 크기로 잡힙니다.

## 느낀 점
개인 일정 때문에 과제할 수 있는 시간이 너무 부족했는데 그래서 그런가 아쉬움이 많이 남은 과제였습니다.

좀 더 잘할 수 있을 것 같은데.. 하는 생각이 계속 들지만,

시간 탓을 하지 않고 더 열심히 공부해서 뚝딱뚝딱 만들 수 있는 단계까지 노력하겠습니다.
