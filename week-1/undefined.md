---
description: 강의 자료와 같이 순서대로 진행하면 개발 환경 세팅 되게
---

# Development Environment

## JavaScript

### 🔳 install Node.js

> JavaScript로
>
> 브라우저 밖에서
>
> [서버](https://namu.wiki/w/%EC%84%9C%EB%B2%84)를 구축하는 등의 코드를 실행할 수 있게 해주는 런타임 환경

Node.js 쓰는 이유?

* JS
* asynchronous I/O - 하나의 이벤트가 완료되지 않아도 다음 이벤트를 처리할 수 있는 방식
  * 대용량의 I/O를 처리해야 하는 서비스에 적합
* NPM
  * Node.js 관련 패키지를 관리하는 툴
  * 사용하려는 대부분의 모듈이 등록되어 있음

```
// mac terminal에서
brew install node
```

version 확인

```
node -v
```

23.04.11 기준 v19.8.1



### 🔳 install fnm

> Fast and simple _Node.js version manager_, built in Rust

```
brew install fnm
```



## TypeScript

### 🔳 install visual studio code

```
brew install visual-studio-code
```



### 🔳 작업 폴더 생성

```
mkdir my-app
cd my-app
```



### 🔳 npm 패키지

Node.js 관련 패키지를 관리할 수 있는 툴 (설치 삭제 업데이트 등)

```
// vsc terminal에서
npm init -y
```



### 🔳 .gitignore 파일 생성

* **git에 업로드 되지 않아야 하는 파일**
* 최소 node\_modules, dist 는 있어야 됨

```
touch .gitignore
```

🔗 복붙 (Raw 클릭하면 더 편함)

{% embed url="https://github.com/github/gitignore/blob/main/Node.gitignore" %}



### 🔳 install TypeScript

```
npm i -D typescript
```

tsconfig.json 생성

```
npx tsc --init
```

#### tsconfig.json

* tsconfig.json 파일이 있는 디렉토리는 TypeScript 프로젝트의 루트가 됨
* 프로젝트를 컴파일하는 데에 필요한 루트 파일과 컴파일러 옵션 설정

#### NPX

* npm의 일부분으로 패키지를 디렉토리에 설치하지 않고 실행
* npm으로 run하는 것보다 빠르고 메모리도 덜 먹음

tsconfig.json 수정

jsx 찾아서 주석 삭제

```jsonc
"jsx": "preserve",
```

#### JSX (JavsScript eXtension)

{% embed url="https://ko.reactjs.org/docs/introducing-jsx.html" %}

* React에서 HTML을 표현할 때 사용하는 JS 확장 문법
  * JS 코드로 HTML을 표현할 수 있음
* JavaScript 코드 안에서 UI 관련 작업을 할 때 시각적으로 더 도움이 됨&#x20;



### 🔳 install ESLint

JS는 동적분석이기에 코드를 실행해야 오류를 알 수 있음 따라서 정적분석도구 ESLint 사용

```
npm i -D eslint
```

```
npx eslint --init
```

세부 설정 하고

.eslintrc.js 수정

```javascript
// 
browser: true,
es2021: true,
jest: true //추가. jest 설치 전이지만 미리 설정
```



### 🔳 테스팅 도구 설치

```
npm i -D jest @types/jest @swc/core @swc/jest
jest-environment-jsdom
@testing-library/react @testing-library/jest-dom
```

jest와 swc를 같이 쓰는 것이 목표라는 것을 기억해 두자

#### @swc/core

🔗 참고

{% embed url="https://www.npmjs.com/package/@swc/core" %}

#### @swc/jest

> To make your Jest tests run faster, you can swap out the default JavaScript-based runner (`ts-jest`) for a [drop-in Rust replacement(opens in a new tab)](https://github.com/swc-project/jest) using SWC.

🔗 참고

{% embed url="https://swc.rs/docs/usage/jest" %}

swc로 빌드하기 위해 jest.config.js 생성

```
touch jest.config.js
```

🔗 복붙

{% embed url="https://github.com/ahastudio/CodingLife/blob/main/20220726/react/jest.config.js" %}

안쓰는거삭제

```javascript
'./jest.setup'
```

만약에<mark style="color:red;">빨간줄</mark>생기면??

```
npx eslint --fix .
```



### 🔳 install parcel

> 불꽃 튀게 빠르고 설정이 필요 없는 웹 애플리케이션 번들러(의존성이 있는 모듈을 묶어줌)

index.html 파일의 변화를 자동으로 반영

```
npm i -D parcel
```

🔗 참고

{% embed url="https://ko.parceljs.org/typeScript.html" %}



### 🔳 package.json 수정

```
"scripts": {
    "start": "parcel --port 8080",
    "build": "parcel build",
    "check": "tsc --noEmit",
    "lint": "eslint --fix --ext .js,.jsx,.ts,.tsx .",
    "test": "jest",
    "coverage": "jest --coverage --coverage-reporters html",
    "watch:test": "jest --watchAll"
  },
```

🔗 복붙

{% embed url="https://github.com/ahastudio/CodingLife/blob/main/20220726/react/package.json" %}

<mark style="color:red;">빨간줄</mark>수정하는다른방법

\--fix가 lint 안에 있어서 npx eslint --fix 하지 않아도&#x20;

```
npm run lint
```

로 가능



### 여기까지 개발 환경 세팅 완료

### 🔳 port 8080 열어 보기

index.html 생성

```
touch index.html
```

package.json 수정

```
"main": "index.js",
⬇️
"source": "index.html",
```

index.html

```
<!DOCTYPE html>
<html lang = "ko">
    <head>
        <meta charset = "UTF-8">
        <title>react demo app</title>
    </head>
    <body>
        <p>hello world</p>
    </body>
</html>
```



## ERROR

코딩 중 뜬 에러



▪️ **save 수시로**

package.json 파일 수정하고 save 안 하니까

Missing script: "start" 에러 뜸



▪️ npm run start 하는데 갑자기 Error: Port "8080" could not be used 뜸

서치해 보니 다른 프로세스나 프로그램이 port를 점유하고 있기 때문이라 함 (갑자기?)

해결법

```
lsof -i tcp:8080
// lsof : Mac에서 사용 중인 port 찾는 명령어
```

COMMAND PID USER 등이 순서대로 뜨는데

```
// kill -9 명령어로 해당 프로세스 종료
sudo kill -9 [PID숫자]
```



&#x20;
