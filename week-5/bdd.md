# BDD

### BDD

Behavior Driven Development 행위 주도 개발

서비스 사용자의 행위에 더 중심을 두고 테스트 코드를 설계한다

이름에서 알 수 있 듯이 TDD에서 파생된 개발 방법이다

TDD를 더 쉽게 하기 위한 것

#### Describe - Context - It 패턴

코드의 행동을 설명하는 테스트 코드 작성 방식

`Describe` 설명할 대상을 명시. 테스트 대상인 class, method

`Context` 테스트 대상이 놓인 상황을 설명. 테스트 할 메서드에 입력할 파라미터

`It` 테스트 대상의 행동을 설명. 테스트 할 메서드가 무엇을 리턴하는가

```TestField.test.tsx
describe('TextField', () => {
  function renderTextField() {
    render((
      <TextField
        label={label}
        placeholder={placeholder}
        filterText={filtertext}
        setFilterText={setFilterText}
      />
    ));
  }

  context('when user types name', () => {
    it('calls "setFilterText" handler', () => {
      // given
      renderTextField();

      // when
      fireEvent.change(screen.getByLabelText(label), {
        target: { value: 'hello' },
      });

      // then
      expect(setFilterText).toBeCalledWith('hello');
    });
  });
});
```

* TextField 클래스는
  * user가 name을 입력하면
    * setFilterText 함수를 리턴한다

테스트 결과가 계층 구조로 출력되어 무엇을 테스트했는지가 깔끔하게 나타난다

참고

[🔗https://johngrib.github.io/wiki/junit5-nested/](https://johngrib.github.io/wiki/junit5-nested/)

#### given - when - then 패턴

준비 - 실행 - 검증

테스트 코드 작성 방식

**when에서 실행한 것을 then에서 검증**

`given` 테스트 대상에게 주어진 조건

`when` 테스트 대상이 실행할 것

`then` 실행한 것을 검증

```TestField.test.tsx
describe('TextField', () => {
  function renderTextField() {
    render((
      <TextField
        label={label}
        placeholder={placeholder}
        filterText={filtertext}
        setFilterText={setFilterText}
      />
    ));
  }

  context('when user types name', () => {
    it('calls "setFilterText" handler', () => {
      // given
      renderTextField();

      // when
      fireEvent.change(screen.getByLabelText(label), {
        target: { value: 'hello' },
      });

      // then
      expect(setFilterText).toBeCalledWith('hello');
    });
  });
});
```

given) TextField를 랜더링한다

when) screen.getByLabelText(label)로 랜더링된 TextFIeld를 불러와 fireEvent 함수를 사용하여 setFilterText의 value 값에 'hello'를 입력한다

then) setFilterText가 'hello'를 입력값으로 가지고 있는지 검증한다
