# Page 1

### Routing

#### DOM

브라우저가 화면을 그릴 때 필요한 정보가 트리 형태로 저장된 데이터

XML, HTML 문서의 각 항목을 계층으로 표현하여 생성, 변형, 삭제할 수 있도록 돕는 인터페이스

객체를 트리 구조로 표현

HTML문서를 브라우저가 이해할 수 있도록 만든 Tree 자료구조

#### HTML DOM API

https://developer.mozilla.org/en-US/docs/Web/API/HTML\_DOM\_API

HTML 의 각 요소 의 기능을 정의하는 인터페이스 와 이들이 의존하는 지원 유형 및 인터페이스 로 구성

**location**

Location 인터페이스는 객체가 연결된 장소(URL)를 표현

<figure><img src="../.gitbook/assets/스크린샷 2023-06-12 오전 11.05.14.png" alt=""><figcaption></figcaption></figure>

### Routes

#### Router

#### React Router

여러 화면으로 구성된 웹 어플리케이션을 만드는 데 사용

리액트의 라우팅 관련 라이브러리들 중에서 가장 오래됐고, 가장 많이 사용되고 있음

컴포넌트 기반으로 라우팅 시스템을 설정할 수 있음

**주로 사용되는 컴포넌트**

**Broswer Router**

페이지를 새로고침하지 않고도 주소를 변경할 수 있도록 해줌 (HTML5 History API 사용)

현재 주소에 관련된 정보를 props로 조회 및 사용이 가능하도록 함

**Memory Router**

위치를 내부적으로 저장하는 라우터 (메모리에 주소 알려줌)

테스팅 할 때 사용하기 적합

브라우저의 주소와 무관, 일체 건들이지 않음

테스트 환경, 임베디드 웹앱, 리액트 네이티브 등에서 사용

### ReactRouter - RouterProvider

React Router 버전 6.4부터 지원

기존 방식처럼 Browser Router로 감싸지 않고 RouterProvider를 사용하여 구성요소를 전달

### Navigation

#### Web APIs - History

브라우저의 세션 기록 스택에 상태를 추가

#### Link

페이지를 이동하고 싶을 때 Link 컴포넌트를 사용

브라우저의 주소만 바뀔 뿐, 페이지를 새로 불러오지는 않음

#### NavLink

special version of the

특정 링크에 스타일을 넣을 수 있다

#### useNavigate

link와 같이 페이지를 이동하는 개념이나

특정 이벤트가 실행됐을 때 동작하도록 하거나 추가적인 로직이 필요한 경우 사용한다
