# TypeScript

🔲 What is TypeScript?

Microsoft가 개발한 JS의 상위 언어

정적 타입을 명시할 수 있는 것이 JS와의 차이점

2023년 3월 PyPL 인기 프로그래밍 랭킹 언어 8위 ..



왜 쓰는가?

객체지향 프로그래밍 가능

모듈성 있는 코드 개발하기 좋음 (정처기 공부할 때 맨날 couping 낮게 cohension 높게 외웠는데&#x20;

타입을 명시하기 때문에 눈에 잘 들어옴

아샬님은 비쥬얼스튜디오에서 너무 편하다고 함



🔲 ts-node

간단히 REPL 쓸 수 있음

REPL? Read-Eval-Print-Loop&#x20;

* 사용자가 입력한 명령어(소스코드)를 읽고(Read) 평가하고(Eval) 출력하고(Print) 다음 입력을 대기하는 상태로 돌아가는 과정을 반복(Loop)
* 간단한 테스트, 소스코드 결과를 빨리 확인해야 할 때 사용

```
npx ts-node

// 나는 종료하려면 .exit 만 되는 듯??..
```

npm 설치된 패키지 list 보기

```
npm list -g
```



## 타입 지정

defining types



🔲 interface vs type ?

{% embed url="https://www.typescriptlang.org/ko/docs/handbook/2/everyday-types.html#%ED%83%80%EC%9E%85-%EB%B3%84%EC%B9%AD%EA%B3%BC-%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90" %}

한줄요약) interface 확장성이 더 좋음

매뉴얼은 interface 사용 권고 / 강의는 type 사용



이거는 코딩하면서 많이 해 봐야 익숙해질 듯





## 타입 추론

변수 선언 할 때 타입을 안 써도 컴파일러가 스스로 알아냄



## Union Type

or

```
// Some code
function fetchProducts({ category }: { category: Category }) {
  console.log(`Fetch ${category}`);
}
```

레거시 환경 또는 코드 때문에 안 쓸 수가 없다 reactnode가 대표적

undefined <- 어려움



## Intersection

and. 타입 확장

