# Mocking, MSW, and Playwright

### Mocking

mock = 가짜의, 임의의 라는 뜻

단어 그대로 테스트하는 코드가 의존하는 class나 function을 일부만 가져와서 가짜로 만드는 것

실제 데이터베이스에서 불러오는 것은 너무 부담이 크기 때문에 (테스트는 기본적으로 외부 요인을 줄이는 것이 좋음)

일단 컨트롤러 작동 여부만 확인하기 위해 가짜를 만들어 테스트 한다

`App.tsx`

```App.tsx
export default function App() {
  const restaurants = useFetchRestaurants();

  return (
    <>
      <TimerControl />
      <hr />
      <p>오늘의 메뉴</p>
      <FilterableProductTable lorr={restaurants} />
    </>
  );
}
```

`App.test.ts`

```App.test.ts
jest.mock('./hooks/useFetchRestaurants', () => () => {
  return [
    {
      "id": "1",
      "category": "중식",
      "name": "메가반점",
      "menu": [
        {"id": "1", "name": "짜장면", "price": 8000},
        {"id": "2", "name": "짬뽕", "price": 8888},
        {"id": "3", "name": "차돌짬뽕", "price": 9000},
        {"id": "4", "name": "탕수육", "price": 14000}
      ]
    },
  ];
});

test('App', () => {
  // when
  render(<App />);

  // then
  screen.getByText('짜장면');
});
```

mocking 없이 App을 render() 하면 실패한다

App은 useFetchRestaurants() 함수에 의존성이 있기 때문이다

따라서 useFetchRestaurants()를 mocking 해야 한다

#### Mocking Method

`jest.mock()` 모듈 전체를 mocking 할 때 사용

`jest.fn()` 개별적으로 mocking 할 때 사용

참고

[🔗https://inpa.tistory.com/entry/JEST-%F0%9F%93%9A-%EB%AA%A8%ED%82%B9-mocking-jestfn-jestspyOn](https://inpa.tistory.com/entry/JEST-%F0%9F%93%9A-%EB%AA%A8%ED%82%B9-mocking-jestfn-jestspyOn)

#### Fixtures

원활한 테스트를 위해 변경되지 않는 데이터를 따로 빼 두는 것

mocking 할 때 불러올 데이터가 방대하면 버거우니까 데이터만 extract 하는 개념이라고 이해함

```App.test.tsx
import fixtures from '../fixtures';

jest.mock('./hooks/useFetchRestaurants', () => () => fixtures.restaurants);
```

#### MSW

Mock Service Worker

network level에서 mock을 구현하는 도구 ( jest.mock() 사용하지 않아도 됨)

MSW는 API 요청을 가로채서 (intercepting requests) 원래 데이터를 mock 데이터로 바꾼다

`App.test.ts`

```App.test.ts
test('App', async () => {
  // when
  render(<App />);

  // then
  await waitFor(() => {
    screen.getByText('짬뽕');
  });
});
```

App을 render() 하면 MSW가 바꾼 mock 데이터 값이 입력되어 랜더링 되는 개념이라고 이해함

`handlers.ts` 원래 데이터 -> mock 데이터 바꾸는 작업 하는 파일

```handlers.ts
import { rest } from 'msw';

const BASE_URL = 'http://localhost:3000';

const handlers = [
  rest.get(`${BASE_URL}/restaurants`, (req, res, ctx) => {
    const restaurants = [
      {
        id: '1',
        category: '중식',
        name: '메가반점',
        menu: [
          { id: '1', name: '짜장면', price: 8000 },
          { id: '2', name: '짬뽕', price: 8888 },
          { id: '3', name: '차돌짬뽕', price: 9000 },
          { id: '4', name: '탕수육', price: 14000 },
        ],
      },
    ];

    return res(
      ctx.json({ restaurants }),
    );
  }),
];

export default handlers;
```

handlers에서 한 번에 관리하기 때문에 재사용이 용이하다

**fetch polyfill**

Fetch API 가 비교적 최신기술이기 때문에 지원되지 않는 브라우저가 있음

그래서 fetch polyfill을 설치하여 해결

#### Playwright

MS에서 만든 웹 브라우저 기반 E2E 테스트 및 자동화 프레임워크

단일 API로 크롬 파이어폭스 웹킷에서 테스트 할 수 있다

**E2E Testing**

End-to-End 테스트의 약자

애플리케이션의 흐름을 처음부터 끝까지 테스트하는 것

```home.spec.ts
test('Filter products', async ({ page }) => {
  await page.goto('/');

  await expect(page.getByText('탕수육')).toBeVisible();

  const searchInput = page.getByLabel('검색');

  await searchInput.fill('메');

  await expect(page.getByText('메가반점')).toBeVisible();

  await searchInput.fill('aa');

  await expect(page.getByText('메가반점')).toBeHidden();
});
```

화면에 '탕수육' 뜨는지 확인하고 '메' 입력하면 '메가반점' 뜨는지 확인한다

과제 제출 전 테스트하는 게 이거였다..!
