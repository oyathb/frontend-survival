# React Hooks

### React Hooks

[🔗Hook 소개](https://ko.legacy.reactjs.org/docs/hooks-intro.html#motivation)

* class를 작성하지 않고도 state와 다른 React의 기능들을 사용할 수 있게 하는 라이브러리
  * 원래 Function Component는 리랜더링 되면 주어졌던 state를 기억 못함
  * Hook은 메모리를 할당하여 Function Component가 state를 기억할 수 있게 해줌
  * 앞으로 Function Component만 사용하겠다
* React 16.8 에서 도입
* Hook을 개발한 이유?
  * 컴포넌트 사이에서 상태 로직 재사용이 어려움 (render props, HOC)
  * 복잡하게 엉킨 컴포넌트 (
  * Class 개념 자체가 헷갈릴 때가 있음 .. 사람도 컴퓨터도
* 기본 Hook
  * useState
  * useEffect
  * useContext

### useEffect

* 컴포넌트가 랜더링 될 때마다 특정 작업을 실행할 수 있도록 하는 Hook
* 리액트 외부의 시스템과 동기화 가능
* 무한루프 방지하기 위해 두 번째 매개변수로 의존성 배열 줌
  * 처음 한 번만 실행할 경우 빈 배열 \[]

fetch 함수를 useEffect 안에서 사용하면 좋다

```App.tsx
const [restaurants, setRestaurants] = useState([]);

  useEffect(() => {
    console.log('!')
    
    // useEffect로 한 번만 fetch
    const fetchRestaurants = async () => {
      const url = 'http://localhost:3000/restaurants';

      const response = await fetch(url);

      const data = await response.json();

      // const { restaurants } = data;

      setRestaurants(data.restaurants);

      console.log(data.restaurants);
    };

    fetchRestaurants();
  }, []); // 의존성배열
```

### React StrictMode

[🔗Strict 모드](https://ko.legacy.reactjs.org/docs/strict-mode.html)

* 애플리케이션 내의 잠재적인 문제를 알아내기 위한 도구
* console.log() 찍으면 2번씩 나옴
* 개발할때만작동

```main.tsx
root.render(
    <React.StrictMode>
      <App />
    </React.StrictMode>
  );
```

### useRef

* Ref = Reference 참조
* .current 프로퍼티로 전달된 인자(initialValue)로 초기화된 변경 가능한 ref 객체를 반환
* 반환된 객체는 컴포넌트의 전 생애주기를 통해 유지
* useState랑 무슨 차이?
  * useState는 상태가 변경되면 본인과 하위 컴포넌트를 리랜더링 함
  * but useRef는 current 값이 변해도 리랜더링 하지 않음. 다른 거 리랜더링 되면 그 때 한 번에 반영됨
* 특정 DOM을 선택해야 할 때도 사용한다고 함 <- 이 부분은 나중에 찾아보자 ..
* 글만 읽으면 좀 뭔소리야 싶은데 강의 예시 보면 잘 이해됨

### Custom Hook

* 재사용이 용이하게 Extract Function 하는 것
* camelCase로 작명 (컴포넌트는 PascalCase)
* extract한 Hook을 사용할 때 Hook의 규칙을 지켜야 함
  * [🔗Hook의 규칙](https://ko.legacy.reactjs.org/docs/hooks-rules.html)
  * 최상위(at the Top Level)에서만 호출. 반복문 조건문 중첩함수 X
  * 오직 React 함수 내에서만 호출

### usehooks-ts

[🔗usehooks-ts](https://usehooks-ts.com/)

* React Hooks을 더 간단하고 명확하게 사용할 수 있다
* 다양한 종류가 있지만 특히 useBoolean과 useFetch가 유용해 보임

useBoolean

```TimerControl.tsx
const { value: playing, toggle } = useBoolean();

  const handleClick = () => {
    toggle();
  };
  
  // const [playing, setPlaying] = useState(false);

  // const handleClick = () => {
  //   setPlaying(!playing);
  // };
```
