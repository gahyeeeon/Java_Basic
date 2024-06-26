# 웹 브라우저의 Cookie 헤더 다루기

# 웹 브라우저의 Cookie 란?

- 웹브라우저에서 쿠키(Cookie)란 서버가 사용자의 웹 브라우저에 전송하는 작은 데이터 조각으로, `key=value` 형식의 문자열 데이터 묶음이다.
- 브라우저는 이 문자열 데이터 조각들을 저장해놓았다가 동일한 서버에 재 요청시 쿠키 데이터를 전송할 수 있다.
- HTTP 프로토콜은 기본적으로 StatelessVisit Website 한 속성을 가지고 있기 때문에, **서버와 클라이언트 간의 연결 유지를 구현**하기 위해서 서로를 인식할수 있는 식별 d데이터가 필요해졌고 그것이 쿠키 데이터 조각이라고 보면 된다.

### 쿠키의 활용도

1. 세션 관리(Session Management) : 서버 간 일시적인 연결 유지에 이용 (로그인)
- 이처럼 쿠키는 활용도가 여러가지가 있지만 명확한 한계점을 가지고 있다.

### 쿠키는 브라우저가 관리

- 쿠키는 웹사이트 도메인에 따라 또는 웹사이트 페이지경로에 따라 저장되도록 각기 다르게 지정할 수 있다.

### 쿠키의 흐름 (로그인 과정)

1. 로그인(/login) 화면에서 클라이언트가 username 과 password를 입력하고 서버에 제출(요청) 한다.

## HTTP Cookie 헤더

### Cookie (요청 헤더)

- HTTP 요청 시 클라이언트에서 서버로 전달하는 쿠키 헤더

### Set-Cookie (응답 헤더)

- 서버에서 클라이언트로 전달하는 쿠키 헤더

### 쿠키의 저장 방식

- 쿠키는 `key=value` 형태로 저장되는 문자열로서 여러개의 데이터를 콤마(,)로 열거하여 저장해 구분한다.

## HTTP Cookie 파라미터

- 쿠키는 key=value 형태로 이루어진 단순한 문자열이지만, 각 쿠키값에 적용되는 쿠키의 유효 기간이나 도메인 설정 등을 파라미터를 통해 추가할 수 있다.
- 이 파라미터들은 클라이언트(브라우저)에 적용되는 속성들이며, 서버에서 응답할때 설정하여 응답 할 수도 있다.
- 크롬 브라우저의 개발자 도구에서는 별도의 쿠키 관리 탭을 이용해 파라미터를 조작할 수도 있다.

| 필드 속성 | 설명 |
| --- | --- |
| NAME=VALUE | 쿠키에 부여된 이름과 값 (필수) |
| Expires=DATE | 쿠키 유효 기한 |
| Path=PATH | 쿠키 적용 대상이 되는 디렉토리 |
| Domain=도메인명 | 쿠키 적용 대상이 되는 도메인 명 |
| Secure | HTTPS로 통신하는 경우에만 쿠키를 송신 |
| HttpOnly | 쿠키를 자바스크립트에서 액세스 하지 못하도록 제한 |
| SameSite | 크로스 사이트(Cross-site)로 전송하는 요청의 경우 서드 파티 쿠키의 전송에 제한 |

### 쿠키 생명 주기

- `expires` 와 `max`-age 를 통해 만료일을 설정할 수 있다.
- `expires=Sat`, `26-Dec-2020 04:39:21 GMT`
    - 구체적인 날짜를 명시
    - 만료일이 지나면 쿠키는 삭제된다.
- `max-age=3600`
    - 쿠키 유효 시간을 명시 (초 단위)
    - 만일 0이나 음수로 지정할 경우 쿠키는 삭제된다.
- 만일 만료 날짜를 생략하면 브라우저 종료시 까지만 유지된다. 이를 세션 쿠키라 부른다.
- 만료 날짜를 입력하면 해당 날짜까지 유지된다. 이를 영속 쿠키라 부른다.

### 쿠키 Path

- 쿠키에 경로를 설정하면, 해당 페이지 경로에서만 쿠키 사용 접근이 가능하다.
- 해당 경로의 하위 경로까지 모두 포함한다. 그래서 루트 경로(/) 로 설정하면 모든 경로에 쿠키가 유효하다는 뜻이 된다.
- `path=/home` 지정
    - /home/level1 → 접근 가능
    - /home/level1/level2 → 접근 가능
    - /hello → 접근불가능 (다른 경로)
- path를 입력하지 않으면 루트 경로로 자동 입력 된다.
- 단, 쿠키의 범위를 좁게 잡을 수록 보안에는 좋다.

### 쿠키 Domain

- 쿠키에 도메인을 설정하면, 해당 도메인 페이지에서만 쿠키 사용 접근이 가능하다.
- 해당 도메인의 서브 도메인까지 모두 포함한다.
- [`domain=example.org`](http://domain=example.org/) 지정
    - .example.org 형태로 저장 (도메인 앞에 점은 서브 도메인도 허용하겠다는 뜻이다)
    - [example.org](http://example.org/) → 쿠키 접근 가능
    - [www.example.org](http://www.example.org/) → 쿠키 접근 가능
- 도메인을 생략하면 현재 문서 기준 도메인으로만 적용된다.
    - 즉, 위 사진과 같이 .inpa.tistory.com 이 아닌 점이 생략된 [inpa.tistory.com](http://inpa.tistory.com/) 으로 저장되어 서브 도메인을 허용하지 않는다.
- 만일 현재 도메인에서 설정한 쿠키를 퍼스트 파티 쿠키(First-party cokkies) 라 하고, 다른 도메인으로 설정된 쿠키를 서드 파티 쿠키(Third-party cokkies)라 한다.

### 서드 파티 쿠키

- 쿠키 도메인 파라미터를 전혀 다른 도메인으로 설정된 쿠키를 서드 파티 쿠키(Third-party Cookie)라고 불리운다.
- 서드 파티 쿠키는 구글 애드센스와 같은 스크립트만 등록되어 있다면 여러 개의 사이트에 쿠키를 생성할 수 있다.
- 예를 들어 사용자가 Example 사이트에 방문해서 로그인을 했다면 다음 로그인할 때 정보를 다시 입력해야 하는 번거로움을 줄일 수 있도록 Example 사이트에서 사용자의 웹브라우저로 Cookie A가 부여된다.
- 그런데 이 웹페이지는 우측에 배너 광고가 표시되는데 이 배너 광고는 Adserver 사이트에서 전달되고 있다고 한다.
- 이 배너를 통해 사용자의 웹브라우저에 다른 도메인 파라미터를 갖는 Cookie B 가 부여되게 된다.
- 즉, 사용자가 방문하고 있는 도메인에서 발행되는 Cookie A를 퍼스트 파티 쿠키(First-party Cookie) 이며, 타 도메인에서 발행되는 Cookie B를 서드 파티 쿠키(Third-party Cookie)라고 하는 것이다.
- 이 서드 파티 쿠키는 주로 타깃 마케팅 광고 목적으로 사용된다. 예를들어 신발 쇼핑몰 사이트를 자주 방문하게 되면 쿠키가 저장되게 되고 구글 애드센스가 이를 가져가 다른 사이트에서의 배너 광고에서 신발 광고가 화면에 나타나는 것이 서드 파티 쿠키를 이용한 원리라고 보면 된다.
### 쿠키 Secure

- 활성화하면, HTTPS 사용 시에만 쿠키 정보 전달
- 미적용 시에는 HTTP, HTTPS 구분하지 않음

## 쿠키 HttpOnly

- 자바스크립트에서 쿠키 사용 접근을 제한한다.
- 그래서 해커가 자바스크립트로 쿠키를 탈취할수 없어, XSS 공격을 방지할 수 있다.

### 자바스크립트로 쿠키 접근 방지

- 쿠키는 꼭 서버에서 만들어 반환하여야 클라이언트가 사용할수 있는것이 아닌 얼마든지 클라이언트에서도 만들어 사용 할 수 있다. 웹브라우저의 개발자 도구를 통해 만들수도 있으며, 자바스크립트로도 직접 쿠키를 만들어 서버에 보낼수도 있다.

```jsx
document.cookie = "user=John; path=/; expires=Tue, 19 Jan 2038 03:14:07 GMT";
alert(document.cookie); // 모든 쿠키 보여주기
```

- 서버로부터 test, test2, test3 쿠키가 응답되었는데, test3 쿠키만 `httpOnly` 속성이 적용되어 있다고 한다.
- 브라우저에서 자바스크립트로 쿠키를 나열하는 코드 `document.cookie` 를 실행해보면 test3 부분만 빠진채 열거됨을 볼 수 있다.

```jsx
console.log(document.cookie);
```

## 쿠키 SameSite

- SameSite 속성은 서드 파티 쿠키의 보안적 문제를 해결하기 위해 만들어진 기술이다.
- XSRF, CSRF 공격을 방지할 수 있다.
- 요청 도메인과 쿠키 정보 내의 도메인이 다른크로스 사이트(Cross-site)로 전송하는 요청에 대해서 제한을 둘 수 있다.

### SameSite 3가지 속성

- 파라미터 값으로 None , Lax , Strict 세 가지 종류를 선택할 수 있고, 각각 동작하는 방식이 다르다.
- None : 쿠키는 크로스 사이트 요청의 경우에도 항상 전송한다. 따라서 보안적으로 SameSite 적용을 하지 않은 쿠키와 다름이 없다.
- Strict : 쿠키는 크로스 사이트 요청에는 항상 전송되지 않는다. 가장 보수적인 정책.
- Lax : Strict에 비해 상대적으로 느슨한 속성. 몇 가지 예외적인 요청에는 전송하도록 한다.

### SameSite Lax 예외 기준

- `SameSite=Lax` 일때 쿠키가 예외적으로 전송되는 경우는 다음과 같다.사용자가 <a> 태크를 클릭해서 302 리다이텍트를 하거나, 자바스크립트로 `window.location.replace` 등으로 인해 자동으로 이루어지는 이동에선 서드 파티 쿠키가 전송된다.
- 하지만 <iframe> 태그나 <img> 태그를 문서에 삽입함으로서 발생하는 http 요청은 전송을 제한한다. 또한 GET 요청에 대해선 쿠키가 전송되지만, POST 나 DELELTE 요청은 제한된다.참고로 SameSite 파라미터의 보안 속성을 서드 파티 쿠키에 한하는 것이며, 퍼스트 파티 쿠키는 Lax나 Strict여도 전송된다.

### SameSite None 주의점

- 크롬 브라우저는 SameSite 값으로 None을 사용하려면 해당 쿠키는 반드시 Secure 가 설정된 쿠키여야 한다는 정책이 있다. 만일 크롬에서 위 정책을 지키지않고 서버에서 Set-Cookie를 하게 되면 쿠키 자체가 제대로 설정되지 않게 된다.