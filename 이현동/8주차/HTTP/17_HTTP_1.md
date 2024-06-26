## HTTP/0.9

- TCP/IP 링크 위에서 동작하는 ASCII 프로토콜
- Get 메서드만 지원
- HTTP 헤더 X, 상태 코드 X
- 응답도 HTML 파일 자체만 보내줌
- 서버와 클라이언트 간의 연결은 모든 요청 후에 닫힘(closed)

## HTTP/1.0

- 기본적인 HTTP 메서드와 요청/응답 헤더 추가
- HTTP 버전 정보가 각 요청 사이내로 전송되기 시작 (HTTP/1.0 이 GET 라인에 붙은 형태로)
- 상태 코드(status code)가  응답의 시작 부분에 붙어 전송되어, 브라우저가 요청에 대한 성공과 실패를 알 수 있고 그 결과에 대한 동작을 할 수 있게 되었다. (특정 방법으로 로컬 캐시를 갱신하거나 ..등)
- 응답 헤더의 Content-Type 덕분에 HTML 파일 형식 외에 다른 문서들을 전송하는 기능이 추가되었다.
- 단기커넥션 : connection 하나당 1 Request & 1 Response 처리 가능

### 문제점

- 1 Request & 1 response
- 매번 새로운 연결로 성능 저하
- 매번 새로운 연결로 서버 부하 비용 증가

## HTTP/1.1

- HTTP 1.1 은 현재 가장 많이 사용되는 프로토콜 버전.
- HTTP를 학습할때 배우는 기본 베이스 지식이기도 함
- 지속 연결(Persistent connection) : 지정한 timeout 동안 연속적인 요청 사이에 커넥션을 닫지 않음. 기존 연결에 대해서 handshake 생략 가능
- 파이프 라이닝(pipelining) : 이전 요청에 대한 응답이 완전히 전송되기 전에 다음 전송을 가능하게 하여,  여러 요청을 연속적으로 보내 그 순서에 맞춰 응답을 받는 방식으로 지연 시간을 줄이는 방식 (불안정하여 사장됨)
- HOST 헤더 추가 : 동일 IP 주소에 다른 도메인을 호스트하는 기능 가능
- Chunk Encoding 전송 : 응답 조각
- 바이트 범위 요청
- 캐시 제어 메커니즘 도입

### 문제점

파이프 라이닝은 보낸 요청 순서대로 응답을 받아야하는 규칙 부분에서 문제가 생기게 된다.

요청하는 데이터의 크기는 제각각 이기 때문에, 첫번째로 요청한 데이터가 용량이 큰 데이터라면, 두번째, 세번째 데이터가 아무리 빨리 처리되어도 우선순위 원칙에 따라 첫번째 데이터의 응답 속도가 늦어지면 다음 데이터 응답속도도 같이 늦어지게 된다.
