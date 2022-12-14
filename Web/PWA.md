# PWA

## 정의

**프로그레시브 웹앱(Progressive Web Apps)** 은 Google I/O 2016에서 소개된 미래의 웹기술이며, **PWA**라고 줄여서 부르기도 한다.

### 구글에서 소개하는 PWA

> PWA는 최고의 웹과 최고의 앱을 결합한 경험이다. 브라우저를 통해 처음 방문한 사용자에게 유용하며, 설치가 필요하지 않다. 사용자가 PWA와 관계를 점진적으로 형성할수록 성능이 더욱 강력해 질 것이다. 느린 네트워크에서도 빠르게 로드되고, 관련된 푸시 알림을 전송한다. 모바일 앱처럼 전체 화면으로 로드되고, 홈 화면에 아이콘이 있다.
> 

쉽게 말하자면, PWA는 **모바일 앱**과 **웹 기술**의 장점을 결합한 웹앱이라고 볼 수 있다. 앱 수준과 같은 사용자 경험을 웹에서 제공하는 것이 목적. 

## 특징

확장성이 좋고, 깊이 있는 앱같은 웹을 만드는 것을 지향한다.

웹 주소만 있다면, 누구나 접근하여 사용이 가능하고 스마트폰의 저장공간을 잡아 먹지 않는다.

**서비스 작업자(Service Worker) API** : 웹앱의 중요한 부분을 캐싱하여 사용자가 다음에 열 때 빠르게 로딩할 수 있도록 도와준다.

→ 네트워크 환경이 좋지 않아도 빠르게 구동되며, 사용자에게 푸시 알림을 보낼 수도 있다. 

## **PWA 제공 기능**

- **프로그래시브** : 점진적 개선을 통해 작성되서 어떤 브라우저든 상관없이 모든 사용자에게 적합
- **반응형** : 데스크톱, 모바일, 테블릿 등 모든 폼 factor에 맞음
- **연결 독립적** : 서비스 워커를 사용해 오프라인에서도 작동이 가능함
- **안전** : HTTPS를 통해 제공이 되므로 스누핑이 차단되어 콘텐츠가 변조되지 않음
- **검색 가능** : W3C 매니페스트 및 서비스 워커 등록 범위 덕분에 '앱'으로 식별되어 검색이 가능함
- **재참여 가능** : 푸시 알림과 같은 기능을 통해 쉽게 재참여가 가능함

## **PWA 제작 기술**

### **manifest.json**

manifest.json은 설치할 때 아이콘은 무얼 사용하고 아이콘을 눌렀을때 접속할 페이지는 무엇인지, 배경색은 무슨색으로 할 것인지 등등..에 대한 설정파일이라고 보시면 됩니다.

### **service-worker**

Service Workers는 PWA의 핵심으로 캐싱은 어떻게 할 것인지 요청시 캐시를 먼저 보여줄지 웹서버를 통해서 먼저 보여줄지, push 등등에 대한 프로그래밍하는 기술입니다. PWA의 거의 80%에 해당하는 기술이라고 보시면 됩니다.

[https://www.youtube.com/watch?v=FEBkne7Nyu4](https://www.youtube.com/watch?v=FEBkne7Nyu4)
