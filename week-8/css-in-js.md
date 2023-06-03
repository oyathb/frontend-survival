# CSS in JS

### Design System

웹이나 각종 서비스 UI 디자인에서 재사용 가능한 컴포넌트와 패턴을 정의하여, 전체 디자인에 일관성 있게 적용할 수 있도록 만든 가이드라인이나 규칙

공유 언어와 시각적 일관성을 유지하면서 중복성을 줄여야 한다

Apple의 Human Interface Guidelines

[https://developer.apple.com/design/human-interface-guidelines](https://developer.apple.com/design/human-interface-guidelines)

#### responsive web design

하나의 웹사이트에서 PC, 스마트폰, 태블릿 PC 등 접속하는 디스플레이의 종류에 따라 화면의 크기가 자동으로 변하도록 만든 웹페이지 접근 기법

#### Atomic Design

모든 물질은 원자로 구성되어 있다는 화학적 관점에서 영감을 얻은 디자인 시스템

원자는 결합하여 분자가 되고 분자는 결합하여 더 복잡한 유기체가 됨

atom -> molecules -> organisms -> templates -> pages 단계 별로 추상적인 것을 구체화

atom : label, input, button 같은 더 이상 분해할 수 없는 기본 컴포넌트

### Style Basics

### CSS

Cascading Style Sheets

HTML, XHTML, XML 등의 마크업 언어가 실제 표시되는 방법을 기술하는 스타일 언어

#### className

CSS를 컴포넌트에 반영하기 위해 className=""으로 네이밍함

id="", class="" 같은 것을 사용하면 동일한 id일 경우 하나만 인식하기 때문에

중복을 피하기 위해 className을 사용해야 한다

#### inline style

CSS를 밖에서 따로 안 잡아도 됨

```
export default function FoodCourt() {

    const style = {
        color: '#00F',
    }
    return (
        <p style={style}>
        푸드코트 키오스크
        </p>
    )
}
```

#### HTML Elements 참고서

[https://developer.mozilla.org/ko/docs/Web/HTML/Element](https://developer.mozilla.org/ko/docs/Web/HTML/Element)

#### Selector

(나중에 찬찬히 공부하자 ..)

스타일을 지정할 웹 페이지의 HTML 요소를 대상으로 하는 데 사용

https://developer.mozilla.org/ko/docs/Learn/CSS/Building\_blocks/Selectors

### CSS in JS

말 그대로 CSS를 JS 안에서 사용하는 것. 스타일 정의를 CSS 파일이 아닌 JavaScript로 작성된 컴포넌트에 바로 삽입하는 스타일 기법

2014년 페이스북 개발자 Christopher Chedeau aka Vjeux가 처음 소개함

Global Namespace 등 CSS의 복잡한 문제를 해결하기 위해 등장함 (자세한 내용 https://www.samsungsds.com/kr/insights/web\_component.html 참고)

#### "Thinking in Components"

HTML + JS + CSS를 묶어서 하나의 JS 파일 안에서 컴포넌트 단위 개발을 가능

CSS를 구현하는 라이브러리는 styled-component, JSS, Emotion 등이 있음

#### styled-components

CSS-in-JS의 대표적인 인기 라이브러리

스타일이 적용된 컴포넌트를 쉽게 만들 수 있는 도구

JS에서 모든 걸 관리할 수 있어서 반응형 웹 만들 때 편리함

이런 식으로 쓸 수 있음

```
import styled from 'styled-components';

const Paragraph = styled.p`
color: #00F;
`;

export default function FoodCourt() {
  return (
    <Paragraph>
      푸드코트 키오스크
    </Paragraph>
  );
}
```

props 값을 받아서 다양한 스타일을 정의할 수 있음

ex) 버튼이 활성화되면 파란색 안 되면 빨간색

attrs도 props와 유사한데 inline style을 적용 가능

#### Reset CSS

CSS를 초기화하지 않으면 margin이 default임

동일한 CSS 스타일을 보여주기 위해 Reset CSS 해야 함

#### box-sizing

박스의 크기를 화면에 표시하는 방식을 변경하는 속성. 요소의 너비와 높이를 계산하는 방법을 지정

https://developer.mozilla.org/ko/docs/Web/CSS/box-sizing
