---

paginate: true
marp: true
theme: my-theme

---


# 3. 리액트 컴포넌트 생명주기

`컴포넌트 생명주기(lifecycle)`란 컴포넌트가 페이지 렌더링 되기 위해 준비하는 과정부터 제거될 때까지의 기간을 뜻한다.
클래스형 컴포넌트는 이러한 생명주기 중 특정 시점에 대해 원하는 구문을 실행할 수 있도록 `생명주기 메서드`를 지원한다.

<br />
<br />
<br />

> 컴포넌트 작성 방식엔 **클래스**, **Hook** 으로 나뉘어진다.
> Hook? function(함수)의 형태로 만들어진 컴포넌트로 클래스 형태의 컴포넌트 작성시 불편한것들을 보완한 형태.
> ex) function H1() { return (<h1>hi</h1>); }


---

## 3.1 컴포넌트 생명주기 공부 이유

- 어디에 어떤 코드를 정확히 넣어야 하는지 알기 위해서
   - ex) "API 불러올 코드 작성 위치", "컴포넌트 생성 전·후에 특정 값 추가하려 할 때"
- 리액트 특징중 하나가 "컴포넌트 방식으로 작성하는것"인데 이 컴포넌트의 생명주기는 그래도 알아야 하지 않을까..

---

![w:1150px](./images/component_render_tree.png)

---

## Mounting(생성 될 때)

1. constructor()
2. getDerivedStateFromProps() // render() 함수 호출 직전 실행되는 함수
3. render()
4. componentDidMount()

---

### constructor()
