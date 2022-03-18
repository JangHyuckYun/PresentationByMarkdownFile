---

theme: gaia
_class: lead
paginate: true
marp: true
backgroundColor:#fff
---

# 리액트 

###### 기술연구소 윤장혁

---

# 목차

1. 리액트를 공부하게 된 이유
2. 리액트란?
3. 리액트 특징
4. 리액트 단점
4. 리액트 개발 환경
5. 리액트 기본 프로젝트 구조

---

# 리액트를 공부하게 된 이유

- javascript에서도 html문법을 그대로 사용하면서 변수들을 쉽게 넣을 수 있다는 것에 흥미를 가지게 되었음.
- 다양한 UI와의 상호작용이 필요할 때 DOM 요소를 하나하나 직접 관리하는게 불편해서

<br />
<br />

> ###### ※ UI란? 사람이 사용하기 쉽고, 이애하기 쉽도록 설계한 것.
> ###### ex) 사람들이 페이지에 오래 머물게 하도록 페이지 구성 하는것 또한 UI라고 할 수 있다.
---

# 리액트란?

####  - 페이스북이 만든 사용자 인터페이스(UI) 개발을 위한 라이브러리
####  - 싱글 페이지 애플리케이션이나 모바일 애플리케이션 개발 시 사용한다.

<br />
<br />
<br />
<br />

> ###### ※ 싱글 페이지 애플리케이션(SPA)란? 웹 사이트의 전체 페이지를 하나의 페이지에 담아 동적으로 화면을 바꿔가며 표현하는 페이지.

---

# 리액트 특징

1. 컴포넌트 기반의 라이브러리로 헤더, 메인 콘텐츠 등을 컴포넌트로 나누어 관리할 수 있다.
2. Virtual DOM 을 활용한 성능 최적화
3. 넓은 생태계
4. JSX 문법

---

# 컴포넌트 기반의 라이브러리

- 메인콘텐츠, 사이드바 메뉴 등을 컴포넌트로 나누고 나눈 컴포넌트들을 하나의 컴포넌트로 나누어 사용할 수 있다.
- 컴포넌트단위로 나누어 사용하기에 재사용성, 유지보수에 좋다.

![bg w:100% right contain](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4f0f2a6a-3761-488b-b4da-02dcd2c7097b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220306%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220306T133521Z&X-Amz-Expires=86400&X-Amz-Signature=88a8b49423bca47ada2cbb6efd63cd39a97c838b86606ee2408174de697ba5aa&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)


---

# 렌더링 과정

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/9df3fdf1-d503-4dcd-89ed-20aa623a8406/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220306%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220306T135006Z&X-Amz-Expires=86400&X-Amz-Signature=2bff91683f95ef2011f04dc5ac87971c71616060af811a84af1e2b934c856cfb&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/bc4b8af3-425b-406b-8bac-0e531192a5e8/render-tree-construction.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220306%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220306T135200Z&X-Amz-Expires=86400&X-Amz-Signature=9d877c415d3ab0e85df966db547f420fd0beac317bf3634324f2763f2769213e&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22render-tree-construction.png%22&x-id=GetObject)

---

# 리플로우(Reflow) / 리페인트(Repaint)

<br />
<br />
<br />
<br />

```javascript
    // 크기가 변경되면 리플로우, 리페인트가 발생함
const div = document.querySelector("div");
div.style.width = "100px";

// =====================================================================

// dom이 만들어지는 과정부터 만들어지면서 리플로우, 리페인트 등의 과정이 발생함
let newDiv = document.createElement("div"); // div 태그 메모리에 추가
div.appendChild(newDiv); // 위에 선언한 div 태그에 새로 만든 div 태그 추가
```

---

> ###### **리플로우(Reflow)가 일어나는 대표적인 CSS 속성들**
> position, width, height, margin, padding, border, font-size, font-weight, line-height, text-align, overflow ...
> ###### **리페인트(Repaint)만 일어나는 대표적인 CSS 속성들**
> background, color, text-decoration, border-style, border-radius, visibility ...
> ###### **리페인트(Repaint)도 일어나지 않는 CSS 속성들**
> transform, opacity, cursor, orphans, perspective ...

---

# Virtual DOM

가상의 DOM(Document Object Model)으로 말 그래도 **실제 돔을 복사하여 메모리에 가상으로 만든 것**이다.
가상돔은 렌더링의 횟수 즉 **연산의 횟수를 줄이는것**이 목적이다.
<br />
실제 돔을 하나라도 수정 할 때마다 페이지에 적용이 되어 렌더링 과정이 계속 발생하지만, 가상돔은 수정해도 **실제 돔에 바로 적용되진 않는다.**
<br />
리액트는 에서 컴포넌트들을 수정하면 virtual dom이 업데이트 된다.
컴포넌트들 수정 전 virtual DOM과, 수정 후 virtual DOM하고 비교해 바뀐 부분만 **실제 DOM에게 딱 한번만 전달**한다.

---

# 많은 인기로 인한 넓은 생태계

![width:1010px](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4a3242a9-e63e-4627-b49f-cfb69abf996a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220306%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220306T092054Z&X-Amz-Expires=86400&X-Amz-Signature=1f06da832e500715b8fc9aba45a54825756e21953965737a14ad8c28ff0f6988&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---

# JSX 문법

###### javascript에서 html 문법을 사용하게 해준다.
###### javascript의 문법(for, 삼항연산자 등), 변수, 함수 등을 바로 넣을 수 있다.

<br />

> ###### ※**최상위 태그는 무조건 한개**이어야 하며 여러개를 쓰고 싶은 경우 최상위에 "<></>"를 추가하거나 "<Fragment></Fragment>"를 추가하여야 한다.

![bg right contain](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/bd0d3cb8-45e1-42f3-8b60-e91a91c81535/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220307T010429Z&X-Amz-Expires=86400&X-Amz-Signature=2fe6ff911a79e2a3575c6f6f4fdfa05582eacc3995bb076d94919e306a2ba36f&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---

# 리액트 단점

- javascript의 기본 문법 이해 없이는 이해하기 힘들다.
- 설계를 잘못하면 순수 JS로 만든 페이지보다 더 큰 성능저하가 올 수 있다.

---

# 리액트 개발 환경

1. Node.js / 개발 툴 (Intellij, Visual Code, Atom 등등)설치
   <br />
   <br />
   <br />
> nodeJs 설치 사이트: https://nodejs.org/ko/
<br />
> ###### Node.js 란? Javascript를 런타임 환경에서 실행할 수 있게 해주는 것
> ###### 런타임 환경이란? 프로그래밍 언어가 구동되는(실행되는) 환경

--- 

# 리액트 개발 환경

2. 프로젝트담을 작업용 폴더 생성
   2.1 개발 툴(Intellij, Visual Code, Atom등등)을 사용해 작업용 폴더 오픈.
   2.2 Intellij 기준 좌측 하단에 Terminal 버튼을 눌러 로컽 터미널을 생성해준다.

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b19285c9-8fec-49a0-a43b-43c666dd882a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220306%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220306T143754Z&X-Amz-Expires=86400&X-Amz-Signature=c9a8a325c0b49cfb43dbf5de14a73d73a17251444669fa547022c95b01ea8ace&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---

# 리액트 개발 환경

3. 터미널에서 다음과 같은 명령어 입력.
   아래 명령어에서 **[app-name]** 부분은 자신이 원하는 프로젝트명으로 하면 된다.
   `npx create-react-app [app-name]`
   3.1 설치가 완료되었으면 다음과 같은 명령어 입력하여 해당 프로젝트 폴더로 이동한다. `cd [app-name]`
   3.2 해당 프로젝트를 실행하고 싶으면 다음과 같은 명령어를 입력하면 된다.
   `npm start`

> ###### NPM(Node Packaged Manager) 이란? NodeJS로 만들어진 package(module)을 관리해주는 툴.
> ###### NPX란? npm의 5.2.0버전부터 새로 추가된 도구로 NPM을 좀 더 편하게 사용하기 위해 **NPM에서 제공해주는 하나의 도구**이다.

---
![left:50%](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8a16b31e-0ca8-4475-a814-2284a98c5e68/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220306%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220306T145001Z&X-Amz-Expires=86400&X-Amz-Signature=e71bcbe48b1bee5cadc1571680169510344334bc9caf870025de3aba1f6c3886&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

![bg right:50%](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6f34dfa0-cc20-4cf6-b247-00069527aad8/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220306%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220306T144646Z&X-Amz-Expires=86400&X-Amz-Signature=2c384a2217008cbfce7764dfbde2975d832653e412738307a674f2a3795224f6&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---

# 리액트 기본 프로젝트 구조

- node_modules: `npm install`명령어를 통해 설치된 모듈들이 위치하는 폴더
- public: static 자원 폴더(), 정적 파일들을 위한 폴더
- src: 리액트를 작업할 폴더

![bg right:45%](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/969f4325-5469-46f3-bd5d-b45d2869ab63/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220307T002634Z&X-Amz-Expires=86400&X-Amz-Signature=02c696f3ba6ea8de3d25cbce2c4fb40192abd3d2468dd467987c091884085961&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---

# public/index.html
<br />

###### 가상돔 생성을 위한 html 파일 (빈 껍데기)
###### index.js 파일에서 렌더링된 결과들이 여기에 표시된다.


![bg right:47%  contain](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/fad12a91-3d98-4f27-b1f8-17b7b27734e4/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220307T003344Z&X-Amz-Expires=86400&X-Amz-Signature=05dedaecd95e01a0412a4c8cc928a3b7704a734187eba252d3b188ba78f88813&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---

# src/index.js

<br/>

> ##### ReactDOM.render() 이란?
> ###### 컴포넌트를 페이지에 렌더링 해주는 역할로 첫번째 파라미터엔 페이지에 렌더링할 내용을 jsx형태로 작성하고, 두 번째 파라미터엔 해당 jsx를 렌더링할 html 파일의 내부 요소를 설정한다.

![bg right:47% contain](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/df0b11ce-011a-4114-a659-1f3aafbd1c16/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220307T004108Z&X-Amz-Expires=86400&X-Amz-Signature=911b72445afabc130e471fee19cacd789eae5c0ba066d3077a56febbb14bbe04&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---

# export / import 란?

###### export: export 뒤에 함수, 변수 등을 붙여서 내보내면 외부 파일에서 import를 이용해 내보낸 함수, 변수 등을 이용할 수 있다.

###### import: import [함수, 변수명] from [경로] 를 사용하여 export로 내보낸 함수, 변수등을 사용할 수 있다.

![bg right:47% contain vertical](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b9f49f0f-72ff-4165-834f-4b5850b20d8d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220307T004824Z&X-Amz-Expires=86400&X-Amz-Signature=8b68971a4ff9b2f42b1b8a0fc197046c4c03b38b65139dbb963578aee7815f45&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)
![bg right contain](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/682628bf-73ac-4cf8-837d-7506c34b8978/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220307T004905Z&X-Amz-Expires=86400&X-Amz-Signature=f7cce29d0ec400557fd534f2488ac0d589e36574689541c5d91e607ee9a5dde2&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---

# src/App.js

<br />

> ###### import를 사용해 이미지, css파일을 가져오는것도 가능하다.

![bg right contain](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6a0806e4-4dcb-4eb9-a8bb-3bc1a56bc8f7/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220307T011934Z&X-Amz-Expires=86400&X-Amz-Signature=3cdf379c349a6c11efd697c5334f006d054621567f3710f7b49c11eb6bc40ba8&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---

# 감사합니다.
