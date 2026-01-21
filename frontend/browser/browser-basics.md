---
title: 브라우저
tags: []
created: ""
updated: ""
source: ""
status: draft
---
# 브라우저

# Broadcast Channel API

Broadcast Channel API는 **같은 origin의 여러 브라우저 컨텍스트(탭, 창, iframe, 워커) 간에 메시지를 주고받을 수 있게 해주는 웹 API**입니다. web platform interface로 역할함. 

- **특징:** 한 탭에서 '채널'에 메시지를 던지면, 다른 탭들이 그 채널을 구독하고 있다가 반응합니다. 웹소켓보다 훨씬 빠르고 서버 부하가 전혀 없습니다.

## 기본 개념

```jsx
// 채널 생성
const channel = new BroadcastChannel('my_channel');

// 메시지 수신
channel.onmessage = (event) => {
  console.log('받은 메시지:', event.data);
};

// 메시지 전송 (같은 채널을 구독한 모든 컨텍스트에 전달)
channel.postMessage('안녕하세요!');

// 채널 닫기
channel.close();
```

## 주요 특징

**동작 방식**: 같은 origin(프로토콜, 도메인, 포트가 동일)에서 같은 이름의 채널을 생성한 모든 컨텍스트가 메시지를 공유합니다. 메시지를 보낸 본인을 제외한 나머지 구독자들이 메시지를 받습니다.

**사용 예시**:

- 여러 탭에서 로그인/로그아웃 상태 동기화
- 탭 간 데이터 실시간 공유
- 한 탭에서의 변경사항을 다른 탭에 즉시 반영

## 웹소켓과의 관계

Broadcast Channel API와 웹소켓은 **완전히 다른 목적**을 가진 기술입니다:

### Broadcast Channel API

- **클라이언트 ↔ 클라이언트** 통신 (같은 브라우저 내)
- 서버 필요 없음
- 같은 origin의 브라우저 컨텍스트 간에만 동작
- 로컬 통신 (네트워크 사용 안 함)

### WebSocket

- **클라이언트 ↔ 서버** 통신
- 서버가 필수
- 서버를 통해 다른 사용자들과 통신 가능
- 네트워크를 통한 실시간 양방향 통신

---
## Merged from 개발 관련 지식/웹 브라우저 2efcee38e89a8073813dde1e7469ce69.md

# 웹 브라우저

[Web platform interface ](%EC%9B%B9%20%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80/Web%20platform%20interface%202efcee38e89a803f96c0f8abc6454eaa.md)