# Fetch API & CORS

### Fetch API

[🔗https://ko.javascript.info/fetch](https://ko.javascript.info/fetch)

[🔗Fetch 사용하기](https://developer.mozilla.org/ko/docs/Web/API/Fetch\_API/Using\_Fetch)

* fetch = 가지고 오다
* 리소스를 가져오기 위해 사용
* Request/Response 오브젝트 제공
  * 클라이언트 -> 서버 : Request
  * 서버 -> 클라이언트 : Response
* fetch() 함수는 첫 번째 인자로 URL 두 번째 인자로 옵션 객체를 받고 Promise 객체를 반환한다
  * fetch(url, options)
  * options에는 HTTP Method 등을 작성 가능 (자세한 내용은 Fetch 사용하기 확인)
  * options에 아무것도 넘기지 않으면 요청은 GET 메서드로 진행되어 url로부터 콘텐츠가 다운로드 됨
* 기본적인 Fetch 요청

```
fetch(url) // (1)
  .then((response) => response.json()) // (2) JavaScript 객체로 변환. 응답을 json 형태로 파싱
  .then((data) => console.log(data));
```

(1) fetch 호출 시 반환받은 promise가 내장 클래스 Response의 인스턴스와 함께 fulfilled(이행) 상태가 됨

**!! 아직 body는 도착하지 않음 !!** 개발자는 헤더 보고 요청 성공 여부를 알게 됨

(2) 추가 메서드를 호출해 body를 받음 (여기에서는 response.json()으로 받음)

<figure><img src="../.gitbook/assets/스크린샷 2023-05-14 오후 4.32.17 (1).png" alt=""><figcaption></figcaption></figure>

async와 await 문법으로 Promise를 더 깔끔하게 사용할 수 있음

[🔗async와 await](https://ko.javascript.info/async-await)

<figure><img src="../.gitbook/assets/스크린샷 2023-05-14 오후 4.43.37.png" alt=""><figcaption></figcaption></figure>

.then().then() 이어지는 게 별로면 await 걸어주면 굳

```main.tsx
async function main() {
  
  const url = 'http://localhost:3000/restaurants';

  const response = await fetch(url);

  const data = await response.json();

  const { restaurants } = data;

  console.log(restaurants);
```

참고

[🔗TIL. fetch()와 Promise](https://velog.io/@seul06/TIL.-fetch)

### Promise

[🔗Promise](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global\_Objects/Promise)

* JavaScript에서 제공하는 비동기 처리에 사용되는 객체(object)
* Callback 함수로 비동기 처리 하면 n중for문 같은 Callback Hell이 만들어짐 .. 따라서 Promise 사용
* 비동기 메서드에서 동기 메서드처럼 반환할 수 있음. 다만 최종 결과를 반환하는 것이 아닌
* 미래의 어떤 시점 (비동기 처리가 완료된 시점 ??) 에 결과를 제공하겠다는 '약속'(Promise)을 반환
* 다음 중 하나의 상태를 가짐
  * pending(대기) : 이행하지도 거부하지도 않은 초기 상태
  * fulfilled(이행) : 연산이 성공적으로 완료됨
  * rejected(거부) : 연산이 실패함

<figure><img src="../.gitbook/assets/스크린샷 2023-05-14 오전 4.35.54.png" alt=""><figcaption></figcaption></figure>

### ReadableStream

* byte 데이터를 읽을 수 있는 스트림 제공
* Fetch API는 Response 객체의 body 속성을 통하여 ReadableStream의 구체적인 인스턴스를 제공

<figure><img src="../.gitbook/assets/스크린샷 2023-05-14 오후 9.32.53.png" alt=""><figcaption></figcaption></figure>

getReader() : ReadableStream의 메서드. reader를 만들고 stream을 잠근다. stream이 잠겨 있는 동안 다른 reader를 얻을 수 없다

read() : ReadableStreamDefaultReader의 메서드. stream 내부 대기열의 next chunk에 액세스를 제공한다
