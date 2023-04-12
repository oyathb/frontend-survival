# Development Environment

## JavaScript

🔳 install Node.js

> JavaScript로
>
> 브라우저 밖에서
>
> [서버](https://namu.wiki/w/%EC%84%9C%EB%B2%84)를 구축하는 등의 코드를 실행할 수 있게 해주는 런타임 환경

Node.js 쓰는 이유?

* JS
* asynchronous I/O - 하나의 이벤트가 완료되지 않아도 다음 이벤트를 처리할 수 있는 방식
  * 대용량의 I/O를 처리해야 하는 서비스에 적합
* NPM - Node.js 관련 패키지를 관리하는 툴 - 사용하려는 대부분의 모듈이 등록되어 있음

<pre><code><strong>// mac terminal에서
</strong><strong>brew install node
</strong></code></pre>

version 확인 ( v19.8.1)

```
node -v
```



🔳 install fnm

> Fast and simple Node.js version manager, built in Rust

```
brew install fnm
```



## TypeScript

🔳 install visual studio code

```
brew install visual-studio-code
```



🔳 작업 폴더 생성

```
mkdir my-app
cd my-app
```



🔳 npm 패키지

Node.js 관련 패키지를 관리할 수 있는 툴 (설치 삭제 업데이트 등)

```
// vsc terminal에서
npm init -y
```



🔳 .gitignore 파일 생성

git에 업로드 되지 않아야 하는 파일

node\_modules, dist 는 있어야 됨

```
touch .gitignore
```

{% embed url="https://github.com/github/gitignore/blob/main/Node.gitignore" %}
복붙
{% endembed %}



🔳 install TypeScript

```
npm i -D typescript
```

NPX

* npm의 일부분으로 패키지를 디렉토리에 설치하지 않고 실행
* npm으로 run하는 것보다 빠르고 메모리도 덜 먹음

tsconfig.json 파일 생성

```
npx tsc --init
```

jsx 찾아서 주석 지우고 아래처럼

```jsonc
"jsx": "preserve",
```



🔳 ESLint 설치

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
jest: true #추가
```



☑️ 테스팅 도구 설치

* jest와 swc를 같이 쓰는 것이 목표

\[npm i -D jest @types/jest @swc/core @swc/jest\
jest-environment-jsdom\
@testing-library/react @testing-library/jest-dom]

swc로 빌드해야 돼서 \[touch jest.config.js]

[https://github.com/ahastudio/CodingLife/blob/main/20220726/react/jest.config.js](https://github.com/ahastudio/CodingLife/blob/main/20220726/react/jest.config.js) 복붙

```javascript
'./jest.setup' #안씀 삭제
```

만약에빨간줄생기면??

\[npx eslint --fix .] 로 고칠 수 있음



☑️ install parcel

\[npm i -D parcel]





