# TDD

### TDD

Test Driven Development 테스트 주도 개발

구현하려는 기능의 테스트 케이스를 먼저 작성하고 이 테스트를 통과하도록 실제 코드(프로덕션 코드)를 작성하는 것

프로덕션 코드를 리팩토링 하며 다듬는 과정 반복

#### TDD Cycle

TDD는 Red(실패) Green(성공) Refactoring 3단계 과정 반복

(1) `Red` 실패하는 테스트 코드 작성. 실패하는 테스트 코드라는 말이 잘 이해 안 됐는데 .. 그냥 프로덕션 코드를 작성하지 않아 실패하는 것

```sample.test.ts
test('add', () => {
    expect(add(1, 2)).toBe(3);
});
```

add 함수가 정의되지 않았으니 당연히 실패함

(2) `Green` 테스트를 통과하는 프로덕션 코드 작성. 이상한 코드여도 됨 통과하는 게 우선. 켄트백피셜 어떤 죄악을 저질러도 좋다

```sample.test.ts
function add(x: number, y: number): number {
    return x + y;
}
```

(3) `Refactoring` 2번에서 탄생한 이상한 코드에 중복 제거, 일반화 등의 리팩토링 작업을 통해 깔끔한 코드로 변화시킨다

!! 리팩토링으로 프로덕션 코드는 바뀌지만 동작은 바뀌지 않는 것이 중요 !!

테스트가 실패할 때만 프로덕션 코드를 변경해야 하고

테스트 결과가 이상 없으면 리팩토링으로 다듬는다

#### TDD를 해야 하는 이유

* "작동하는 깨끗한 코드를 작성하는 것" 이 목표
* 요구사항을 더 확실히 이해할 수 있다
* 수시로 작성한 코드를 검증하여 오류를 빨리 찾아낼 수 있다
* 작성한 코드에 자신감을 가질 수 있다
* 자유롭게 리팩토링 가능. TDD를 하면 코드 수정 결과를 외부에서 확인 안 해도 되니까 안정성이 높아지고 개발자도 코드 수정을 덜 주저하게 된다
* 개발 및 테스팅 시간과 비용 절감
* 소프트웨어 품질 향상
* 나중에 테스트 작성하기 귀찮음

#### Unit Test 단위 테스트

컴퓨터 프로그래밍에서 소스 코드의 특정 모듈이 의도된 대로 정확히 작동하는지 검증하는 절차

실패하는 단위 테스트를 작성하는 것이 TDD의 첫 단계

참고

[🔗https://brainhub.eu/library/test-driven-development-tdd](https://brainhub.eu/library/test-driven-development-tdd)

[🔗https://hudi.blog/test-driven-development/](https://hudi.blog/test-driven-development/)
