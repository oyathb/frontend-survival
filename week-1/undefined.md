# 개발 환경 세팅

## JavaScript

install Node.js

terminal에서 \[brew install node]&#x20;

version 확인 \[node -v] (v19.8.1)



install fnm

\[brew install fnm]



## TypeScript

install visual studio code

\[brew install visual-studio-code]



작업 폴더 만들기



\*npm패키지 사용할 수 있게

* Node.js의 패키지를 관리할 수 있는 도구

visual studio code terminal에서 \[npm init -y]



\*.gitignore 파일 만들기

* git에 업로드 되지 않아야 하는 파일
* node\_modules, dist 는 있어야 됨

\[touch .gitignore]

[https://github.com/github/gitignore/blob/main/Node.gitignore](https://github.com/github/gitignore/blob/main/Node.gitignore)



TypeScript 설치

\[npm i -D typescript]

\[npx tsc --init]

tsconfig.json 생김

jsx 찾아서 주석 지우고 아래처럼

```jsonc
"jsx": "preserve",
```



ESLint 설치



