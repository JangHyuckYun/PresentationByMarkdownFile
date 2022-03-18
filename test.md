---

theme: gaia
_class: lead
paginate: true
marp: true 

---

# 리액트 컴포넌트 생명주기

###### 기술연구소 윤장혁

---

# 목차

1. 사전지식
    1. class
    2. 객체, 배열 구조 분해 할당이란
2. 리액트 컴포넌트 생명주기

---

# 1. Javascript의 class

Java, C++ 등에 잇는 클래스를 사용한 문법에 익숙한 프로그래머들의 좀 더 빠른 학습을 도와주기 위해 도입된 ES6 문법.
<br />
<br />
<br />
> ###### ES6란? "ECMAScript6 or ES2015"를 줄인말로 모든 브라우저에서 사용되는 javascript의 문법(사용 규칙) 표준화?

---

```javascript

class App {
    name = "";

    constructor(name) { // 생성될 때 실행되는 함수
        this.name = name;
    }

    get name() {
        return this.name;
    }

    set name(name) {
        // app.name = value를 실행할때 실행되는 코드
        this.name = name;
    }
}

const app = new App("hello");
console.log(app.name); // result: "hello"

```

---

## 1-1. extends와 super

```javascript
class Animal {
    constructor(height, weight) {
        this.height = height;
        this.weight = weight;
    }
}

class Bird extends Animal {
    constructor(height, weight, color) {
        super(height, weight);
        this.color = color;
    }
}

const bird = new Bird(3, 6, 'blue');
console.log(bird.height, bird.color); // result: 3, 'blue'
```

---

# 2. 배열, 객체 구조분해 할당

MDN 정의에 따르면 **배열이나 객체의 속성을 해체하여 그 값을 개별 변수에 담을 수 있게 하는 Javascript 표현식**이라고 나와있다.

--- 

## 2-1. 배열 구조분해 할당

```javascript
const word_arr = ["Apple", "Banana", "Orange"];

const [apple, banana, orange] = word_arr;

console.log(apple, banana, orange); // result: "Apple", "Banana", "Orange" 
```

---

## 2-2. 객체 구조분해 할당

```javascript
const word_object = {
    "apple": "Apple",
    "banana": "Banana",
    "orange": ["BlackOrange", "RedOrange"]
};

const { apple, banana, orange } = word_object;

console.log(apple, banana, orange); // result: "Apple", "Banana", ["BlackOrange", "RedOrange"] 
```

---

# 3. 리액트 컴포넌트 생명주기

`컴포넌트 생명주기(lifecycle)`란 컴포넌트가 페이지 렌더링 되기 위해 준비하는 과정부터 제거될 때까지의 기간을 뜻한다.
클래스형 컴포넌트는 이러한 생명주기 중 특정 시점에 대해 원하는 구문을 실행할 수 있도록 `생명주기 메서드`를 지원한다.

![w:1150px](./images/component_render_tree.png)

---



