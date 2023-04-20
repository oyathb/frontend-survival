# week 2

## asdf



### JSX



* JavaScript Syntax eXtension
* 경우에 따라 JavaScript XML 이라고도 함
* React에서 JavaScript로 HTML을 쓰는 것처럼 쓸 수 있음
  * JSX의 syntax가 XML/HTML과 비슷
  * 따라서 편하고 가독성이 좋음 (Syntactic sugar, React는 JSX 사용이 필수가 아니지만 이런 장점이 굳)
* JSX는 브라우저가 실행할 수 없음
* 따라서 브라우저가 이해할 수 있는 JavaScript 코드로 변환해주어야 함
* Babel : JavaScript Transfiler
* **한줄요약) JSX는 편하지만 Babel으로 React.createElement로 변환해야 브라우저에서 실행 가능**



#### 💎 교재) Babel에서 변환해 보기



JSX 코드

```
<p>Hello, world!</p>
```

변환된 JS 코드

```
import { jsx as _jsx } from "react/jsx-runtime";
/*#__PURE__*/_jsx("p", {
  children: "Hello, world!"
});
```



강의자료에는 React.createElement 로 변환 되는데\
나는 \_jsx 로 나옴\
이유는 잘 모르겠지만..

#### \_jsx

* React 17부터 도입된 JSX Transform의 새로운 방식
  * [🔗 Introducing the New JSX Transform](https://ko.reactjs.org/blog/2020/09/22/introducing-the-new-jsx-transform.html)
* JSX를 사용할 경우 React가 범위 안에 있어야 하는 것 때문에 개선됨 (React needed to be in scope if you used JSX)
  * import React from 'react'; 를 꼭 써야 하는 것
* 그리고 성능 향상과 단순화가 되었다 함 (There are some performance improvements and simplifications that React.createElement does not allow.)



```
<div className="test">
 <p>Hello, world!</p>
 <Button type="submit">Send</Button>
</div>
```

```
import { jsx as _jsx } from "react/jsx-runtime";
import { jsxs as _jsxs } from "react/jsx-runtime";
/*#__PURE__*/_jsxs("div", {
  className: "test",
  children: [/*#__PURE__*/_jsx("p", {
    children: "Hello, world!"
  }), /*#__PURE__*/_jsx(Button, {
    type: "submit",
    children: "Send"
  })]
});
```

```
<div>
 <p>Count: {count}!</p>
 <button type="button" onClick={() => setCount(count + 1)}>Increase</button>
</div>
```

```
import { jsxs as _jsxs } from "react/jsx-runtime";
import { jsx as _jsx } from "react/jsx-runtime";
/*#__PURE__*/_jsxs("div", {
  children: [/*#__PURE__*/_jsxs("p", {
    children: ["Count: ", count, "!"]
  }), /*#__PURE__*/_jsx("button", {
    type: "button",
    onClick: () => setCount(count + 1),
    children: "Increase"
  })]
});
```



### React.createElement

* JSX는 XML/HTML 부분을 React.createElement를 써서 변환해야 한다
  * JSX는 React.createELement의 Syntatic Sugar
* 만약 JSX를 안 쓴다면? 그냥 내가 React.createElement 호출해서 작성하면 됨
  * 굳이? 싶긴 한데 공식 사이트는 컴파일(트랜스파일) 설정하기 싫을 때 이렇게 하라고 함
* 구성 요소
  * createElement(type, props, ...children)

```
React.createElement(
 type
 [props]
 [...children]
);
```



### React Architecture

<figure><img src=".gitbook/assets/react-architecture.jpeg" alt=""><figcaption><p>React Architecture</p></figcaption></figure>

[🔗 이미지 출처](https://jsforall.com/reactjs/how-to-create-react-app-2019-how-virtual-dom-component-work/)



JSX를 변환한 JavaScript file

\= React Element

\= Virtual DOM Tree의 Node

\= DOM의 객체

라고 이해함



### React Element

* 리액트 앱을 구성하는 가장 작은 단위
* 컴포넌트의 구성 요소
* 화면에 표시할 내용을 기술

### Components

* 재사용할 수 있는 UI 단위
* props를 입력 받고 React Element를 출력한다
* Element ㄷ Component 개념이 어려웠는데 붕어빵 비유 보고 이해함
  * [🔗 잘 정리된 글](https://velog.io/@sjmh0507/React-%EC%99%84%EC%A0%84-%EC%A4%91%EC%9A%94%ED%95%9C-Components%EC%99%80-Props-%EA%B0%9C%EB%85%90)
  * Component는 붕어빵 **틀**
  * Element는 틀로찍어낸 **붕어빵**
  * props는 속재료 **팥 슈크림** 등등



### DOM

[🔗 잘 정리된 글](https://ko.javascript.info/dom-nodes)

* Document Object Model (문서 객체 모델)
* 브라우저가 화면을 그릴 때 필요한 정보가 트리 형태로 저장된 데이터
  * XML, HTML 문서의 각 항목을 계층으로 표현하여 생성, 변형, 삭제할 수 있도록 돕는 인터페이스
  * 객체를 트리 구조로 표현
* 객체는 JavaScript를 통해 접근 가능
* DOM은 JavaScript와 HTML 사이에 위치한다고 이해함



### Virtual DOM

* 말 그대로 가상 DOM으로 Real DOM의 복사본 같은 개념
* UI의 이상적인 또는 “가상”적인 표현을 메모리에 저장하고 ReactDOM과 같은 라이브러리에 의해 “실제” DOM과 동기화하는 프로그래밍 개념
  * 모든 변경 사항은 Virtual DOM에 먼저 반영됨
  * Virtual DOM과 Real DOM을 비교하여 변경된 부분이 있다면 Real DOM에 적용함
  * 이러한 방식은 React의 선언적 API를 가능하게 함
* 왜 사용할까?
  * Real DOM으로 많은 작업을 처리하면 느리기 때문
  * 이라고 생각하지만 유지보수가 용이한 것이 진짜 장점



#### 선언형 API

* 애플리케이션의 각 상태에 대한 간단한 뷰만 설계하면
* 데이터가 변경됨에 따라 적절한 컴포넌트만 효율적으로 갱신하고 렌더링
* 즉 JSX로 구조만 설계하면 React가 Virtual DOM으로 변경된 부분을 찾아서 Real DOM을 업데이트 함
  * JavaScript로 UI 만드는 것보다 쉬움



| Imperative Programming  | Declarative Programming       |
| ----------------------- | ----------------------------- |
| 절차(How)에 중점             | 무엇(What)을 원하는지에 중점            |
| 어떤 방법으로 나타내야 하는지 일일히 기술 | 무엇을 나타내야 하는지에만 집중             |
| JavaScript가 직접 DOM 조작   | JavaScript가 DOM 조작을 React에 위임 |



#### ReactDOM

* UI를 브라우저에 렌더링 할 때 사용하는 라이브러리
