# HTTP Overhead란?
### 오버헤드란?

- 오버헤드가 됬다라는 말은, 처리 시간 및 메모리등이 추가적으로 사용되는 현상을 말한다

### HTTP(Protocol) 오버헤드

- 네트워크를 통해 대상으로 라우팅 되는 데이터와 함께 전송되어야 하는 정보를 말하며, 올바른 대상에 도달하기 위해 전송중인 데이터에 추가로 보내지는 정보
- ‘원하는 대상을 정확히 찾아내어’ 라는 간접적인 처리를 프로토콜 오버헤드를 통해 하는것이다
- 프로토콜 오버헤드가 있기에 정보 전송의 신뢰성을 높일 수 있고 시스템을 안정적으로 운용할 수 있게된다
- 통상 패킷/프레임 등의 선두에 있는 헤더(Header)상에 위치하기에 Header라고도 한다