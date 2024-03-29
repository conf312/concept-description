### RTMP(Real-Time Messaging Protocol)
Adobe Systems에서 개발한 멀티미디어 데이터 및 상호작용을 전송하기 위한 프로토콜입니다. RTMP는 스트리밍 미디어를 전송하는 데 주로 사용되며, 주로 Adobe Flash 플랫폼에서 사용되었습니다.

RTMP는 클라이언트와 서버 간에 실시간 데이터를 교환하기 위한 TCP 기반 프로토콜입니다. RTMP를 사용하여 오디오, 비디오, 텍스트 및 기타 데이터를 스트리밍할 수 있습니다. 이 프로토콜은 비디오 및 오디오 스트리밍, 게임, 실시간 채팅 등과 같은 다양한 멀티미디어 응용 프로그램에 사용됩니다.

RTMP는 주로 스트리밍 서비스에서 사용되었지만, 최근에는 HTTP 기반의 스트리밍 프로토콜인 HLS(HTTP Live Streaming) 및 DASH(Dynamic Adaptive Streaming over HTTP)와 같은 대안이 더 인기를 얻고 있습니다.

### 구조
RTMP 프로토콜은 클라이언트와 서버 간에 실시간 데이터를 주고받기 위한 여러 가지 메시지와 명령을 정의하는 구조를 갖고 있습니다. 일반적으로 RTMP는 TCP를 기반으로 동작하며, 클라이언트와 서버 간에 연결이 설정되면 데이터 스트림이 주고받아집니다.

RTMP는 크게 두 가지 형태로 사용됩니다. **첫째, 실시간 데이터 전송을 위한 "라이브"** 방식이 있고, **둘째, 데이터를 저장하고 재생하는 "녹화"** 방식이 있습니다.

라이브 방식에서는 클라이언트는 RTMP 스트림 서버로 비디오, 오디오 및 기타 데이터를 보낼 수 있습니다. 이러한 데이터는 RTMP 패킷으로 분할되어 스트림으로 전송됩니다. 서버는 이러한 패킷을 수신하고 디코딩하여 실시간으로 스트리밍 데이터를 처리하고 다른 클라이언트에 전달합니다.

녹화 방식에서는 클라이언트가 RTMP 서버로 데이터를 업로드하면, 서버는 해당 데이터를 저장하고 필요할 때 클라이언트에게 제공합니다. 이는 비디오 플랫폼이나 온디맨드 스트리밍 서비스에서 사용되는 방식입니다.

RTMP는 여러 가지 유형의 메시지와 명령을 지원합니다. 일반적으로 사용되는 메시지 유형으로는 오디오, 비디오, 데이터 및 제어 메시지가 있습니다. 오디오 메시지는 오디오 데이터를 전송하고, 비디오 메시지는 비디오 데이터를 전송합니다. 데이터 메시지는 클라이언트와 서버 간에 사용자 정의 데이터를 전송하는 데 사용됩니다. 제어 메시지는 연결 제어, 스트림 제어, 대역폭 제어 등과 같은 프로토콜 수준의 제어 기능을 수행합니다.

이러한 구조와 메시지 유형을 통해 RTMP는 실시간 멀티미디어 스트리밍과 상호작용을 위한 효율적인 프로토콜을 제공합니다.
