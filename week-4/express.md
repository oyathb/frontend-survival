# Express

### Express

[🔗https://expressjs.com/ko/](https://expressjs.com/ko/)

* Node.js를 위한 웹 프레임워크
  * 웹 프레임워크란? 웹 서버를 구축할 때 Node.js로 하나하나 짜면 힘드니까 웹 프레임워크로 간편하게
* Node.js로 웹 서버를 구축할 때 가장 많이 사용하는 프레임워크

#### Node.js

* "Run JavaScript Everywhere"
* Node.js is a free, open-sourced, cross-platform JavaScript run-time environment that lets developers write command line tools and server-side scripts outside of a browser.
  * JavaScript로 서버를 구축하는 등의 서버 쪽 작업을 가능하게 하는 런타임 시스템
* asynchronous I/O - 하나의 이벤트가 완료되지 않아도(결과를받지않아도) 다음 이벤트를 처리할 수 있는 방식
  * 대용량의 I/O를 처리해야 하는 서비스에 적합
* NPM
  * Node.js 관련 패키지를 관리하는 툴
  * 사용하려는 대부분의 모듈이 등록되어 있음

### URL 구조

#### URL

* Uniform Resource Locater
* 인터넷에서 실제 네트워크 경로를 표시하기 위해 표준화된 논리 주소 (인터넷상의파일주소)

```
https:// //protocol
search.naver.com/ //Domain
search.naver //path
?where=image&sm=tab_jum&query=%ED%8E%AD%EA%B7%84 //parameter(query string)
#top //Fragment
```

* protocol
  * 컴퓨터와 컴퓨터 사이, 또는 한 장치와 다른 장치 사이에서 데이터를 원활히 주고받기 위하여 약속한 여러 가지 규약
  * 서버에 접속할 때 어떤 방식으로 통신할지 정의
  * HTTP
    * HyperText Transfer Protocol
    * World Wide Web 에서 HyperText 문서를 주고받기 위해 사용되는 프로토콜
  * HTTPS
    * HTTP + Secure
    * HTTP 보안 강화 버전
* domain
  * IP 주소 <- 외우기 힘드니까 asdf.com 형식으로 만든 것
* path
  * /
  * 파일의 경로를 가리킨다
* parameter
  * 데이터가 전달된다
  * ? 로 시작
  * key(파라미터의이름)=value(파라미터의값) 형태
  * 여러 개면 & 으로 구분
* fragment
  * 특정 요소 지시
  * 예시에 #top은 내가 임의로 추가한 건데 맨 위가 뜨게 하는 것을 의도함

### REST API & HTTP Method(CRUD)

[🔗week 3 참고](https://github.com/oyathb/frontend-survival/blob/410912946f3edd96932fc7e0529506b460e8e143/week-3/react-component.md)
