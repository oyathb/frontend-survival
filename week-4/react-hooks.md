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
* 무한루프 방지하기 위해 두 번째 매개변수로 의존성 배열 줌
  * 한 번만 실행할 경우 빈 배열 \[]

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
