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



### React Element

* 리액트 앱을 구성하는 가장 작은 단위
* 컴포넌트의 구성 요소
* 화면에 표시할 내용을 기술

### Components

* UI를 재사용 가능한 개별적인 여러 조각으로 나눈 것
* props를 입력 받고 React Element를 출력한다
* Element ㄷ Component 개념이 어려웠는데 붕어빵 비유 보고 이해함
  * [🔗 잘 정리된 글](https://velog.io/@sjmh0507/React-%EC%99%84%EC%A0%84-%EC%A4%91%EC%9A%94%ED%95%9C-Components%EC%99%80-Props-%EA%B0%9C%EB%85%90)
  * Component는 붕어빵 **틀**
  * Element는 틀로찍어낸 **붕어빵**
  * props는 속재료 **팥 슈크림** 등등
