# React Component

## 🥒

component hierarchy

### REST API 와 GraphQL

#### API

[🔗 reference) API란 무엇입니까?](https://aws.amazon.com/ko/what-is/api/)

* Application Programming Interface
  * Application : 소프트웨어
  * Interface : 두 Application 간의 서비스 계약
  * 계약 : 요청과 응답을 사용하여 서로 통신하는 방법을 정의
* **두 소프트웨어 구성 요소가 서로 통신할 수 있게 하는 매커니즘**
* ex) 어떤 시스템이 카카오톡 시스템의 로그인 기능을 사용하고 싶다면\
  카카오톡 로그인 API를 통해 통신
* API 문서 에는 개발자가 요청과 응답을 구성하는 방법에 대한 정보가 들어 있음



#### REST API

[🔗 reference) RESTful API란 무엇입니까?](https://aws.amazon.com/ko/what-is/restful-api/)

* Representational State Transfer
* API 작동 방식에 대해 조건을 부과하는 소프트웨어 아키텍쳐
* 구성
  * RESOURCE - URI
  * Verb - HTTP Method
  * Representations
* 어떻게 작동하는지?
  * client가 RESOURCE가 필요할 때 API를 사용하여 server에 접속
    1. client가 server에 요청을 전송
    2. server가 client를 인증하고 해당 요청을 수행할 수 있는 권한이 있는지 확인
    3. server가 요청을 수신하고 내부적으로 처리
    4. server가 client에 응답을 반환. 요청이 성공했는지 여부와 요청한 정보를 알려줌

<figure><img src="../.gitbook/assets/rest_api_works.png.webp" alt=""><figcaption></figcaption></figure>

[🔗 이미지 출처](https://www.altexsoft.com/blog/rest-api-design/)



* RESOURCE에 대한 행위는 HTTP Method로 표현한다
* HTTP Method (CRUD랑비슷)
  * POST : 등록
  * GET : 조회
  * PUT : 수정
  * DELETE : 삭제
* client request에 포함되는 것
  * 고유 리소스 식별자
    * server는 고유 리소스 식별자로 각 RESOURCE 식별
    * 일반적으로 URL 사용
  * HTTP Method
  * HTTP 헤더
    * client와 server 간에 교환되는 메타데이터
* REST API는 확장성, 유연성, 독립성에 이점이 있다
* REST 특징은 참고 문서 보자
