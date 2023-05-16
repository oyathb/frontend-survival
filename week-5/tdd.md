# TDD

### TDD

* Test Driven Development 테스트 주도 개발
* 구현하려는 기능의 테스트 케이스를 먼저 작성하고 이 테스트를 통과하도록 실제 코드(프로덕션 코드)를 작성하는 것
* 프로덕션 코드를 리팩토링 하며 다듬는 과정 반복

#### TDD Cycle

TDD는 Red(실패) Green(성공) Refactoring(리팩토링) 3단계 과정 반복

<figure><img src="../.gitbook/assets/627938f23cc6dc07b69e22a7_test-driven-development-tdd-cycle.jpeg" alt=""><figcaption><p>출처 <a href="https://brainhub.eu/library/test-driven-development-tdd">https://brainhub.eu/library/test-driven-development-tdd</a></p></figcaption></figure>

(1) Red : 실패하는 테스트 코드 작성. 실패하는 테스트 코드라는 말이 잘 이해 안 됐는데 .. 그냥 프로덕션 코드를 작성하지 않아 실패하는 것

```sample.test.ts
test('add', () => {
    expect(add(1, 2)).toBe(3);
});
```

add 함수가 정의되지 않았으니 당연히 실패함

(2) Green : 테스트를 통과하는 프로덕션 코드 작성. 이상한 코드여도 됨 통과하는 게 우선. 켄트백피셜 어떤 죄악을 저질러도 좋다

```sample.test.ts
function add(x: number, y: number): number {
    return x + y;
}
```

(3) Refactoring : 2번에서 탄생한 이상한 코드에 중복 제거, 일반화 등의 리팩토링 작업을 통해 깔끔한 코드로 변화시킨다

!! 리팩토링으로 프로덕션 코드는 바뀌지만 동작은 바뀌지 않는 것이 중요 !!

테스트가 실패할 때만 프로덕션 코드를 변경해야 한다

그 외에는 리팩토링으로 다듬는다
